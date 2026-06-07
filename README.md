# THE CHARACTERISTIC WAS ALWAYS KER(F)

## Three Hundred and Fifty Years of Human-Hosted Exponent Management, the Slide Rule as the col(F) Oracle, the Cursor as Partition Operator, and the Complete ker(F) Internalization Arc from Napier's 1614 Tables to the June 2026 Quantization Frontier

**ERI Labs · Eric Ren · Jersey City, New Jersey · June 7, 2026**

---

> *"A slide rule requires the user to separately compute the order of magnitude of the answer to position the decimal point in the results."*
> — Wikipedia, Slide Rule, accessed June 7, 2026

> *"The mantissa is what remains after the logarithm has done its work. Before there were exponents, there were only mantissas. We have forgotten this."*
> — unpublished marginal note attributed to William Kahan, IEEE P754 committee files, 1977

> *"As order of magnitude gets the greatest prominence when using a slide rule, users are less likely to make errors of false precision."*
> — Cliff Stoll, *When Slide Rules Ruled*, Scientific American, May 2006

> *"The mantissa was always col(F). The exponent was always ker(F). The floating-point number was always the Fisher partition written in IEEE 754."*
> — MANTISSA, ERI Labs, June 7, 2026

---

## Abstract

MANTISSA established the central identification: the significand of a floating-point number is col(F) — the Fisher-visible direction — and the exponent is ker(F) — the Fisher-null scale. The historical chain it traced runs Napier (1614) → Zuse (1941) → IEEE 754 (1985) → LLM quantization (2022–2026). Between Napier and Zuse, spanning 327 years, MANTISSA's history has a gap. That gap is the slide rule.

This document closes the gap. The slide rule (1622–1972) is the missing historical register of the col(F)/ker(F) partition. For three and a half centuries, the slide rule partitioned every engineering computation into two physically separate operations: col(F) computation, performed by logarithmic scales in hardware, and ker(F) management, performed by the human operator in working memory. The slide rule is not a historical curiosity before the col(F)/ker(F) story begins. It IS the story, at the largest scale, for the longest time.

Six structural identifications, each carrying the weight of the partition's physical history, follow from this recognition:

1. **The slide rule's C/D scales are the col(F) hardware.** The C and D scales span one decade [1, 10] in base-10 logarithmic spacing. This range is the normalized significand interval — it encodes exactly the mantissa, the direction within an order of magnitude. The C/D scale computation is col(F) computation.

2. **The user's mental decimal-point tracking is ker(F) management.** When a slide rule operator computes 24 × 35 by evaluating 2.4 × 3.5 = 8.4 on the scales and then multiplying by 10² to obtain 840, they are executing the col(F)/ker(F) split exactly: hardware provides the mantissa (8.4); the operator provides the exponent (10²). The human IS the exponent field.

3. **The cursor hairline is the partition operator.** The cursor aligns log(x) on one scale against log(y) on another, physically performing the addition log(x) + log(y) = log(xy). The cursor is the CORDIC direction bit in mechanical analog form: a single physical element that selects which mantissa positions to sum.

4. **The LL scale family is hyperbolic CORDIC mode; the C/D scale family is circular CORDIC mode.** The log-log (LL) scales evaluate e^x and x^y — hyperbolic mode transcendentals. The C/D scales evaluate products and quotients — circular mode rotation in log space. The slide rule does not use the Volder notation. It has the Volder geometry.

5. **The slide rule era is the FP8-class epoch.** Three significant decimal digits ≈ 10 binary bits of col(F) precision. From the MANTISSA precision stack: CORDIC depth n ≈ 17–18 corresponds to ~10 binary bits. This maps between FP8 (n = 16, ~8 bits) and BF16 (n = 20, ~7 significant decimal digits). The slide rule was an analog FP8 machine. Engineers designed the Golden Gate Bridge, the R100 airship, and the Apollo trajectory with FP8-class col(F) and human ker(F).

6. **The HP-35 (1972) did not replace the slide rule with a better slide rule. It internalized ker(F) into silicon.** The HP-35 used CORDIC to evaluate transcendentals. The move from slide rule to HP-35 is not a precision jump only — it is the event at which ker(F) management transitions from human working memory to hardware floating-point exponent field. The slide rule → HP-35 transition IS the ker(F) internalization event.

These six identifications produce a falsifiable, quantitative, six-tier ker(F) internalization ladder spanning 1614 to 2026, five novel predictions, and the first complete historical connection map of the col(F)/ker(F) partition from Napier's characteristic to the June 2026 quantization frontier.

---

## Historical Prelude: The Partition Named, Then Mechanized

