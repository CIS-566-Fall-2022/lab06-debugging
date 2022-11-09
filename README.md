# bugs
- bug 1: compile error. uv2 was type vec and not vec2
- bug 2: incorrect inputs to raycast() in mainImage().  uv was inputted and not uv2.
- bug 3: improper resolution. the spheres were smooshed. after creating uv2 (mapping from [0,1] to [-1,-1]), 
         we need to multiply uv2.x by iresX/iresY. this is because when we start with the uv (uv = fragCordXY/resXY), we could have any mix of x and y lengths. if x >> y then the y domain will look very smooshed, and so on. so we need to preserve the aspect ratio. in total we have 
         
    * fragCoord : [[0, resX], [0, resY]]
    * * uv = fragCordXY/resXY
    * uv: [[0:1], [0:1]]
    * * uv2 = 2. * uv - vec2(1.)
    * * uv2 = 2. * ((fcX/resX), (fcY/resY)) - (1., 1.)
    * *  *(this was what we added to fix the bug!)* --> uv2.x *= resX/resY 
    * * uv2 = 2. * ((fcX/resY), (fcY/resY)) - (1., 1.)   
    
    ^ now that both components of uv2 have the same denominator, the aspect ratio is preserved
    
    
- bug 4: the reflections were off.
  <p align = "center">
  <p align = "left">**before**</p> 
  <p align = "right">**after**</p>
</p>

  <p align="center">
  <img height="200" alt="image" src="https://user-images.githubusercontent.com/60904107/200894768-60a7e9ef-e2c1-446b-8456-136956a63dd3.png">
  <img height="200"  alt="image" src="https://user-images.githubusercontent.com/60904107/200895226-0bb1eb29-645f-4077-8adb-49debbc77903.png">
</p>

  ** Initially i had thought that the error was in computeMaterial, but this just computes the geometry and color of the hit object based on a point and a direction. The reflection error was in the sdf3D() fucntion. after we get the interseciton point along our direction **dir** (which is from the eye to the pixel), we want to call the raymarch function with a reflected direction. on line 75, the bug was *dir = reflect(eye, nor)*; when in fact, we want to reflect dir along the normal. so, **dir = reflect(dir, nor)**. In march(), the raymarching function, the inputs are march(origin = isect + dir * 0.01, dir = dir, t = t, hitObj = hitObj). this allows us to find the color of the reflected object, since we raymarch along the reflected direction. once we get that hidObj id, we can use computeMaterial to get this reflected color (specReflCol in code). The final color is a mix of the original object color, the original times the specRefColor, using "fresnel".
  
 bug 5: idk, didn't have time

    
    
    
# -   



# lab06-debugging

# Setup 

Create a [Shadertoy account](https://www.shadertoy.com/). Either fork this shadertoy, or create a new shadertoy and copy the code from the [Debugging Puzzle](https://www.shadertoy.com/view/flGfRc).

Let's practice debugging! We have a broken shader. It should produce output that looks like this:
[Unbelievably beautiful shader](https://user-images.githubusercontent.com/1758825/200729570-8e10a37a-345d-4aff-8eff-6baf54a32a40.webm)

It don't do that. Correct THREE of the FIVE bugs that are messing up the output. You are STRONGLY ENCOURAGED to work with a partner and pair program to force you to talk about your debugging thought process out loud.

Extra credit if you can find all FIVE bugs.

# Submission
- Create a pull request to this repository
- In the README, include the names of both your team members
- In the README, create a link to your shader toy solution with the bugs corrected
- In the README, describe each bug you found and include a sentence about HOW you found it.
- Make sure all three of your shadertoys are set to UNLISTED or PUBLIC (so we can see them!)
