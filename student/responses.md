# Week 07 Controls Lab — Responses

Answers and recorded model results from `submission.json`. This document does not recompute or independently validate the results.

## Submission status

- Schema: week07.submission/v1

- Record ID: dd466b20-b9e4-4877-bf60-c6b0f1baba07

- Record revision: 1182

- Model hash: fnv1a-596d5cb5

- Readiness: Marked incomplete or not ready; missing: claim, reflection, aiUse

## Supplied setup (instructor supplied)

### question — instructor supplied
Calculate required control moment, elevator moment, and the change with airspeed. Explain whether the nominal response meets +0.12 rad/s².

### system — instructor supplied
Illustrative planar pitch model. Aircraft geometry, integration, force conversion and constraints are supplied.

### representation — instructor supplied
Body axes forward/right/down. Positive pitch moment nose-up. Positive Fz downward. Positive elevator trailing edge down. Reference/CG X=0 m; tail X=-3 m.

### inputs — instructor supplied
Iy=5000 kg·m²; target=+0.12 rad/s²; competing=-750 N-m; density=1.225 kg/m³; V=40 m/s; S=16 m²; chord=1.5 m; Cmδ=-0.8/rad; elevator=-5°. Inputs are illustrative, not calibrated.

## Student responses

### physics
**Prompt:** Explain why a downward force aft of the CG gives a positive nose-up moment.

**Student response:**
```
aft cg by x tail = -3m from the cg. which creates a rotation around the cg, resulting in a nose up pitch moment 
```

### assumptions
**Prompt:** Explain one supplied assumption and what could invalidate it: planar motion, fixed reference, local linear effectiveness, no trim or damping.

**Student response:**
```
local linear effectiveness, invalidation is control surface stall or flow separation when the elevator over deflect3ed
```

### model
**Prompt:** Write your demand, dynamic-pressure, coefficient and moment equations. Identify which quantities are supplied and which are unknown.

**Student response:**
```
demand = (Iy)(target)-competing
dynamic pressure is q infinity
delta Cm = Cmδ × δe
Cm = M/(qinfinity)S(C)
M=(Cm)(Qinfinity)(S)(C)

Supplied ρ V S C Cmδ, Iyy, q target
unknown q infinity delta Cm and M


```

### prediction
**Prompt:** Before running your own implementation, predict the sign of its elevator moment and the effect of halving airspeed. Explain the competing moment.

**Student response:**
```
Sign of Elevator Moment: Negative
for a trailing-edge UP deflection (which produces a downward force aft of CG, causing nose-UP rotation 
M corelates to Vsquared
reducing V reduces M/4 

wing and body pitching moment, CG, drive opposite with elevator input

```

### verification
**Prompt:** Show one independent hand calculation with units. Compare it with your model, and explain a sign, unit, or limiting-case check.

**Student response:**
```
v=20m/s

q infinity = 1/2 pv^2=0.5x1.225x20=245Pa
delta Cm = -0.8x-0.087266 = 0.069813
M elevator = 245 x 16 x1.5 x0.069813 = 410.501
q dot = -339.499/ 5000= -0.067900
```

### claim
**Prompt:** What do your computed results support at the stated condition? Include a limitation.

**Student response:**
_Missing — no response supplied._

### reflection
**Prompt:** What additional evidence or missing physics would you investigate next?

**Student response:**
_Missing — no response supplied._

### AI use
**Prompt:** Identify the AI tool and how you used it, what you changed, and how you independently checked the result. State “No AI used” if applicable.

**Student response:**
_Missing — no response supplied._

## Equations and model source

The recorded model JSON/expression source follows exactly as supplied. It is not interpreted or recomputed here.

