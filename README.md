# lab06-debugging

# Setup 

Create a [Shadertoy account](https://www.shadertoy.com/). Either fork this shadertoy, or create a new shadertoy and copy the code from the [Debugging Puzzle](https://www.shadertoy.com/view/flGfRc).

Let's practice debugging! We have a broken shader. It should produce output that looks like this:
[Unbelievably beautiful shader](https://user-images.githubusercontent.com/1758825/200729570-8e10a37a-345d-4aff-8eff-6baf54a32a40.webm)

It don't do that. Correct THREE of the FIVE bugs that are messing up the output. You are STRONGLY ENCOURAGED to work with a partner and pair program to force you to talk about your debugging thought process out loud.

Extra credit if you can find all FIVE bugs.

# Results

***Teammates:*** Wenqing Wang, Yuqi Zhang

## Bug01
Shadertoy: https://www.shadertoy.com/view/msS3Rt
```GLSL
// line 97 vec2 -> vec
vec2 uv2 = 2.0 * uv - vec2(1.0);
```
This is a simple compiler error!

## Bug02
Shadertoy: https://www.shadertoy.com/view/ddSGzt
```GLSL
// line 100 uv -> uv2
raycast(uv2, dir, eye, ref);
```
It looks like the intersection is not correct, after we change the uv, we do not use the uv2 to cast the ray

## Bug03
Shadertoy: https://www.shadertoy.com/view/mdS3zt
```GLSL
// line 11 iResolution.x -> iResolution.y
H *= len * iResolution.x / iResolution.y;
```
After fixing the raycast, the resolution looks weird, so we checked all the place that might use resolution

## Bug04
```GLSL
// line 18 i = 64 -> i = 200
for(int i = 0; i < 200; ++i) {
```
It first looks like smooth intersection to me, then I found out rather than smooth intersection, the further ground is not shows, so it might be raymarching ends too early

## Bug05
```GLSL
// line 75 eye -> dir
dir = reflect(dir, nor);
```
After all the above errors, specular seems not right. So we check for the specular part and find out the reflect is not correct. It should not reflect eye with normal, but the former dir with normal

# Submission
- Create a pull request to this repository
- In the README, include the names of both your team members
- In the README, create a link to your shader toy solution with the bugs corrected
- In the README, describe each bug you found and include a sentence about HOW you found it.
- Make sure all three of your shadertoys are set to UNLISTED or PUBLIC (so we can see them!)
