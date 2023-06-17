# Motion_Detection_OpenCV

--> Import the cv2 module

--> Initialize the video capture object (cap) by calling cv2.VideoCapture(0).

--> Create a background subtractor object (bgsub) using cv2.createBackgroundSubtractorMOG2().

-->Apply background subtraction to the frame by calling bgsub.apply(frame). This creates a binary mask (mask) 
    that highlights the differences between the current frame and the background.

--> Apply thresholding to the binary mask using cv2.threshold(). This converts the grayscale mask into a binary image (thresh),
    where pixel values above a certain threshold (60 in this case) are set to white (255), and pixel values below the threshold are 
    set to black (0).

--> Perform morphological operations on the binary image to remove noise. The code creates a kernel using cv2.getStructuringElement() 
    and then applies morphological opening using cv2.morphologyEx() with the cv2.MORPH_OPEN flag. Morphological opening helps 
    to eliminate small noise and smooth out the detected regions.

--> Find contours in the thresholded image using cv2.findContours(). Contours are the continuous curves that represent 
    the boundaries of objects in an image. The function returns a list of contours (contours) and a hierarchy representing 
    the relationship between contours (hierarchy).

--> Loop over the detected contours and draw rectangles around the moving objects. The loop skips contours with an area 
    below a specified threshold (500 in this case) using cv2.contourArea(). For contours that meet the area threshold,
    the code retrieves the bounding rectangle coordinates using cv2.boundingRect(), and then draws a green rectangle on 
    the original frame using cv2.rectangle().
    
--> Check if the 'q' key is pressed by using cv2.waitKey(1) & 0xFF == ord('q'). If the 'q' key is pressed, 
    it breaks the loop and exits the program.

--> After exiting the loop, release the video capture resources using cap.release() and close any OpenCV windows 
    that were opened using cv2.destroyAllWindows().