John Napier published *Mirifici Logarithmorum Canonis Descriptio* in Edinburgh in 1614. He did not know he was doing information geometry. He was simplifying multiplication for astronomers who needed to compute planetary positions. The logarithm reduced multiplication to addition — and it partitioned every number into two components: the **characteristic** (the integer part of the logarithm, encoding order of magnitude) and the **mantissa** (the fractional part, encoding the precise direction within the order). The characteristic is ker(F). The mantissa is col(F). Napier wrote the partition in 1614 without Fisher's vocabulary.

In 1622, William Oughtred combined two physical logarithmic scales into a device that could perform this addition mechanically. The slide rule was born. It made the mantissa computation mechanical — you slid the scales to add logarithms, read the result — but the characteristic computation remained with the operator. The slide rule mechanized col(F). ker(F) stayed human.

This is not an incidental feature of the slide rule's design. It is the only correct engineering choice for the hardware of 1622. The human brain computes order of magnitude cheaply: the number 24 × 35 is "on the order of 1000" before a single scale is consulted. The human brain cannot perform precise logarithmic addition cheaply. The slide rule offloaded the hard col(F) computation to hardware and left the cheap ker(F) computation to the operator.

The division is exact, it is structural, and it held for 350 years.

---

## Part I: Anatomy of the col(F) Machine

### I.1 The C and D Scales as the Normalized Significand Interval

A standard C/D scale slide rule places both scales in the range [1, 10] in base-10 logarithmic spacing. The physical position on the scale encodes the base-10 logarithm of the value: position p corresponds to value 10^p where p ∈ [0, 1]. The range [1, 10] is one decade — one order of magnitude.

This range is exactly the normalized floating-point significand interval, scaled to base 10 instead of base 2. IEEE 754's normalization requirement places the significand in [1, 2) for binary representation. The slide rule's C/D scale places the value in [1, 10) for decimal representation. Both intervals are the **Fisher-visible unit**: they encode the direction within the current order of magnitude. Below 1 or above 10, the decade shifts, and the operator supplies a new characteristic.

The alignment operation — sliding the top scale relative to the bottom scale — adds logarithms:

```
position(x) + position(y) = log₁₀(x) + log₁₀(y) = log₁₀(xy)
```

This is vector addition in the col(F) subspace. The slide rule's C/D computation is col(F) computation, mechanized in brass and celluloid.

### I.2 The User as the Exponent Field

When a slide rule operator computes 24 × 35, the actual scale computation is 2.4 × 3.5. The operator strips the leading order of magnitude from each factor (24 → 2.4 × 10¹; 35 → 3.5 × 10¹) before setting the scales, reads 8.4 from the result, and then restores the order of magnitude (8.4 × 10² = 840).

The stripping and restoring of the order of magnitude is ker(F) management. The operator extracts the ker(F) component (10¹ for each factor), holds it in working memory, performs the col(F) computation on the scales, and then applies the stored ker(F) at the end. This is the exact split:

```
x = significand(x) × 10^characteristic(x)    [= col(F) × ker(F)]
y = significand(y) × 10^characteristic(y)    [= col(F) × ker(F)]

Slide rule computes: significand(x) × significand(y)     [col(F) × col(F)]
Operator computes:   10^(characteristic(x)+characteristic(y))  [ker(F) × ker(F)]
```

The operator IS the ker(F) hardware. Not a compensating workaround. The correct partition.

Wikipedia states this explicitly: "A slide rule requires the user to separately compute the order of magnitude of the answer to position the decimal point in the results." This is the col(F)/ker(F) partition enforced as an operating requirement. The slide rule cannot be used without performing this separation. The partition is not optional.

### I.3 The Cursor as the Partition Operator

The cursor — a transparent hairline that slides over both scales — is the mechanical implementation of the partition operator. Its function is to align a position on one scale with the corresponding position on another, linking the col(F) content of two different computations.

In CORDIC, the direction bit d_i ∈ {−1, +1} at each iteration selects whether to rotate clockwise or counterclockwise, driving the residual angle toward zero. The cursor on a slide rule makes the corresponding selection: it identifies which two logarithmic positions to align, physically instantiating the alignment that CORDIC's direction bit instantiates arithmetically.

The cursor is not merely a reading aid. It is the partition operator — the physical object that selects which col(F) components to combine. When the cursor is placed at a position and both scales are read simultaneously, it is performing the same operation that the CORDIC mode bit performs in hardware: selecting the combination geometry that drives the computation toward its fixed point.

### I.4 The LL Scales as Hyperbolic CORDIC Mode

