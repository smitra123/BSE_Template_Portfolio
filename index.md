# Arduino Based Floor Cleaning Robot
This project uses an arduino to control a floor cleaning a robot. It utilizes an ultrasonic sensor to know when to stop and turn,and uses 4 DC motors and a motor driver to control the movement. A vacuum and a brush are attached to the car to clean the floor.

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Saagnik M | Amador Valley Highschool | Mechanical Engineering | Incoming Junior

![Headstone Image](https://cdn.discordapp.com/attachments/807072542095441940/860222212652269638/unknown.png)
  
# Final Milestone
still in progress

[![Saagnik's Final Milestone](https://res.cloudinary.com/marcomontalbano/image/upload/v1625241372/video_to_markdown/images/youtube--0ozzSzQWXgQ-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=0ozzSzQWXgQ "Saagnik's Final Milestone"){:target="_blank" rel="noopener"}

# Second Milestone
My second milestone was the completion of the base project without any mods. This included tying in the ultrasonic sensor, motors, motordriver, and the obstacle avoidance code together.The glueing down of the battery and establishing of the arduino and motor driver on the chassis was also included. Finally, I also attached the desktop vacuum to the robot by sticking it underneath a breadboard. Tying everything together and anchoring it with the code, the arduino-based floor cleaning robot was ready to go and was completed. Looking towards the next milestone, I am thinking of adding some modifications in the future.

[![Saagnik's Second Milestone](https://res.cloudinary.com/marcomontalbano/image/upload/v1625068198/video_to_markdown/images/youtube--wL2sqCYj9jg-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=wL2sqCYj9jg "Saagnik's Second Milestone"){:target="_blank" rel="noopener"}

# First Milestone
My first milestone was getting my wiring set up for the motor driver and motors, and the ultrasonic sensor. I also wanted to test the range of the ultrasonic sensor and calibrate it properly. Lastly, I completed the assembly of the chassis of the car as well. I got my ultrasonic sensor wire to the arduino and test it properly with a set of code. Afterwards, I assembled the chassis of the car and put the motors on the wheels. Then, I moved onto to the DC motors and the motor driver. I hooked up the motors to the motor driver and tested the motors going both forwards and backwards. Now I felt confident with the parts that I had, and was ready to move on.
[![Saagnik's First Milestone](https://res.cloudinary.com/marcomontalbano/image/upload/v1624637713/video_to_markdown/images/youtube--c-zeE-uog2Q-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://youtu.be/c-zeE-uog2Q "Saagnik's First Milestone"){:target="_blank" rel="noopener"}

# Ultrasonic Sensor Circuit and Code
![Ultrasonic Sensor Circuit Image](https://cdn.discordapp.com/attachments/807072542095441940/858024902699515944/unknown.png)
<pre>
<font color="#00979c">const</font> <font color="#00979c">int</font> <font color="#000000">trigPin</font> <font color="#434f54">=</font> <font color="#000000">12</font><font color="#000000">;</font>
<font color="#00979c">const</font> <font color="#00979c">int</font> <font color="#000000">echoPin</font> <font color="#434f54">=</font> <font color="#000000">13</font><font color="#000000">;</font>
<font color="#00979c">long</font> <font color="#000000">duration</font><font color="#000000">;</font>
<font color="#00979c">int</font> <font color="#000000">distance</font><font color="#000000">;</font>

<font color="#00979c">void</font> <font color="#5e6d03">setup</font><font color="#000000">(</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">trigPin</font><font color="#434f54">,</font> <font color="#00979c">OUTPUT</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">echoPin</font><font color="#434f54">,</font><font color="#00979c">INPUT</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">begin</font><font color="#000000">(</font><font color="#000000">9600</font><font color="#000000">)</font><font color="#000000">;</font>
<font color="#000000">}</font>


<font color="#00979c">void</font> <font color="#5e6d03">loop</font><font color="#000000">(</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">trigPin</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">delay</font><font color="#000000">(</font><font color="#000000">2</font><font color="#000000">)</font><font color="#000000">;</font>

 &nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">trigPin</font><font color="#434f54">,</font> <font color="#00979c">HIGH</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">delay</font><font color="#000000">(</font><font color="#000000">10</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">trigPin</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>

 &nbsp;<font color="#000000">duration</font> <font color="#434f54">=</font> <font color="#d35400">pulseIn</font><font color="#000000">(</font><font color="#000000">echoPin</font><font color="#434f54">,</font> <font color="#00979c">HIGH</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#000000">distance</font> <font color="#434f54">=</font> <font color="#000000">duration</font><font color="#434f54">*</font><font color="#000000">0.034</font><font color="#434f54">&#47;</font><font color="#000000">2</font><font color="#000000">;</font>

 &nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">print</font><font color="#000000">(</font><font color="#005c5f">&#34;Distance:&#34;</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">println</font><font color="#000000">(</font><font color="#000000">distance</font><font color="#000000">)</font><font color="#000000">;</font>
<font color="#000000">}</font>

</pre>

# Motor Driver Circuit and Code
![Motor Driver Circuit Image](https://media.discordapp.net/attachments/807072542095441940/858032058814955590/unknown.png?width=1133&height=646)

<pre>
<font color="#00979c">int</font> <font color="#000000">in1</font> <font color="#434f54">=</font> <font color="#000000">2</font><font color="#000000">;</font>
<font color="#00979c">int</font> <font color="#000000">in2</font> <font color="#434f54">=</font> <font color="#000000">4</font><font color="#000000">;</font>
<font color="#00979c">int</font> <font color="#000000">enA</font> <font color="#434f54">=</font> <font color="#000000">3</font><font color="#000000">;</font>
<font color="#00979c">void</font> <font color="#5e6d03">setup</font><font color="#000000">(</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">enA</font><font color="#434f54">,</font> <font color="#00979c">OUTPUT</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">in1</font><font color="#434f54">,</font> <font color="#00979c">OUTPUT</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">in2</font><font color="#434f54">,</font> <font color="#00979c">OUTPUT</font><font color="#000000">)</font><font color="#000000">;</font>
<font color="#000000">}</font>

<font color="#00979c">void</font> <font color="#5e6d03">loop</font><font color="#000000">(</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">in1</font><font color="#434f54">,</font> <font color="#00979c">HIGH</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">in2</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">analogWrite</font><font color="#000000">(</font><font color="#000000">enA</font><font color="#434f54">,</font> <font color="#000000">200</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">delay</font><font color="#000000">(</font><font color="#000000">1500</font><font color="#000000">)</font><font color="#000000">;</font>

 &nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">in1</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">in2</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">analogWrite</font><font color="#000000">(</font><font color="#000000">enA</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">delay</font><font color="#000000">(</font><font color="#000000">500</font><font color="#000000">)</font><font color="#000000">;</font>

 &nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">in1</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">in2</font><font color="#434f54">,</font> <font color="#00979c">HIGH</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">analogWrite</font><font color="#000000">(</font><font color="#000000">enA</font><font color="#434f54">,</font> <font color="#000000">200</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">delay</font><font color="#000000">(</font><font color="#000000">1500</font><font color="#000000">)</font><font color="#000000">;</font>
<font color="#000000">}</font>

</pre>
