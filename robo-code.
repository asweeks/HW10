#include <Adafruit_MotorShield.h>
#include <IRremote.h>

int RECV_PIN = 11;
IRrecv irrecv(RECV_PIN);
decode_results results;

Adafruit_MotorShield AFMS = Adafruit_MotorShield();

// The DC motor connected to M1
Adafruit_DCMotor *leftMotor = AFMS.getMotor(1);

// The DC motor connected to M2
Adafruit_DCMotor *rightMotor = AFMS.getMotor(2);

void setup() {
  Serial.begin(19200);
  AFMS.begin();
  leftMotor->setSpeed(150);
  rightMotor->setSpeed(150);
  Serial.println("Startup");
  irrecv.enableIRIn();
}

void forward() {
  Serial.print("Moving forward...");
  leftMotor->run(BACKWARD);
  rightMotor->run(FORWARD);
  delay(1000);
  leftMotor->run(RELEASE);
  rightMotor->run(RELEASE);
  Serial.println("Stopped");
}

void backward() {
  Serial.print("Moving forward...");
  leftMotor->run(FORWARD);
  rightMotor->run(BACKWARD);
  delay(1000);
  leftMotor->run(RELEASE);
  rightMotor->run(RELEASE);
  Serial.println("Stopped");
}
void right() {
  Serial.print("Moving right...");
  leftMotor->run(BACKWARD);
  rightMotor->run(BACKWARD);
  delay(1000);
  leftMotor->run(RELEASE);
  rightMotor->run(RELEASE);
  Serial.println("Stopped");
}

void left() {
  Serial.print("Moving right...");
  leftMotor->run(FORWARD);
  rightMotor->run(FORWARD);
  delay(1000);
  leftMotor->run(RELEASE);
  rightMotor->run(RELEASE);
  Serial.println("Stopped");
}
void loop() {
   if (irrecv.decode(&results)) {
    Serial.println(results.value);
    irrecv.resume();
  }
  char c = Serial.read();
   

  if (c == 'b' || results.value == 1474546994) {
    backward();
  }

  if (c == 'f') {
    forward();
  }
  if(c== 'r'){
right();
  }
  if(c== 'l'){
left();
  }
  
}
