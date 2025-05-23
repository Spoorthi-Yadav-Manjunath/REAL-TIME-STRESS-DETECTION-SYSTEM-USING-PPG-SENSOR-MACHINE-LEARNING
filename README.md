# REAL-TIME-STRESS-DETECTION-SYSTEM-USING-PPG-SENSOR-MACHINE-LEARNING
This project builds a real-time stress detection system using a PPG sensor and Arduino UNO R4. Pulse data is processed in Python to extract features and predict stress with a Random Forest model. Visual (LED) and email alerts provide instant, low-cost feedback for personal stress monitoring.
# PROJECT OVERVIEW
 This project presents a real-time stress detection system using a PPG (Photoplethysmogram) sensor and Arduino UNO R4. The sensor captures pulse data, which is transmitted to a Python program where features like mean, standard deviation, range, and median are extracted from 5-second windows. A trained Random Forest model classifies the user’s state as calm or stressed. If stress is detected, a sad face is shown on the Arduino's LED matrix and an alert email is sent. Calm predictions display a happy face. The system is portable, low-cost, and provides immediate visual and remote feedback, making it useful for stress monitoring and human-computer interaction projects.
# PROJECT DESIGN
# a. Data Collection:
PPG signals are collected using an Arduino UNO R4 through the A0 analog input pin. The data is continuously streamed to a Python script via the serial port (COM3). For analysis, each 5-second window—comprising 100 samples—is processed to extract key statistical features, including the mean, standard deviation, range, and median. Each data segment is then labeled as either calm (0) or stressed (1), and the resulting dataset is saved in a CSV file for further use. 
# b. Model Training: 
The dataset is divided into training and testing sets using an 80/20 split. A Random Forest Classifier is then trained on the extracted features from the training data. Once the model is trained, it is serialized 
and saved as named stress_model.pkl for future use. 
# c. Real-Time Stress Prediction: 
The prediction Python script continuously reads PPG data in real time and feeds it to the trained model for classification. If the model predicts a "Stressed" state, a sad face is displayed on the LED matrix, and an email alert is sent using the SMTP protocol. Conversely, if the prediction is "Calm," a happy face is shown on the LED matrix. 

![image](https://github.com/user-attachments/assets/1ef0f62d-9c5d-4fb4-bb94-a596f19f73fd)

# Plots

![image](https://github.com/user-attachments/assets/61aabac1-e431-42da-bea5-b6752a558c3c)

This bar chart shows which features were most influential in the model’s decisions.Mean and Standard Deviation of the PPG signal were the most important, followed by range, while median had minimal impact.
These insights can guide future improvements in feature engineering.

![image](https://github.com/user-attachments/assets/f0c4ee14-4fd8-4a17-b389-95667e685137)

This plot shows how many instances were predicted as calm vs. stressed. It visually confirms balanced performance and proper labeling in our dataset.

![image](https://github.com/user-attachments/assets/2ab611a6-5490-4948-8877-e936f1f64add)

This matrix shows our model's performance.All 16 calm instances and 9 stressed instances were classified correctly, achieving 100% accuracy on the test set.This confirms strong separation between the two classes and that the model is not overfitting.

#  PROJECT OUTCOME
The trained model achieved 100% accuracy on the test data. Real-time system worked reliably with minimal latency (response within seconds). Distinct feedback was given to the user with strong differentiation between “Calm” and “Stressed” conditions. All collected data was consistently labeled, and feature extraction was robust. Alerts via email were tested and delivered successfully. The system responded reliably and showed clear differences between calm and stressed conditions.

# CONCLUSION & FUTURE WORK
The system effectively detects stress in real time using a PPG sensor, machine learning, and the Arduino UNO R4. It provides visual and email alerts, making it useful for personal stress monitoring. Future improvements include adding HRV features, mobile app integration, and cloud-based data logging.
