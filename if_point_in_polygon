import numpy as np
import pygame, os, sys
from pygame.locals import *
from copy import deepcopy
import time


pygame.init()
title      =   pygame.display.set_caption("caption")
window     =   pygame.display.set_mode((800,800))
window.fill((255,255,255))

point = []
points = [[100,100],[200,100],[300,100]]

def judgeIfInPolygon(polySides, polyX, polyY, point):

    in_bool = False
    j = polySides-1

    for i in range(polySides):
        if ((((polyY[i]<point[1])and(polyY[j]>=point[1]))or((polyY[j]<point[1])and(polyY[i]>=point[1]))) \
            and ((polyX[i]<=point[0])or(polyX[j]<=point[0]))):
            if (polyX[i]+(point[1]-polyY[i])/(polyY[j]-polyY[i])*(polyX[j]-polyX[i])<point[0]):
                in_bool = (not in_bool)
        j = i

    return in_bool


while 1:

    pygame.display.update()

    # judge
    if len(point) >= 1:
        inOrOut = judgeIfInPolygon(polySides=polySides, polyX=polyX, polyY=polyY, point=point[-1])
        print("point ",point[-1],"in or out :",inOrOut)
    
    time.sleep(1)

    # 多边形算法
    polySides = len(points)
    polyX = [deepcopy(i[0]) for i in points]
    polyY = [deepcopy(i[1]) for i in points]

    for event in pygame.event.get():


        if event.type == MOUSEBUTTONDOWN:
            
            # 左键：多边形
            if event.button == 1:
                points.append(list(event.pos))
            
            # 右键：点
            if event.button == 3:
                point.append(list(event.pos))

        if event.type == QUIT:
            pygame.quit()
            sys.exit()

    if points:
        pygame.draw.polygon(window, (0,255,0), points)

    for po in point:
        pygame.draw.circle(window, (0,0,255), po, 5, 0)
