# Servo Motor with Arduino UNO

مهام الاسبوع الثاني



----------------------------------------------------------------------------------------------------------------------------------------------------------------


## المقدمة

تم عمل المشروع باستخدام برنامج الاوردينو وبرنامج التنكر كاد للتحكم بمحرك يعمل على حركة بزوايا دقيقة يسمى السرفو موتر ويستخدم عادة باذرع الروبوتات للتحرك من درجة 0 الى 180 درجة بالاضافة الى مقاوم متغير تتغير حركة السرفو موتر بتغير المقاوم المتغير مما يجعل ذلك سهولة التحكم بزاوية السرفو موتر  















## تم انشاء المشروع باستخدام


1-استخدام Arduino IDE 1.8.19 [للتنزيل](https://www.arduino.cc/en/software)



2-استخدام AUTODESK TINKERCAD [انقر هنا](https://www.tinkercad.com/)









## الادوات المطلوبة

1-اوردينو اونو

2-سرفو موتر

3-بطارية 5 فولت

4-اسلاك

5-مقاوم متغير

6-لوحةPCA9685 













## طريقة التوصيل

##### 1-استخدام السرفو موتر متصل مع الاوردينو اونو  


> توصيل السلك الاحمر من البطارية الى السرفو موتر 

> توصيل السلك الاسود من الطارية الى السرفو موتر ومن السرفو موتر الى PIN الارضي GRN في الاردينو اونو

> توصيل السلك الاخضر من السرفو موتر signal الى PIN 9




##### 2- استخدام السرفو موتر مع مقاوم متغير على breadboard متصل على الاوردينو اونو



> توصيل السلك الاخضر من السرفو موتر  signal الى pin 9 

> توصيل السلك الاسود ground من البطارية الى السرفو موتر وثم توصيله من البطارية الى breadboard ثم الى الاوردينو GNR 

> توصيل السلك الاحمر من الطارية الى السرفو موتر power وثم توصيله من البطارية الى breadboard ومن ثم الى الاوردينو 5V

> توصيل المقاوم المتغير على ال breadboard وتوصيل الاقطاب positive : negative ثم توصيل السلك الازرق من المقاوم المتغير الى الاوردينو PIN A0  



##### 3-استخدام السرفو موتر مع PCA9586 متصل مع الاوردينو اونو

> توصيل SCL من PCA9685 الى الاوردينو SCL
> 
> توصيل SDA من PCA9685 الى الاوردينو SDA
> 
> توصيل GNR من PCA9685 الى الوردينو GNR
> 
> توصيل VCC من PCA9685 الى الاوردينو 5V
> 
> توصيل السرفو موتر الى PCA9685-OUTPUT 0
> 
> توصيل البطارية 5V الى PCA9685



##### 4-استخدام السرفو موتر مع مفاوم متغير مع PCA9685 متصل مع الاوردينو اونو

>  توصيل SCL من PCA9685 الى الاوردينو SCL
> 
> توصيل SDA من PCA9685 الى الاوردينو SDA
> 
> توصيل GNR من PCA9685 الى الوردينو GNR
> 
> توصيل VCC من PCA9685 الى الاوردينو 5V
> 
> توصيل السرفو موتر الى PCA9685-OUTPUT 0
> 
> توصيل البطارية 5V الى PCA9685

> توصيل المقاوم المتغير SIGNAL الى الاوردينو A0

> توصيل المقاوم المتغير GNR الى الاوردينو GNR

> توصيل المقاوم المتغير VDD الى الاوردينو 5V




## الرسم البياني والمحاكاة



 [للمشاهدة انقر هنا](https://www.tinkercad.com/things/kn2olnurWz0-powerful-blorr-sango/editel)









![Powerful Blorr-Sango (3)](https://user-images.githubusercontent.com/109243989/179120601-ea58e642-6070-4107-af1e-417b5e145e55.png)

تحرك السرفو موتر من 0 الى 100 درجة 







![Powerful Blorr-Sango (4)](https://user-images.githubusercontent.com/109243989/179120731-16ad697c-a20f-4f6a-8fe0-e2bd42842e7e.png)

تحرك السرفو موتر من 100 الى 0 درجة
## the code

// Include Wire Library for I2C Communications

#include <Wire.h>

// Include Adafruit PWM Library

#include <Adafruit_PWMServoDriver.h>

#define MIN_PULSE_WIDTH 650

#define MAX_PULSE_WIDTH 2350

#define FREQUENCY 50

Adafruit_PWMServoDriver pwm = Adafruit_PWMServoDriver();

// Define Potentiometer Inputs

int controlA = A0;

// Define Motor Outputs on PCA9685 board

int motorA = 0;

void setup() { pwm.begin();

pwm.setPWMFreq(FREQUENCY);

}

void moveMotor(int controlIn, int motorOut)

{ int pulse_wide, pulse_width, potVal;

// Read values from potentiometer

potVal = analogRead(controlIn);

// Convert to pulse width

pulse_wide = map(potVal, 0, 1023, MIN_PULSE_WIDTH, MAX_PULSE_WIDTH);

pulse_width = int(float(pulse_wide) / 1000000 * FREQUENCY * 4096);

//Control Motor

pwm.setPWM(motorOut, 0, pulse_width);

}

void loop() {

//Control Motor A

moveMotor(controlA, motorA);

}


--------------------------------------------------------------------------------------------------------------------------------------------------






 [انقر هنا للمشاهدة](https://www.tinkercad.com/things/j3NHTseED0d-exquisite-fulffy-bojo/editel)









![Exquisite Fulffy-Bojo (2)](https://user-images.githubusercontent.com/109243989/179135920-b5f51e0a-0d67-4187-9986-c6a84dbe8aab.png)











![Exquisite Fulffy-Bojo (3)](https://user-images.githubusercontent.com/109243989/179136028-f95ea52c-69ce-4022-b8c3-c10472559571.png)


## The code
#include <Servo.h>

Servo myservo; // create servo object to control a servo

int potpin = 0; // analog pin used to connect the potentiometer

int val; // variable to read the value from the analog pin

void setup() { myservo.attach(9); // attaches the servo on pin 9 to the servo object }

void loop() {

val = analogRead(potpin); // reads the value of the potentiometer (value between 0 and 1023)

val = map(val, 0, 1023, 0, 180); // scale it to use it with the servo (value between 0 and 180)

myservo.write(val); // sets the servo position according to the scaled value

delay(15); // waits for the servo to get

}


-------------------------------------------------------------------------------------------------------------------------------------------------




![SERVO 1](https://user-images.githubusercontent.com/109243989/179320926-e6591b4a-a00e-402a-8bdb-570356992b22.png)


## The Code

#include <Wire.h>

#include <Adafruit_PWMServoDriver.h>

Adafruit_PWMServoDriver pwm = Adafruit_PWMServoDriver();

#define MIN_PULSE_WIDTH 650

#define MAX_PULSE_WIDTH 2350

#define DEFAULT_PULSE_WIDTH 1500

#define FREQUENCY 50

int servonum =0;

void setup() {

Serial.begin(9600);

Serial.println("16 channel Servo test!");

pwm.begin();

pwm.setPWMFreq(FREQUENCY);

} int pulseWidth(int angle) { int pulse_wide, analog_value;

pulse_wide = map(angle, 0, 180, MIN_PULSE_WIDTH, MAX_PULSE_WIDTH);

analog_value = int(float(pulse_wide) / 1000000 * FREQUENCY * 4096);

Serial.println(analog_value);

return analog_value;

}

void loop() {

pwm.setPWM(0, 0, pulseWidth(0));

delay(1000);

pwm.setPWM(0, 0, pulseWidth(90));

delay(500);

pwm.setPWM(0, 0, pulseWidth(120));

delay(1000);

}


![SERVO2](https://user-images.githubusercontent.com/109243989/179321150-952b5dae-a0ff-4c5e-9ae3-ee2a2201e676.png)


The code

// Include Wire Library for I2C Communications

#include <Wire.h>

// Include Adafruit PWM Library

#include <Adafruit_PWMServoDriver.h>

#define MIN_PULSE_WIDTH 650

#define MAX_PULSE_WIDTH 2350

#define FREQUENCY 50

Adafruit_PWMServoDriver pwm = Adafruit_PWMServoDriver();

// Define Potentiometer Inputs

int controlA = A0;

// Define Motor Outputs on PCA9685 board

int motorA = 0;

void setup() { pwm.begin();

pwm.setPWMFreq(FREQUENCY);

}

void moveMotor(int controlIn, int motorOut)

{ int pulse_wide, pulse_width, potVal;

// Read values from potentiometer

potVal = analogRead(controlIn);

// Convert to pulse width

pulse_wide = map(potVal, 0, 1023, MIN_PULSE_WIDTH, MAX_PULSE_WIDTH);

pulse_width = int(float(pulse_wide) / 1000000 * FREQUENCY * 4096);

//Control Motor

pwm.setPWM(motorOut, 0, pulse_width);

}

void loop() {

//Control Motor A

moveMotor(controlA, motorA);

}

