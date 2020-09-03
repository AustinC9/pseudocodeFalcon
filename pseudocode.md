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
'''
<! Deconstruct: did launch go as planned, re-position itself to make fall back onto droneship, deploy grid fins, calculate needed speeds and positions to land appropiately, re-entry burn and landing burn, landing legs  >

<!Objects: equalizing and balancing rocket, re-entry burn, Airspeed of rocket, Ground speed of rocket, Fuel left on board, locations of droneship, difference of altitude of rocket vs droneship, final landing burn,  deploying carbon fiber landing legs,>
<!Functions: INIT cold gas thrusters to upright and stabalize rocket
INIT Airspeed indicators
INIT Groundspeed indicators
INIT GPS
INIT Thrust >

Start: MECO (Main engine cut-off) and seperation of stage 1 rocket
Read: horizontal and vertical position of stage 1 rocket
ifVert deploy gridfins to guide
    not compute x,y positions 
INIT cold gas thrusters to stabalize rocket
    ifVert THEN deploy gridfins
        NOT calculate attitude
INIT GPS
Display: x,y axis of rocket to Droneship
INIT airspeed and groundspeed indicactors
Calculate poisition and speed needed for re-entry
    IF speed>4700 km/h THEN activate re-entry burn to slow speeds
        NOT continue calcute speed 
    ENDIF
IF re-entry burn successfull THEN send droneship position
    NOT successful READ position

END re-entry sequence


Start: Desecent of stage 1 rocket
Read: Speeds and locations
Calculate distance and attitude
IF att \= vert THEN activate gridfins
    ELSE INIT thrusters
INPUT position
CASE 
    vert: INIT gridfins 
    non-vert: INIT thrusters to increment/ decrement x value to 0 
ENDCASE 

Start: Final landing sequence
'''