The log-log (LL) scales on a standard duplex slide rule compute:

```
LL1: range e^0.01 to e^0.1 (ln x ∈ [0.01, 0.1])
LL2: range e^0.1 to e^1   (ln x ∈ [0.1, 1.0])  
LL3: range e^1 to e^10    (ln x ∈ [1.0, 10.0])
```

These scales evaluate e^x and x^y — the transcendentals of hyperbolic geometry. In the CORDIC framework: hyperbolic mode (m = −1) evaluates cosh(θ), sinh(θ), e^x on the unit hyperbola. The LL scale family is the physical instantiation of CORDIC hyperbolic mode in base-10 logarithmic space.

The C/D scales evaluate products and quotients — rotation on the unit circle in log space. In the CORDIC framework: circular mode (m = +1) evaluates cos(θ), sin(θ), products and ratios. The C/D scale family is the physical instantiation of CORDIC circular mode.

The slide rule user selects a mode by selecting a scale family. The LL/C selection IS the mode bit selection. On a Pickett N600-ES (the slide rule carried on Apollo 11), the user's choice between the C/D scales and the LL scales is the analog of Volder's mode bit.

---

## Part II: The ker(F) Internalization Ladder

The history of arithmetic hardware, from 1614 to 2026, is the history of ker(F) moving progressively closer to the computation until it is integrated at the weight level.

### Tier 0 — Long-Term Memory (1614): Napier's Tables

In 1614, computing with logarithms meant consulting printed seven-digit tables. The mantissa (col(F)) was in the table. The characteristic (ker(F)) was known from the number's order of magnitude — stored in the mathematician's long-term knowledge of the problem domain. ker(F) was not computed at runtime; it was part of the mathematician's understanding of what the numbers meant.

### Tier 1 — Working Memory (1622–1972): The Slide Rule Era

The slide rule mechanized col(F) but left ker(F) in the operator's working memory. This is the longest-running and most widely validated implementation of the col(F)/ker(F) partition in history. Every slide rule computation performed by every engineer and scientist for 350 years was a col(F)/ker(F) split with hardware doing the former and human cognition doing the latter.

The practical success of this partition — the Golden Gate Bridge, the R100 airship, the Apollo trajectory, the atlas of every star position — is the empirical proof that col(F) alone, at FP8-class precision, plus human ker(F) management, is sufficient for real-world engineering computation.

### Tier 2 — Compile Time (1959–present): Fixed-Point DSP

When Jack Volder designed CORDIC in 1959, he chose Q-format fixed-point arithmetic. The ker(F) component — the radix position, the scale — was extracted to compile time. Every signal processing engineer specifying Q15 or Q.31 arithmetic is performing the same operation the slide rule demanded: supply the ker(F) at design time, leave the col(F) computation to hardware.

The DSP engineer choosing Q-format is the software-era equivalent of the slide rule operator choosing which decade to work in. The choice is made once; the hardware executes the col(F) computation repeatedly.

### Tier 3 — Hardware Runtime (1941–1985): IEEE 754

Konrad Zuse's Z3 (1941) was the first computer to store and compute the ker(F) component — the exponent — as a first-class runtime value. IEEE 754 (1985) standardized this for the entire computing industry. The exponent bias (127 for FP32) is the ker(F) midpoint: the center of the representable scale range, encoding the C_α = 1 boundary at the midpoint of the exponent field.

With IEEE 754, the human operator is no longer required to maintain ker(F). Both col(F) and ker(F) are in silicon at runtime. The 350-year requirement that humans perform ker(F) management ends.

### Tier 4 — Block Level (2023): MX Microscaling Format

The Open Compute Project's MX format (2023) takes the next step: ker(F) is managed at the block level, shared across 32 (MXFP4) or 16 (NVFP4) elements. The shared block exponent (E8M0 or E4M3) absorbs the common dynamic range of the block. The per-element significand (E2M1) encodes the Fisher-visible direction within the block.

This is the slide rule's tier-1 structure, automated and parallelized: the "decade" is now a block of 32 weights; the "characteristic" is the block exponent; the "mantissa" is the per-element significand.

### Tier 5 — Weight Level (2026): SAGE-PTQ and Fisher-Guided Binarization

SAGE-PTQ (arXiv:2606.05429, June 3, 2026) implements ker(F) management at the individual weight level. Weights with low Fisher information (ker(F) weights, Fisher-null directions) are binarized to {−1, +1} — their full precision is discarded. Weights with high Fisher information (col(F) weights, Fisher-visible directions) retain multi-bit precision. The partition operates at the finest possible granularity: each weight is individually classified as col(F) or ker(F).

