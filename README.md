Have you ever asked yourself 'How do 3D coordinates get projected onto a 2D screen'? If so, this page might be for you.

**CURRENTLY UNDER CONSTRUCTION, CHECK BACK IN A COUPLE DAYS!**

In this page, I will go over the basic formula for projecting 3D coordinates onto a 2D 'camera' screen, and explain the logic that helped me figure these concepts out.

TL;DR: First normalize your points with either of these formulas: (camera_x=x/z, camera_y=y/z) or (arctan(z/x), arctan(z/y)). Once you have these normalized x and y coordinates, 'stretch' them by the width and height of your screen. Voila, you're rendering 3D! To have camera rotation / movement, simply find the 'localized' coordinates you want to render before projecting them (localized meaning that the coordinates are the distance from the camera to the object, and they have been rotated by the rotation of the camera).

Getting started: The first step to understanding the concepts here is to look at the desired behavior. Our situation is that we have a single 3D point, and we want to draw a point on our screen that mimics our view of the world. To make things simpler, we'll examine things one plane at a time, so first the x-z plane, and then the y-z plane. Let's assume x is some small positive number, and think about what should happen on screen as z changes. As z increases (the point gets farther away), the point should get ever-closer to 0. For a better idea of how this should look, view the diagram below.
