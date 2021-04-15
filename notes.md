# Notes for Fractal Canvas

## 04/15/2021

The images which include 'mandelbrot' in the name were made using z -> z**2 + c. The images with 'variation' in the name were made using z -> dz + (z+c)^2 + (z+c)^4 where dz is the change between n-1 and n-2, where n is the current iteration. Images named variation2 use z -> dz^2 + (z+c)^2 + (z+c)^4. color gradeitn images so far have been made using argmin to select the minimum index in a history array that includes all iterations. For values in the (e.g.) mandelbrot set, this approach colors the values depending on when they have a minimum, but for values outside the set it will show which iteration they first pass a threshold, since we subtract the threshold and take the absolute value (i.e., np.argmin(abs(abs(history) - THRESH), 0)). where 0 denotes the argmin across the 0th axis of the history array, corresponding to iterations of the map z -> z^2 + c, etc. variation3 takes the c outside paranthesis: z -> dz^2 + z^2 + z^4 + c. lotus2 uses z -> abs(dz)^2 + abs(z+c)^2 + abs(z+c)^4.

lotus3 uses ```z = (history[n-1,:] - history[n-2, :])**2 + (z+c)**2 + (z+c)**3 + (z+c)**4```

So if I want to go the OpenGL route, there's a way to vary values between vertices: http://pyopengl.sourceforge.net/context/tutorials/shader_2.html ... I would have a vertex for each point of 'interest' in the fractal, and color based on the absolute value at that point after some number of iterations. Zooming in or panning could be accomodated.

I could also use Three.js or webGL or canvas if I want to go with a browser-based solution. I should still be able to make use of the GPU via the browser-based route. See 'ref/CS4406-U7-PA.html' for reference of a parametric geometry rendering.