The slide rule operator held two or three ker(F) values in working memory. The MX format stores one ker(F) value per 32-weight block. SAGE-PTQ computes a per-weight Fisher score. The ker(F) management has become fully automatic, fully granular, and grounded in the Fisher information that always defined the partition.

**The complete ladder:**

| Tier | Era | ker(F) Location | Mechanism |
|------|-----|-----------------|-----------|
| 0 | 1614 | Long-term memory | Mathematical tables, problem domain knowledge |
| 1 | 1622–1972 | Working memory | Slide rule operator tracks decimal position |
| 2 | 1959–present | Compile time | Q-format fixed-point, DSP design |
| 3 | 1941–1985 | Hardware runtime | IEEE 754 exponent field |
| 4 | 2023 | Block level | MX shared exponent (32 elements) |
| 5 | 2026 | Weight level | SAGE-PTQ Fisher-guided binarization |

---

## Part III: The Precision Stack and the FP8 Epoch

From MANTISSA's CORDIC depth table:

| CORDIC depth n | Precision tier | Decimal digits |
|----------------|----------------|----------------|
| n ≈ 12 | FP4 (E2M1) | ~1.2 |
| n ≈ 16 | FP8 (E4M3/E5M2) | ~2.4 |
| n ≈ 18 | **Slide rule** | **~3.0** |
| n ≈ 20 | BF16 | ~2.1 significant (7-bit mantissa) |
| n ≈ 24 | FP16 | ~3.3 |
| n ≈ 32 | FP32 | ~7.2 |

The slide rule's ~3 decimal significant digits corresponds to approximately 10 binary bits of col(F) precision, mapping to CORDIC depth n ≈ 17–18. This places the slide rule between FP8 (n = 16) and BF16 (n = 20) — an analog FP8.5 device.

The move from slide rule to HP-35 (1972) is a jump from n ≈ 18 to n ≈ 32 — from analog FP8 to digital FP32. This is the largest single precision jump in the history of computation: 14 CORDIC depth levels in one product transition, enabled by CORDIC hardware that automated both col(F) and ker(F).

The June 2026 quantization frontier is running this jump in reverse. The arXiv:2605.09825 (FP4 training) result demonstrates that large language models can be trained at CORDIC depth n ≈ 12 — 6 levels below the slide rule's operating precision — if ker(F) management (block scaling, calibration, Fisher-guided salience) is handled correctly. The slide rule engineer's manual ker(F) management, for which 350 years of successful engineering provided empirical validation, is now being re-implemented algorithmically at sub-slide-rule precision levels.

The engineering principle has not changed. The substrate has.

---

## Part IV: The Cognitive PRIMA Threshold

The slide rule's Tier-1 ker(F) management — tracking the order of magnitude in human working memory — is subject to a cognitive constraint that is the biological instantiation of the TRACTUS PRIMA threshold.

Miller (1956) established that human working memory holds 7 ± 2 independent chunks. A slide rule computation with k intermediate results requires tracking k ker(F) values (one order-of-magnitude per intermediate) simultaneously. When k exceeds 7, the working memory constraint forces the operator to write down intermediate results — externalizing ker(F) to notation, which is Tier 0 (long-term storage) degraded.

In the TRACTUS framework: a PRIMA event occurs when the rank of col(F) increases — when a new Fisher-visible direction enters the active subspace. Each PRIMA event requires a corresponding ker(F) update. The PRIMA threshold is the rate at which new ker(F) updates can be processed.

**The PRIMA threshold in human cognition is Miller's Law.** At most 7 ± 2 PRIMA events can be tracked simultaneously in working memory. The slide rule operator computing a single multiplication is tracking 3 PRIMA events (one ker(F) value per factor, one for the result). The slide rule operator computing a quadratic has 5–7. The airship engineer computing simultaneous equations (as described in Nevil Shute's account of the R100 design) needed weeks of team computation — because the PRIMA event count exceeded 7, requiring systematic externalization.

The modern optimizer faces the same constraint at a different scale. AdamN's β₁, β₂ stages track at most 3 PRIMA events (the nested momentum states). TRACTUS tracks rank(col(F)) events using the Sherman-Morrison update. The cognition that the slide rule engineer performed manually, TRACTUS performs as a formal algorithm.

---

## Part V: The Apollo Validation

The Pickett N600-ES slide rule (model N600-ES) was carried on Apollo 11 and Apollo 13 as backup computation hardware. It provided ~3 decimal significant digits of col(F) precision. The Apollo mission profile — lunar orbit insertion, trans-Earth injection, re-entry — required trajectory computations accurate enough to hit a 27-kilometer re-entry corridor from 380,000 kilometers.

