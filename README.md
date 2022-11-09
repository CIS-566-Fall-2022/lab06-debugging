# lab06-debugging

# Submission

Name: Megan Reddy

Partner: Sakshi Rathore

Shadertoy link: https://www.shadertoy.com/view/msSGRt

#### Bug 1. Compile Error
When I loaded the Shadertoy, there was a red compile error on line 97. This was because the type name was incomplete and showed `vec` instead of `vec2.` 

#### Bug 2. Aspect Ratio
After fixing the compile error,  I noticed that the spheres were stretched. This led me to believe either the uv coordinate was wrong, or the ray direction computation was wrong. After verifying that the uv computation looked okay, I looked inside of the raycast function and saw that the aspect ratio was being calculated as `iResolution.x / iResolution.x` instead of `iResolution.x / iResolution.y`.

#### Bug 3. Wrong Argument
The image looked as if it was centered at the bottom left hand corner of the screen, so I went back to check the uv computation. It turns out that the uv computation was correct, but the wrong variable was being passed into the raycast function. I changed the argument from `uv` to `uv2` on line 100.

#### Bug 4. Ray Marching Artifacts
I noticed some artifacts around the edges of the spheres, which reminded me of similar things I saw while implementing the SDF homework. To fix this, I went to the ray march function and changed the total number of ray steps from `64` to `256`.

#### Bug 5. Reflection Direction
Since the spheres had no reflection, I immediately looked inside the `sdf3D` function for the reflection code. The incident ray direction passed into the `reflect` function was incorrect; it should be the incoming ray direction `dir` and not the eye position. 

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
