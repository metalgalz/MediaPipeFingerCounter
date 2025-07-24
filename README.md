Of course, here is a README for your GitHub project.

-----

# Real-Time Finger Counter 🖐️

This web application uses your webcam to detect hands and count the number of raised fingers in real-time. It's built using modern web technologies and the powerful **MediaPipe Hand Landmarker** library from Google.

The application is designed to be fully responsive and works seamlessly across different screen sizes, from mobile devices to desktops.

## Features ✨

  * **Real-Time Hand Detection:** Utilizes the MediaPipe Hand Landmarker model to accurately detect and track one or two hands in the webcam feed.
  * **Finger Counting:** Implements a logic to determine which fingers are raised and displays the total count on the screen.
  * **Responsive Design:** The user interface automatically adapts to any screen size for an optimal viewing experience.
  * **GPU Acceleration:** Leverages the user's GPU for processing, ensuring smooth performance without freezing the browser.
  * **Automatic Camera Activation:** The webcam is automatically enabled once the detection model is loaded, simplifying the user experience.
  * **Mirrored Video Feed:** The video on the canvas is flipped horizontally to create a more intuitive "mirror" effect for the user.

## How It Works 💡

The application's logic is contained within a single HTML file:

1.  **Initialization:** When the page loads, it asynchronously loads the MediaPipe Hand Landmarker model. A loading message is displayed to the user.
2.  **Camera Access:** Once the model is ready, the application requests permission to access the user's webcam.
3.  **Detection Loop:** On every frame of the video stream, the application performs the following:
      * It sends the current video frame to the Hand Landmarker API.
      * The API returns landmark data for each detected hand (if any).
      * The video frame is drawn onto a canvas element.
      * The detected hand landmarks and connecting lines are drawn on top of the video.
4.  **Finger Counting Logic:**
      * For the four fingers (index, middle, ring, pinky), it checks if the fingertip landmark is positioned higher than the lower knuckle landmarks.
      * For the thumb, it uses a more complex calculation based on its distance from other landmarks to determine if it's extended outwards or upwards.
      * The total count of raised fingers from all detected hands is then updated on the screen.

## Technologies Used 🛠️

  * **[MediaPipe Tasks for Vision](https://www.google.com/search?q=https://developers.google.com/mediapipe/solutions/vision)**: The core library used for hand detection and landmark tracking.
  * **HTML5/CSS3**: For the basic structure and styling.
  * **JavaScript (ES6 Modules)**: For all the application logic, from camera handling to UI updates.
  * **[Tailwind CSS](https://tailwindcss.com/)**: A utility-first CSS framework used for rapid and responsive UI development.
  * **[Google Fonts](https://fonts.google.com/)**: Used for the "Inter" font to enhance typography.

## How to Run 🚀

Since this is a client-side application with no server-side dependencies, you can run it directly in your web browser.

1.  Save the `Hand.html` file to your local machine.
2.  Open the file with a modern web browser that supports WebGL and has webcam access (e.g., Chrome, Firefox, Edge).

Due to browser security policies regarding `file://` protocols, you might need to serve the file from a local web server for the MediaPipe models to load correctly. An easy way to do this is by using Python's built-in HTTP server:

```bash
# Navigate to the directory where you saved the HTML file
cd path/to/your/folder

# Run a simple HTTP server (for Python 3)
python -m http.server
```

Then, open your browser and go to `http://localhost:8000/Hand.html`.
