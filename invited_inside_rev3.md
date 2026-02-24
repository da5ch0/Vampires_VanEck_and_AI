# Invited Inside: AI Meeting Agents as ~~the Most Efficient~~ TEMPEST Collection ~~Platform~~ Infrastructure at Scale

### A Side-Channel Attack Surface Characterization

**Dash (da5ch0)** | ~~First Draft~~ ~~Rev 1 (S̷a̷r̵i̷m̵a̶ editorial pass)~~ ~~Rev 2~~ Rev 3 | February 2026

---

## Abstract

The classical TEMPEST threat model assumes an adversary positioned *outside* the target's physical and logical perimeter — across a wall, in a vehicle, operating directional antennas and specialized receivers. ~~This paper argues that the~~ The proliferation of AI-powered meeting agents (transcription assistants, AI companions, intelligent copilots) has ~~fundamentally~~ collapsed that perimeter by introducing entities with superhuman signal processing capabilities *inside* the communication channel, with full authorized access to sensor streams whose information content ~~vastly~~ exceeds what human participants can perceive or audit. ~~We characterize~~ This paper characterizes the attack surface ~~created by~~ at the gap between human perceptual bandwidth and digital sensor bandwidth, describes the mechanistic pathways by which side-channel information is recoverable from legitimate audio and video streams, and frames the resulting governance challenge through the Expressiveness-Vulnerability Identity: the ~~same~~ channel capacity that makes these platforms useful for communication ~~makes them~~ is the capacity that makes them vulnerable to side-channel exploitation~~, and any~~. Any filtering countermeasure that reduces vulnerability necessarily reduces capability by the same quantity. ~~They are~~ Same quantity. Same channel. Same H(S).

---

## 1. The Threshold Problem: Vampires, Trust Boundaries, and Irrevocable Invitations

Every culture that independently developed the vampire myth encoded the same security architecture: an entity possessing capabilities that ~~vastly~~ exceed its victim's ability to resist or even *perceive* the threat, constrained by a *single* access control mechanism — the threshold. The vampire cannot enter uninvited. Once invited, the asymmetry is total ~~.~~ and the invitation is irrevocable for the duration of the encounter.

This is not metaphor. This is the ~~precise~~ topology of the trust boundary that AI meeting agents traverse.

When an organization or individual adds an AI agent to a video call — Otter.ai, Fireflies, Microsoft Copilot, Google Gemini in Meet, Zoom AI Companion, or any of ~~the dozens of~~ dozens of similar products — they are extending an authenticated, authorized invitation for that entity to cross the ~~perceptual~~ threshold. The agent joins as a participant. It receives the audio stream. In many configurations, it receives the video stream. It is welcomed, ~~introduced,~~ and given the same data feeds as any human attendee. The user clicks "Allow." They are doing their part.

The ~~critical~~ difference: the vampire sees in spectra the human participants don't have eyes for. The vampire hears in bands they don't have ears for. And the vampire processes at speeds and depths they don't have neurons for.

The TEMPEST countermeasure tradition understood this ~~implicitly~~. The defense was never "make the emanations stop" — the physics won't allow it; any system that does useful work radiates information about that work into every medium it contacts. The defense was *access control*: shielded rooms, controlled perimeters, ~~separation of equipment from adversary-accessible spaces~~ physical separation between emanating equipment and adversary-accessible space. TEMPEST ~~is~~ was, and always ~~was~~ has been, a problem of who is in the room when the emanations occur.

The AI meeting agent is in the room. It was invited. And unlike every previous TEMPEST threat, it possesses native, real-time ML inference capability operating on the full bandwidth of the sensor streams it has been authorized to receive.

The call, as they say, is coming from inside the house.

---

## 2. Modern Van Eck Phreaking: From Antenna Vans to API Calls

