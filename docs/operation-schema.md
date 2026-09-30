# Complete Operation Schema

## Smart Museum Artifact Conservation System

---

# OS-01 — Perform Sensor Self-Check

### Purpose
Verify that all required sensors are functioning correctly before the system enters normal operation.

### Trigger
The conservation chamber is powered on.

### Inputs
- Temperature sensor
- Humidity sensor
- Light sensor
- Vibration sensor
- Door sensor
- Artifact-condition sensor
- Power sensor

### Preconditions
- Chamber power is available.
- System startup has begun.

### Processing
1. Activate the required sensors.
2. Obtain test readings from each sensor.
3. Check whether each sensor responds correctly.
4. Record the results of the self-check.

### Guard / Condition
All required sensors must be functioning correctly.

### Postconditions
- Sensor status has been verified.
- The system may continue startup if all sensors pass.

### Alternative Flow
If one or more required sensors fail, the chamber cannot enter normal conservation operation.

---

# OS-02 — Verify Environmental-Control Devices

### Purpose
Verify that the environmental-control devices required for artifact conservation are functioning correctly.

### Trigger
System startup.

### Inputs
- Heating/cooling mechanism
- Humidity-control mechanism
- Lighting-control mechanism
- Other environmental-control devices

### Preconditions
- System has power.
- Startup self-check is in progress.

### Processing
1. Test each environmental-control device.
2. Check the response of each device.
3. Record the status of each device.

### Guard / Condition
All required environmental-control devices must be available.

### Postconditions
The status of environmental-control devices is known.

### Alternative Flow
If a required environmental-control device fails, normal conservation operation cannot begin.

---

# OS-03 — Record Artifact Identification

### Purpose
Record the identification information of an artifact placed inside the conservation chamber.

### Trigger
An artifact is placed inside the chamber.

### Inputs
- Artifact identification
- Artifact ID
- Identification information

### Preconditions
- Chamber is operational.
- Artifact is detected inside the chamber.

### Processing
1. Obtain the artifact identification information.
2. Validate the information.
3. Store the artifact identification.
4. Associate the artifact with the current chamber session.

### Postconditions
The artifact identity is recorded and available to the system.

---

# OS-04 — Load Artifact Environmental Profile

### Purpose
Load the environmental conditions required for safe conservation of the artifact.

### Trigger
Artifact identification has been recorded.

### Inputs
- Artifact ID
- Required temperature range
- Required humidity range
- Permitted light exposure
- Permitted vibration threshold

### Preconditions
- Artifact has been identified.
- An environmental profile is available.

### Processing
1. Retrieve the artifact's environmental requirements.
2. Validate the requirements.
3. Load the required limits into the control system.
4. Associate the limits with the artifact.

### Guard / Condition
The environmental profile must be successfully loaded.

### Postconditions
The artifact's required environmental limits are available for monitoring and control.

### Alternative Flow
If the environmental profile cannot be loaded, active conservation cannot begin.

---

# OS-05 — Monitor Environmental Conditions

### Purpose
Continuously monitor the chamber and artifact environment.

### Trigger
An artifact is present inside the chamber.

### Inputs
- Temperature
- Humidity
- Light exposure
- Vibration
- Door status
- Artifact condition
- Power availability

### Preconditions
- Required sensors are functioning.
- Artifact is inside the chamber.

### Processing
1. Read sensor values.
2. Record environmental measurements.
3. Compare measurements with required limits.
4. Detect abnormal conditions.
5. Initiate the appropriate response when necessary.

### Postconditions
- Current environmental conditions are available.
- Abnormal conditions are detected and handled.

---

# OS-06 — Compare Temperature with Permitted Range

### Purpose
Determine whether the actual temperature is within the range required by the artifact.

### Trigger
A temperature reading is received.

### Inputs
- Current temperature
- Minimum permitted temperature
- Maximum permitted temperature

### Preconditions
- Artifact environmental profile has been loaded.
- Temperature sensor is functioning.

### Processing
1. Obtain the current temperature.
2. Compare it with the minimum permitted temperature.
3. Compare it with the maximum permitted temperature.
4. Determine whether the temperature is acceptable.

### Guard / Condition
Temperature is acceptable when:

