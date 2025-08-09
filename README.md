# Climbing_Tracker
A project that aims to assess the accuracy of using a computer vision model (MediaPipe) to track features such as such as joint angles and CoM from climbers. Using inertial measurement units (IMUs) as a ground truth to compare the computer vision results.

Basic Testing Procedure:
- Using Mediapipe to record climbers on the wall and retrieve PoseLandMarks
  - Using the PoseLandMarks to calculate elbow joint angle and centre of mass (CoM)
  - Joint angle is calculate with a custom function taking shoulder, elbow and wrist landmarks and using basic trigonemtry to calculate elbow angle
  - CoM is calculated by giving each body segment (upper arm, lowearm, torso, upper thigh etc.) a specific weighting and calcualting the weighted midpoint. This is based on the following research paper: Le Mouel (2025) Improved accuracy of the whole body Center of Mass position through Kalman filtering, https://doi.org/10.1101/2024.07.24.604923
- Climbers are asked to wear inertial measurement units (IMUs) while climbing. One is placed in the middle of the forearm and the second is placed in the middle of the upper arm.
  - Using the IMUs outputed quaternion data, a ground truth for the elbow angle can be calculated from which we can compare the Mediapipe elbow angle output.

Running the code yourself: 
- Download code directory
- Change local file path for the MediaPipe model to match your personal device
- Run Pose_Landmarks.ipynb file sequentially.
- Code will access device camera. Iterupt code once you your test is complete.
- Continue running the rest of the code
- Code will output a results.csv file containing Timestamps, PoseLandMarks, WorldLandMarks, Elbow Angle, CoM (Men), CoM (Women)
- Run Quaternion_analysis.ipynb code to analyse computer vision and IMU data. Change file paths for your data accordingly.
