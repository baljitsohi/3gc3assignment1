from OpenGL.GL import *
from OpenGL.GLU import *
from OpenGL import GL as gl
import glfw
import numpy as np
import sys

def cubedraw():


    glClear(GL_COLOR_BUFFER_BIT | GL_DEPTH_BUFFER_BIT)  
    
    glBegin(GL_POLYGON)
    glColor3f(1,  1, 0)
    glVertex3f(1, -1, -1)
    glVertex3f(1, -1, 1)
    glVertex3f(1, 1, 1)
    glVertex3f(1, 1, -1)
    glEnd()
    
    glBegin(GL_POLYGON)
    glColor3f(1,  0, 1)
    glVertex3f(-1, -1, 1)
    glVertex3f(-1,  1, 1)
    glVertex3f(1,  1, 1)
    glVertex3f(1, -1, 1)
    glEnd()
    
    glBegin(GL_POLYGON)
    glColor3f(1,  0, 0)
    glVertex3f(-1, -1, -1)
    glVertex3f(-1,  1, -1)
    glVertex3f(1,  1, -1)
    glVertex3f(1, -1, -1)
    glEnd()
    
    glBegin(GL_POLYGON)
    glColor3f(0,  1, 0)
    glVertex3f(-1, -1, -1)
    glVertex3f(-1, -1, 1)
    glVertex3f(-1, 1, 1)
    glVertex3f(-1, 1, -1)
    glEnd()
    
    glBegin(GL_POLYGON)
    glColor3f(0,  0, 1)
    glVertex3f(-1, -1, -1)
    glVertex3f(-1,  -1, 1)
    glVertex3f(1,  -1, 1)
    glVertex3f(1, -1, -1)
    glEnd()
    
    glBegin(GL_POLYGON)
    glColor3f(0,  1, 1)
    glVertex3f(-1, 1, -1)
    glVertex3f(-1,  1, 1)
    glVertex3f(1,  1, 1)
    glVertex3f(1, 1, -1)
    glEnd()
    
    
def dump_framebuffer_to_ppm(ppm_name, fb_width, fb_height):
    pixelChannel = 3
    pixels = gl.glReadPixels(0, 0, fb_width, fb_height, gl.GL_RGB, gl.GL_UNSIGNED_BYTE)
    fout = open(ppm_name, "w")
    fout.write('P3\n{} {}\n255\n'.format(int(fb_width), int(fb_height)))
    for i in range(0, fb_height):
        for j in range(0, fb_width):
            cur = pixelChannel * ((fb_height - i - 1) * fb_width + j)
            fout.write('{} {} {} '.format(int(pixels[cur]), int(pixels[cur+1]), int(pixels[cur+2])))
        fout.write('\n')
    fout.flush()
    fout.close()
screen_width, screen_height = 1024, 768

if not glfw.init():
    sys.exit(1)
glfw.window_hint(glfw.RESIZABLE, glfw.FALSE)
title = 'Assignment 1'
window = glfw.create_window(screen_width, screen_height, title, None, None)

if not window:
    print('GLFW Window Failed')
    sys.exit(2)
glfw.make_context_current(window)
glClearColor(0.3, 0.4, 0.5, 0)
glEnable(GL_DEPTH_TEST)
glClearDepth(1.0) 
glDepthFunc(GL_LESS)
glEnable(GL_DEPTH_TEST)
glShadeModel(GL_SMOOTH)   
glMatrixMode(GL_PROJECTION)
gluPerspective(30, 4/3, 0.1, 1000.0)
glMatrixMode(GL_MODELVIEW)
gluLookAt(3, 4, 5, 0, 0, 0, 1, 1, 1)
#gluLookAt(-6, -7, -8, 0, 0, 0, 0, 1, 0)

def cube():
    ss_id = 1 
    while (
        glfw.get_key(window, glfw.KEY_ESCAPE) != glfw.PRESS and
        not glfw.window_should_close(window)
    ):
        # press key p will capture screen shot
        if glfw.get_key(window, glfw.KEY_P) == glfw.PRESS:
            print("Capture Window ", ss_id)
            buffer_width, buffer_height = glfw.get_framebuffer_size(window)
            ppm_name = "cube" + str(ss_id) + ".ppm"
            dump_framebuffer_to_ppm(ppm_name, buffer_width, buffer_height)
            ss_id += 1
        cubedraw()
        glfw.swap_buffers(window)
        glfw.poll_events()

cube()