Minimum Temperature <= Actual Temperature <= Maximum Temperature

### Postconditions
The temperature status is determined.

### Alternative Flow
If the temperature is outside the permitted range, temperature correction is initiated.

---

# OS-07 — Compare Humidity with Permitted Range

### Purpose
Determine whether humidity is within the required range.

### Trigger
A humidity reading is received.

### Inputs
- Current humidity
- Minimum permitted humidity
- Maximum permitted humidity

### Preconditions
- Artifact environmental profile has been loaded.
- Humidity sensor is functioning.

### Processing
1. Obtain the current humidity.
2. Compare it with the minimum permitted value.
3. Compare it with the maximum permitted value.
4. Determine whether humidity is acceptable.

### Postconditions
The humidity status is determined.

### Alternative Flow
If humidity is outside the permitted range, the system identifies the condition as abnormal and initiates the appropriate environmental response.

---

# OS-08 — Adjust Temperature

### Purpose
Attempt to restore the temperature to the required range.

### Trigger
Actual temperature is outside the permitted range.

### Inputs
- Current temperature
- Required temperature range
- Environmental-control mechanism

### Preconditions
- Temperature is outside the permitted range.
- Environmental-control mechanism is available.

### Processing
1. Determine the required temperature correction.
2. Issue an environmental-control command.
3. Allow the control mechanism to respond.
4. Obtain new temperature readings.

### Postconditions
A temperature correction attempt has been made.

### Important Rule
The system must not assume that the correction succeeded merely because a control command was issued.

The actual sensor reading must be checked.

---

# OS-09 — Verify Environmental Recovery

### Purpose
Verify through sensor readings that an environmental correction has actually restored the required condition.

### Trigger
An environmental correction command has been issued.

### Inputs
- New environmental reading
- Required environmental limits
- Allowed recovery period

### Preconditions
- A correction command has been issued.
- Relevant sensor is operational.

### Processing
1. Wait for the required recovery interval.
2. Obtain a new environmental reading.
3. Compare the new reading with the permitted range.
4. Determine whether the condition has recovered.

### Guard / Condition
Recovery is successful when the actual condition is within the required range.

### Postconditions
Either:
- Environmental recovery is confirmed, or
- Failure to recover is identified.

### Alternative Flow
If the condition cannot be corrected within the allowed recovery period, protection measures are activated.

---

# OS-10 — Activate Protection Measures

### Purpose
Protect the artifact when normal environmental recovery cannot be achieved.

### Trigger
An environmental condition remains outside its permitted range after the allowed recovery period.

### Inputs
- Environmental readings
- Artifact environmental requirements
- Recovery status
- Protection controls

### Preconditions
- Artifact is inside the chamber.
- Environmental recovery has failed or exceeded its allowed period.

### Processing
1. Suspend normal conservation activities where necessary.
2. Activate additional environmental controls.
3. Reduce harmful environmental exposure.
4. Generate an alert for the museum operator.
5. Continue monitoring the artifact.

### Postconditions
- Protective measures are active.
- Operator notification is generated.
- Artifact protection is prioritized.

---

# OS-11 — Reduce Light Exposure

### Purpose
Reduce light exposure when necessary to protect the artifact.

### Trigger
Excessive light exposure is detected or protection measures require light reduction.

### Inputs
- Current light exposure
- Permitted light level
- Lighting-control system

### Preconditions
- Artifact is inside the chamber.
- Lighting-control system is available.

### Processing
1. Obtain the current light reading.
2. Compare it with the permitted level.
3. Reduce light exposure.
4. Verify the resulting light level.

### Postconditions
Light exposure is reduced where the control mechanism is available.

---

# OS-12 — Detect Significant Vibration

### Purpose
Detect vibration that may increase the risk to the artifact.

### Trigger
A vibration sensor produces a reading.

### Inputs
- Current vibration level
- Permitted vibration threshold

### Preconditions
- Vibration sensor is functioning.
- Artifact is inside the chamber.

### Processing
1. Obtain the vibration reading.
2. Compare the reading with the permitted threshold.
3. Determine whether the vibration is significant.
4. If significant vibration is detected, suspend activities that could increase risk.

### Guard / Condition
Significant vibration exists when:

