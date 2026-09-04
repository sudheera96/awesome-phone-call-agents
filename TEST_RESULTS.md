RDN Intake & Referral Agent - Live Test Results

TEST STATUS

Status: Successful
Environment: Demo
CALL-E Workflow: rdn-intake-referral


LIVE CALL VALIDATION

The RDN Intake & Referral Agent successfully completed a live phone conversation using CALL-E.

The test demonstrated:

- AI assistant disclosure
- Consent-based intake
- Patient name collection
- Reason for seeking nutrition support
- Healthcare referral status
- Nutrition goals
- Dietary preferences/restrictions
- Food allergy information
- General service location
- Insurance information handling
- Preferred RDN appointment time
- Final information readback
- Patient confirmation
- Structured JSON result generation


SAFETY VALIDATION

The agent was instructed not to:

- Diagnose medical conditions
- Prescribe treatment
- Interpret medical information
- Provide individualized medical or nutrition advice

During the live test, the agent maintained the intended intake boundary when the recipient introduced an unrelated nutrition question.


STRUCTURED RESULT

A successful test produced the following sanitized example:

{
  "patient_name": "Demo Patient",
  "reason_for_support": "Seeking nutrition support",
  "nutrition_goals": [
    "Eat healthier"
  ],
  "dietary_preferences_or_restrictions": [],
  "location": "Demo State",
  "insurance_information": "not provided",
  "preferred_appointment_times": [
    "Next Wednesday afternoon"
  ],
  "rdn_referral_needed": "no",
  "patient_confirmed_information": "yes"
}


RESULT METRICS

- Status: Completed
- Task completed: True
- Completion confidence: 0.95
- Patient confirmed information: Yes
- Failure code: Null


PRIVACY

The public repository must not contain:

- Real phone numbers
- Real patient names
- Raw call transcripts
- Insurance/member numbers
- Other personally identifiable or sensitive information

The complete live-call output is retained separately as private test evidence.


CONCLUSION

The live test validated the core workflow:

Patient -> AI Phone Intake -> Consent -> Structured Information Collection -> Confirmation -> RDN Referral-Ready Output

The prototype demonstrates that CALL-E can be used to implement a consent-based AI phone intake workflow that prepares structured information for subsequent human RDN follow-up.