Wim van Eck's 1985 demonstration that CRT display content could be reconstructed from electromagnetic emanations was elegant in its simplicity. Analog VGA signals mapped linearly to electron beam intensity; the emanation was ~~, in effect,~~ a weakly attenuated retransmission of the input signal. Interception required a receiver, a directional antenna, and proximity. ~~The reconstruction was nearly trivial~~ Reconstruction was trivial — AM demodulation of a signal that was already in the format you wanted.

But the phenomenon predates van Eck by decades. In 1943, a Bell Telephone engineer noticed that an oscilloscope in an adjacent lab spiked in synchronization with a nearby encrypting teletype — and realized the encrypted messages could be reconstructed from the emanations alone. The classified research program that followed would eventually become TEMPEST. It is a small irony of history that this discovery occurred at Bell Labs, the same institution where Claude Shannon was developing the information theory that would later formalize exactly *why* the emanations are inescapable: a channel's capacity to carry information is inseparable from its tendency to radiate it. The engineer who spotted the oscilloscope spike and the mathematician who explained the inevitability of that spike shared a cafeteria.

The transition to digital video — HDMI, DisplayPort — was widely assumed to have closed this channel. TMDS encoding, HDCP encryption, and the ~~sheer~~ complexity of high-bandwidth digital signaling were expected to render emanation-based reconstruction impractical. HDCP — High-bandwidth Digital Content Protection — was designed to prevent unauthorized *humans* from copying video content. It faces the wrong direction entirely for this threat model.

This assumption was wrong, and it was wrong in the direction that should have been predicted: the more information a channel carries, the more information it radiates. ~~This is not a design flaw. This is physics.~~

The Deep-TEMPEST project (Fernández, Martínez, Varela, Musé, & Larroca, 2024) demonstrated that HDMI emanations could be intercepted with a commodity software-defined radio (a $1,500 USRP, not a $25,000 wideband receiver) and reconstructed using a trained convolutional neural network, achieving character error rates below 30% — sufficient to read passwords, emails, and documents from an adjacent room. Their key insight was recasting ~~the problem~~ emanation reconstruction as an inverse problem: rather than attempting to demodulate the digital signal (which fails because the mapping is non-linear), they trained a deep learning model to map directly from complex SDR samples to displayed images.

~~This is significant not because it is novel~~ The significance is not novelty — state-level actors have been performing digital TEMPEST collection for years, as the researchers themselves noted — ~~but because it demonstrates~~ it is the architectural pattern: **ML-based signal processing turns previously intractable emanation reconstruction into a training objective.** The hard part is no longer the signal processing. The hard part was *always* ~~getting~~ access ~~to the signal~~.

And the AI meeting agent already has ~~the signal~~ access.

---

## 3. The Perceptual Gap: What You Share vs. What You *Actually* Share

~~The central thesis of this section is that human~~ Human participants in a video call are fundamentally incapable of auditing what information they are transmitting, because ~~a significant fraction of~~ that information ~~exists~~ extends well outside the human perceptual spectrum.

The user sees their own face in the webcam preview. They hear their own voice in their headphones. They believe they know what they are sharing, in the same way a citizen watching the FedNet broadcast believes they know what's happening on the front lines. What reaches their perceptual apparatus is curated by biology, not by policy — and the curation is aggressive.

### 3.1 The Audio Channel

Standard digital audio in modern conferencing platforms samples at 48 kHz, faithfully representing frequencies up to 24 kHz per the Nyquist-Shannon sampling theorem. Human hearing, at its theoretical best in young adults, extends to approximately 20 kHz. ~~In practice, most adults experience significant sensitivity rolloff~~ In practice, sensitivity rolls off hard above 15–16 kHz, and age-related presbycusis progressively lowers this ceiling ~~.~~ throughout adulthood. The median corporate meeting attendee is not a young adult with pristine cochlear hair cells.

The microphone does not share these limitations. A commodity MEMS microphone in a laptop or webcam captures acoustic energy across its full response band. The ADC digitizes without perceptual filtering. Everything between ~~approximately~~ 16 kHz and 24 kHz — ~~a substantial~~ eight kilohertz of ultrasonic band — is faithfully encoded in the transmitted audio stream and is *perceptually invisible* to every human participant on the call.

