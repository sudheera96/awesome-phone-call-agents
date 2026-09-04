Great. Let's do it one step at a time.



\## Step 1 — Create your project README



In your CMD, you're already inside:



```text

C:\\Users\\csris\_i58bcul\\rdn-intake-agent\\awesome-phone-call-agents

```



Run:



```cmd

notepad skills\\rdn-intake-referral\\README.md

```



When Notepad asks whether you want to create the file, click \*\*Yes\*\*.



Paste this complete README:



````markdown

\# RDN Intake \& Referral Agent



A consent-based AI phone intake workflow built with CALL-E to collect structured nutrition-support information and prepare a referral-ready summary for Registered Dietitian Nutritionist (RDN) review.



\## Overview



The RDN Intake \& Referral Agent explores how an AI phone agent can support the initial intake stage of a healthcare nutrition workflow.



The current prototype uses CALL-E to conduct an outbound phone conversation with a patient on behalf of an RDN or care team. The AI identifies itself, requests consent, collects structured intake information, reads the information back for confirmation, and produces a structured JSON result for human review.



The AI is designed to support the intake and coordination process, not replace the RDN.



\## Why I Built This



Healthcare nutrition support often begins with collecting basic information before an RDN can review a patient's needs and determine the appropriate next step.



A phone conversation can require repetitive information gathering, while important details need to be captured consistently.



This project explores whether an AI phone agent can handle this initial information-collection step while keeping the RDN or care team responsible for clinical review and follow-up.



The goal is to transform an unstructured phone conversation into organized, patient-confirmed information that can support the next stage of the workflow.



\## Current Workflow



The current prototype follows this workflow:



```text

RDN / Care Team

&#x20;      |

&#x20;      v

CALL-E AI Phone Agent

&#x20;      |

&#x20;      v

AI Disclosure

&#x20;      |

&#x20;      v

Patient Consent

&#x20;      |

&#x20;      v

Structured Intake

&#x20;      |

&#x20;      +-- Patient name

&#x20;      +-- Reason for nutrition support

&#x20;      +-- Healthcare referral status

&#x20;      +-- Nutrition goals

&#x20;      +-- Dietary preferences / restrictions

&#x20;      +-- Food allergies

&#x20;      +-- General location

&#x20;      +-- Optional insurance information

&#x20;      +-- Preferred RDN appointment time

&#x20;      |

&#x20;      v

Information Readback

&#x20;      |

&#x20;      v

Patient Confirmation

&#x20;      |

&#x20;      v

Structured JSON Result

&#x20;      |

&#x20;      v

RDN / Care Team Review

&#x20;      |

&#x20;      v

Human Follow-up

````



The current prototype collects a preferred appointment time but does not schedule or confirm an appointment.



\## What the AI Does



The AI phone agent is responsible for communication and information collection.



It:



1\. Identifies itself as an AI assistant.

2\. Requests consent before continuing.

3\. Collects the required intake information.

4\. Handles optional information such as insurance.

5\. Collects the patient's preferred appointment time.

6\. Reads the collected information back to the patient.

7\. Requests confirmation.

8\. Produces structured JSON for downstream human review.

9\. Maintains defined healthcare safety boundaries.

10\. Stops or hands off when the conversation is outside the intended intake scope.



\## What the AI Does Not Do



The prototype is intentionally not a medical advisor.



It does not:



\* Diagnose medical conditions.

\* Prescribe treatment.

\* Interpret medical information.

\* Provide individualized medical or nutrition advice.

\* Make clinical decisions.

\* Confirm a medical appointment.

\* Replace an RDN or other qualified healthcare professional.



Clinical decisions and appropriate patient follow-up remain with the RDN or care team.



\## Project Structure



```text

rdn-intake-referral/

|

+-- README.md

|   Complete project documentation, architecture, workflow,

|   design decisions, and future direction.

|

+-- SKILL.md

|   Core CALL-E Agent Skill. Defines the phone interaction,

|   intake workflow, structured output, confirmation behavior,

|   and operational safety requirements.

|

+-- TEST\_RESULTS.md

|   Sanitized documentation of live CALL-E testing and

|   validation results.

|

+-- references/

&#x20;   |

&#x20;   +-- safety.md

&#x20;   |   Healthcare safety boundaries and fail-closed behavior.

&#x20;   |

&#x20;   +-- examples.md

&#x20;       Examples that demonstrate the intended skill behavior.

