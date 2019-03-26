# code
Mushroom farming
*PROGRAM FOR RASPBERRYPI MODEL 3B+*/
/*PROGRAM SOURCE - https://www.github.com/gs369/mushroompi*/

/*LIBRARY*/
#include<stdio.h>
#include<wiringPi.h>
#include<string.h>
/*DECLARAION OF RASPBERRYPI PINS*/
#define RELAY 9		//Moisture Pump
#define RELAY2 11	//Cooling Pump
#define RELAY3 0	//Nutrient Pump
#define RELAY4 18	//bulb
#define RELAY5 6 	//Heater
#define SOIL_S 17	//SOIL SENSOR
#define TEMP_S 22	//TEMPERATURE SENSOR
#define LIGHT_S 27	//LIGHT SENSOR(LDR)
#define ION_S 10 	//NUTRIENT SENSOR(ION)
/*FOR LINES*/
char *dash(char *buf, int len ) {
   memset(buf, '-', len);
   buf[len] = 0;
   return buf;
}
/*DISPLAY - PROJECT,NAME,STUDENT_ID,INSTRUCTORS*/
int main (void)
{
	char buf[60];
	printf("%s\n", dash(buf,60));
	printf("PROJECT     : EMBEDDING EMBEDDED IN MUSHROOM GROWING\n");
	printf("%s\n", dash(buf,60));
	printf("BY          : NAME\t\t\tSTUDENT ID\n");
	printf("              GURLAL SINGH\t\tC0717098\n");
	printf("              SANDEEP KAUR\t\tC0722494\n");
	printf("              HARPREET SINGH\t\tC0719364\n");
	printf("              HARJAP KAUR\t\tC0721913\n");
	printf("%s\n", dash(buf,60));
	printf("INSTRUCTORS : PROF. TAKIS ZOURNTOS\n\t      PROF. MIKE ALESHAMS\n");
	printf("%s\n", dash(buf,60));
	/*GPIO*/
	wiringPiSetupGpio();
	/*WiringPi GPIO*/
	/*DECLARATION OF OUTPUTS*/
	pinMode(RELAY,OUTPUT);	//Moisture Pump
	pinMode(RELAY2,OUTPUT);	//Cooling Pump
	pinMode(RELAY3,OUTPUT);	//Nutrient Pump
	pinMode(RELAY4,OUTPUT);	//BULB
	pinMode(RELAY5,OUTPUT); //HEATER
	/*DECLARATION OF INPUTS*/
	pinMode(SOIL_S,INPUT);
	pinMode(TEMP_S,INPUT);
	pinMode(LIGHT_S,INPUT);
	pinMode(ION_S,INPUT);
        digitalWrite(RELAY3,LOW);
        digitalWrite(RELAY5,LOW);

	/*SENSOR FUNCTIONS*/
	while(1){
	if(digitalRead(SOIL_S)==1){
	   digitalWrite(RELAY,HIGH);
	}
	else{
	  digitalWrite(RELAY,LOW);
		}
	}
	if(digitalRead(TEMP_S)==0){
	 digitalWrite(RELAY2,HIGH);
	}
	else{
	 digitalWrite(RELAY2,LOW);
	}
	if(digitalRead(LIGHT_S)==0){
	 digitalWrite(RELAY4,HIGH);
	}
	else{
 if(digitalRead(LIGHT_S)==0){
         digitalWrite(RELAY4,HIGH);
        }
        else{
         digitalWrite(RELAY4,LOW);
        }
 	 digitalWrite(RELAY4,LOW);
	}
	if(digitalRead(ION_S)==0){
	 digitalWrite(RELAY5,HIGH);
	}
	else{
	 digitalWrite(RELAY5,LOW);
	}
return 0;
}
//int x;
//for (x=0;x<5;x++);
