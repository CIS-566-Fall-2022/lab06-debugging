Submission: 

https://www.shadertoy.com/view/msBGzt

Collaborators: None

Bug number 1:

Spheres look deformed. Cause: aspect ratio was incorrect in the projection part of the raycast function!

Bug number 2:

Spheres are off center, rotation is weird. Cause: Incorrect uv coordinates sent! We calculated NDC uv2, but never actually inputted it into the raycast function. This would explain the offset.

Bug number 3:

Specular reflection missing. I knew that the bug would have to be inside sdf3d. It turns out we were reflecting eye instead of dir! Replacing eye with dir fixed this bug.

Bug number 0:

Compiler error- fixed by adding type declaration vec2 to uv2!

Bug number 5:

Fixed floor artifacts by increasing number of iterations of march! This issue happens to rays that get very close but dont actually intersect objects in sphere tracing, since many iterations are used up by very small increments forward, resulting in no intersection if the number of iterations isnt high enough.

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
