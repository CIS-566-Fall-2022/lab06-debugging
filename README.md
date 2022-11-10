# lab06-debugging

[Shadertoy]( https://www.shadertoy.com/view/mdj3Rt)

Name: Yilin Liu

# Bugs

- Bug 1: changed "vec" to "vec2" in mainImage(); -- Found by compiling.

- Bug 2: changed "uv" to "uv2" in mainImage() -- found uv2 was derived from uv but unused.

- Bug 3: changed "eye" to "dir" in sdf3D() -- the reflection was clearly not corrected so I looked into the reflect function. The first input should be the incident light, aka incoming light, which should take "dir" as the input. 

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
