# PROG101_ASSIGNMENT1_EMMANUEL_ROLAND_FAULKNER_905006547
This is Assignment one for programming Logic and Design About the busiest of traffic in the Congo cross road 

## PROBLEM DESCRIPTION 
Congo Cross is one of the busiest road intersections in Freetown, connecting traffic from the city centre, the east end and the western peninsula. At peak hours vehicles queue in every direction,signals (where they work) run on fixed timings that ignore how many vehicles are actually waiting,and traffic officers must manage the junction by hand. The result is long delays, wasted fuel, higher exhaust pollution, late workers and students, and slow passage for ambulances and fire engines.

### PEOPLE AFFECTED  
office workers , commercial drivers (okada, keke, poda-poda and taxi operators),pedestrians, school children, traffic police and emergency services.

#### PROPOSED SOLUTIONS  
A modular traffic-control logic that repeats in cycles. In each cycle it 
(1) Reads vehicle counts and emergency flags for North, East, South and West approaches. (2) Validates the data.
(3) overrides normal timing if an emergency vehicle is present.
(4)Calculates a green time and a priority score for every approach.
(5)Activates signals in priority order
(6)Logs the cycle for later analysis by planners.

##### SDG ALIGNMENT 
The project mainly supports Sustainable Development Goal.
SDG 11 (Sustainable Cities and Communities): safer, more efficient urban transport.This goal includes making public transportation affordable and and creating safe roads and public spaces
SDG 9 (Industry, Innovation and Infrastructure): resilient, low-cost digital infrastructure.It focuses on improving roads, bridges, transportation, technology, and communication systems. It also encourages the use of modern technology to create jobs, support businesses, and improve people's lives.
 SDG 3 (Good Health and Well-being): faster ambulance passage, fewer road injuries and less
air pollution
SDG 13 (Climate Action): less idling means lower emissions.

##### PSEUDOCODE
Pseudocode is a simple way of explaining the steps a system follows to solve a problem. It uses plain English and basic programming instructions without following the rules of a specific programming language. In this project, pseudocode explains how to control the traffic problem at Congo cross


START

Set MIN_GREEN = 15 seconds
Set MAX_GREEN = 90 seconds
Set DEFAULT_GREEN = 30 seconds
Set WAIT_WEIGHT = 10
Set VEHICLE_FACTOR = 2
Set AMBER_TIME = 3 seconds

For each of the 4 roads, keep: car count, waiting turns,
green time, score, emergency flag
Set waiting turns to 0 for every road

REPEAT
    Read the sensors (car counts and emergency flags)

    IF any count is missing or below 0 THEN
        Run the default plan (DEFAULT_GREEN for each road in turn)
        Write "SENSOR FAULT" in the log

    ELSE
        Check if any road has an emergency vehicle

        IF there is an emergency THEN
            Make that road green and all other roads red
            WHILE the emergency is still there
                Read the sensors again
            END WHILE
            Write "EMERGENCY PRIORITY" and the road number in the log

        ELSE
            FOR each road
                IF car count = 0 THEN
                    Green time = MIN_GREEN
                ELSE
                    Green time = MIN_GREEN + (VEHICLE_FACTOR x car count)
                    IF green time > MAX_GREEN THEN
                        Green time = MAX_GREEN
                    END IF
                END IF
                Score = car count + (WAIT_WEIGHT x waiting turns)
            END FOR

            Find the road with the highest score
            Show GREEN for that road for its green time
            Show AMBER for AMBER_TIME, then RED
            Set that road's waiting turns to 0

            FOR each other road
                Add 1 to its waiting turns
            END FOR

            Show the signal plan
            Write "NORMAL" in the log
        END IF
    END IF

UNTIL the user presses stop

END

## ALGORITHM 
Constants: MIN_GREEN = 15 s, MAX_GREEN = 90 s, DEFAULT_GREEN = 30 s, WAIT_WEIGHT = 10, VEHICLE_FACTOR = 2 s per vehicle. Variables: count[1..4] (integer), emergency[1..4] (Boolean), waiting[1..4] (integer), green[1..4] (integer seconds). Approaches: 1 = North, 2 = East, 3 = South, 4 = West. 
1. Start. Set constants and set waiting[i] = 0 for all approaches.
2.  2. Read count[i] and emergency[i] for i = 1 to 4.
3. Validate: if any count is negative or missing, run the DEFAULT plan (DEFAULT_GREEN for each approach), log a sensor fault, go to step 11.
4. If any emergency[i] is TRUE, give that approach green, set all others red, hold until emergency[i] becomes FALSE, log it, go to step 11.
5. For each approach i, calculate green[i] = MIN_GREEN + VEHICLE_FACTOR x count[i]; cap at MAX_GREEN; if count[i] = 0 use MIN_GREEN.
6. For each approach i, calculate score[i] = count[i] + WAIT_WEIGHT x waiting[i].
7. Sort approaches from highest to lowest score.
8. Activate green for each approach in that order for green[i] seconds (with a 3 s amber between phases).
9. Update waiting: set waiting[i] = 0 for approaches served; add 1 to waiting[i] for any approach not served this cycle.
10. Display the signal plan (output).
11. Log the cycle (time, counts, plan, events). If stop is not requested, return to step 2; otherwise end.



## FLOWCHART 

Figure 1: Main system Flowchart (drawn to show input, processing, output, decision, and repetition)
<img width="1284" height="1105" alt="image" src="https://github.com/user-attachments/assets/6f62ba4a-da50-4533-a633-48c7b51d79f3" />
Figure 2:Flowchart of the calculateGreenTime(count) function 
<img width="3797" height="2628" alt="image" src="https://github.com/user-attachments/assets/199b988f-1fe4-4cf1-9d31-209b0ec1bcef" />

## AUTHOR
EMMANUEL ROLAND FAULKNER - 905006547