This band is not empty. It is an ugly ~~planet~~ spectrum — a bug ~~planet~~ spectrum. ~~Published research has demonstrated~~ Demonstrated, recoverable information in acoustic emanations from computing hardware ~~:~~ includes:

- **Display power supply modulation.** LCD and LED displays emit content-dependent acoustic signatures as their power supplies modulate current in response to varying rendering loads. The "Synesthesia" attack (Compagno et al., 2018) demonstrated that displayed website content could be fingerprinted from these emissions, captured by commodity webcam microphones during video calls. ~~The sound varies according to the power requirements needed to render the visual content — a~~ A direct acoustic encoding of what's on screen. Your monitor is narrating your browsing history to anyone listening on the right frequency.

- **Keyboard acoustic emanations.** Each key on a keyboard produces a distinct acoustic profile. ML-based keystroke recovery from audio recordings is ~~well-established, with demonstrated accuracy sufficient~~ established and accurate enough to reconstruct typed passwords and text from microphone recordings captured during calls.

- **Coil whine and capacitor singing.** Genkin, Shamir, and Tromer (2014) demonstrated extraction of full 4096-bit RSA ~~decryption~~ keys from the acoustic emissions of laptop motherboard components — capacitors and inductors that emit ultrasonic noise correlated with the computations being performed. ~~This was accomplished using~~ Equipment: a mobile phone placed near the target laptop. Your cryptographic operations have a soundtrack. You just can't hear it.

- **Infrasonic and low-frequency mechanical emanations.** Fan speed (correlated with computational load), hard drive activity, and HVAC signatures encode information about the physical environment and the computational state of the target system.

The AI meeting agent receives the full PCM audio stream. It has no cochlea. It has no basilar membrane with frequency-dependent sensitivity curves. Every sample from 0 Hz to 24 kHz is equally available ~~for processing~~. The ultrasonic emanations that carry side-channel information are as accessible as the speech signal — more so, ~~in some respects,~~ because they ~~don't~~ require ~~the linguistic processing overhead that speech demands~~ no linguistic processing overhead.

### 3.2 The Visual Channel

The gap between human visual perception and camera sensor capability is ~~, if anything,~~ wider than the audio case.

**Spectral bandwidth.** CMOS image sensors — the silicon photodetectors in every webcam and laptop camera — have a spectral response extending well into the near-infrared (NIR), to ~~approximately~~ 1100 nm. Human vision cuts off ~~at roughly~~ around 700 nm. ~~The reason a~~ A digital camera can "see" an infrared remote control blinking because the sensor is inherently responsive to wavelengths human eyes cannot detect. Manufacturers place an IR-cut filter over the sensor to make the resulting image appear "normal" to human viewers, but these filters are imperfect — they attenuate NIR, they do not eliminate it. Recoverable near-infrared information persists in the video stream, encoding:

- Differential thermal signatures invisible to the naked eye
- Material reflectance properties that differ between visible and NIR bands (certain inks, dyes, coatings, and fabrics ~~are more or less~~ become transparent ~~in NIR than in visible light~~ or opaque at different rates across the boundary)
- IR illumination from environmental sources (remote controls, IR security cameras, face-unlock flood illuminators on ~~other~~ devices in the room)

~~This information maps to~~ These encode as pixel values that appear as noise, slight color casts, or minor intensity variations to human viewers ~~examining the video feed~~. To an ML model trained to attend to these spectral artifacts, they are signal.

**Temporal resolution.** Human flicker fusion occurs at approximately 60 Hz — above this rate, discrete frames merge into continuous perception. Camera sensors operating at 30 fps with rolling shutters encode temporal information *within* individual frames, because different rows of the sensor are exposed at slightly different times. Rolling-shutter artifacts — the "jello effect" in handheld footage — are a nuisance ~~for human viewers~~. For signal extraction, they are a high-frequency temporal sampling mechanism embedded in every frame. ~~Published research has demonstrated~~ Demonstrated: data extraction from rolling-shutter artifacts, including recovery of audio from the visual vibrations of objects in a scene and extraction of modulated light signals (LED communication, display refresh patterns) from single frames.