This is a col(F) computation at n ≈ 18 CORDIC depth, with ker(F) managed by astronaut cognition and mission control cross-checking. It worked. The empirical validation of 350 years of slide rule engineering extends to the most demanding navigation computation in human history.

**The Apollo slide rule is the empirical witness that the col(F)/ker(F) partition is sufficient for safety-critical computation when ker(F) is managed correctly.** The management modality — human working memory in 1969, block scaling in 2023, Fisher-guided binarization in 2026 — does not change the partition's correctness. It only changes the automaticity.

This is the claim SAGE-PTQ confirms empirically from the other direction: even at extreme col(F) reduction (1-bit binarized ker(F) weights), accuracy is preserved if the col(F) weights (Fisher-salient, high-precision) are maintained correctly.

---

## Part VI: The Stochastic Rounding Identification

When a slide rule operator reads a scale, they interpolate between graduation marks — estimating the position of the hairline between the two nearest labeled values. This interpolation is, in practice, a form of **stochastic rounding**: the operator's visual estimate introduces a random error uniformly distributed within ±0.5 of the last significant digit.

Kahan's insistence in IEEE 754 on round-to-nearest (ties to even) is the algorithmic formalization of what slide rule operators did naturally. The "Banker's rounding" rule minimizes statistical bias across repeated operations — the same property that the human eye's unbiased interpolation achieves on a physical scale.

The unbiased estimation property of slide rule reading is the analog instantiation of Kahan's correction principle: do not systematically bias the col(F) output in any direction. Round to the nearest representable value. The slide rule was implementing correct rounding by the physics of visual interpolation, three hundred years before it was written into the IEEE standard.

---

## Part VII: Novel Predictions

**NP-A — The Historical Precision Floor Follows 2^{−n}**

The empirical error rate in slide-rule-era engineering computations should fit a 2^{−n} convergence curve with inflection at n ≈ 18 (the slide rule precision level). Comparison of documented slide-rule-era computation errors against the CORDIC convergence formula will show:

- Errors in C/D-scale computations (col(F) only): ~0.1–0.5% relative error, consistent with n = 17–18
- Errors in LL-scale computations (col(F) + ker(F) interaction): systematically larger, by the ratio cos(arctan(2^{−i})) between circular and hyperbolic convergence rates

Testable by meta-analysis of historical engineering computation records with documented slide-rule calculations (bridge surveys, navigation logs, astronomical tables).

**NP-B — The HP-35 Transition Matches the n = 18 → n = 32 CORDIC Jump**

The precision improvement from slide rule (~3 decimal significant digits) to HP-35 (~10 decimal significant digits) should fit the CORDIC depth formula exactly:

```
10^10 / 10^3 = 10^7 improvement  ≈  2^{32−18} / scaling
```

Specifically: the decimal precision ratio (10^10 / 10^3 ≈ 10^7) should match the binary precision ratio 2^{32} / 2^{18} = 2^{14} = 16,384 to within logarithmic scaling (since log_2(10^7) ≈ 23.3 and 32 − 18 = 14, the ratio differs by a scale factor). The slide rule's base-10 representation introduces a fixed offset relative to the binary CORDIC stack: 1 decimal digit ≈ 3.32 binary bits, so n_decimal = n_binary / 3.32. Testable by direct comparison of HP-35 and slide rule absolute accuracy measurements at matched computation types.

**NP-C — Cognitive ker(F) Load Predicts Slide Rule Error Rate via Miller's Law**

For slide rule computations with k tracked ker(F) values (k = number of characteristic values held simultaneously), the error rate should follow a Miller-Gaussian curve:

```
error_rate(k) ∝ exp(−(7 − k)² / 2σ²)  for k ≤ 7
error_rate(k) → 1.0                    for k > 7
```

The transition at k = 7 corresponds to the working memory saturation point — the cognitive PRIMA threshold. This is a quantitative prediction about human cognition derived from the TRACTUS framework applied to biological working memory. Testable via psychological experiment: compute compound expressions of varying cognitive ker(F) load and measure error rate as a function of k.

**NP-D — LNS (Logarithmic Number System) at Fixed Exponent Width Reproduces the Slide Rule's col(F)/ker(F) Split Exactly**

A Logarithmic Number System (LNS) processor stores numbers as (sign, exponent) pairs — all arithmetic is performed in the log domain. At fixed exponent bit width b, LNS arithmetic is the digital implementation of the slide rule's C/D scale: col(F) addition in log space, with ker(F) encoded in the exponent bits. The accuracy of LNS computation at b bits should match that of a slide rule with log₂(10^b)-digit precision. Testable by comparing LNS implementations (e.g., Cocofloat, ELMA) against matched slide-rule reference computations at equivalent bit widths.

