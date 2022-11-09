Team Members: just me

Shadertoy: https://www.shadertoy.com/view/ddS3Rt

Bugs:

Pasted my comments on the bugs from the shadertoy here

// BUG #1: previously this said vec not vec2, causing a compiler error
// the compile error was pretty obvious to find
// from the values on the right side of the equals sign I could see it was meant to be a vec2

// BUG #2: this wasn't using the -1 to 1 uv2 and was instead using the origin 0 to 1 uv
// after correcting bug 1, I noticed uv2 wasn't used anywhere, so on a hunch I changed it here

// BUG #3: this was originally dividing by iResolution.x, not iResolution.y, causing warping
// noticing the spheres seemed to be stretched clued me into the fact that there was probably
// an issue accounting for screen dimensions/resolution
    
// BUG #4: this was previously reflect(eye, nor), so instead of view direction it was eye position which was messing up the reflections
// I saw that the reflections seemed to look very flat, which guided me to inspect the reflection code more

// BUG #5: raised raymarch max steps to get rid of artifacts around sphere edges
// Adam pointed me to the visual artifact, and I'd seen it before in other SDF projects 
// so I knew that the raymarch steps were too lot

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