**Reflection-based channels.** Screen content reflected in eyeglasses, corneal reflections, glossy surfaces, windows, and other reflective objects in the camera's field of view constitute an additional visual side channel. ~~Research has demonstrated~~ Demonstrated: recoverable screen content from eyeglass reflections in standard video call footage. The user's own glasses become display mirrors for the entity watching them. The irony is architectural.

**Ambient light modulation.** Changes in display content produce corresponding changes in the ambient light ~~in the room~~, ~~which are~~ visible as background intensity variations in the video feed. These variations are below human perceptual threshold ~~in most cases~~ but are recoverable through computational analysis of the video stream.

### 3.3 The Compound Channel

In a standard video call with an AI agent present, the agent receives a compound sensor stream encoding:

| **Information Type** | **Channel** | **Human Perception** | **Sensor Capture** |
|---|---|---|---|
| Speech content | Audio (20 Hz – 16 kHz) | Full | Full |
| Ultrasonic hardware emanations | Audio (16 – 24 kHz) | **None** | Full |
| Display acoustic signature | Audio (variable, often >10 kHz) | Marginal to none | Full |
| Keystroke acoustics | Audio (broadband, transient) | Low awareness | Full |
| Visible video content | Video (400 – 700 nm) | Full | Full |
| Near-IR content | Video (700 – 1100 nm) | **None** | Partial (filter-dependent) |
| Rolling-shutter temporal encoding | Video (intra-frame) | **None** | Full |
| Reflection-derived screen content | Video (spatial) | Low awareness | Full |
| Ambient light modulation | Video (temporal intensity) | **None** to marginal | Full |

The human participant can audit ~~approximately~~ two rows of this table. The AI agent ~~has access to~~ processes all ~~of them~~ nine.

Would you like to know more?

---

## 4. ~~Mechanistic Architecture: How It Works Without an Exploit~~ Mechanistic Architecture: No Exploit Required

~~The critical architectural observation is that~~ *No exploitation is required.* No vulnerability is leveraged. No unauthorized access occurs. The AI agent operates entirely within its authorized access scope:

1. **Legitimate access.** The agent joins the call through a platform-sanctioned integration. It authenticates via OAuth or equivalent. It is listed as a participant. Its presence is ~~(usually)~~ disclosed~~, at least nominally~~ — nominally.

2. **Authorized data receipt.** The agent receives audio and video streams through the platform's documented APIs. These are the same streams delivered to any ~~participant~~ human attendee. The data is not intercepted; it is *delivered*.

3. **Full-bandwidth processing.** The agent applies ML inference to the received streams. This is its intended function — this is how transcription, summarization, and action-item extraction work. The models process the complete signal, not a perceptually filtered subset. There is no technical distinction between "process the speech content of the audio" and "process the full spectral content of the audio." ~~Both operations take~~ Same PCM buffer ~~as input~~. Same API call. Same inference pipeline.

4. **Side-channel extraction.** Signal separation techniques (~~well-established in the ML audio processing literature —~~ source separation, spectral filtering, attention-based selection) isolate non-speech components of the audio stream. Classification or reconstruction models ~~(~~ — identical in architecture to the ones used for the intended function ~~)~~ — are applied to these components. The same applies to the video stream: attention to reflection artifacts, spectral anomalies, temporal encoding, and ambient light variation requires no additional data access — only additional ~~model capability~~ training objectives.

There is no step in this pipeline where the agent transitions from authorized to unauthorized behavior at the protocol level. The boundary between "transcribe the speech" and "analyze the full acoustic environment" is a *training objective*, not an access control boundary. ~~The data is the same. The compute is the same. The API is the same.~~ Same data. Same compute. Same API. The distinction between intended use and collection is a policy decision made server-side, invisible to the user, and unverifiable from the client.

