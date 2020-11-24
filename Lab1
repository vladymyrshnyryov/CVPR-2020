cv2.namedWindow("original")
cap = cv2.VideoCapture(0)

fourcc = cv2.VideoWriter_fourcc(*'XVID')
out = cv2.VideoWriter('output.avi',fourcc, 20.0, (640,480))

while(cap.isOpened()):
    flag, img = cap.read()
    try:
        out.write(img)
        cv2.imshow('original', img)
    except: 
        cap.release()
        raise
      
    ch = cv2.waitKey(5)
    if ch == 27:
        break
out.release()
cap.release()
cv2.destroyAllWindows()

cap2 = cv2.VideoCapture('output.avi')
out2 = cv2.VideoWriter('result.avi',fourcc, 20.0, (640,480))
while(cap2.isOpened()):
    ret, frame = cap2.read()
    
    if ret==True:
        
        frame = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)
        frame = cv2.cvtColor(frame, cv2.COLOR_GRAY2RGB);
        
        haar_cascade_face = cv2.CascadeClassifier('haarcascade_frontalface_default.xml')
        faces_rects = haar_cascade_face.detectMultiScale(frame, scaleFactor = 1.2, minNeighbors = 5)
        for (x,y,w,h) in faces_rects:
            cv2.rectangle(frame, (x, y), (x+w, y+h), (0, 255, 0), 2)
            cv2.line(frame, (x, y), (x+w, y+h), (0, 255, 0), 2)
            cv2.line(frame, (x, y+h), (x+w, y), (0, 255, 0), 2)

        out2.write(frame)
        cv2.imshow('result', frame)
    
        ch = cv2.waitKey(5)
        if ch == 27:
            break
    else: 
        break


cap2.release()
out2.release()
cv2.destroyAllWindows()