```
{
  "schemaVersion": "week07.student-model/v1",
  "id": "week07-student-model",
  "version": "1.0.0",
  "slots": [
    {
      "id": "controls.demand",
      "expressions": [
        {
          "name": "requiredMoment",
          "expression": "pitchInertia * requestedAcceleration - competingMoment",
          "unit": "N*m"
        }
      ]
    },
    {
      "id": "controls.effectiveness",
      "expressions": [
        {
          "name": "dynamicPressure",
          "expression": "0.5 * density * airspeed * airspeed",
          "unit": "Pa"
        },
        {
          "name": "deltaCm",
          "expression": "elevatorDerivative * elevatorAngle",
          "unit": "1"
        },
        {
          "name": "deltaMoment",
          "expression": "dynamicPressure * referenceArea * referenceChord * deltaCm",
          "unit": "N*m"
        }
      ]
    }
  ]
}
```

## Recorded verification status

Recorded as passed for the submitted model hash.

- Checked at: 2026-09-17T04:54:33.956Z
- Detail: Student artifact passed demand, baseline elevator, quadratic speed, and neutral-deflection checks.

## Recorded model runs

### Run 1
- Recorded: 2026-09-17T04:53:06.668Z
- Run ID: 206493e7-17d6-4f8e-b66c-9acdbbf8bc07
- Record revision: 920
- Model hash recorded with run: fnv1a-596d5cb5
- Prediction recorded with run:

```
Sign of Elevator Moment: Negative
for a trailing-edge UP deflection (which produces a downward force aft of CG, causing nose-UP rotation 
M corelates to Vsquared
reducing V reduces M/4 

wing and body pitching moment, CG, drive opposite with elevator input

```
- Result status: recorded values shown below
- Values: `requiredMoment=1350 N*m`; `dynamicPressure=980 Pa`; `deltaCm=0.06981317007977318 1`; `deltaMoment=1642.0057602762652 N*m`

### Run 2
- Recorded: 2026-09-17T04:53:20.220Z
- Run ID: 655d47bf-cbfc-4c2b-87e4-35952ff170a7
- Record revision: 920
- Model hash recorded with run: fnv1a-596d5cb5
- Prediction recorded with run:

```
Sign of Elevator Moment: Negative
for a trailing-edge UP deflection (which produces a downward force aft of CG, causing nose-UP rotation 
M corelates to Vsquared
reducing V reduces M/4 

wing and body pitching moment, CG, drive opposite with elevator input

```
- Result status: recorded values shown below
- Values: `requiredMoment=750 N*m`; `dynamicPressure=980 Pa`; `deltaCm=0.06981317007977318 1`; `deltaMoment=1642.0057602762652 N*m`

### Run 3
- Recorded: 2026-09-17T04:53:26.738Z
- Run ID: eb8f9f60-f0f4-42cb-884b-f2bbf8911e1f
- Record revision: 920
- Model hash recorded with run: fnv1a-596d5cb5
- Prediction recorded with run:

```
Sign of Elevator Moment: Negative
for a trailing-edge UP deflection (which produces a downward force aft of CG, causing nose-UP rotation 
M corelates to Vsquared
reducing V reduces M/4 

wing and body pitching moment, CG, drive opposite with elevator input

```
- Result status: recorded values shown below
- Values: `requiredMoment=1350 N*m`; `dynamicPressure=245 Pa`; `deltaCm=0.06981317007977318 1`; `deltaMoment=410.5014400690663 N*m`

### Run 4
- Recorded: 2026-09-17T04:53:45.356Z
- Run ID: e1ebfd0c-2e91-4b6d-a2ee-5035468c7f89
- Record revision: 920
- Model hash recorded with run: fnv1a-596d5cb5
- Prediction recorded with run:

```
Sign of Elevator Moment: Negative
for a trailing-edge UP deflection (which produces a downward force aft of CG, causing nose-UP rotation 
M corelates to Vsquared
reducing V reduces M/4 

wing and body pitching moment, CG, drive opposite with elevator input

```
- Result status: recorded values shown below
- Values: `requiredMoment=1350 N*m`; `dynamicPressure=245 Pa`; `deltaCm=0.06981317007977318 1`; `deltaMoment=410.5014400690663 N*m`

