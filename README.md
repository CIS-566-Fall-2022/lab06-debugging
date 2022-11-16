# lab06-debugging

## Submission
### Team
Sakshi & Megan

[Solution Link](https://www.shadertoy.com/view/ddBGRt)

### Bugs

1. **Compile time Error**

    Line 97: Syntax error vec2 (not vec)
    
    Compile time error that was present from the beginning. Easy to spot, Shadertoy indicates such errors and will not run untill they are solved.
   
2. **Aspect Ratio**

    Line 11: Correct the aspect ratio (iResolution.x / iResolution.y)
    
    The spheres were not uniform and stretched along the x direction. Since the UV calculation looked right, we looked at the ray cast code and found that the aspect ratio was being calculated incorrectly.

3. **Incorrect Argument**
  
    Line 100: Pass in the correct UVs (uv2)
    
    The image was centered at the lower left corner, so we suspected something with the UVs was still incorrect. This one took me a while and I went back to verify the ray cast code (even pulled up Adam's raycasting slides :P). Finally Megan found out that the uvs being input to the raycast funtion were incorrect.
    
4. **Raycast Distance**
    
    Line 18: Increase the max distance for ray marching (was 64, changed to 300)
    
    The edges of the ground near where they met the spheres were warped and those artifacts were similar to what we've seen in the class.
    
5. **Ray Direction**
    
    Line 75: Fixed ray calculation for specular reflection
    
    The sphere reflection looked off and that made us look into the code handling reflection. I had to look up the parameters for the reflect function that made it clear that the 1st expected input parameter is ray direction and not ray origin

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
