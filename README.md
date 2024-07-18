# Dual-Axis-Solar-Tracker-
Project upon dual axis solar tracker which could rotate horizontally and vertically.
//Commenting out all the vertical movements testing of horizontal servo with LDR

#include  <Servo.h>

//  180 horizontal max
Servo horizontal;       //Horizontal servo
int servoh = 50;

//Servo vertical;             //vertical servo
//int servov =50;

int servovLimitHigh=125;      //Vertical limits
int servovLimitLow=0;

//LDR connections
int AL =A2;       //LDR A
int BL =A0;     //LDR B
int CL =A3;     //LDR C
int DL =A1  ;    //LDR D

void setup() {
  //LDR connection setup
  pinMode(AL,INPUT);       //LDR at A
  pinMode(BL,INPUT);   //LDR at B
  pinMode(CL,INPUT);   //LDR at C
  pinMode(DL,INPUT);;    //LDR at D
  
  Serial.begin(9600);
  
  //Servo connections
  horizontal.attach(5);
  //vertical.attach(6);
  horizontal.write(50);
  //vertical.write(80);
}

void loop() {
  int A =  analogRead(AL); //left
  int B = analogRead(BL); //Right
  int C=  analogRead(CL); //up
  int D =  analogRead(DL); //down

    
    
    int lrdiff=abs(A-B);
    //Serial.println(lrdiff);
      if(A>B &&  lrdiff>100) 
      {
      servoh= servoh+1;
      horizontal.write(servoh);
      } 
      else if(B>A  &&  lrdiff>100)
      {
      servoh  = servoh-1;
      horizontal.write(servoh);
      }  
      //if(C>D && C-D>100)
      //{
        //servov=servov-1;
        //if(servov < servovLimitLow)
        //{
        //  servov  = servovLimitLow;
       // }
        //vertical.write(servov);
      
      //} else if (D>C  && D-C>150)
      //{
        //servov=servov+1;
        //if(servov > servovLimitHigh){
          //servov  = servovLimitHigh;
        }
        //vertical.write(servov);
      //}
    
    
    delay(100);

  
}


