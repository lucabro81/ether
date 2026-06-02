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

**Physical stress level**
A dynamic value representing the character's current physical condition. Injuries and pain contribute. Degrades Ether parameters in a continuous, progressive way. Used by Ether as a modifier on three parameters:
- Coherence Roll probability
- Mastery effective efficiency
- EP accumulation rate

The curve is not linear — degradation is gradual in the high range and accelerates significantly at low values. Exact scaling requires calibration during mechanic design.

Ether does not define how the host system represents or tracks this value — only that it must be available at cast time.

**Mental stress level**
A dynamic value representing the character's current psychological state. Fear, panic, and shock contribute. Distinct from physical stress: behaves discontinuously, producing threshold effects rather than smooth degradation. Below a certain threshold it has no meaningful effect on channel performance. Above it, it begins to interfere with the nervous system's ability to direct the channel. At acute levels — panic, shock — it can saturate the interface entirely, collapsing the ability to impose structured effects while leaving the channel active.

A saturated interface does not silence the channel. It removes conscious direction from it. Involuntary discharges under acute mental stress are the channel responding to an overwhelmed nervous system, not a failure of the channel itself.

Ether does not define the threshold values or their effects in detail — only that mental stress must be provided as a separate input from physical stress, and that it must be available at cast time.

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

**Consumption level (Rogue Path)**
The accumulated structural degradation from chronic channel overextension. Ether tracks this value. The host system is responsible for translating it into readable symptoms. See Interface Points.

**Poisoning level (Rogue Path)**
The accumulated contamination from extraction from living sources. Ether tracks this value separately from consumption. The host system is responsible for translating it into readable symptoms — behavioral drift, perceptual distortion, craving. See Interface Points.

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

**Rogue Path → symptom representation**
Direction: bidirectional
Ether tracks two separate values: consumption level and poisoning level. Both contribute to the overall progression. The host system is responsible for surfacing readable symptoms to the player. Consumption symptoms map to capability degradation — the mage perceives them as loss. Poisoning symptoms map to behavioral drift and perceptual distortion — the mage may not perceive them accurately at all. The symptom representation must be legible enough to make the point of no return a meaningful choice rather than an accident, without making the curve trivially avoidable.

**Rogue Path → point of no return**
Direction: Ether → host
Past the midpoint of either corruption curve, each stage carries a growing probability of being the point of no return. Ether tracks proximity to threshold. The host system is responsible for representing the consequences of crossing it: permanent ceiling reduction for consumption, permanent contamination baseline for poisoning. Past the threshold, untreated degradation continues — the condition does not plateau. Management through substances or practices is possible; full recovery belongs to the host system.

**Channel activation → character creation**
Direction: host → Ether
The host system determines whether a character's attributes place them above the channel activation threshold. Below the threshold, Ether is entirely inactive for that character. Above it, Ether becomes available — involuntarily at first, requiring training to control.

**Physical stress → channel performance**
Direction: host → Ether
The host system's physical health representation feeds into Ether at cast time as a continuous modifier. Injuries and pain degrade Coherence Roll probability, reduce effective Mastery efficiency, and accelerate EP accumulation. Degradation is progressive and non-linear. The host system must provide a current physical stress value that Ether can consume.

**Mental stress → channel control**
Direction: host → Ether
The host system's psychological state representation feeds into Ether at cast time as a threshold modifier. Fear and panic interfere with the nervous system's ability to direct the channel. At acute levels the interface saturates, collapsing structured effect capability while leaving the channel active. The host system must provide a current mental stress value that Ether can consume, distinct from physical stress.

---

## OPEN PROBLEMS

**Rogue Path corruption curve**
The corruption curve must be calibrated so that symptoms provide sufficient signal to make the point of no return a meaningful player choice — not an accident, not trivially avoidable. The shape of the curve, the symptom progression, and the threshold location require dedicated mechanic design.

**Stress modifier scaling**
How physical stress maps to Ether modifiers requires calibration. The curve is non-linear — flat in the high range, steep at low values. Mental stress threshold values and their specific effects also require definition. Both require dedicated mechanic design.

**Temporary channel enhancement**
Whether channel capability can be temporarily elevated — through components, substances, rituals, or other means — is noted as a possibility but not yet defined. If it exists, the mechanism and cost require dedicated design.

**Channel activation in classless systems**
In a classless host system, any character above the activation threshold could potentially develop channel capability through training. The interaction between host system advancement and channel development ceiling requires explicit calibration to avoid degenerate cases.