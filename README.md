1. Pump Project (Show_1_myPump): Analog & Digital Tank/Pump Control with Alarms

Overview & Process: Built a comprehensive tank level control system in AVEVA Wonderware HMI linked to RSLogix 500 ladder logic (emulated MicroLogix), featuring a pump and valve for fill/drain operations. Analog input (e.g., 4-20mA sensor scaled to N7:0 for level 0-100%) drives dynamic animations (bar graph fill, color shifts on thresholds), while digital controls (e.g., O:0/0 for pump ON/OFF, O:0/1 for valve) handle modes. Alarms trigger at LL (low-low), L (low), HH (high-high), H (high) levels with notifications (visual/audible alerts).

2. Project 2 (Show_2_proj2_hoppers): Dual Hopper Filling System with Conveyor Control

Overview & Process: From the provided PDF, designed a conveyor-based box filling system for pecans/walnuts using color-labeled boxes. Proximity switch (I:0/0) detects arrival, level switch (I:0/1) signals full, red/blue photo eyes (I:0/2, I:0/3) identify labels to select hopper. Conveyor motor (O:0/0) advances boxes, while solenoids (O:0/1 walnut, O:0/2 pecan) dispense nuts.
Technical Implementation: RSLogix 500 ladder logic with XIC/XIO for sensor conditions (e.g., XIC I:0/0 AND I:0/2 OTE O:0/2 for pecan fill), TON for timing (e.g., 5s dispense delay). Wonderware HMI displays hopper status (animations for ON/OFF, totals counter via INC on I:0/0 rising edge).

3. Project 3 (Show_3_proj_calculus_manualPIDShowcase): Vacuum Pump Control System

Overview & Process: From the PDF, developed a custom vacuum control for a receiver system using a VFD pump drive. Vacuum sensor (N7:0, 0-30 inHg scaled) compares to setpoint (15 inHg); logic adjusts pump speed every 10s based on error % (4-15% add/sub 20, 15-30% 60, >30% 100). Note: Lower inHg = more vacuum, no PID block—manual logic sim.
Technical Implementation: RSLogix 500 ladder with CMP for error bands (e.g., SUB setpoint sensor_value >4% branch to ADD speed 20), TIM for 10s interval (TON preset 10000ms). Wonderware HMI shows sensor value (analog display), speed (bar graph), alarms on extremes.

4. Show 4: ( in progress )

5. SCADA Project WW (scada_project_ww): Full Oil Pump SCADA with Filter and Backwash

Overview & Process: Comprehensive SCADA for oil pumping system from ground storage to user pipe, including filter and backwash for cleaning. Main flow: ground oil → pump → filter → pipe; backwash reverses flow to flush filter (e.g., on pressure delta >10 PSI). Includes alarms, notifications, and controls for efficiency.
Technical Implementation: Wonderware HMI with dynamic graphics (pump icons, filter status bars), tags for pressure (analog N7:1), flow (N7:2), backwash valve (O:0/3). RSLogix 500 ladder handles interlocks (e.g., XIC pressure_high OTE backwash_on, TON 300s cycle).
EE Considerations & Examples: Sourcing outputs for valve solenoids (push 24V to load); analog sensors (4-20mA loop powered from 24V supply). Example: Backwash trigger on delta pressure CMP, reversing pump direction (bit flip B3:0/4) to clean without shutdown.
