email : cklam12345@gmail.com

This is a fix for 3479 driver used by Arduino UNO but failed on Esp32. the change is minor and involve the break up of WWire_request from 5 argument(not documented by Arduino Commumity) to 3 argument. Additional set to the Ai thinker default SDA SDC for I2c is also performed.

#define SIOD_GPIO_NUM  26
#define SIOC_GPIO_NUM  27


refer to change from original master 

423     /** I2C read function */
424     //Wire.requestFrom(chip_select,1);
425     //value = Wire.read();
426     Wire.beginTransmission(chip_select);
427     Wire.write(reg);
428     if(!Wire.endTransmission()){
429     Wire.requestFrom(chip_select,1,true);
430
431       value = Wire.read();
432
433
434     delayMicroseconds(100);
435     } else {
436       Serial.println("> nack");
# 3479A_esp32_driver