Current Vibration > Permitted Vibration Threshold

### Postconditions
Significant vibration is detected and an appropriate response is initiated.

---

# OS-13 — Verify Vibration Stabilization

### Purpose
Confirm that vibration has remained below the permitted threshold for the required stabilization period.

### Trigger
Significant vibration has previously been detected.

### Inputs
- Current vibration readings
- Permitted vibration threshold
- Required stabilization period

### Preconditions
- Significant vibration has been detected.
- Vibration sensor is functioning.

### Processing
1. Continue monitoring vibration.
2. Compare readings with the permitted threshold.
3. Verify that readings remain below the permitted threshold.
4. Measure the stabilization period.
5. Confirm stabilization only after the required period is completed.

### Guard / Condition
Vibration must remain below the permitted threshold for the complete stabilization period.

### Postconditions
Vibration stabilization is confirmed.

### Alternative Flow
If vibration exceeds the threshold again during stabilization, the stabilization period must be restarted.

---

# OS-14 — Suspend Conservation Activities

### Purpose
Immediately suspend normal conservation activities when the chamber door is opened.

### Trigger
The chamber door is opened while conservation is active.

### Inputs
- Door status
- Current conservation activities

### Preconditions
- Artifact is inside the chamber.
- Conservation activity is in progress.

### Processing
1. Detect the door-open condition.
2. Immediately suspend normal conservation activities.
3. Continue monitoring relevant conditions.
4. Prevent normal environmental operation while the door remains open.

### Postconditions
Normal conservation activities are suspended.

### Alternative Flow
When the door is closed again, conservation must not automatically resume.

The system must verify environmental conditions and sensor status first.

---

# OS-15 — Verify Safe Artifact Removal

### Purpose
Ensure that an operator can remove an artifact only when the chamber is safe.

### Trigger
An operator requests artifact removal.

### Inputs
- Environmental conditions
- Sensor status
- Chamber status
- Artifact status
- Protection-response status

### Preconditions
- Artifact is inside the chamber.
- Operator has requested removal.

### Processing
1. Check environmental conditions.
2. Verify sensor status.
3. Check chamber status.
4. Determine whether a protection response is active.
5. Confirm that conditions are safe.

### Guards / Conditions

Artifact removal is permitted only when:

Chamber Condition = Safe

AND

No Active Protection Response

AND

Required Sensors = Operational

### Postconditions
If all conditions are satisfied, artifact removal may proceed.

### Alternative Flow
If any safety requirement is not satisfied, artifact removal is prevented.

---

# OS-16 — Switch to Emergency Power

### Purpose
Maintain system operation using an emergency power source when primary power is lost.

### Trigger
Primary power becomes unavailable.

### Inputs
- Primary power status
- Emergency power availability

### Preconditions
- System is operating.
- Primary power failure has been detected.

### Processing
1. Detect primary power failure.
2. Check whether emergency power is available.
3. Switch the system to emergency power.
4. Verify emergency power operation.

### Guard / Condition
Emergency power must be available.

### Postconditions
The system operates using emergency power.

### Alternative Flow
If emergency power is unavailable, the system records the incident and performs a safe shutdown.

---

# OS-17 — Record Power Failure Incident

### Purpose
Record power failure information for auditing and later analysis.

### Trigger
A power failure occurs.

### Inputs
- Power status
- Timestamp
- Chamber status
- Artifact status
- Emergency power status

### Preconditions
Power failure has been detected.

### Processing
1. Record the power failure.
2. Record the time of the incident.
3. Record chamber status.
4. Record artifact status.
5. Record whether emergency power was available.

### Postconditions
The power failure incident is stored.

---

# OS-18 — Perform Safe Shutdown

### Purpose
Place the system into a safe condition when usable power is unavailable.

### Trigger
Primary and emergency power are unavailable.

### Inputs
- Power status
- Current system status
- Artifact status
- Chamber status

### Preconditions
- Primary power is unavailable.
- Emergency power is unavailable.

### Processing
1. Stop non-essential activities.
2. Preserve important system information.
3. Record the current system status.
4. Place equipment into a safe shutdown condition.

### Postconditions
- System is safely shut down.
- Important incident information is preserved.
- The system does not continue normal conservation operation without adequate power.
