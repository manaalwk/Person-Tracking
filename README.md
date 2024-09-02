# Person Detection and Tracking
Objective:
The goal of this code is to detect and track specific individuals (children and adults) in a video using the YOLOv8 model for detection and DeepSORT for tracking. The main objectives are:
1.Assign unique IDs to each detected person.
2.Track re-entries, i.e., if a person leaves and re-enters the frame, they should retain the same ID.
3.Assign new IDs to new persons entering the frame.
4.Re-track and correctly ID persons after occlusion or partial visibility.
Model Loading:
The YOLOv8 model is loaded using the ultralytics library. 
This model is used for object detection in the video.
The DeepSORT tracker is initialized with specific parameters such as maximum IOU distance, maximum age, and cosine distance to track objects over time.
Object Detection:
A frame is grabbed from the video stream using vs.read(). If no frame is grabbed, the loop breaks.The YOLOv8 model is used to predict objects in the frame. The model is configured to detect only persons (children and adults).A green line is drawn in the middle of the frame. This line is used later to count the number of persons crossing it.
Object Tracking:
For each detected object, the bounding box coordinates, confidence score, and class ID are extracted. A bounding box is drawn around each detected object, and the class name (e.g., "person") is displayed on the frame.The extracted bounding boxes and other details are fed into the DeepSORT tracker to update the track information. The tracker assigns a unique ID to each detected person and maintains this ID across frames.
Counting and ID Assignment:
The unique ID assigned by DeepSORT.The code checks if a person has crossed the predefined line (drawn in the middle of the frame). If a person crosses the line and their ID is not in the counter_cache, they are counted, and their ID is added to the cache to prevent double counting.
Conclusion:
1.The model is designed to detect only persons (children and adults) using YOLOv8, but it currently does not differentiate between children and adults. To do so, a more specialized model or additional logic based on size, posture, or other visual cues would be required.
2.This code provides a basic yet effective pipeline for detecting and tracking persons in a video. 
3.By analyzing each frame, detecting objects, and tracking them over time, the system achieves the objectives of assigning unique IDs, tracking re-entries, and handling post-occlusion tracking. 

