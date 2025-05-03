# # 
```cpp
Name : Ananda Setiawati Abidin  
Information Technology  
University of Brawijaya  
```
# 👁️ Dual-Camera Face Detection on Mac and iPhone
This project enables dual-camera face detection using OpenCV on macOS and CoreML on iOS devices.
The goal is to use two camera feeds simultaneously, process face detection, and display the detected faces.

# 🔧 Features
- Uses OpenCV for face detection on macOS with dual cameras.
- Implements CoreML model for real-time face detection on iPhone.
- Supports both front and rear cameras for detection.
- Displays bounding boxes around detected faces.

# 🖥️ MacOS Setup (OpenCV)

To begin with, you need Python and OpenCV installed. For face detection, we’ll use a pre-trained Haar Cascade classifier. 
```cpp
pip install opencv-python
pip install opencv-python-headless 
```
#💻 MacOS Code Example (Dual-Camera with OpenCV)
```cpp
import cv2

# Load face detection model
face_cascade = cv2.CascadeClassifier(cv2.data.haarcascades + 'haarcascade_frontalface_default.xml')

# Buka kamera (index 0 = webcam utama MacBook)
cap = cv2.VideoCapture(1)

if not cap.isOpened():
    print("Tidak bisa membuka kamera!")
    exit()

while True:
    ret, frame = cap.read()
    if not ret:
        print("Gagal membaca frame")
        break

    # Konversi ke grayscale untuk deteksi wajah
    gray = cv2.cvtColor(frame, cv2.COLOR_BGR2GRAY)

    # Deteksi wajah
    faces = face_cascade.detectMultiScale(gray, 1.3, 5)

    # Gambar kotak di sekitar wajah
    for (x, y, w, h) in faces:
       cv2.rectangle(frame, (x, y), (x + w, y + h), (0, 0, 255), 2)


    # Tampilkan hasil
    cv2.imshow('Deteksi Wajah', frame)

    # Tekan 'q' untuk keluar
    if cv2.waitKey(1) & 0xFF == ord('q'):
        break

# Tutup kamera dan jendela
cap.release()
cv2.destroyAllWindows()

```

# 🚀 How to Run the Project
For macOS:
Install OpenCV and run the Python code.
Ensure that both cameras are available and connected.
