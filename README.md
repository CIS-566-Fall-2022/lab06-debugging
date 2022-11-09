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

# Actual Submission
- Only San Jewell worked on this
- link is here: https://www.shadertoy.com/view/mdS3Rt
- I found 4/5 bugs (I think, though it looks pretty good), all of them are marked in the shadertoy as well
  - line 102, fixed syntax error because it was obvious and the compiler told me
  - line 105, changed uv to uv2. I found this because it seemed very obvious that the entire rendering was shifted in screen space, so I looked first at the uv2 calculation and it seemed right, and then I saw it was not used.
  - line 11, changed the resolution x to y. This one was a bit of luck, I did notice that the screen looked a little stretched but I wasn't actually sure it was a bug. But then after looking over everything for a few minutes I managed to see this in the third pass. Very sneaky
  - line 75, the main issue with pretty much everything not working. I didn't immediately have on my mind how the reflection algorithm worked so I spent a lot of time just trying to add parenthesis around operations and scan for any more variable mis usages. This didn't work so I started going through line by line and actually trying to understand what was being done at each step. Eventually I looked up a similar algorithm description and I saw the reflection used in it and I realized that there the wrong variable was used there. 
  
  I think it looks pretty good, so either I accidentally fixed another bug while messing around with a bunch of the code, or I'm just missing what the final issue is. 
