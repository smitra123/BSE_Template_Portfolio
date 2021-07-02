# Arduino Based Floor Cleaning Robot
This project uses an arduino to control a floor cleaning a robot. It utilizes an ultrasonic sensor to know when to stop and turn,and uses 4 DC motors and a motor driver to control the movement. A vacuum and a brush are attached to the car to clean the floor.

| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Saagnik M | Amador Valley Highschool | Mechanical Engineering | Incoming Junior

![Headstone Image](https://cdn.discordapp.com/attachments/807072542095441940/860222212652269638/unknown.png)

# Final Presentation

[![Saagnik's Final Presentation](https://res.cloudinary.com/marcomontalbano/image/upload/v1625243592/video_to_markdown/images/youtube--i0kgQgX-1yc-c05b58ac6eb4c4700831b2b3070cd403.jpg)](https://www.youtube.com/watch?v=i0kgQgX-1yc&t=70s "Saagnik's Final Presentation"){:target="_blank" rel="noopener"}

# Reflection
After 3 weeks at Bluestamp Engineering, I can say that I've learned a lot. Coming into the program, I had little experience with Arduino and the electrical aspect of things. After working hard throughout the course of the program I have learned a lot about these. I have gained an understanding  about problem solving, and working through bugs. Problems such as working through the obstacle avoidance and attaching the vacuum were quite daunting at first, but with time and thinking the solutions were found. Ultimately, my experience at Bluestamp Engineering was very fruitfl and exciting. I think I gained a lot of wisdom and I it definitely fueled the passion to keep diving into mechanical engineering.
  
# Final Milestone
The third and final milestone was just about my modification. I wanted to create a sort of chime after a certain amount of time to let the user know that the robot's cleaning job was over with. I did the by adding a buzzer, and using the millis function which allowed me to keep track of time. In this case I made the chime the Mario theme and it played after a certain amount of time.

# Final Code
<pre>
<font color="#5e6d03">#include</font> <font color="#005c5f">&#34;pitches.h&#34;</font>

<font color="#5e6d03">#define</font> <font color="#000000">melodyPin</font> <font color="#000000">11</font>

<font color="#00979c">int</font> <font color="#000000">melody</font><font color="#000000">[</font><font color="#000000">]</font> <font color="#434f54">=</font> <font color="#000000">{</font>
 &nbsp;<font color="#000000">NOTE_E7</font><font color="#434f54">,</font> <font color="#000000">NOTE_E7</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">NOTE_E7</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">NOTE_C7</font><font color="#434f54">,</font> <font color="#000000">NOTE_E7</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">NOTE_G7</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font> &nbsp;<font color="#000000">0</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">NOTE_G6</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font>

 &nbsp;<font color="#000000">NOTE_C7</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">NOTE_G6</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">NOTE_E6</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">NOTE_A6</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">NOTE_B6</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">NOTE_AS6</font><font color="#434f54">,</font> <font color="#000000">NOTE_A6</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font>

 &nbsp;<font color="#000000">NOTE_G6</font><font color="#434f54">,</font> <font color="#000000">NOTE_E7</font><font color="#434f54">,</font> <font color="#000000">NOTE_G7</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">NOTE_A7</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">NOTE_F7</font><font color="#434f54">,</font> <font color="#000000">NOTE_G7</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">NOTE_E7</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">NOTE_C7</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">NOTE_D7</font><font color="#434f54">,</font> <font color="#000000">NOTE_B6</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font>

 &nbsp;<font color="#000000">NOTE_C7</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">NOTE_G6</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">NOTE_E6</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">NOTE_A6</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">NOTE_B6</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">NOTE_AS6</font><font color="#434f54">,</font> <font color="#000000">NOTE_A6</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font>

 &nbsp;<font color="#000000">NOTE_G6</font><font color="#434f54">,</font> <font color="#000000">NOTE_E7</font><font color="#434f54">,</font> <font color="#000000">NOTE_G7</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">NOTE_A7</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">NOTE_F7</font><font color="#434f54">,</font> <font color="#000000">NOTE_G7</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">NOTE_E7</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">NOTE_C7</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">NOTE_D7</font><font color="#434f54">,</font> <font color="#000000">NOTE_B6</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">0</font>
<font color="#000000">}</font><font color="#000000">;</font>

<font color="#00979c">int</font> <font color="#000000">tempo</font><font color="#000000">[</font><font color="#000000">]</font> <font color="#434f54">=</font> <font color="#000000">{</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font>

 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font>

 &nbsp;<font color="#000000">9</font><font color="#434f54">,</font> <font color="#000000">9</font><font color="#434f54">,</font> <font color="#000000">9</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font>

 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font>

 &nbsp;<font color="#000000">9</font><font color="#434f54">,</font> <font color="#000000">9</font><font color="#434f54">,</font> <font color="#000000">9</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font>
<font color="#000000">}</font><font color="#000000">;</font>

<font color="#00979c">int</font> <font color="#000000">underworld_melody</font><font color="#000000">[</font><font color="#000000">]</font> <font color="#434f54">=</font> <font color="#000000">{</font>
 &nbsp;<font color="#000000">NOTE_C4</font><font color="#434f54">,</font> <font color="#000000">NOTE_C5</font><font color="#434f54">,</font> <font color="#000000">NOTE_A3</font><font color="#434f54">,</font> <font color="#000000">NOTE_A4</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">NOTE_AS3</font><font color="#434f54">,</font> <font color="#000000">NOTE_AS4</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">0</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">NOTE_C4</font><font color="#434f54">,</font> <font color="#000000">NOTE_C5</font><font color="#434f54">,</font> <font color="#000000">NOTE_A3</font><font color="#434f54">,</font> <font color="#000000">NOTE_A4</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">NOTE_AS3</font><font color="#434f54">,</font> <font color="#000000">NOTE_AS4</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">0</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">NOTE_F3</font><font color="#434f54">,</font> <font color="#000000">NOTE_F4</font><font color="#434f54">,</font> <font color="#000000">NOTE_D3</font><font color="#434f54">,</font> <font color="#000000">NOTE_D4</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">NOTE_DS3</font><font color="#434f54">,</font> <font color="#000000">NOTE_DS4</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">0</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">NOTE_F3</font><font color="#434f54">,</font> <font color="#000000">NOTE_F4</font><font color="#434f54">,</font> <font color="#000000">NOTE_D3</font><font color="#434f54">,</font> <font color="#000000">NOTE_D4</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">NOTE_DS3</font><font color="#434f54">,</font> <font color="#000000">NOTE_DS4</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">NOTE_DS4</font><font color="#434f54">,</font> <font color="#000000">NOTE_CS4</font><font color="#434f54">,</font> <font color="#000000">NOTE_D4</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">NOTE_CS4</font><font color="#434f54">,</font> <font color="#000000">NOTE_DS4</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">NOTE_DS4</font><font color="#434f54">,</font> <font color="#000000">NOTE_GS3</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">NOTE_G3</font><font color="#434f54">,</font> <font color="#000000">NOTE_CS4</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">NOTE_C4</font><font color="#434f54">,</font> <font color="#000000">NOTE_FS4</font><font color="#434f54">,</font> <font color="#000000">NOTE_F4</font><font color="#434f54">,</font> <font color="#000000">NOTE_E3</font><font color="#434f54">,</font> <font color="#000000">NOTE_AS4</font><font color="#434f54">,</font> <font color="#000000">NOTE_A4</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">NOTE_GS4</font><font color="#434f54">,</font> <font color="#000000">NOTE_DS4</font><font color="#434f54">,</font> <font color="#000000">NOTE_B3</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">NOTE_AS3</font><font color="#434f54">,</font> <font color="#000000">NOTE_A3</font><font color="#434f54">,</font> <font color="#000000">NOTE_GS3</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">0</font>
<font color="#000000">}</font><font color="#000000">;</font>

<font color="#00979c">int</font> <font color="#000000">underworld_tempo</font><font color="#000000">[</font><font color="#000000">]</font> <font color="#434f54">=</font> <font color="#000000">{</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">6</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">3</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">6</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">3</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">6</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">3</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">12</font><font color="#434f54">,</font> <font color="#000000">6</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">6</font><font color="#434f54">,</font> <font color="#000000">18</font><font color="#434f54">,</font> <font color="#000000">18</font><font color="#434f54">,</font> <font color="#000000">18</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">6</font><font color="#434f54">,</font> <font color="#000000">6</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">6</font><font color="#434f54">,</font> <font color="#000000">6</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">6</font><font color="#434f54">,</font> <font color="#000000">6</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">18</font><font color="#434f54">,</font> <font color="#000000">18</font><font color="#434f54">,</font> <font color="#000000">18</font><font color="#434f54">,</font> <font color="#000000">18</font><font color="#434f54">,</font> <font color="#000000">18</font><font color="#434f54">,</font> <font color="#000000">18</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">10</font><font color="#434f54">,</font> <font color="#000000">10</font><font color="#434f54">,</font> <font color="#000000">10</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">10</font><font color="#434f54">,</font> <font color="#000000">10</font><font color="#434f54">,</font> <font color="#000000">10</font><font color="#434f54">,</font>
 &nbsp;<font color="#000000">3</font><font color="#434f54">,</font> <font color="#000000">3</font><font color="#434f54">,</font> <font color="#000000">3</font>
<font color="#000000">}</font><font color="#000000">;</font>

<font color="#00979c">const</font> <font color="#00979c">int</font> <font color="#000000">trigPin</font> <font color="#434f54">=</font> <font color="#000000">8</font><font color="#000000">;</font>
<font color="#00979c">const</font> <font color="#00979c">int</font> <font color="#000000">echoPin</font> <font color="#434f54">=</font> <font color="#000000">9</font><font color="#000000">;</font>
<font color="#00979c">long</font> <font color="#000000">duration</font><font color="#000000">;</font>
<font color="#00979c">int</font> <font color="#000000">distance</font><font color="#000000">;</font>
<font color="#00979c">int</font> <font color="#000000">in1</font> <font color="#434f54">=</font> <font color="#000000">2</font><font color="#000000">;</font>
<font color="#00979c">int</font> <font color="#000000">in2</font> <font color="#434f54">=</font> <font color="#000000">4</font><font color="#000000">;</font>
<font color="#00979c">int</font> <font color="#000000">enA</font> <font color="#434f54">=</font> <font color="#000000">3</font><font color="#000000">;</font>
<font color="#00979c">int</font> <font color="#000000">enB</font> <font color="#434f54">=</font> <font color="#000000">6</font><font color="#000000">;</font>
<font color="#00979c">int</font> <font color="#000000">in3</font> <font color="#434f54">=</font> <font color="#000000">5</font><font color="#000000">;</font>
<font color="#00979c">int</font> <font color="#000000">in4</font> <font color="#434f54">=</font> <font color="#000000">7</font><font color="#000000">;</font>
<font color="#00979c">void</font> <font color="#5e6d03">setup</font><font color="#000000">(</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">11</font><font color="#434f54">,</font> <font color="#00979c">OUTPUT</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">enA</font><font color="#434f54">,</font> <font color="#00979c">OUTPUT</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">enB</font><font color="#434f54">,</font> <font color="#00979c">OUTPUT</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">in1</font><font color="#434f54">,</font> <font color="#00979c">OUTPUT</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">in2</font><font color="#434f54">,</font> <font color="#00979c">OUTPUT</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">in3</font><font color="#434f54">,</font> <font color="#00979c">OUTPUT</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">in4</font><font color="#434f54">,</font> <font color="#00979c">OUTPUT</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">trigPin</font><font color="#434f54">,</font> <font color="#00979c">OUTPUT</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">pinMode</font><font color="#000000">(</font><font color="#000000">echoPin</font><font color="#434f54">,</font> <font color="#00979c">INPUT</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">begin</font><font color="#000000">(</font><font color="#000000">9600</font><font color="#000000">)</font><font color="#000000">;</font>
<font color="#000000">}</font>


<font color="#00979c">void</font> <font color="#5e6d03">loop</font><font color="#000000">(</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;<font color="#00979c">long</font> <font color="#000000">timestart</font> <font color="#434f54">=</font> <font color="#d35400">millis</font><font color="#000000">(</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#434f54">&#47;&#47;Serial.println(timestart);</font>
 &nbsp;<font color="#5e6d03">while</font> <font color="#000000">(</font><font color="#d35400">millis</font><font color="#000000">(</font><font color="#000000">)</font> <font color="#434f54">&lt;</font> <font color="#000000">timestart</font> <font color="#434f54">+</font> <font color="#000000">5000</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">println</font><font color="#000000">(</font><font color="#005c5f">&#34;In the main loop!&#34;</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">trigPin</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#d35400">delay</font><font color="#000000">(</font><font color="#000000">2</font><font color="#000000">)</font><font color="#000000">;</font>

 &nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">trigPin</font><font color="#434f54">,</font> <font color="#00979c">HIGH</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#d35400">delay</font><font color="#000000">(</font><font color="#000000">10</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">trigPin</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>

 &nbsp;&nbsp;&nbsp;<font color="#000000">duration</font> <font color="#434f54">=</font> <font color="#d35400">pulseIn</font><font color="#000000">(</font><font color="#000000">echoPin</font><font color="#434f54">,</font> <font color="#00979c">HIGH</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">distance</font> <font color="#434f54">=</font> <font color="#000000">duration</font> <font color="#434f54">*</font> <font color="#000000">0.034</font> <font color="#434f54">&#47;</font> <font color="#000000">2</font><font color="#000000">;</font>

 &nbsp;&nbsp;&nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">print</font><font color="#000000">(</font><font color="#005c5f">&#34;Distance:&#34;</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">println</font><font color="#000000">(</font><font color="#000000">distance</font><font color="#000000">)</font><font color="#000000">;</font>


 &nbsp;&nbsp;&nbsp;<font color="#5e6d03">if</font> <font color="#000000">(</font><font color="#000000">distance</font><font color="#434f54">&lt;</font><font color="#000000">15</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Serial.println(&#34;In If 1!&#34;); &#47;&#47;Check to see if code has entered into the If statement</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">in1</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">in2</font><font color="#434f54">,</font> <font color="#00979c">HIGH</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">analogWrite</font><font color="#000000">(</font><font color="#000000">enA</font><font color="#434f54">,</font> <font color="#000000">200</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">in3</font><font color="#434f54">,</font> <font color="#00979c">HIGH</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">in4</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">analogWrite</font><font color="#000000">(</font><font color="#000000">enB</font><font color="#434f54">,</font> <font color="#000000">200</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">delay</font><font color="#000000">(</font><font color="#000000">1000</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#5e6d03">if</font> <font color="#000000">(</font><font color="#000000">distance</font><font color="#434f54">&lt;</font><font color="#000000">20</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Serial.println(&#34;In If 2!&#34;); &#47;&#47;Check to see if code has entered the nested if statement</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">in1</font><font color="#434f54">,</font> <font color="#00979c">HIGH</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">in2</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">analogWrite</font><font color="#000000">(</font><font color="#000000">enA</font><font color="#434f54">,</font> <font color="#000000">250</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">in3</font><font color="#434f54">,</font> <font color="#00979c">HIGH</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">in4</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">analogWrite</font><font color="#000000">(</font><font color="#000000">enB</font><font color="#434f54">,</font> <font color="#000000">250</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">delay</font><font color="#000000">(</font><font color="#000000">1000</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#000000">}</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">}</font>
 &nbsp;&nbsp;&nbsp;<font color="#5e6d03">else</font> <font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Serial.println(&#34;In Else!&#34;); &#47;&#47;Check to see if code has entered the else statement</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">in1</font><font color="#434f54">,</font> <font color="#00979c">HIGH</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">in2</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">analogWrite</font><font color="#000000">(</font><font color="#000000">enA</font><font color="#434f54">,</font> <font color="#000000">200</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">in3</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">in4</font><font color="#434f54">,</font> <font color="#00979c">HIGH</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">analogWrite</font><font color="#000000">(</font><font color="#000000">enB</font><font color="#434f54">,</font> <font color="#000000">200</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">delay</font><font color="#000000">(</font><font color="#000000">500</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">}</font>
 &nbsp;&nbsp;&nbsp;<font color="#434f54">&#47;&#47;Serial.println(millis()); &#47;&#47;Millis check to see how much time has passed through one loop</font>
 &nbsp;<font color="#000000">}</font>
 &nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">println</font><font color="#000000">(</font><font color="#005c5f">&#34;I made it!&#34;</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">in1</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">in2</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">analogWrite</font><font color="#000000">(</font><font color="#000000">enA</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">in3</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">in4</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#d35400">analogWrite</font><font color="#000000">(</font><font color="#000000">enB</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#000000">sing</font><font color="#000000">(</font><font color="#000000">1</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#000000">sing</font><font color="#000000">(</font><font color="#000000">1</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#000000">sing</font><font color="#000000">(</font><font color="#000000">2</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#434f54">&#47;&#47;delay(2000);</font>
 &nbsp;<font color="#5e6d03">while</font> <font color="#000000">(</font><font color="#000000">1</font><font color="#000000">)</font><font color="#000000">;</font>
<font color="#000000">}</font>

<font color="#00979c">int</font> <font color="#000000">song</font> <font color="#434f54">=</font> <font color="#000000">0</font><font color="#000000">;</font>

<font color="#00979c">void</font> <font color="#000000">sing</font><font color="#000000">(</font><font color="#00979c">int</font> <font color="#000000">s</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;<font color="#000000">song</font> <font color="#434f54">=</font> <font color="#000000">s</font><font color="#000000">;</font>
 &nbsp;<font color="#5e6d03">if</font> <font color="#000000">(</font><font color="#000000">song</font> <font color="#434f54">==</font> <font color="#000000">2</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">println</font><font color="#000000">(</font><font color="#005c5f">&#34; &#39;Underworld Theme&#39;&#34;</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#00979c">int</font> <font color="#d35400">size</font> <font color="#434f54">=</font> <font color="#00979c">sizeof</font><font color="#000000">(</font><font color="#000000">underworld_melody</font><font color="#000000">)</font> <font color="#434f54">&#47;</font> <font color="#00979c">sizeof</font><font color="#000000">(</font><font color="#00979c">int</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#5e6d03">for</font> <font color="#000000">(</font><font color="#00979c">int</font> <font color="#000000">thisNote</font> <font color="#434f54">=</font> <font color="#000000">0</font><font color="#000000">;</font> <font color="#000000">thisNote</font> <font color="#434f54">&lt;</font> <font color="#d35400">size</font><font color="#000000">;</font> <font color="#000000">thisNote</font><font color="#434f54">++</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#00979c">int</font> <font color="#000000">noteDuration</font> <font color="#434f54">=</font> <font color="#000000">1000</font> <font color="#434f54">&#47;</font> <font color="#000000">underworld_tempo</font><font color="#000000">[</font><font color="#000000">thisNote</font><font color="#000000">]</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#000000">buzz</font><font color="#000000">(</font><font color="#000000">melodyPin</font><font color="#434f54">,</font> <font color="#000000">underworld_melody</font><font color="#000000">[</font><font color="#000000">thisNote</font><font color="#000000">]</font><font color="#434f54">,</font> <font color="#000000">noteDuration</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#00979c">int</font> <font color="#000000">pauseBetweenNotes</font> <font color="#434f54">=</font> <font color="#000000">noteDuration</font> <font color="#434f54">*</font> <font color="#000000">1.30</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">delay</font><font color="#000000">(</font><font color="#000000">pauseBetweenNotes</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#000000">buzz</font><font color="#000000">(</font><font color="#000000">melodyPin</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">noteDuration</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">}</font>
 &nbsp;<font color="#000000">}</font>
 &nbsp;<font color="#5e6d03">else</font> <font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;<b><font color="#d35400">Serial</font></b><font color="#434f54">.</font><font color="#d35400">println</font><font color="#000000">(</font><font color="#005c5f">&#34; &#39;Mario Theme&#39;&#34;</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#00979c">int</font> <font color="#d35400">size</font> <font color="#434f54">=</font> <font color="#00979c">sizeof</font><font color="#000000">(</font><font color="#000000">melody</font><font color="#000000">)</font> <font color="#434f54">&#47;</font> <font color="#00979c">sizeof</font><font color="#000000">(</font><font color="#00979c">int</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#5e6d03">for</font> <font color="#000000">(</font><font color="#00979c">int</font> <font color="#000000">thisNote</font> <font color="#434f54">=</font> <font color="#000000">0</font><font color="#000000">;</font> <font color="#000000">thisNote</font> <font color="#434f54">&lt;</font> <font color="#d35400">size</font><font color="#000000">;</font> <font color="#000000">thisNote</font><font color="#434f54">++</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#00979c">int</font> <font color="#000000">noteDuration</font> <font color="#434f54">=</font> <font color="#000000">1000</font> <font color="#434f54">&#47;</font> <font color="#000000">tempo</font><font color="#000000">[</font><font color="#000000">thisNote</font><font color="#000000">]</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#000000">buzz</font><font color="#000000">(</font><font color="#000000">melodyPin</font><font color="#434f54">,</font> <font color="#000000">melody</font><font color="#000000">[</font><font color="#000000">thisNote</font><font color="#000000">]</font><font color="#434f54">,</font> <font color="#000000">noteDuration</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#00979c">int</font> <font color="#000000">pauseBetweenNotes</font> <font color="#434f54">=</font> <font color="#000000">noteDuration</font> <font color="#434f54">*</font> <font color="#000000">1.30</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#d35400">delay</font><font color="#000000">(</font><font color="#000000">pauseBetweenNotes</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;<font color="#000000">buzz</font><font color="#000000">(</font><font color="#000000">melodyPin</font><font color="#434f54">,</font> <font color="#000000">0</font><font color="#434f54">,</font> <font color="#000000">noteDuration</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#000000">}</font>
 &nbsp;<font color="#000000">}</font>
<font color="#000000">}</font>
<font color="#00979c">void</font> <font color="#000000">buzz</font><font color="#000000">(</font><font color="#00979c">int</font> <font color="#000000">targetPin</font><font color="#434f54">,</font> <font color="#00979c">long</font> <font color="#000000">frequency</font><font color="#434f54">,</font> <font color="#00979c">long</font> <font color="#d35400">length</font><font color="#000000">)</font> <font color="#000000">{</font>

 &nbsp;<font color="#00979c">long</font> <font color="#000000">delayValue</font> <font color="#434f54">=</font> <font color="#000000">1000000</font> <font color="#434f54">&#47;</font> <font color="#000000">frequency</font> <font color="#434f54">&#47;</font> <font color="#000000">2</font><font color="#000000">;</font>
 &nbsp;<font color="#00979c">long</font> <font color="#000000">numCycles</font> <font color="#434f54">=</font> <font color="#000000">frequency</font> <font color="#434f54">*</font> <font color="#d35400">length</font> <font color="#434f54">&#47;</font> <font color="#000000">1000</font><font color="#000000">;</font>
 &nbsp;<font color="#5e6d03">for</font> <font color="#000000">(</font><font color="#00979c">long</font> <font color="#000000">i</font> <font color="#434f54">=</font> <font color="#000000">0</font><font color="#000000">;</font> <font color="#000000">i</font> <font color="#434f54">&lt;</font> <font color="#000000">numCycles</font><font color="#000000">;</font> <font color="#000000">i</font><font color="#434f54">++</font><font color="#000000">)</font> <font color="#000000">{</font>
 &nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">targetPin</font><font color="#434f54">,</font> <font color="#00979c">HIGH</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#d35400">delayMicroseconds</font><font color="#000000">(</font><font color="#000000">delayValue</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#d35400">digitalWrite</font><font color="#000000">(</font><font color="#000000">targetPin</font><font color="#434f54">,</font> <font color="#00979c">LOW</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;&nbsp;&nbsp;<font color="#d35400">delayMicroseconds</font><font color="#000000">(</font><font color="#000000">delayValue</font><font color="#000000">)</font><font color="#000000">;</font>
 &nbsp;<font color="#000000">}</font>
<font color="#000000">}</font>

</pre>

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