```



\## Why Each File Exists



\### `SKILL.md`



`SKILL.md` is the core instruction layer for the Agent Skill.



It defines what the CALL-E agent should do during the phone conversation, what information should be collected, how the result should be structured, and how the agent should behave when safety or consent conditions are not satisfied.



Without `SKILL.md`, the project would not have a defined Agent Skill workflow.



\### `references/safety.md`



Healthcare conversations can move beyond basic intake.



This file provides explicit safety boundaries so the agent does not cross from information collection into medical or nutrition advice.



It supports fail-closed behavior for situations such as unclear consent, requests to stop, emergencies, incorrect recipients, or unreliable information.



\### `references/examples.md`



Examples make the intended behavior easier to understand and extend.



They provide concrete scenarios that help explain how the Skill should behave during different types of phone interactions.



\### `TEST\_RESULTS.md`



`TEST\_RESULTS.md` records evidence from live CALL-E testing.



The results are sanitized so that the public repository does not expose real phone numbers, patient information, raw transcripts, insurance/member numbers, or other sensitive information.



The test results demonstrate that the workflow was validated through an actual CALL-E phone interaction.



\### `README.md`



This README provides the larger context around the project.



It explains why the project exists, how the components work together, what each file is responsible for, the current limitations, and the future direction.



\## Structured Output



The conversation is converted into structured information rather than relying only on a raw transcript.



Example:



```json

{

&#x20; "patient\_name": "Demo Patient",

&#x20; "reason\_for\_support": "Seeking nutrition support",

&#x20; "nutrition\_goals": \[

&#x20;   "Eat healthier"

&#x20; ],

&#x20; "dietary\_preferences\_or\_restrictions": \[],

&#x20; "location": "Demo State",

&#x20; "insurance\_information": "not provided",

&#x20; "preferred\_appointment\_times": \[

&#x20;   "Next Wednesday afternoon"

&#x20; ],

&#x20; "rdn\_referral\_needed": "no",

&#x20; "patient\_confirmed\_information": "yes"

}

```



The structured result is intended to give the RDN or care team a concise, organized starting point for human review.



\## Why Patient Confirmation Matters



Voice conversations are unstructured and can contain misunderstandings.



Before producing the final intake result, the agent reads the collected information back to the patient and asks for confirmation.



This creates an additional verification step before the information is passed to the downstream human workflow.



\## Why the RDN Remains in the Loop



The purpose of this project is not to automate clinical decision-making.



The AI handles communication and repetitive information collection, while the RDN or care team remains responsible for reviewing the information, determining appropriate care, and communicating with the patient.



This separation keeps the prototype focused on workflow support rather than clinical automation.



\## Testing



The prototype was validated using live CALL-E phone calls.



The successful demonstration included:



\* AI disclosure

\* Consent

\* Structured intake

\* Safety-boundary handling

\* Information readback

\* Patient confirmation

\* Structured JSON generation



The final demonstration test completed successfully with a completion confidence of `0.95`.



See \[`TEST\_RESULTS.md`](TEST\_RESULTS.md) for the sanitized validation results.



\## Design Principles



The project follows several design principles:



\### Consent first



The agent identifies itself and obtains consent before proceeding with the intake.



\### Human-centered workflow



The AI supports the RDN and care team instead of replacing them.



\### Structured information



Important information is converted from natural conversation into structured output.



\### Confirmation before handoff



The patient is given an opportunity to confirm the collected information.



\### Safety boundaries



The AI remains within information collection and referral coordination and does not provide individualized medical or nutrition advice.



\### Fail closed



When the agent cannot safely continue, it should stop or defer to appropriate human handling rather than guessing.



\### Privacy by design



Public testing artifacts are sanitized and should not contain real patient information, phone numbers, insurance/member numbers, or raw sensitive transcripts.



\## Current Prototype vs. Future Development



\### Current prototype



The current prototype supports:



\* Outbound AI phone calls

\* AI disclosure

\* Consent-based intake

\* Nutrition-support information collection

\* Patient confirmation

\* Structured JSON output

\* RDN-ready referral information

\* Human/RDN follow-up



\### Future development



A future production implementation could connect the structured intake output to an RDN scheduling or care-management system.



A possible future workflow would be:



```text

RDN / Care Team

&#x20;      |

&#x20;      v

CALL-E AI Intake

&#x20;      |

&#x20;      v

Patient Consent + Intake

&#x20;      |

&#x20;      v

Patient Confirmation

&#x20;      |

&#x20;      v

Structured Patient Information

&#x20;      |

&#x20;      v

RDN / Care Management System

&#x20;      |

&#x20;      v

Appointment Coordination

&#x20;      |

&#x20;      v

Human / Authorized System Confirmation

```



Scheduling and appointment confirmation are intentionally outside the current prototype.



\## Technology



\* CALL-E

\* Agent Skills

\* Python

\* AI / LLM-based conversational workflow

\* Structured JSON

\* Voice AI

\* Healthcare AI safety patterns



\## Project Goal



The project demonstrates how phone-based AI can reduce repetitive intake work while preserving a human-centered healthcare workflow.



The intended outcome is not to replace the RDN.



The intended outcome is to help the RDN begin with organized, patient-confirmed information instead of an unstructured phone conversation.



\## Hackathon Context



This project was developed for the CALL-E hackathon, exploring practical applications of AI-powered phone interactions.



The project contributes an RDN-focused healthcare intake workflow as a reusable CALL-E Agent Skill.



\## Status



\*\*Prototype — Live CALL-E validation completed.\*\*



The current implementation focuses on intake and referral coordination. Production deployment would require appropriate healthcare, privacy, security, consent, clinical, and operational review.



````





