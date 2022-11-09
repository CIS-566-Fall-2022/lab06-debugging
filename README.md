# lab06-debugging

# Group
Yuqi Zhang, Dongying Liu, Wenqing Wang

# Setup 

Create a [Shadertoy account](https://www.shadertoy.com/). Either fork this shadertoy, or create a new shadertoy and copy the code from the [Debugging Puzzle](https://www.shadertoy.com/view/flGfRc).

Let's practice debugging! We have a broken shader. It should produce output that looks like this:
[Unbelievably beautiful shader](https://user-images.githubusercontent.com/1758825/200729570-8e10a37a-345d-4aff-8eff-6baf54a32a40.webm)

It don't do that. Correct THREE of the FIVE bugs that are messing up the output. You are STRONGLY ENCOURAGED to work with a partner and pair program to force you to talk about your debugging thought process out loud.

Extra credit if you can find all FIVE bugs.

1 . https://www.shadertoy.com/view/ddS3zt
I find the bug that it should be vec2 uv2 = 2.0 * uv - vec2(1.0); I need a "2" after "vec". I find that bug because it has a compile error that pointing to this spot. 

2. https://www.shadertoy.com/view/ddB3zt
I find the bug that I should pass the uv2 to the raycast function. I find that bug because I find the camera position is not right. I checked the iResolution and find that is correct. I checked raycast function and the input of the raycast. I find that I need to pass the uv2 instead of uv. 

3. https://www.shadertoy.com/view/msB3zt
The sphere is not look correct. It looks like Ellipsoid at this point. I find the bug that in raycast function, When we calculating the H vec, we should use iResolution.x / iResolution.y instead of iResolution.x / iResolution.x. 

4. https://www.shadertoy.com/view/msSGRd
In the scene, my teammate noticed that there is a gap between the sphere and the background. We checked again the march function and we noticed that the iteration happens 64 times. We increased the iteration number and fixed this bug. 

5. https://www.shadertoy.com/view/ddBGRd
We noticed the specular problem not solved, we checked the line 74 because there is a comment that Specular reflection applied to all surfaces. We checked the specular function, we should pass in the dir, the vector, instead of eye, the eye position. 
# Submission
- Create a pull request to this repository
- In the README, include the names of both your team members
- In the README, create a link to your shader toy solution with the bugs corrected
- In the README, describe each bug you found and include a sentence about HOW you found it.
- Make sure all three of your shadertoys are set to UNLISTED or PUBLIC (so we can see them!)
