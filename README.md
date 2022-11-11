# lab06-debugging
Team members: Leo Liang, Wayne Wu   
[Shader Toy link](https://www.shadertoy.com/view/dsSGRt)   

Bug:   
1. `vec uv2 = 2.0 * uv - vec2(1.0);`   
    It's a syntax error and it won't compile with this.    
    Should be `vec2 uv2 = 2.0 * uv - vec2(1.0);` 
2. `raycast(uv, dir, eye, ref);`   
   The camera looks off so there could be something wrong with the raycast.    
   So I found that uv2 is computed but uv is used instead. Should be `raycast(uv, dir, eye, ref);`   
3. `H *= len * iResolution.x / iResolution.x;`   
   The aspect ratio still looks wrong after fixing the above bugs. By looking through the code I found iResolution.x/iResolution.x, which looks absolutely wrong.   
   It should be `H *= len * iResolution.x / iResolution.y;`
4. `dir  = reflect(eye, nor);`   
  There is no reflection so something must be wrong. We figured out it's something wrong with how `dir` is computed but didn't figure out how to fix it properly. Adam taught us how to do it.   
  It should be `dir  = reflect(dir, nor);`   
5. Not sure if this is a bug but if we keep `i < 64` in `void march()`, there will be some artifacts on the floor.   
  It's technically not a bug because sometimes people just want smaller marching distance for better performance. If we increase it to `i < 128`, there will be no more artifacts on the floor. 
