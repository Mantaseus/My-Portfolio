---
layout: job
category: Academic Projects

title: Android Table Tennis Game

start_date: 28 Nov, 2016
end_date: 5 Dec, 2016

feature_img: /assets/feature-img/vr_table_tennis_left.png
feature_from_left: true
feature_img_tablet: /assets/feature-img/vr_table_tennis_top.png
feature_from_top: true

home_color: '#24c3eb'
home_color_dark: '#51a5ba'
---

***

### Summary
* Worked with another team member to design a 3D model for a Table Tennis racket to hold a 9DOF IMU sensor (with 3DOF accelerometer, 3DOF magnetometer, 3DOF gyroscope), a Bluetooth module and an Arduino powered from an enclosed battery. 
* Programmed an Arduino to transmit the sensor data over Bluetooth.
* Created an Android app to connect to the electronics on the 3D printed table tennis racket using Bluetooth and obtain the sensor data to play a simple table tennis game on the Android phone.
* Started and finished the project within 1 week

***

### About the Course (MECH 423)
As the final project for one of our fourth year courses in Mechatronics (MECH 423), we were required to work in teams of two members to create any mechatronics device that we could feasibly create in the limited time frame. In MECH 423 we were formally taught how to create C# programs, write C code for embedded microcontrollers, assemble SMD components on a PCB, and use embedded microcontrollers to control the motion of a motor using a simple discrete proportional controller. The final project for MECH 423 challenged us to use the knowledge we had gained throughout our engineering education to create a functional mechatronics device.

### About the project
For this project, I teamed up with Amandeep Singh who is also an highly qualified and hard working mechatronics engineer. Despite our high course load and the demanding nature of [Capstone projects]({{ site.baseurl }}{% post_url academic_projects/2017-04-01-flexoline-braiding-machine %}), we were able to work on this project and complete it successfully within 1 week.

Our objective for this project was to create a Virtual Reality Table Tennis game using a custom 3D printed racket (which would house the electronics) and the Google Cardboard (with an Android phone). The racket was designed in SolidWorks to have an outward appearance and shape of a normal table tennis racket but also with enough space to house the electronics on the inside. The racket was designed to hold a 400mAh Li-Po battery and the breakout boards for the 9 DOF (Degree of Freedom) IMU (Inertial Measurement Unit) sensor (LSM9DS1), Bluetooth module (RN-42), battery manager and the Adafruit Trinket (Arduino-based MCU board). The racket could operate wirelessly, be turned on and off using a switch, and charged using a standard USB cable. An app was developed on Android to connect to the racket via Bluetooth, process the gyroscope data being transmitted by the racket, and translate that into racket motion inside the app to play the table tennis game.

We decided to pursue this project because we wanted to experiment with VR technology and see if we can use Google's Cardboard platform to build interesting VR use cases. We were aware that we might not be able to do justice to our ambitious project within the given time frame but we felt that VR technology provides a unique way of playing games and that the games and products currently available on market do not fully utilize the potential of this technology. In the end, we were not able to make enough progress to play the game on the Google Cardboard, but we still managed to gain valuable knowledge and engineering experience from this project.

### Design of the Racket
First, we mapped the basic functionalities for our racket and how the various elements will interact with each other.

{% include content-img.html num="1" url="/assets/content-img/android-table-tennis/flow-chart.png" caption="A chart showing the key interactions between the various elements used in the device" width="100%" %}

Once we knew all the elements required for our device, I started looking for off-the-shelf breakout boards for the IMU, Bluetooth module, battery, battery manager and the microcontroller. I selected and ordered all the required components so that we could receive them in a timely fashion. Amandeep created the 3D models for our custom table tennis racket and I got it 3D printed from a 3D printing shop in Vancouver.

{% include content-img.html num="2" url="/assets/content-img/android-table-tennis/racket-3d-model.png" caption="The 3D model designed by Amandeep for the racket" width="75%" %}

Together, we assembled the electronics onto our 3D printed racket and started working on the software for the racket and the Android app. Amandeep took responsibility for writing the Arduino code to continuously get data from the IMU and send data packets to the Bluetooth module for wireless transmission to any connected Bluetooth device.

{% include content-img.html num="3" url="/assets/content-img/android-table-tennis/racket-with-electronics.png" caption="The 3D printed racket with the IMU, MCU and battery management systems" width="75%" %}

### The Android App
While Amandeep was working on designing the racket and writing the software for the Arduino, I started working on an Android app which would wirelessly receive sensor data using Bluetooth and allow the user to play a game of virtual table tennis using the racket on their phone. I had previous experience of creating Android apps but had absolutely no experience in displaying 3D graphics or designing games with realistic physics. We were both ignorant to all the tools that were already available for displaying 2D and 3D graphics on a modern device. We were so keen to finish our ambitious project in time that we decided to not spend extra time on learning new tools and try to keep it simple. Little did I know that I would essentially end up making my own rudimentary game engine.

I began by trying to learn OpenGL ES and wrote a few basic classes and functions that would allow me to abstract away from the low level implementation of OpenGL ES on Android. After working on it for a day, I was able to display basic 3D shapes using OpenGL on my Android phone.

{% include content-img.html num="4" url="/assets/content-img/android-table-tennis/opengl-test-app.jpg" caption="The Android app I created in order to test 3D models in OpenGL" width="50%" %}

I further developed my app so that I could display any 3D model in my app. In order to do that, I created a .NET C# program that reads a 3D model's `.mtl` and `.obj` files and generates a custom `.model` file. The `.model` file contains the byte data of the original float values which define various properties for each polygon of the 3D model in 3D space. The `.model` file could then be loaded by my Android app. 

{% include content-img.html num="5" url="/assets/content-img/android-table-tennis/3d-model-converter.jpg" caption="The C# program used to convert a 3D model into `.model` files that can be used by the Android app" width="50%" %}

The 3D table tennis scene shown in figure 6 was created in the open source 3D modeling software called Blender, converted to `.obj` and `.mtl` files, converted to `.model` files using my C# program, and then displayed in the Android app.

{% include content-img.html num="6" url="/assets/content-img/android-table-tennis/vr-table-tennis.jpg" caption="The final Android app that I created for the table tennis game. The numbers below the 3D scene could be used to set various parameters of the game and the visual scene." width="50%" %}

After spending a considerable amount of time, I was also able to receive data over Bluetooth between my Android app and the racket. The android app takes the Bluetooth gyroscope data stream and uses it to change the x position (from side to side) of the player’s on screen racket using various geometric and trigonometric relationships.

### Conclusion
This project was a great learning experience for both Amandeep and I. Based on our experience at the time, the Android aspect of the project was too ambitious for us but we worked hard and achieved good results despite having to reduce our scope and not implement the game in VR. We were able to finish our project in time and also received good marks for MECH 423.