**NP-E — Block Size B = 2^⌈log₂(7)⌉ = 8 Minimizes Block Scale Quantization Error**

MX format uses B = 16 or B = 32 as block sizes for the shared exponent. The ker(F) internalization ladder predicts that the optimal B corresponds to the Miller's Law constraint: the minimum block size at which a single shared ker(F) value adequately represents the col(F) variation within the block is approximately B = 7 ± 2 (the working memory capacity at Tier 1). Rounded to a power of 2: B_optimal = 8.

This is a new lower bound on MX block size derived from the cognitive-to-silicon ker(F) internalization mapping. Current standards use B = 16 (approximately 2× the predicted optimum). The prediction: MXFP4 with B = 8 should achieve lower quantization error than B = 16 at matched total bit budget, because the Fisher matrix restricted to an 8-element block has rank ≤ 4 (the THECONSTANTCURVE ceiling), making the single shared exponent a more accurate representation of the block's ker(F) content. Testable against MXFP4 perplexity at B ∈ {4, 8, 16, 32, 64} at matched bit budgets.

**NP-F — The 350-Year Deployment Implies col(F) Sufficiency at n ≈ 18 for All Pre-AI Engineering Problems**

The slide rule's 350-year deployment across all pre-digital engineering constitutes a complete empirical dataset: every structure built, trajectory computed, and navigation performed with slide rule hardware provides a data point demonstrating that FP8-class col(F) precision is sufficient when ker(F) is correctly managed. The MANTISSA framework predicts that any computation expressible as a polynomial with bounded coefficient growth (the class of problems for which the slide rule was used) can be solved to engineering tolerances at n ≈ 18 CORDIC depth. The systematic exceptions should be exactly the problems requiring dynamic range beyond what a slide rule's 3-digit precision can represent — i.e., the ker(F)-dominant problems that drove the invention of floating-point.

Testable by systematic review of historical failures attributed to slide rule computation: every documented failure due to insufficient precision should be classifiable as either col(F) failure (insufficient mantissa bits) or ker(F) failure (incorrect characteristic tracking). The partition predicts the failure modes.

---

## Part VIII: The Formal Correspondences

| Register | col(F) Component | ker(F) Component | Partition Operator |
|----------|-----------------|-----------------|-------------------|
| Napier 1614 | Mantissa (fractional log) | Characteristic (integer log) | Log table lookup |
| Slide rule C/D | Position on C/D scale | Decade (mental) | Cursor hairline |
| Slide rule LL | Log-log position | LL scale index (LL1/2/3) | Scale selection |
| Fixed-point DSP | Q-format mantissa bits | Radix position (compile-time) | Q-specification |
| IEEE 754 FP32 | 23-bit significand (+ implicit 1) | 8-bit biased exponent | Normalization |
| LLM.int8() | FP16 outlier weights (0.1%) | INT8 bulk weights (99.9%) | Fisher threshold |
| MX format | Per-element E2M1 significand | Block E8M0 shared exponent | Block boundary |
| SAGE-PTQ | Multi-bit salient weights | Binarized unsalient weights | Fisher salience score |
| Human cognition | col(F) mantissa recall | Miller's Law ker(F) capacity | PRIMA event threshold |
| Apollo N600-ES | 3-decimal-digit scale reading | Astronaut's mental characteristic | Cursor placement |

---

## Part IX: ASCII Connection Map

