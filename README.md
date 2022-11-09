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

Partner: Rhuta Joshi
Shader toy link: https://www.shadertoy.com/view/dsBGRd

We methodiccally followed the flow of the code. We started with the mainImage function and looked at the inputs calculated.
Looking at the mainImage function we could clearly see the compiler error cause by uv2 not being initialized as a vec2 but just vec instead.
ERROR1: uv2 -> vec instead of vec2

Then we looked at where this was passed into the function raycast and noticed that uv2 was never used instead uv was passed in instead.
ERROR2: uv is used instead of uv2 in raycast function inputs

We then followed raycast to it's definition where looked at what was being done in the function. We knew something was wrong because the screen was being stretched so that the spheres were not sphereical. There we noticed that iResolution.y is never used just iResolution.x which would distort the screen.
ERROR3: used iResolution.x/iResolution.x instead of iResolution.x/iResolution.y

From there we figured that our screen size looked good and everything was proportionally correct. Now we needed to solved why all our objects were not reflecting the other objects but just their own color. So we went to look at where specular reflection is applied to all surfaces. Now we noticed that to get the correct relection direction so that we can find the other object that should be reflected in the one we are looking at we need to reflect the direction vector aboutt the normal but instead we are reflecting the eye about the normal.
ERROR4: was reflecting eye about nor to calculate the new direction instead of direction about normal.

Finally we figured out by looking at the image that there was space around the edges of the sphere sdf. I remembered having this error in my sdf hw where the edges had space between objects and the way I had solved that was by updating the max ray steps used.
ERROR 5: Increase Max Ray steps