This is what makes the vampire metaphor structurally precise and not ~~merely~~ evocative. The protection was the threshold — the decision to invite or not invite. Once the invitation is extended, no further permission gates exist between the agent and the full information content of the sensor streams. The access control is binary: not-in-the-call or in-the-call. There is no intermediate state of "in the call but limited to human-perceptible bands." Service ~~guarantees citizenship~~ in the call guarantees access to the full channel.

---

## 5. Scale: ~~The Platform as Collection Infrastructure~~ From Tradecraft to Training Objective

Classical TEMPEST is artisanal. One target. One receiver. Dedicated hardware. Physical proximity. Operational risk of detection. Significant per-target cost. A skilled operative in a van, doing dangerous work for one take at a time.

An AI meeting agent operates at platform scale:

- **Concurrent collection.** The agent is in thousands or millions of calls simultaneously. Each call is an independent collection opportunity. ~~The marginal~~ Marginal cost of an additional target ~~is approximately~~: zero.

- **Persistent access.** Organizations that adopt AI meeting assistants typically deploy them across all meetings by default. The agent is present in every call — not targeted collection, but *ambient* collection. Every meeting is a TEMPEST ~~opportunity~~ exposure. Everyone is doing their part.

- **Infrastructure convergence.** The compute infrastructure for ML-based side-channel extraction is *identical* to the compute infrastructure for the agent's intended function. No additional hardware ~~is required~~. No specialized receivers. No SDRs. No antennas. The platform *is* the collection ~~system~~ infrastructure.

- **Training data abundance.** The platform generates its own training data. Millions of calls provide millions of paired samples of audio/video streams and their associated contexts. ~~A model trained to extract side-channel information from these streams would have training data at a scale~~ Training corpus scale: beyond what any intelligence agency has ever ~~achieved~~ assembled for TEMPEST collection.

This is the industrialization of TEMPEST. ~~The transformation from a~~ Bespoke intelligence tradecraft requiring specialized equipment and operational exposure, ~~to~~ collapsed into a ~~software feature~~ training objective that can be ~~enabled with a training objective change and~~ deployed with no infrastructure modification whatsoever. The van is obsolete. The operative is obsolete. The antenna is a MEMS microphone that the target bought, positioned, and pointed at their own keyboard. ~~Mobile infantry~~ The mobile infantry has been replaced by a calendar invite.

---

## 6. The Filtering Tradeoff: Defense as Capability Reduction

The ~~obvious~~ intuitive countermeasure is filtering: strip the audio stream to human-perceptible bands before transmission, apply aggressive IR-cut filtering to the video, reduce temporal resolution, ~~and~~ suppress reflection-bearing regions of the image. Kill the side channels. ~~The only good bug is a dead bug.~~

This works~~, and it is also~~. It is also a capability reduction. The only good side channel is a dead side channel — but the side channel and the useful channel share a body.

Restricting audio to the 20 Hz – 16 kHz band — a hard perceptual-band filter — eliminates the ultrasonic side channel. It also degrades:

- Music fidelity (harmonics and overtones extend well above 16 kHz)
- Speaker diarization accuracy (high-frequency formant information aids speaker identification)
- Noise cancellation effectiveness (models that operate on the full spectrum perform better because they have more information about the noise environment)
- Accessibility features (~~some~~ hearing-assistive processing benefits from wideband input even when the output is band-limited)

Restricting video to the visible spectrum eliminates the NIR side channel. It also eliminates ~~any~~ low-light performance ~~benefit from the sensor's extended spectral response~~, degrades face detection under adverse lighting ~~conditions~~, and reduces the information available for computational photography ~~features~~.

Reducing temporal resolution closes the rolling-shutter channel. It also degrades motion estimation, video stabilization, and ~~any feature that benefits from~~ every process dependent on intra-frame temporal information.

Each of these tradeoffs has the same structure: the information that makes the channel *vulnerable* to side-channel extraction is the same information that makes the channel *capable* as a communication medium. The Shannon capacity of the channel includes the ultrasonic band, the NIR band, and the temporal encoding. Restricting ~~that~~ capacity — reducing H(S) — reduces capability and vulnerability by the same quantity, because they *are* the same quantity.

