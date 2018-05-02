# SEIS744IoT
IoT Final Project 


// This #include statement was automatically added by the Particle IDE.
#include <RelayShield.h>

// Create an instance of the RelayShield library, so we have something to talk to
RelayShield myRelay;

// Create prototypes of the Spark.functions that I declare in setup()
int relayOn(String command);
int relayOff(String command);
int toggleRelay(String command);



void setup() {
    
    myRelay.begin();

    // Register Spark.functions and assign them names
    Particle.function("relayOn", relayOn);
    Particle.function("relayOff", relayOff);
    Particle.function("toggleRelay", toggleRelay);

}

int relayOn(String command){

    // Turn on Relay 1  
    // Within the Do Button config I call Relay 1 by passing through variable = 1
    myRelay.on(1);
    
    // Respond
    return 1;    
}


// Momentarily turn on, then off Relay 1
// This simulates a button press.  Again, pass in value 1 for Relay 1
// In IFTTT Do Button app I called the Photon 'stacianicole', then pointed the function to toggleRelay, and in the arguments field I just put 1 
int toggleRelay(String command){

    // Turn the desired relay on
    myRelay.on(1);
    delay(1000);
    myRelay.off(1);
    // Respond
    return 1;    
}

//  This is used in toggleRelay, however, it can also be used stand alone if you have a normally closed relay and want to temporarily open it.
int relayOff(String command){
    
    // Turn the desired relay off
    myRelay.off(1);
    
    // Respond
    return 1;    
}
