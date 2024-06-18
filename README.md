//Canal de YouTube -> Robot UNO
//Proyecto -> Brazo robotico version1
#include <Servo.h>
#include <Stepper.h>
Servo servomotor3; //Servomotor pinza
Servo servomotor2; //Servomotor enmedio
Servo servomotor1; //Servomotor abajo
Stepper motor(2048, 4, 6, 5, 7);
void setup() {
  servomotor3.attach(11);
  servomotor2.attach(10);
  servomotor1.attach(9);
  motor.setSpeed(5);
}
void loop() {
  //Reinicio
  servomotor1.write(0);
  servomotor2.write(0);
  servomotor3.write(0);
  //motor.step(512);
  delay(3000);
  //COJE EL OBJETO
  for(int i=0; i<=45; i++){
    servomotor3.write(i);
    delay(25);
  }
  delay(1000); 
  for(int i=0; i<=90; i++){
    servomotor2.write(i);
    delay(25);
  }
  delay(1000);  
  for (int i=0; i<=90; i++){
    servomotor1.write(i);
    delay(25);
  }
  delay(1000);
  for(int i=45; i>=0; i--){
    servomotor3.write(i);
    delay(25);
  }
  delay(1000);
   for (int i = 90; i>=0; i--){
    servomotor1.write(i);
    delay(25);
  }
  delay(1000);
  for (int i = 90; i>=0; i--){
    servomotor2.write(i);
    delay(25);
  }
  delay(1000);
  //GIRA CON EL OBJETO
  motor.step(512);
  delay(1000);
  //DEJA EL OBJETO
  for(int i=0; i<=90; i++){
    servomotor2.write(i);
    delay(25);
  }
  delay(1000);
  for (int i=0; i<=90; i++){
    servomotor1.write(i);
    delay(25);
  }
  delay(1000);  
  for(int i=0; i<=45; i++){
    servomotor3.write(i);
    delay(25);
  }
  delay(1000);
  //VUELVE A LA POSICION INICIAL
  servomotor1.write(0);
  servomotor2.write(0);
  motor.step(-512);
  delay(3000);
}