### Run 5
- Recorded: 2026-09-17T04:53:49.510Z
- Run ID: af5573cf-1675-438a-83f5-7b267949acbb
- Record revision: 920
- Model hash recorded with run: fnv1a-596d5cb5
- Prediction recorded with run:

```
Sign of Elevator Moment: Negative
for a trailing-edge UP deflection (which produces a downward force aft of CG, causing nose-UP rotation 
M corelates to Vsquared
reducing V reduces M/4 

wing and body pitching moment, CG, drive opposite with elevator input

```
- Result status: recorded values shown below
- Values: `requiredMoment=1350 N*m`; `dynamicPressure=980 Pa`; `deltaCm=0 1`; `deltaMoment=0 N*m`

### Run 6
- Recorded: 2026-09-17T04:53:55.040Z
- Run ID: 2a6058b5-bc5a-4998-aeee-b95740d9e401
- Record revision: 920
- Model hash recorded with run: fnv1a-596d5cb5
- Prediction recorded with run:

```
Sign of Elevator Moment: Negative
for a trailing-edge UP deflection (which produces a downward force aft of CG, causing nose-UP rotation 
M corelates to Vsquared
reducing V reduces M/4 

wing and body pitching moment, CG, drive opposite with elevator input

```
- Result status: recorded values shown below
- Values: `requiredMoment=750 N*m`; `dynamicPressure=980 Pa`; `deltaCm=0.06981317007977318 1`; `deltaMoment=1642.0057602762652 N*m`

### Run 7
- Recorded: 2026-09-17T04:54:00.460Z
- Run ID: ed00e77a-61f4-46ed-b499-7157ce6c5a75
- Record revision: 920
- Model hash recorded with run: fnv1a-596d5cb5
- Prediction recorded with run:

```
Sign of Elevator Moment: Negative
for a trailing-edge UP deflection (which produces a downward force aft of CG, causing nose-UP rotation 
M corelates to Vsquared
reducing V reduces M/4 

wing and body pitching moment, CG, drive opposite with elevator input

```
- Result status: recorded values shown below
- Values: `requiredMoment=1350 N*m`; `dynamicPressure=980 Pa`; `deltaCm=0.06981317007977318 1`; `deltaMoment=1642.0057602762652 N*m`

### Run 8
- Recorded: 2026-09-17T04:54:11.598Z
- Run ID: cdcf5080-6fbd-4f9b-a7ff-baa284ce49b0
- Record revision: 920
- Model hash recorded with run: fnv1a-596d5cb5
- Prediction recorded with run:

```
Sign of Elevator Moment: Negative
for a trailing-edge UP deflection (which produces a downward force aft of CG, causing nose-UP rotation 
M corelates to Vsquared
reducing V reduces M/4 

wing and body pitching moment, CG, drive opposite with elevator input

```
- Result status: recorded values shown below
- Values: `requiredMoment=750 N*m`; `dynamicPressure=980 Pa`; `deltaCm=0.06981317007977318 1`; `deltaMoment=1642.0057602762652 N*m`

### Run 9
- Recorded: 2026-09-17T04:54:17.008Z
- Run ID: 15a3db2e-b613-46b5-af90-d43da737a393
- Record revision: 920
- Model hash recorded with run: fnv1a-596d5cb5
- Prediction recorded with run:

```
Sign of Elevator Moment: Negative
for a trailing-edge UP deflection (which produces a downward force aft of CG, causing nose-UP rotation 
M corelates to Vsquared
reducing V reduces M/4 

wing and body pitching moment, CG, drive opposite with elevator input

```
- Result status: recorded values shown below
- Values: `requiredMoment=1350 N*m`; `dynamicPressure=980 Pa`; `deltaCm=0.06981317007977318 1`; `deltaMoment=1642.0057602762652 N*m`

## Submission instructions

Use Save to GitHub in the app to save both files, commit, and push. Submit your fork URL and the saved commit SHA. Manual fallback: save this file beside `student/submission.json`, run `npm run student:prepare` and `npm run student:validate`, then commit and push student/.
