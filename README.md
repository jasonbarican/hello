*add Motor library
*add sensor library

int curDist = 0;
int speedSet = 0;
int colldist = 30;
int MAX_SPEED_OFFSET 40

void setup() {
  myservo.attach(10);  // attaches the servo on pin 10 
  delay(1000); // delay for one seconds
 }

//this is the main loop
void loop() {
  delay(100);
  curDist = readPing();   // read distance
  if (curDist < colldist) {turnRight();}  // if distance is certain value, robot turns right
  moveForward();  
  delay(500);
 }

void turnRight() {
  motorSet = "RIGHT";
  leftMotor1.run(FORWARD);      // turn motor 1 forward
  leftMotor2.run(FORWARD);      // turn motor 2 forward
  rightMotor1.run(BACKWARD);    // turn motor 3 backward
  rightMotor2.run(BACKWARD);    // turn motor 4 backward
  rightMotor1.setSpeed(speedSet+MAX_SPEED_OFFSET);      
  rightMotor2.setSpeed(speedSet+MAX_SPEED_OFFSET);     
  delay(1500); // run motors this way for 1500         
}  

void moveForward() {
    motorSet = "FORWARD";
// turn it on going forward
    leftMotor1.run(FORWARD);      
    leftMotor2.run(FORWARD);      
    rightMotor1.run(FORWARD);     
    rightMotor2.run(FORWARD);     
    
  }
  
// read the ultrasonic sensor distance
int readPing() { 
  delay(70);   
  unsigned int uS = sonar.ping();
  int cm = uS/US_ROUNDTRIP_CM;
  return cm;
}
