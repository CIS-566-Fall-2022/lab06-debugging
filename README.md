# lab06-debugging

Link to ShaderToy: https://www.shadertoy.com/view/ddB3Rt

<img width="475" alt="shadertoyyyy" src="https://user-images.githubusercontent.com/43520504/200883352-91b97e0a-c945-4349-9e9b-809310882f92.PNG">

I believe I found all 5 bugs.

The first was on line 97:\
  This ndc conversion tried to use a vec class instead of vec2
  
The second was on line 100:\
  I simply used the same uv vec2 for all uv usages, so no need for uv2
  
The third was on line 11:\
  The aspect ratio calculation used the screen width divided by width instead of width divided by height
  
The fourth was on line 18:\
  The number of ray marching iterations was too small so I increased to 128
  
The fifth was on line 75:\
  The eye, or camera position, was passed as the incident ray direction in the glsl reflect function. Instead I pass the actual direction of the incident ray dir
  
To find all these bugs, I simply went in sequential order in terms of code execution: I started with the main function, then moved to raycast and sdf3D and march etc.
Luckily, I have become very familiar with ray casting and marching, so finding the bugs only required me to look through the code and notice anything that
seemed out of place. In something I was less familiar with, I would probably have had to start incrementally testing the functions to understand the output.
  
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
