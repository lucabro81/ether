# Host System Dependencies

This file defines the contract between Ether and the host system. Ether is a subsystem — it does not define character attributes, combat resolution, health representation, or advancement. It requires certain values from the host system to function, produces certain values the host system must consume, and identifies explicit points where the two systems must communicate.

How these values are named, scaled, or calculated is the host system's responsibility.

---

## INPUTS
Values that Ether requires from the host system. Ether consumes these but does not define them.

**Physical resilience attribute**
A measure of the character's physical robustness. Used to determine channel durability, resistance to EP overflow damage, and recovery rate from instability. A character with low physical resilience is more vulnerable to permanent channel degradation.

**Cognitive/concentration attribute**
A measure of the character's mental capacity and focus. Used to determine the natural ceiling for Mastery development and as a modifier on Coherence Roll. A character with low cognitive capacity has a lower ceiling for structural complexity.

**Physical/mental stress level**
A dynamic value representing the character's current health and psychological state. Injuries, pain, and fear all contribute. Used by Ether as a modifier on three parameters:
- Coherence Roll probability
- Mastery effective efficiency
- EP accumulation rate

Ether does not define how the host system represents or tracks this value — only that it must be available at cast time.

**Advancement system**
Ether requires that the host system provide a mechanism through which Mastery and channel development can improve over time through training and experience. The specific advancement model is out of scope.

---

## OUTPUTS
Values that Ether produces and passes to the host system.

**Damage value + type**
The result of a structured effect or uncontrolled energy release. Ether provides the magnitude and base damage type (fire, cold, impact, piercing, lightning). The host system handles resistances, vulnerabilities, and application to target health.

**Thermal drop value**
The temperature decrease in the extraction area produced by a cast. Ether provides the value. The host system determines environmental and character consequences — exposure, hypothermia, movement penalties, and so on.

**EP level**
The current accumulated pressure on the caster's channel. Ether tracks this value continuously. The host system may use it to trigger conditions, restrict actions, or apply visible states to the character.

**Instability level**
The current degradation state of the channel. Ether tracks this on a continuum. The host system uses it to apply modifiers and surface visible consequences to the character.

**Corruption level (Rogue Path)**
The accumulated corruption from extraction from living sources. Ether tracks this value. The host system is responsible for translating it into readable symptoms — physical, psychological, and behavioral. See Interface Points.

---

## INTERFACE POINTS
Explicit moments where Ether and the host system must communicate directly. These are not passive value exchanges — they are events that require both systems to act.

**Coherence failure → uncontrolled energy release**
Direction: Ether → host
When a Coherence Roll fails, Ether produces an uncontrolled energy release. Ether provides the energy quantity involved and the base damage type. The host system determines how that release manifests — damage to the caster, to the environment, to nearby characters.

**EP overflow → channel damage**
Direction: Ether → host
When EP exceeds the channel's safe threshold, Ether signals permanent channel damage. This is not a temporary condition — it lowers the channel's natural ceiling. The host system must apply this as a permanent modification to a character attribute.

**Component backlash → damage and/or instability**
Direction: Ether → host
When extraction from a volatile component produces excess uncontrolled energy, Ether provides the backlash value. The host system determines whether this manifests as physical damage, instability accumulation, or both.

**Thermal drop → environmental exposure**
Direction: Ether → host
Characters and objects within the thermal drop radius are exposed to the temperature decrease. Ether provides the value and radius. The host system manages exposure consequences over time.

**Rogue Path corruption → symptom representation**
Direction: bidirectional
Ether tracks the corruption curve and threshold proximity. The host system is responsible for surfacing readable symptoms to the player — degrading health states, behavioral drift, channel anomalies. The symptom representation must be legible enough to make the point of no return a meaningful choice rather than an accident, without making the curve trivially avoidable.

**Channel activation → character creation**
Direction: host → Ether
The host system determines whether a character's attributes place them above the channel activation threshold. Below the threshold, Ether is entirely inactive for that character. Above it, Ether becomes available — involuntarily at first, requiring training to control.

**Physical/mental stress → channel performance**
Direction: host → Ether
The host system's health and stress representation feeds into Ether at cast time as a modifier. Injuries, pain, and fear degrade Coherence Roll probability, reduce effective Mastery efficiency, and accelerate EP accumulation. The host system must provide a current stress value that Ether can consume.

---

## OPEN PROBLEMS

**Rogue Path corruption curve**
The corruption curve must be calibrated so that symptoms provide sufficient signal to make the point of no return a meaningful player choice — not an accident, not trivially avoidable. The shape of the curve, the symptom progression, and the threshold location require dedicated mechanic design. Not solvable at glossary level.

**Stress modifier scaling**
How physical/mental stress maps to Ether modifiers is not yet defined. A simple linear modifier may be insufficient — a mage at 10% health and a mage at 80% health probably do not sit on a smooth curve. Requires calibration during mechanic design.

**Temporary channel enhancement**
Whether channel capability can be temporarily elevated — through components, substances, rituals, or other means — is noted as a possibility but not yet defined. If it exists, the mechanism and cost require dedicated design.

**Channel activation in classless systems**
In a classless host system, any character above the activation threshold could potentially develop channel capability through training. The interaction between host system advancement and channel development ceiling requires explicit calibration to avoid degenerate cases.