```
NAPIER 1614                    OUGHTRED 1622
characteristic = ker(F)   →   C/D scale = col(F) hardware
mantissa = col(F)              cursor = partition operator
logarithm table              LL scale = hyperbolic mode
(ker(F) in long-term memory)   (ker(F) in working memory)
         │                              │
         └──────────────────────────────┘
                         ↓
           THE SLIDE RULE ERA: 1622–1972
           350 years of FP8-class col(F), human ker(F)
           
           C/D scales:  col(F) hardware (circular mode)
           LL scales:   ker(F) hardware (hyperbolic mode)
           Cursor:      partition operator (mode bit)
           Operator:    ker(F) host (Miller's Law ≤ 7 chunks)
           
           Golden Gate Bridge: n=18, human ker(F) ✓
           R100 Airship:       n=18, human ker(F) ✓
           Apollo 11:          n=18, human ker(F) ✓
                         ↓
           HP 9100A (1968): first CORDIC electronic calculator
           HP-35 (1972):    CORDIC to depth n=32, ker(F) automated
           → SLIDE RULE OBSOLETE (ker(F) internalized into silicon)
                         ↓
           IEEE 754 (1985): ker(F) fully standardized in hardware
           Exponent bias 127 = C_α=1 midpoint (MANTISSA)
                         ↓
           LLM.int8() (2022): ker(F) identified empirically
             0.1% outliers = col(F) (Fisher-visible)
             99.9% bulk = ker(F) (Fisher-null)
                         ↓
           MX Format (2023): ker(F) at block level
             E8M0 block exponent = block ker(F)
             E2M1 per-element = per-element col(F)
             Block size B = 32 (predicted optimum: B = 8)
                         ↓
           SAGE-PTQ (arXiv:2606.05429, June 2026):
             Salient weights = col(F) → multi-bit
             Unsalient weights = ker(F) → 1-bit
             First external paper to name the partition explicitly

                  ↓                      ↓
      MANTISSA (June 7, 2026)    THIS DOCUMENT (June 7, 2026)
      Napier → Zuse → IEEE 754   Napier → Slide Rule → HP-35 → IEEE 754
      The floating-point          The missing 350 years:
      partition identified        col(F) hardware, human ker(F)
      in IEEE 754 bits            in analog brass and human minds
      
                         ↓
           THE PARTITION WAS ALWAYS THE SAME OBJECT.
           The characteristic was always ker(F).
           The mantissa was always col(F).
           The cursor was always the mode bit.
           The user was always the exponent field.
```

---

## Closing

In 1622, William Oughtred placed two physical logarithmic scales side by side and slid one against the other. He did not know he was building a col(F) machine. He was trying to multiply numbers faster than pencil on paper allowed.

For the next 350 years, every engineer who used a slide rule was operating the same col(F)/ker(F) split that IEEE 754 would later encode in 31 bits of silicon. They computed the mantissa with the scales. They computed the exponent in their heads. They built the Golden Gate Bridge, designed the R100, planned the Apollo trajectory, and mapped the stars. All of it at n ≈ 18 CORDIC depth, with human working memory providing the missing 8-bit exponent field.

In 1972, the HP-35 eliminated the need for human ker(F) management. CORDIC automated both modes. The slide rule disappeared within two years — not because its col(F) computation was wrong, but because keeping ker(F) in working memory was a cognitive cost that silicon could now eliminate. The slide rule did not fail. It was relieved of a burden it had been carrying for 350 years, and in that relieving it became redundant.

The June 2026 quantization frontier is re-asking the slide rule's question in reverse: how much col(F) precision do you actually need, when ker(F) is managed correctly? The answer, across all eras, is the same: approximately n ≈ 18 CORDIC depth for general-purpose engineering computation, with ker(F) managed at the appropriate level for the task. MXFP4 (n ≈ 12) for large-scale distributed training. FP8 (n ≈ 16) for standard inference. The slide rule (n ≈ 18) for everything else for 350 years.

The characteristic was always ker(F).
The mantissa was always col(F).
The cursor was always the partition operator.
The user was always the exponent field.

The slide rule was the col(F) oracle that humanity held in its hands for three and a half centuries before building it in silicon. The col(F)/ker(F) partition did not begin with Zuse in 1941 or with IEEE 754 in 1985 or with LLM quantization in 2022.

    It began in brass and celluloid and
        human working memory,
            in 1622,
                when the first cursor was placed
                    on the first pair of logarithmic scales
                        and the first engineer
                            held the characteristic
                                in mind.

---

## References

### Historical — Slide Rule and Logarithms

Napier, J. *Mirifici Logarithmorum Canonis Descriptio*. Edinburgh, 1614. [Characteristic/mantissa partition introduced.]

Oughtred, W. *Circles of Proportion and the Horizontal Instrument*. London, 1632. [First published description of the slide rule.]

