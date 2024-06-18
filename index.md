# Phone Controlled Robotic Arm
<!---The phone-controlled robotic arm is a 3-jointed arm with a rotating base. It has a claw that opens and closes to pick up and grab objects. My biggest challenges, takeaways, and triumphs were...-->


| **Engineer** | **School** | **Area of Interest** | **Grade** |
|:--:|:--:|:--:|:--:|
| Linus F | Borel Middle School | Mechanical Engineering | Incoming Freshman

<!---**Replace the BlueStamp logo below with an image of yourself and your completed project. Follow the guide [here](https://tomcam.github.io/least-github-pages/adding-images-github-pages-site.html) if you need help.**

![Headstone Image](logo.svg)
  
# Final Milestone

**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**

<iframe width="560" height="315" src="https://www.youtube.com/watch?v=v7GNhi7AYkI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

For your final milestone, explain the outcome of your project. Key details to include are:
- What you've accomplished since your previous milestone
- What your biggest challenges and triumphs were at BSE
- A summary of key topics you learned about
- What you hope to learn in the future after everything you've learned at BSE-->



# Second Milestone

<!---**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**-->

<iframe width="560" height="315" src="https://www.youtube.com/watch?v=w3uiwzpNiVI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Summary

My second milestone was finishing assembling my 3 jointed robotic arm and making sure that everything worked properly and there were no bugs in my code. I also built the wired controller so that I could control my robot.

## Components Used

- 8 Female-Female Jumper Wires: Connect the controller to the Arduino Shield
- Wooden Cutouts: Creates the bulk of the physical part of the arm and controller
- Screws, nuts, and columns: Holds together all the parts of the robot and controller
- 3 Servo Arms: Connect the cutouts to the servos so they can move together
- 3 MG90s Servos: Rotate to move the arms of the robot
- Zip Ties and Wire Organizing Tubes: Organize all the wires so they don't interfere with the movement of the arm
- 2 Joysticks: Takes physical input from the user so they can control the robot.

## Challenges Faced

The biggest challenge that I faced was when I used the controller the close the claw of the arm, the claw would close but the servo would be able to rotate a little bit more so the other servos in the arm would start rotating to try to compensate for the claw not being able to close. The way that I fixed it was by making an if else statement in the code so that the servo was only allowed to rotate so much so that the claw would close but if it kept on trying to close, it would just stop the operation of that servo and rotate it back a little bit and then resume the operation of the servo.

## Next Steps

I plan on hooking the robot arm up to Bluetooth on a phone so that I can program an app to control the robot remotely on a phone.

# First Milestone

<!---**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**-->

<iframe width="560" height="315" src="https://www.youtube.com/watch?v=v7GNhi7AYkI" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

<!---For your first milestone, describe what your project is and how you plan to build it. You can include:
- An explanation about the different components of your project and how they will all integrate together
- Technical progress you've made so far
- Challenges you're facing and solving in your future milestones
- What your plan is to complete your project-->

## Summary

My first milestone was assembling the base of the robotic arm so that I could test it and make sure that the Arduino Nano, the Arduino Shield, the first servo, and the batteries were all working properly. It was also so I could test uploading the code from the Arduino software to the Arduino Nano to make sure that it was all connected properly

## Components Used

- 1 Arduino Nano: Controls all the servos
- 1 Arduino Shield: Receives power from batteries and hooks up to all the wires
- 1 USB cable: Receives signals and power from laptop
- 1 Servo: Rotate the base of the arm
- Wooden Cutouts: Creates the bulk of the physical part of the base
- Batteries: Powers everything
- Wires: Connects everything to electricity
- Velcro: Holds the battery holder in place
- Screws, nuts, and columns: Secures all the parts to each other
- Turntable: Uses a ball bearing to allow the base to rotate 360 degrees

## Challenges Faced

The biggest challenge that I faced was when I was assembling the base, I kept screwing in the wrong servo arm into the hole where it is supposed to go. So when I realized my misteake, I would have to take apart half the base just to put in the right servo arm. The screws that kept the servo arm in place were also super tiny so it was really hard getting them in and out. And I actually put the wrong servo arm in twice before I got the right one in.

## Next Steps

I plan on completeing the physical part of my robotic arm so that I can control it with a controller using joysticks. To control the servos that will move the arm.

# Schematics 
<!---Here's where you'll put images of your schematics. [Tinkercad](https://www.tinkercad.com/blog/official-guide-to-tinkercad-circuits) and [Fritzing](https://fritzing.org/learning/) are both great resoruces to create professional schematic diagrams, though BSE recommends Tinkercad becuase it can be done easily and for free in the browser.-->
! [Wiring Diagram] (wiring diagram.pdf)


# Code
<!---Here's where you'll put your code. The syntax below places it into a block of code. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize it to your project needs. -->

```c++
#include "src/CokoinoArm.h"
#define buzzerPin 9

CokoinoArm arm;
int xL,yL,xR,yR;

const int act_max=10;    //Default 10 action,4 the Angle of servo
int act[act_max][4];    //Only can change the number of action
int num=0,num_do=0;
///////////////////////////////////////////////////////////////
void turnUD(void){
  if(xL!=512){
    if(0<=xL && xL<=100){arm.up(10);return;}
    if(900<xL && xL<=1024){arm.down(10);return;} 
    if(100<xL && xL<=200){arm.up(20);return;}
    if(800<xL && xL<=900){arm.down(20);return;}
    if(200<xL && xL<=300){arm.up(25);return;}
    if(700<xL && xL<=800){arm.down(25);return;}
    if(300<xL && xL<=400){arm.up(30);return;}
    if(600<xL && xL<=700){arm.down(30);return;}
    if(400<xL && xL<=480){arm.up(35);return;}
    if(540<xL && xL<=600){arm.down(35);return;} 
    }
}
///////////////////////////////////////////////////////////////
void turnLR(void){
  if(yL!=512){
    if(0<=yL && yL<=100){arm.right(0);return;}
    if(900<yL && yL<=1024){arm.left(0);return;}  
    if(100<yL && yL<=200){arm.right(5);return;}
    if(800<yL && yL<=900){arm.left(5);return;}
    if(200<yL && yL<=300){arm.right(10);return;}
    if(700<yL && yL<=800){arm.left(10);return;}
    if(300<yL && yL<=400){arm.right(15);return;}
    if(600<yL && yL<=700){arm.left(15);return;}
    if(400<yL && yL<=480){arm.right(20);return;}
    if(540<yL && yL<=600){arm.left(20);return;}
  }
}
///////////////////////////////////////////////////////////////

void turnCO(void){
  if(arm.servo4.read()>7){
    if(0<=xR && xR<=100){arm.close(0);return;}
    if(900<xR && xR<=1024){arm.open(0);return;} 
    if(100<xR && xR<=200){arm.close(5);return;}
    if(800<xR && xR<=900){arm.open(5);return;}
    if(200<xR && xR<=300){arm.close(10);return;}
    if(700<xR && xR<=800){arm.open(10);return;}
    if(300<xR && xR<=400){arm.close(15);return;}
    if(600<xR && xR<=700){arm.open(15);return;}
    if(400<xR && xR<=480){arm.close(20);return;}
    if(540<xR && xR<=600){arm.open(20);return;} 
    }
  else{arm.servo4.write(8);

  }  
}
///////////////////////////////////////////////////////////////
void date_processing(int *x,int *y){
  if(abs(512-*x)>abs(512-*y))
    {*y = 512;}
  else
    {*x = 512;}
}
///////////////////////////////////////////////////////////////
void buzzer(int H,int L){
  while(yR<420){
    digitalWrite(buzzerPin,HIGH);
    delayMicroseconds(H);
    digitalWrite(buzzerPin,LOW);
    delayMicroseconds(L);
    yR = arm.JoyStickR.read_y();
    }
  while(yR>600){
    digitalWrite(buzzerPin,HIGH);
    delayMicroseconds(H);
    digitalWrite(buzzerPin,LOW);
    delayMicroseconds(L);
    yR = arm.JoyStickR.read_y();
    }
}
///////////////////////////////////////////////////////////////
void C_action(void){
  if(yR>800){
    int *p;
    p=arm.captureAction();
    for(char i=0;i<4;i++){
    act[num][i]=*p;
    p=p+1;     
    }
    num++;
    num_do=num;
    if(num>=act_max){
      num=0;
      buzzer(600,400);
      }
    while(yR>600){yR = arm.JoyStickR.read_y();}
    //Serial.println(act[0][0]);
  }
}
///////////////////////////////////////////////////////////////
void Do_action(void){
  if(yR<220){
    buzzer(200,300);
    for(int i=0;i<num_do;i++){
      arm.do_action(act[i],15);
      }
    num=0;
    while(yR<420){yR = arm.JoyStickR.read_y();}
    for(int i=0;i<2000;i++){
      digitalWrite(buzzerPin,HIGH);
      delayMicroseconds(200);
      digitalWrite(buzzerPin,LOW);
      delayMicroseconds(300);        
    }
  }
}
///////////////////////////////////////////////////////////////
void setup() {
  Serial.begin(9600);
  //arm of servo motor connection pins
  arm.ServoAttach(4,5,6,7);
  //arm of joy stick connection pins : xL,yL,xR,yR
  arm.JoyStickAttach(A0,A1,A2,A3);
  pinMode(buzzerPin,OUTPUT);
}
///////////////////////////////////////////////////////////////
void loop() {
  xL = arm.JoyStickL.read_x();
  yL = arm.JoyStickL.read_y();
  xR = arm.JoyStickR.read_x();
  yR = arm.JoyStickR.read_y();
  date_processing(&xL,&yL);
  date_processing(&xR,&yR);
  turnUD();
  turnLR();
  turnCO();
  C_action();
  Do_action();
  Serial.println(arm.servo4.read());
}
```

<!---# Bill of Materials
Here's where you'll list the parts in your project. To add more rows, just copy and paste the example rows below.
Don't forget to place the link of where to buy each component inside the quotation marks in the corresponding row after href =. Follow the guide [here]([url](https://www.markdownguide.org/extended-syntax/)) to learn how to customize this to your project needs. 

| **Part** | **Note** | **Price** | **Link** |
|:--:|:--:|:--:|:--:|
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |
| Item Name | What the item is used for | $Price | <a href="https://www.amazon.com/Arduino-A000066-ARDUINO-UNO-R3/dp/B008GRTSV6/"> Link </a> |

# Other Resources/Examples
One of the best parts about Github is that you can view how other people set up their own work. Here are some past BSE portfolios that are awesome examples. You can view how they set up their portfolio, and you can view their index.md files to understand how they implemented different portfolio components.
- [Example 1](https://trashytuber.github.io/YimingJiaBlueStamp/)
- [Example 2](https://sviatil0.github.io/Sviatoslav_BSE/)
- [Example 3](https://arneshkumar.github.io/arneshbluestamp/)

To watch the BSE tutorial on how to create a portfolio, click here.-->

# Starter Project

<!---**Don't forget to replace the text below with the embedding for your milestone video. Go to Youtube, click Share -> Embed, and copy and paste the code to replace what's below.**-->

<iframe width="560" height="315" src="https://www.youtube.com/watch?v=syb-JsTi7dA" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Summary 

My starter project was the BlueStamp Arduino Starter. There is an Arduino Uno Board and Arduino Shield stacked on top of each other and they are connected to a breadboard with a circuit where a red LED light lights up when you press a button. It is meant to have one input of my choice: a switch, button, pressure sensor, and much more. And one output of my choice could be a motor or a light. The Arduino Uno Board came pre-built and I just had to connect wires to it, but I had to solder all the parts onto my Arduino Shield to build it. 

## Components u=Used

- 1 Arduino Uno
- 1 USB A->B cable
- 1 Arduino Proto Shield
- 1 Breadboard
- 3 Buttons
- 3 LEDs
- 4 Resistors
- 2 Ceramic Capacitors
- 2 8-pin female 0.1" headers (1*6)
- 5 5-pin female 0.1" headers (1*8)

##  Challenges Faced

The biggest challenge that I faced was trying to build the circuit on the breadboard and Arduino Uno becuase I had never done anything like it before so I didn't fully understand how a breadboard worked and how to make it so that I could put multiple circuits on one breadboard so that they would both work but not interfere with each other. Another challenge was mounting the Arduino Proto Shield onto the Arduino Uno because I had soldered the female pins on but they were a little bit offset so the female and male pins would not fit together. I had to resolder it all so that they would line up.

## Next Steps

I plan to start on my main project, the Phone-Controlled Robotic Arm. I have to build the arm, create a Bluetooth connection between the arm and the phone, and code the arm so that the phone can make the arm work remotely.
