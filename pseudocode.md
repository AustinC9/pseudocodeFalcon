# Falcon 9 re-entry and landing
## Falcon 9 specs
The Falcon 9 rocket consists of two stages. Stage 1 propels the rocket almost into orbit and detaches and then returns to a landing drone "safely". the stage 1 rocket has nine engines that help guide the rocket back down to earh along with other functions:
* reposition rocket vertically after seperation
    * uses nitrogen (cold gas) thrusters to flip over the rocket so that it is head up
        * Uses thrusters to keep attitude vertical
* Uses rocket fuel leftover to burn after it is vertical to slow speeds and keep rocket from burning up as it returns to earth
* deploys grid fins which assist in guiding the rocket without using all reserved fuel
* activates final landing burn which slows rocket down to 20 km/h
* deploys three carbon fiber landing legs to help absorb impact and stabilize rocket on the ground

## Program Falcon 9
```

Functions: 
    INIT cold gas thrusters // to upright and stabalize rocket 
    INIT Airspeed indicators // to determine airspeed used for gridfins, thrusters, and burns 
    INIT Groundspeed indicators // to indicate how fast rocket is moving along the ground to compare to droneship movement 
    INIT GPS // Calculate and communicate positions
    INIT rocketThruster // to assist rocket guidance
    INIT seperation // uses air pressure to seperate stage 1 from stage 2

START(MECO (Main engine cut-off) and seperation of stage 1 rocket)

READ; rocket(x,y) // reads horizontal and vertical position of rocket
INIT seperation
    APP(activateAir) // to seperate stage 1 
    UNTIL(seperation=true)
END seperation


INIT(rocketThruster) 
    fireEngines(A,2)(B,2)UNTIL(x,y)=(0,y)
IF(rocket)=vert THEN(deployGridfins) // to guide
    not APP(fireEngines(A,B)) UNTIL(x,y)=(0,y) 
WHILE(fireEngines) = true THEN(INIT(GPS))
    IF(vert) THEN(deploy gridfins)
WHILE(alt≠0 CALCULATE(vert) IF vert≠0(fireEngines))

END(seperation and restabalizing)
    

DISPLAY(x,y axis of rocket to Droneship)

INIT(airspeed &amp; groundspeed indicactors)

CALCULATE(position and speed for re-entry) 
    IF(speed=4700) THEN(activate re-entry burn to slow speeds)
        NOT(continue calcute speed) 
    ENDIF
IF(re-entry burn successfull) THEN(send droneship position)
    NOT successful READ position
CALCULATE(position and speed) WHILE(re-entry process) = true

END(re-entry sequence)


START(Desecent of stage 1 rocket)

READ(Speed &amp; locations)

CALCULATE(distance &amp; attitude)

IF(att≠vert) THEN(INIT(thruster))
    ELSE INIT gridfins
INPUT position
CASE 
    vert: INIT gridfins 
    non-vert: INIT thrusters to increment/ decrement x value to 0 
ENDCASE 

START(Final landing sequence)
CALCULATE(altitude) // calculates difference in altitude from droneship to rocket
IF(alt=>0 BUT(<300) THEN(fireLandingburn))
    NOT(abortMission)
WHILE(alt=true THEN(deployLandinglegs))
IF(alt=150 THEN(fireEngines) UNTIL alt=0)
    NOT(fireThrusters(A,B))


```