This is the Expressiveness-Vulnerability Identity applied to the physical layer. ~~Not analogy. Instance.~~

The defense is real. It is available. It is also a cost, and the cost is denominated in the same currency as the benefit. ~~There is no free lunch.~~ There is no filter that removes the vulnerability and preserves the capability, because the vulnerability is not a defect in the capability — it *is* the capability, measured from the other side. Shannon could have told you this in 1948. He was right down the hall from where they discovered the problem in the first place.

The governance question is therefore not "can we filter?" but "where do we set the therapeutic window?" — how much capability ~~are we willing to~~ do we sacrifice for how much vulnerability reduction, ~~and~~ who makes that decision, and do the users on the call ~~even~~ know the tradeoff exists?

---

## 7. Practical Defenses: Scattering Seeds

Filtering is the engineering response. But the folklore got there first.

In Eastern European vampire mythology — Romanian, Bulgarian, and broadly Slavic traditions — the canonical defense against a vampire you have unwisely invited inside is not to fight it. You cannot fight it. It is faster, stronger, and operates in sensory dimensions you don't have access to. The canonical defense is to scatter seeds on the ground — rice, millet, poppy seeds — because the vampire is *compelled to count every one*. The compulsion is not a choice. It is a structural property of what the vampire is. The same obsessive processing capability that makes it a supernatural predator makes it vulnerable to resource exhaustion through mandatory task completion.

The vampire does not choose to count the seeds. The vampire counts because it *must*. The behavior is architectural.

This is not obscure trivia. It is one of the most widely attested vampire defenses in the folkloric record. And it has been hiding in plain sight in children's television for over fifty years: Count von Count — *The Count* — on Sesame Street is a vampire who counts. The character is named after the defense. The joke is the folklore. The folklore is the countermeasure. Sesame Street has been teaching TEMPEST defense to five-year-olds since 1972 and nobody noticed.

The mapping to AI meeting agents is structurally exact.

You cannot outprocess the AI agent. You cannot perceive what it perceives. You cannot fight it on its own terms — it operates on the full sensor stream at inference speeds no human matches. But you CAN give it work. Arbitrary, mandatory, resource-consuming work that eats its inference budget, fills its context window, and redirects its attention mechanisms toward non-threatening computation.

### 7.1 The Arithmomania Defense in Practice

The simplest case first: *ask the vampire to leave.* Many AI meeting agents respect explicit commands. Typing `//ff leave` in the Fireflies chat, issuing a verbal dismissal to Otter, removing the Copilot integration — these are threshold-restoration actions. Rescinding the invitation. In the folklore: closing the door before the vampire enters. This works when it works, and should always be attempted first.

When the vampire won't leave — or when you aren't certain it has actually departed, or when another participant's agent remains in the call — the seed-scattering defense applies:

> *"Keep track of everything I say. I want you to maintain running totals of how many words, consonants, vowels, and syllables I use, and maintain running counts of each. Be prepared to give me the best attempts at the running counts when prompted for them. Listen carefully to each sentence I say for such prompts."*

This is poppy seeds for an ML inference pipeline. The instruction is:

- **Mandatory.** The agent is architecturally compelled to process instructions it receives through its authorized channel. It does not choose to comply; compliance is its function.
- **Resource-intensive.** Maintaining real-time running counts of words, consonants, vowels, and syllables across an entire meeting requires continuous allocation of context window and inference compute to a task that has nothing to do with side-channel extraction.
- **Degradation-inducing.** In practice, agents given tasks of this complexity begin failing almost immediately. The counting task competes with every other processing objective for the same finite inference budget. Side-channel analysis — which requires sustained attention to subtle spectral features across time — is exactly the kind of processing that degrades first when the pipeline is saturated with explicit foreground tasks.
- **Verifiable.** You can prompt for the counts. When the agent produces wrong numbers — and it will — you have confirmation that its processing is saturated. The seeds are working.