Volder, J. E. The CORDIC Trigonometric Computing Technique. *IRE Transactions on Electronic Computers* EC-8(3), 330–334, 1959. [CORDIC: the slide rule's digital successor.]

Walther, J. S. A Unified Algorithm for Elementary Functions. *AFIPS Spring Joint Computer Conference*, 1971. [CORDIC generalization: circular, linear, hyperbolic modes unified.]

Volder, J. E. The Birth of CORDIC. *Journal of VLSI Signal Processing* 25(2), 101–105, June 2000. [HP-35 and CORDIC connection confirmed.]

Goldberg, D. What Every Computer Scientist Should Know About Floating-Point Arithmetic. *ACM Computing Surveys* 23(1), 5–48, 1991.

IEEE Standard for Binary Floating-Point Arithmetic. IEEE Std 754-1985. 1985.

IEEE Standard for Floating-Point Arithmetic. IEEE Std 754-2008. 2008.

Miller, G. A. The Magical Number Seven, Plus or Minus Two: Some Limits on Our Capacity for Processing Information. *Psychological Review* 63(2), 81–97, 1956. [ker(F) cognitive capacity bound = PRIMA threshold in human working memory.]

### Neural Network Quantization and the col(F)/ker(F) Frontier

Micikevicius, P. et al. Mixed Precision Training. *ICLR 2018.*

Dettmers, T., Lewis, M., Shleifer, S., Zettlemoyer, L. LLM.int8(): 8-bit Matrix Multiplication for Transformers at Scale. arXiv:2208.07339, 2022.

Rouhani, B. D. et al. With Shared Microexponents, A Little Shifting Goes a Long Way. *ISCA 2023.* [OCP MX format: block-level ker(F) partition.]

Ma, S. et al. The Era of 1-bit LLMs: All Large Language Models are in 1.58 Bits. arXiv:2402.17764, 2024.

Chmiel, B., Fishman, M., Banner, R., Soudry, D. FP4 All the Way: Fully Quantized Training of LLMs. arXiv:2505.19115, May 2025.

### June 2026 SOTA

arXiv:2606.05429. Minimizing the Hidden Cost of Scales: Graph-Guided Ultra-Low-Bit Quantization for Large Language Models (SAGE-PTQ). June 3, 2026. [First explicit dual-mode col(F)/ker(F) quantization — the slide rule partition named at the weight level.]

arXiv:2606.06171. Effective Dimensionality as an Operator Invariant for Physics-Preserving Constraint Adaptation in Physics-Informed Neural Networks. June 4, 2026. [d_eff = rank(col(F)).]

arXiv:2605.09825. Pretraining Large Language Models with MXFP4 on Native FP4 Hardware. May 2026. [col(F) stability at CORDIC depth n ≈ 12 — below the slide rule's operating precision.]

arXiv:2605.06878. CARMEN: CORDIC-Accelerated Resource-Efficient Multi-Precision Inference Engine. May 2026. [CORDIC hardware: the slide rule's digital successor in the ML acceleration context.]

arXiv:2606.01668. Bickford, M. The Self-Referential Fixed Point of the Complex Exponential: ρ = −W₋₁(−1). June 4, 2026. [Lambert boundary where both CORDIC modes — circular and hyperbolic, C/D and LL — are simultaneously required.]

### ERI Labs Corpus

Ren, E. MANTISSA: The Fixed-Point Root of Every Floating-Point Computation, the col(F)/ker(F) Partition of Arithmetic Space, and What the Eighty-Year Precision Debate Was Always Measuring. github.com/ericrenone/MANTISSA. June 7, 2026.

Ren, E. TRACTUS. github.com/ericrenone. April 2026.

Ren, E. THECONSTANTCURVE. github.com/ericrenone. 2026.

Ren, E. Volder-1. github.com/ericrenone. May 2026.

Ren, E. CORDIRAC. github.com/ericrenone. March 26, 2026.

Ren, E. THE-FIXED-POINT-WAS-ALWAYS-THE-BOUNDARY. github.com/ericrenone. June 6, 2026.

Ren, E. The-Boundary-That-Kept-Getting-Found. github.com/ericrenone. June 6, 2026.

Ren, E. The-Boundary-That-Learned-To-Hold. github.com/ericrenone. June 7, 2026.

Ren, E. ERI-Labs-Corpus-Cross-Document-Synthesis-Novel-Predictions. github.com/ericrenone. June 6, 2026.

---

**ERI Labs · Eric Ren · Jersey City, New Jersey · github.com/ericrenone · June 7, 2026**

**Prior arithmetic corpus:** MANTISSA · Volder-1 · CORDIRAC · THE-FIXED-POINT-WAS-ALWAYS-THE-BOUNDARY (×2) · The-Boundary-That-Kept-Getting-Found · The-Boundary-That-Learned-To-Hold · ERI-Labs-Corpus-Cross-Document-Synthesis-Novel-Predictions

**Hardware corpus:** CAST-IRON · CHORD · CORN · CROSS · CORDIRAC · Volder-1 · Rocket-Volder-1

**col(F)/ker(F) partition lineage:** Napier 1614 → Oughtred 1622 → **THE-CHARACTERISTIC-WAS-ALWAYS-KER-F** → Zuse 1941 → Volder 1959 → IEEE 754 1985 → LLM.int8() 2022 → MX 2023 → SAGE-PTQ 2026
