# object-detection
code to detect black object through opencv 
import cv2
import numpy as np
cap=cv2.VideoCapture(0)
while True:
    ret , frame=cap.read()
    hsv = cv2.cvtColor(frame , cv2.COLOR_BGR2HSV)
    lower_black = np.array([0,0,0])
    upper_black = np.array([140,150,150])
    mask = cv2.inRange(hsv,lower_black,upper_black)
    res= cv2.bitwise_and(frame,frame,mask=mask)
    cv2.imshow('frame',frame)
    cv2.imshow('mask',mask)
    cv2.imshow('res',res)
    if cv2.waitKey(1) == ord('q'):
        break
cap.release()
cv2.destroyAllWindows()