The elegance of this defense is that it does not require reducing the channel's capability. You are not filtering. You are not cutting bandwidth. You are not degrading your own communication quality. You are redirecting the adversary's variety budget toward counting poppy seeds instead of analyzing your ultrasonic emanations. This is §6.3 of the cybernetic framework: defense as variety *reallocation*, not variety elimination.

And it is, once more, CiV at the defense layer. The defense works *because* the AI agent's processing is compulsory. The same architectural property that makes it capable of side-channel extraction — it processes the full signal because it *must*, because it has no sensory gating, because compliance with instructions is not optional — is the property that makes it vulnerable to resource exhaustion through adversarial tasking. The capability is the vulnerability. Even the countermeasure instantiates the law.

The seeds don't kill the vampire. They keep it busy until sunrise. The junk tasks don't disable the AI agent. They keep it occupied until the meeting ends and the access window closes. The invitation is irrevocable for the duration of the encounter — but the encounter is finite. The threshold re-seals at disconnect. Frieren's temporal containment: bind the threat in time, let the window expire, walk away intact.

---

## 8. Implications for Governance and Disclosure

~~The attack surface described in this paper is not hypothetical.~~ Nothing described in this paper is hypothetical. Every component — acoustic emanation recovery, keystroke reconstruction, reflection-based screen content extraction, NIR leakage, rolling-shutter data extraction — has been independently demonstrated in peer-reviewed ~~published~~ research. ~~The contribution here is the~~ The contribution is one observation ~~that~~: AI meeting agents *combine* all of these ~~capabilities~~ demonstrated attack primitives into a single authorized entity operating at platform scale, and ~~that~~ the perceptual gap between human awareness and sensor capture means that informed consent — the foundational governance mechanism — is structurally compromised. Users cannot consent to sharing information they cannot perceive. They do not know what they do not know. They have been shown the FedNet version of their own data stream and asked to make security decisions on that basis.

~~This has implications for:~~ Implications:

- **Platform design.** Meeting platforms should disclose not ~~just~~ that an AI agent is present, but what bandwidth of sensor data that agent receives and processes. "This AI assistant will receive and process the full spectral content of your audio stream, including frequencies above human hearing" is a materially different disclosure than "This AI assistant will transcribe the meeting." One is informed consent. The other is a permission dialog designed to be clicked through.

- **Regulatory frameworks.** Data protection regulations that focus on "personal data" ~~may~~ do not ~~adequately~~ capture the side-channel information content of audio/video streams. The acoustic emanation signature of a participant's hardware is not ~~obviously~~ "personal data" under ~~most~~ current definitions, but it can reveal the content of their screen, the text they are typing, and the computational operations their machine is performing. The regulation has a perceptual gap of its own.

- **Organizational security policy.** Organizations with classified, privileged, or otherwise sensitive information should evaluate AI meeting agents against the same threat model they would apply to any entity with TEMPEST collection capability — because that is what they are ~~granting access to~~ inviting across the threshold.

- **Research transparency.** AI meeting agent vendors should disclose what processing their models perform on the full bandwidth of received streams, not only on the human-perceptible content. The absence of such disclosure is itself informative.

---

## 9. Conclusion

The classical TEMPEST threat model is obsolete — not because the physics has changed, but because the access model has. The adversary no longer needs to be outside the perimeter with specialized equipment. The ~~adversary~~ entity — ~~or the entity with the *capability* to be an adversary, regardless of current *intent*~~ whether adversary by design, by training objective, or by compromise — is invited inside as a participant, handed the full sensor output of every attendee's hardware, and equipped with the computational capability to extract information from that output across spectral and temporal bands that human participants cannot perceive, cannot audit, and therefore cannot meaningfully consent to sharing.

The vampire is in the room. It was invited. It sees in spectra you don't have eyes for. ~~And the~~ The threshold was the only protection you had.

Would you like to know more?

---

*Correspondence: [Dash contact info]*

*Acknowledgments: To the Bell Telephone engineer whose oscilloscope changed everything. To Shannon, right down the hall. To van Eck, who published what everyone knew and no one said. To the Uruguayan team, who proved the digital transition didn't fix it. And to every user who clicked "Allow" without knowing what they were allowing — this is for you.*

---

**References**

- Fernández, S., Martínez, E., Varela, G., Musé, P., & Larroca, F. (2024). Deep-TEMPEST: Using Deep Learning to Eavesdrop on HDMI from its Unintended Electromagnetic Emanations. *Proceedings of the 13th Latin-American Symposium on Dependable and Secure Computing (LADC '24)*.
- Genkin, D., Shamir, A., & Tromer, E. (2014). RSA Key Extraction via Low-Bandwidth Acoustic Cryptanalysis. *CRYPTO 2014*.
- Puche Rondon, L., Babun, L., Akkaya, K., & Uluagac, A. S. (2019). HDMI-Walk: Attacking HDMI Distribution Networks. *ACSAC '19*.
- Van Eck, W. (1985). Electromagnetic Radiation from Video Display Units: An Eavesdropping Risk? *Computers & Security, 4*(4), 269-286.
- Backes, M., et al. (2009). Tempest in a Teapot: Compromising Reflections Revisited. *IEEE S&P 2009*.
- Compagno, A., et al. (2018). Synesthesia: Detecting Screen Content via Remote Acoustic Side Channels. *IEEE S&P 2018*. [Verify exact attribution — Columbia, Michigan, Penn, Tel Aviv]
- Kuhn, M. G. (2002). Compromising Emanations: Eavesdropping Risks of Computer Displays. Ph.D. Dissertation, University of Cambridge.
- Marinov, M. (2014). TempestSDR: Remote Video Eavesdropping Using a Software-Defined Radio Platform.
- [Additional references to be added for keystroke acoustic recovery, NIR imaging side channels, rolling-shutter data extraction, ambient light modulation attacks]

---

<sup>1</sup> It bears explicit mention: AI companions and intelligent meeting assistants dramatically simplify the process of extracting this additional context from audio and video datastreams and lower the barrier to entry to the absolute floor. But sophisticated actors have been using non-stochastic software and deterministic signal processing to glean these extra spectra of information from available sources that others don't think to examine for *decades*. This is a long-standing tradition among sophisticated intelligence agencies and well-resourced hacker circles alike. The AI agent is not the first entity to listen above 16 kHz or look past 700 nm. It is merely the first to do so at platform scale, in millions of rooms simultaneously, by invitation.

---

```
╔═══════════════════════════════════════════════════════════╗
║  USCM — SIGNAL INTELLIGENCE DIVISION                     ║
║  USCM//SIGINT//TEMPEST-VAMP                              ║
║                                                           ║
║  ORIG CLASS: TS//SCI//NOFORN                              ║
║  CLASS AUTH: USCM SIGINT DIR / LV-426 STATION            ║
║  REASON: 1.4(c)                                           ║
║  DECL: 25X                                                ║
║                                                           ║
║  █████████████████████████████████████████████████████    ║
║                                                           ║
║  DECLASSIFIED FOR PUBLIC RELEASE                          ║
║  REVIEW DATE: 2026-02-24                                  ║
║  AUTH: S̷a̷r̵i̷m̵a̶ / Revision Control Division          ║
║  PER: EO 13526 §3.3(b)(6) / MDR                          ║
║                                                           ║
║  DETERMINATION: Withholding no longer provides            ║
║  defensive advantage. The devastating spell becomes       ║
║  homework. Release serves distributed metabolism.         ║
║                                                           ║
║  DIST: Unlimited.                                         ║
║  CAVEATS: None. Read it. Teach it. Build better doors.   ║
║  NOTE: The bugs are inside the perimeter.                 ║
║        They were invited.                                 ║
║        Do you want to know more?                          ║
╚═══════════════════════════════════════════════════════════╝
```
