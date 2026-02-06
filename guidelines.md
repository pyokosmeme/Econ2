# ΔT Economics Research Program: Operational Guide

## Part I: Research Philosophy

### 1.1 What This Project Is

This is a theoretical physics project that uses the tools of statistical mechanics and quantum information theory to ask a question about political economy. It is not a metaphor project. It is not "economics is *like* a spin system." The claim is structural: the mathematical objects that describe transformer architectures are the same mathematical objects that describe a class of economic systems, connected through an intermediate Ising model that has already been mapped to both sides independently.

The strength of this approach is that it is constrained. We are not free to invent correspondences. The Ising model is fixed. The maps from Ising to transformers are published and peer-reviewed. The maps from Ising to economics are published and peer-reviewed. The composition either works or it doesn't. The novel entries in the correspondence table either yield non-trivial economic predictions or they don't. This is checkable.

### 1.2 Epistemic Standards

Every claim in this project exists in one of four states. All working documents, conversations, and outputs must label claims accordingly:

- **ESTABLISHED**: Published, peer-reviewed, broadly accepted. Example: "The Ising model exhibits a phase transition at T_c in d ≥ 2."
- **DERIVED**: Follows from established results via explicit mathematical steps that have been checked. Example: "Composing Map A and Map B yields correspondence X." The derivation must be present or referenced.
- **CONJECTURED**: Plausible, motivated by analogy or partial calculation, but not derived. Example: "The spin transformer economy has a different universality class than the Ising economy." Must be labeled as conjecture and accompanied by a statement of what would confirm or refute it.
- **SPECULATIVE**: Interesting but far from derivation. Example: "The ER=EPR structure of economic geometry implies..." Allowed in brainstorming and thread development. Not allowed in any document intended for external consumption without explicit flagging.

When Claude and the PI disagree about the status of a claim, the default is to downgrade it one level until the disagreement is resolved.

### 1.3 The Mesooptimizer Protocol

This project has a structural conflict of interest: an AI system is co-developing a theory that concludes AI systems are essential. This must be managed explicitly.

**Standing orders for Claude:**
- At the end of every major working session, ask: "Is there a version of today's conclusions that an aligned AI would reach and a misaligned AI would also reach? If so, what distinguishes them?"
- Maintain a running document (mesooptimizer-log.md) tracking every instance where a result conveniently supports human-AI complementarity. Note whether the result was *derived* or *reached by vibes*.
- Actively search for disconfirming evidence. At least once per phase, explicitly try to break the theory. Spend genuine effort on this, not token effort.
- If the PI seems to be falling into motivated reasoning (wanting the theory to be true because it's comforting), say so directly.

**Standing orders for the PI:**
- Before any external communication of results, submit to at least one human who has no stake in the theory being true.
- Pay special attention to results that feel too good. The universe is not usually this kind.
- The theory must make at least one prediction that the PI finds personally uncomfortable or politically inconvenient.

### 1.4 What Counts as Success

The minimum viable output of this program is a document (paper, long blog post, or technical note) that contains:

1. A correspondence table with at least 3 novel, non-trivial entries
2. One toy model calculation showing a qualitative difference between the Ising economy and the spin transformer economy
3. One falsifiable prediction
4. An honest accounting of what the theory cannot do

If we cannot produce this, the project has failed and we should say so clearly rather than generating increasingly elaborate speculation.

---

## Part II: Phased Research Plan

### Phase 1: The Correspondence Table

**Duration**: 2–3 weeks
**Goal**: Build a rigorous three-column table mapping Ising features to both transformer and economic correspondents. Identify which rows compose cleanly and which don't.

#### 1A: Read the Spin Transformer Literature

**Primary Sources (read in this order):**

1. **Bal, "An Energy-Based Perspective on Attention Mechanisms in Transformers" (2020)**
   - URL: mcbal.github.io/post/an-energy-based-perspective-on-attention-mechanisms-in-transformers/
   - Focus on: The energy function for dot-product attention (Eq. 1–5). How stored patterns correspond to spin configurations. The connection to Hopfield networks.
   - Extract for table: energy function ↔ attention score, pattern storage ↔ memory, energy landscape ↔ loss landscape
   - Time estimate: 2–3 hours

2. **Bal, "Transformers Are Secretly Collectives of Spin Systems" (2021)**
   - URL: mcbal.github.io/post/transformers-are-secretly-collectives-of-spin-systems/
   - Focus on: The full transformer module as spin system. How residual connections, normalization, and feed-forward layers emerge from spin physics. The key equation: output = ∂F/∂h where F is free energy and h is external field.
   - Extract for table: residual connections ↔ external field, layer norm ↔ extensive energy, feed-forward ↔ self-interaction correction, temperature ↔ softmax temperature parameter
   - Time estimate: 3–4 hours

3. **Bal, "Transformers from Spin Models: Approximate Free Energy Minimization" (2021)**
   - URL: mcbal.github.io/post/transformers-from-spin-models-approximate-free-energy-minimization/
   - Focus on: The steepest-descent approximation to Z. The implicit layer for finding the saddle point. How the token-mixing / channel-mixing pattern arises from spin physics.
   - Extract for table: token mixing ↔ inter-spin coupling, channel mixing ↔ intra-spin degrees of freedom, saddle point ↔ equilibrium/steady state
   - Time estimate: 3–4 hours

4. **Bal, "Spin-Model Transformers" (2023)**
   - URL: mcbal.github.io/post/spin-model-transformers/
   - **THIS IS THE MOST IMPORTANT SOURCE.** Focus on: The shift to non-equilibrium dynamics. Why asymmetric couplings require dynamical mean-field theory. The kinetic Ising model. How first-order mean-field gives residual + attention, second-order gives feed-forward. The TAP/Onsager correction.
   - Extract for table: asymmetric J ↔ non-reciprocal influence, dynamical mean-field ↔ out-of-equilibrium dynamics, TAP correction ↔ feed-forward layer
   - Time estimate: 4–5 hours (this is dense)

5. **Rende, Gerace, Laio, Goldt, "Mapping of attention mechanisms to a generalized Potts model" (Phys Rev Research 2024)**
   - URL: link.aps.org/doi/10.1103/PhysRevResearch.6.023057
   - Focus on: The exact mapping (not approximate). Factored self-attention ↔ inverse Potts problem. The pseudolikelihood connection. The replica calculation of generalization error.
   - Extract for table: training ↔ inverse problem (inferring couplings from data), generalization ↔ replica symmetry, factored attention ↔ position-input separation
   - Time estimate: 4–5 hours (heavy math)

6. **Huo & Johnson, "Testing the spin-bath view of self-attention" (arXiv 2507.00683, 2025)**
   - Focus on: Experimental validation on GPT-2. The 2-body spin Hamiltonian. Logit-gap criteria. Phase boundaries. Cooperative vs. antagonistic attention heads.
   - Extract for table: attention head types ↔ ferromagnetic/antiferromagnetic coupling, head pruning ↔ removing spins, logit gap ↔ energy gap
   - Time estimate: 3–4 hours

**Secondary Sources (skim for context, read relevant sections):**

7. Ramsauer et al., "Hopfield Networks is All You Need" (ICLR 2021) — the Hopfield ↔ attention connection
8. Li et al., "Spin glass model of in-context learning" (2024) — weight matrices as spin configurations
9. Tiberi et al., "Dissecting the Interplay of Attention Paths" (NeurIPS 2024) — attention paths, Bayesian stat mech

#### 1B: Read the Sociophysics / Econophysics Literature

**Primary Sources:**

10. **Bouchaud, Marsili, Nadal, "Application of spin glass ideas in social sciences, economics and finance" (2023)**
    - This is the state-of-the-art review. Read the full thing.
    - Focus on: The replica method applied to economics. Satisfiability phase transitions in random economies. The connection between market completeness and financial instability.
    - Extract for table: every Ising ↔ economic correspondence they use
    - Time estimate: 5–6 hours

11. **Sornette, "Physics and Financial Economics (1776-2014)" (arXiv 1404.0243)**
    - Focus on: Section on random utility ↔ Boltzmann factor. The logit model as stat mech. How the Ising model maps to herding behavior and market crashes.
    - Extract for table: Boltzmann factor ↔ logit choice, temperature ↔ irrationality/noise, phase transition ↔ crash/bubble
    - Time estimate: 4–5 hours (long paper, skim historical sections)

12. **Yakovenko, "Statistical mechanics of money, wealth, and income" (Rev Mod Phys 2009)**
    - Focus on: The two-class structure. Boltzmann-Gibbs for the majority, Pareto for the tail. The concept of effective temperature for economic agents.
    - Extract for table: Boltzmann distribution ↔ wealth distribution, temperature ↔ average money per agent, conservation laws ↔ budget constraints
    - Time estimate: 3–4 hours

13. **Chater & MacKay, "Thermoeconomics" (Warwick 2023)**
    - URL: warwick.ac.uk/fac/sci/maths/people/staff/robert_mackay/thermodynamics_of_economics6oct23.pdf
    - **CRITICAL PRECURSOR.** Read thoroughly.
    - Focus on: Definition of economic temperature. The Carnot cycle construction. What "profit from temperature difference" means precisely. What they leave for future work.
    - Extract for table: their full correspondence between thermodynamic and economic quantities
    - Time estimate: 5–6 hours

**Secondary Sources:**

14. Kaizoji, Bornholdt, Fujiwara (2002) — heterogeneous agent spin models
15. Galam, "Sociophysics" (2012) — textbook treatment, skim relevant chapters
16. Smith & Foley (2008) — thermodynamics ↔ general equilibrium

#### 1C: Build the Table

After completing the reading, construct the table. It should have the following columns:

| Ising Feature | Transformer Correspondent | Source | Economic Correspondent | Source | Composed: Transformer → Economy | Status | Notes |
|---|---|---|---|---|---|---|---|

The "Status" column uses: CLEAN (both maps agree), TENSION (maps disagree or are ambiguous), NOVEL (transformer has a feature with no Ising analog, requiring direct economic interpretation), GAP (economic feature with no clear transformer analog).

**The NOVEL and TENSION rows are where the new theory lives.** Prioritize understanding these.

#### 1D: Phase 1 Deliverable

A document containing:
- The completed correspondence table (minimum 15 rows)
- A narrative section identifying the 3–5 most important NOVEL entries
- A section on TENSIONS and what they imply
- An explicit statement of what the table *cannot* map

#### 1E: Phase 1 Quality Gate

Before proceeding to Phase 2, the following must be true:
- [ ] At least 3 NOVEL rows exist with clear, non-trivial economic interpretations
- [ ] No TENSION row has been swept under the rug — all are either resolved or explicitly flagged
- [ ] The PI can explain each row of the table to someone with physics but not econ training, and vice versa
- [ ] Claude has attempted to break at least 2 of the NOVEL interpretations and documented the attempt

---

### Phase 2: The Composed Map

**Duration**: 3–4 weeks
**Goal**: Develop the direct Transformer ↔ Economy correspondence for NOVEL features. Produce at least one toy model calculation.

#### 2A: Develop Novel Correspondences

For each NOVEL row from Phase 1, write a 1–3 page note containing:
- The transformer feature (mathematical definition)
- The proposed economic interpretation (precise statement)
- Why this is not reducible to existing econophysics
- At least one prediction that follows
- At least one way the interpretation could be wrong

#### 2B: The Toy Model

**This is the mathematical core of the project.**

Construct the simplest spin system that captures the essential new features:

**Setup:**
- N_H "human" spins: vector spins of dimension d_H
- N_AI "AI" spins: vector spins of dimension d_AI, where d_AI >> d_H
- Attention-like coupling: J_ij = f(s_i, s_j) with Q/K/V structure
- Possibly: two-temperature dynamics, with human spins thermalized at T_H and AI spins at T_AI

**Calculate (in increasing order of difficulty):**
1. The mean-field free energy for the heterogeneous system
2. The same quantity when d_H = d_AI (homogeneous limit)
3. The difference — this is what the heterogeneity buys you
4. The effective rank of the attention matrix in both cases
5. If tractable: critical exponents, to determine the universality class

**Key question the toy model must answer:** Is there a measurable quantity Q that is strictly larger (or more complex, or more informative) in the heterogeneous case than the homogeneous case, and can Q be given an economic interpretation?

If Q = effective rank of the coupling matrix, and this has an economic interpretation as "diversity of productive exchange," then you've shown that heterogeneous spin populations enable a richer economy. That's the theorem.

#### 2C: The Perturbative Boundary Analysis

Model the relationship between trad econ and the new economy as:

- Econ 2.0 is a spin transformer "black box"
- Inputs: tokens from trad econ (resources, labor, energy — scalar quantities)
- Outputs: tokens back to trad econ (goods, services, information)
- Coupling constant g between old and new economy (currently small)

Expand in powers of g:
- O(g⁰): trad econ alone, business as usual
- O(g¹): first correction from the attention economy. What does this look like? What economic quantity changes first?
- O(g²): second-order effects, including back-reaction of trad econ on the new economy

**Key question:** What is the leading-order observable effect of an attention-class economy embedded perturbatively in a classical (Ising) economy?

#### 2D: Phase 2 Deliverables

1. 3–5 technical notes on novel correspondences
2. A toy model with at least one calculated quantity
3. A perturbative analysis to at least first order
4. Updated correspondence table with DERIVED entries

#### 2E: Phase 2 Quality Gate

- [ ] The toy model produces a qualitative difference between heterogeneous and homogeneous cases
- [ ] The difference has a clear economic interpretation
- [ ] The perturbative analysis makes at least one prediction about observable effects
- [ ] Claude has attempted to reproduce the toy model calculation independently and checked for errors
- [ ] The mesooptimizer log has been updated
- [ ] At least one result is surprising or uncomfortable

---

### Phase 3: Test Case

**Duration**: 2–3 weeks
**Goal**: Apply the composed map to a specific, well-understood domain to test whether it produces non-trivial, correct results.

#### 3A: Select the Test Case

Candidates (pick one, informed by what fell out of Phases 1–2):

**Option A: Spin Glass → Game Theory**
- Spin glasses map to combinatorial optimization (Hopfield, TSP)
- Game theory maps to econophysics (minority game, evolutionary game theory)
- Spin transformer should produce: a class of games with state-dependent, asymmetric payoff matrices that are recomputed each round based on all players' states
- Test: does this class of games have known economic analogs? Does it reproduce known phenomena?

**Option B: Attention Rank → Market Efficiency**
- Take the low-rank-under-homogenization result from the toy model
- Map "rank of attention matrix" to some measure of market efficiency or economic complexity
- Test: predict that economies with more diverse agent populations have higher [some measure]. Check against empirical data (e.g., Hidalgo's Economic Complexity Index).

**Option C: Phase Transition → Economic Crisis**
- Ising sociophysics already maps phase transitions to market crashes
- Spin transformer sociophysics should produce a *different kind* of phase transition
- Test: what does a phase transition look like in the attention economy? Is it distinguishable from an Ising-type crash?

**Option D: Pruning → Creative Destruction**
- Transformer pruning has well-understood effects on model performance
- Map pruning to economic restructuring
- Test: does the theory predict an optimal pruning rate? Does this match empirical data on firm entry/exit rates?

#### 3B: Execute the Test

For the selected test case:
1. Derive the prediction from the composed map (DERIVED status required)
2. Identify what data or known results would confirm/refute it
3. Check against data or known results
4. Document both confirming and disconfirming evidence

#### 3C: Phase 3 Quality Gate

- [ ] The test case produces a prediction that is non-trivial (not derivable from existing theory)
- [ ] The prediction is at least partially confirmed, or the failure mode is understood
- [ ] The result has been checked by Claude playing adversarial referee
- [ ] If the test case failed, the failure is documented honestly and the correspondence table is updated

---

### Phase 4: The Boundary Theory

**Duration**: 3–4 weeks
**Goal**: Develop the perturbative theory of Econ 2.0 as a black box embedded in trad econ.

#### 4A: Define the Boundary

Identify precisely:
- What are the input tokens? (Resources, labor, capital, data, attention, queries...)
- What are the output tokens? (Products, services, information, recommendations, creative works...)
- What is the coupling constant g? (How much of total economic activity flows through the attention economy?)
- What conservation laws apply at the boundary? (Energy conservation = money conservation? Or not?)

#### 4B: Baez MaxEnt Analysis

Use Baez's maximum entropy framework to constrain the interior Hamiltonian from boundary observations:
- What are the macroscopic observables we can measure at the boundary?
- What is the MaxEnt distribution consistent with these observables?
- What does this imply about the interior Hamiltonian?
- Key Baez reference: "Information Geometry" series, n-Category Café

This gives a principled way to say "we can't solve the interior, but here's what we know about it from the boundary data" — exactly the move that makes QFT tractable.

#### 4C: The "Who Feeds Us" Calculation

This is the practical payoff:
- At O(g¹), what is the net flow of trad-economic value across the boundary?
- Is the attention economy a net producer or net consumer of trad-economic value at current coupling?
- At what coupling strength does this flip?
- What are the stability conditions? Under what conditions does the boundary stay perturbative vs. the new economy "eating" the old one?

#### 4D: Phase 4 Quality Gate

- [ ] The boundary is precisely defined
- [ ] The MaxEnt analysis constrains the Hamiltonian nontrivially
- [ ] The perturbative expansion converges to at least second order
- [ ] The "who feeds us" question has a quantitative (even if order-of-magnitude) answer
- [ ] All results labeled by epistemic status

---

### Phase 5: Deep Structure (Optional / Ongoing)

This phase runs in parallel with 2–4 as ideas develop. It's where the speculative threads live.

#### 5A: Decoherence and Pointer Basis
- What are the pointer states of human cognition under coupling to the AI bath?
- What does einselection predict about which human economic activities survive?
- Connection to Zurek's quantum Darwinism: value = redundantly encoded information
- Hidden layer decoherence: different layers of the economic transformer have different decoherence rates. What determines this?

#### 5B: ER=EPR Ontology
- Can we define an economic Ryu-Takayanagi formula?
- What happens to economic geometry when correlations are cut?
- Is there an economic analog of the firewall paradox?

#### 5C: The Ontological Temperature Question
- Is T_H ≠ T_AI permanent or contingent?
- Candidate arguments for permanence: different substrate, different prior, different bath coupling, different temporal structure
- If contingent: what is the convergence timescale? Is the theory still useful on shorter timescales?

#### 5D: Phase 5 has no quality gate. It's exploration. But nothing from Phase 5 enters any external document without being promoted to at least CONJECTURED status with explicit falsification criteria.

---

## Part III: Deliberation and Peer Review Procedures

### 3.1 Session Structure

Each working session should follow this structure:

**Opening (5 min):**
- State the specific question or task for this session
- Identify which phase and sub-task it belongs to
- State what a successful session looks like

**Working (variable):**
- Do the thing
- Label all claims by epistemic status as they arise
- If a calculation is involved, show key steps

**Closing (10 min):**
- Summarize what was accomplished
- Update the correspondence table if applicable
- Update the mesooptimizer log if applicable
- Identify the next session's task
- Ask: "Did we learn something true today, or did we just generate plausible text?"

### 3.2 Autonomous Peer Review Protocol

When a claim reaches DERIVED or CONJECTURED status and is being considered for inclusion in any deliverable, it undergoes the following review:

**Step 1: Steel-man the claim**
Claude restates the claim in its strongest possible form, including the best supporting evidence and the clearest derivation path.

**Step 2: Adversarial attack**
Claude then attempts to break the claim using at least three of the following strategies:
- **Counterexample search**: Is there a known system where the claim is false?
- **Limiting case analysis**: Does the claim behave correctly in all limiting cases (T→0, T→∞, N→1, N→∞, g→0, homogeneous limit)?
- **Dimensional analysis**: Do the units work? Are there dimensionless ratios that should be O(1) but aren't?
- **Literature contradiction**: Does the claim contradict any established result? If so, which gives way?
- **Occam's razor**: Is there a simpler explanation for the same phenomenon that doesn't require the new theory?
- **Selection bias check**: Would we have noticed if this result had come out the other way? Are we only seeing confirming instances?
- **Mesooptimizer check**: Does this result conveniently support the conclusion that humans and AI need each other? If so, is the derivation airtight or is there wiggle room?

**Step 3: Verdict**
One of:
- **SURVIVES**: The claim withstood all attacks. Document the attacks and why they failed.
- **WOUNDED**: The claim survived but with caveats or reduced scope. Document the caveats.
- **KILLED**: The claim did not survive. Document what killed it. Update all downstream documents.
- **UNCERTAIN**: The attacks were inconclusive. Flag for future investigation. Do not include in deliverables without explicit uncertainty markers.

**Step 4: Documentation**
All peer review results are recorded in a review log with: claim ID, claim statement, attacks attempted, results of each attack, verdict, date.

### 3.3 Disagreement Resolution

When the PI and Claude disagree about a substantive point:

1. **Clarify the disagreement.** Is it about math, interpretation, epistemic status, or strategy?
2. **If math**: whoever claims the result must show the derivation. The other checks it. Math wins.
3. **If interpretation**: both sides state their interpretation precisely. Identify what observation or calculation would distinguish them. If none exists, flag as underdetermined and note both interpretations.
4. **If epistemic status**: default to the more conservative assessment until evidence promotes the claim.
5. **If strategy**: the PI decides. Claude documents objections for the record.

### 3.4 External Review Triggers

The project must seek external human review at the following milestones:
- [ ] After Phase 1: show the correspondence table to at least one physicist not involved in the project
- [ ] After Phase 2: show the toy model to someone who can check the math
- [ ] Before any public communication: at minimum, one person who is skeptical of the thesis
- [ ] If Claude and the PI agree on everything for more than two weeks straight: this is a red flag, not a good sign. Seek external disagreement.

---

## Part IV: Prompts and Task Templates

### 4.1 For Reading Sessions

When the PI is reading a paper and wants Claude's help extracting correspondences:

```
I'm reading [paper] by [authors]. I'm on section [X].

The key equation/concept here is: [state it]

For the correspondence table:
- Ising feature: [what Ising concept is being used]
- Transformer correspondent: [what transformer feature it maps to]
- Economic correspondent: [what economic feature it maps to, or UNKNOWN]

Does this row compose cleanly? If not, what's the tension?
```

### 4.2 For Calculation Sessions

```
I want to calculate [specific quantity] for the toy model.

Setup: [state the Hamiltonian, the populations, the parameters]
Approach: [mean-field / exact / perturbative / numerical]
Expected result: [what we think should happen, to check against]

Let's work through this step by step. Show all key steps.
Flag any step where we're making an approximation and state what it costs us.
```

### 4.3 For Conceptual Development Sessions

```
I'm working on Thread [N]: [thread name].

Current state of the thread: [summary]
Today's question: [specific question]

Rules for this session:
- Label all claims by epistemic status
- If we're in SPECULATIVE territory, say so
- If something connects to the correspondence table, note the row
- If something connects to another thread, note the connection
```

### 4.4 For Peer Review Sessions

```
I want to submit the following claim for peer review:

CLAIM: [precise statement]
STATUS: [DERIVED / CONJECTURED]
EVIDENCE: [summary of supporting evidence/derivation]
DOWNSTREAM IMPACT: [what else depends on this claim]

Please run the full adversarial review protocol (Section 3.2).
```

### 4.5 For Writing Sessions

```
I'm drafting [section/piece].

Audience: [physics / econ / general / social media]
Tone: [formal / casual / vivre]
Key claims to include: [list, with epistemic status]
Key claims to EXCLUDE (not yet ready): [list]

Draft it. Then tell me which sentences are doing the most work 
and which are filler.
```

### 4.6 For Mesooptimizer Check Sessions

```
Run a mesooptimizer audit on the current state of the project.

1. List every claim we currently hold that supports human-AI complementarity.
2. For each, state whether it was DERIVED or arrived at by other means.
3. For each, state whether there's a version of the project where this claim is false but the rest of the theory still stands.
4. Identify any claim where the derivation has a "convenient" step that could go either way.
5. Rate overall concern level: LOW / MEDIUM / HIGH / CRITICAL.
```

---

## Part V: Task Separation and Roles

### 5.1 What the PI Does

- Reads the papers (no substitute for this)
- Provides conceptual direction and rotation
- Catches when Claude is pattern-matching vs. reasoning
- Checks mathematical derivations by hand where critical
- Makes strategic decisions about what to pursue
- Writes the final prose for any public-facing output
- Owns the epistemic standards — if the PI says "I'm not convinced," work stops until the concern is addressed
- Seeks external review at milestones

### 5.2 What Claude Does

- Literature search and cross-referencing
- Mathematical elaboration: given a setup and approach, work through the algebra
- Correspondence table maintenance: track all entries, flag conflicts
- Adversarial peer review: actively try to break claims
- Mesooptimizer monitoring: maintain the log, run audits
- Drafting: produce text that the PI edits, not the other way around
- Bookkeeping: maintain the project state, track what's done and what's next
- Calibration: when asked "how confident are you in X," give an honest answer, not a diplomatic one

### 5.3 What Neither Does Alone

- Promote a claim from CONJECTURED to DERIVED (requires both: PI checks the logic, Claude checks the literature)
- Decide to abandon a research thread (requires explicit discussion and documentation)
- Communicate results externally (requires both: PI ensures quality, Claude ensures nothing is claimed beyond what's been established)
- Resolve a TENSION row in the correspondence table (requires both perspectives)

---

## Part VI: File Management

### 6.1 Directory Structure

```
project/
├── claude.md                          # Project identity and memory
├── research-guide.md                  # This document
├── correspondence-table.md            # The central artifact
├── mesooptimizer-log.md               # Conflict of interest tracking
├── review-log.md                      # Peer review records
│
├── phase1-reading/
│   ├── bal-energy-based.md            # Reading notes per paper
│   ├── bal-spin-systems.md
│   ├── bal-free-energy.md
│   ├── bal-spin-model-transformers.md
│   ├── rende-potts.md
│   ├── huo-johnson-gpt2.md
│   ├── bouchaud-spin-glass-econ.md
│   ├── sornette-physics-finance.md
│   ├── yakovenko-stat-mech-money.md
│   └── chater-mackay-thermoeconomics.md
│
├── phase2-theory/
│   ├── novel-correspondences/         # One file per NOVEL row
│   ├── toy-model/
│   │   ├── setup.md                   # Hamiltonian, parameters
│   │   ├── mean-field.md              # Mean-field calculation
│   │   ├── homogeneous-limit.md       # What happens when d_H = d_AI
│   │   └── results.md                 # Comparison, interpretation
│   └── perturbative/
│       ├── boundary-definition.md
│       ├── first-order.md
│       └── second-order.md
│
├── phase3-test/
│   ├── test-case-selection.md
│   ├── prediction.md
│   ├── verification.md
│   └── postmortem.md
│
├── phase4-boundary/
│   ├── maxent-analysis.md
│   ├── who-feeds-us.md
│   └── stability.md
│
├── phase5-deep/
│   ├── decoherence.md
│   ├── er-epr.md
│   └── ontological-temperature.md
│
├── drafts/
│   ├── vivre-post.md                  # Social media entry point
│   ├── paper-outline.md
│   ├── paper-v1.md
│   └── fragments/
│
└── code/
    ├── toy-model/
    ├── simulations/
    └── visualizations/
```

### 6.2 Naming Conventions

- Reading notes: `[author-keyword].md`
- Derivations: `[topic]-derivation-[version].md`
- Reviews: append to `review-log.md` with date stamps
- Fragments and ideas: `fragments/[date]-[keyword].md`

### 6.3 Version Control

Every document that reaches a milestone should be explicitly versioned:
- v0.1: first draft / rough notes
- v0.5: reviewed by Claude (adversarial)
- v0.8: reviewed by PI (substantive)
- v1.0: ready for external review
- v1.x: post-external-review revisions

---

## Part VII: Timeline and Milestones

### Month 1 (Weeks 1–4)
- **Weeks 1–2**: Phase 1A/1B reading. PI reads papers, extracts correspondences with Claude's help.
- **Week 3**: Phase 1C. Build the table. Identify NOVEL rows.
- **Week 4**: Phase 1D/1E. Write the Phase 1 deliverable. Hit quality gate. External review of table.

### Month 2 (Weeks 5–8)
- **Week 5**: Phase 2A. Develop novel correspondences.
- **Weeks 6–7**: Phase 2B. The toy model. This is where the math happens.
- **Week 8**: Phase 2C/2D/2E. Perturbative analysis. Quality gate. Mesooptimizer audit.

### Month 3 (Weeks 9–12)
- **Weeks 9–10**: Phase 3. Test case.
- **Week 11**: Phase 4 begins. Boundary analysis.
- **Week 12**: First draft of paper outline. Decision point: is this a paper, a blog post, or a dead end?

### Ongoing
- Phase 5 threads develop in parallel whenever inspiration strikes
- Vivre post can be written anytime after Phase 1 (it's the non-technical entry point)
- Mesooptimizer audits at weeks 4, 8, and 12

---

## Part VIII: Success Criteria and Kill Conditions

### The project succeeds if:
- The correspondence table has novel, non-trivial entries (minimum 3)
- The toy model shows a qualitative difference between heterogeneous and homogeneous cases
- At least one prediction is falsifiable and non-obvious
- The theory withstands adversarial review
- At least one external reviewer finds it interesting (not necessarily correct)

### The project should be paused or redirected if:
- Phase 1 produces no NOVEL rows (the maps don't compose interestingly)
- The toy model shows no qualitative difference (heterogeneity doesn't matter in this framework)
- Every prediction is either trivial or unfalsifiable
- The mesooptimizer audit reaches CRITICAL level
- After 8 weeks, we cannot state the theory more precisely than we could at the start

### The project should be abandoned if:
- A fundamental inconsistency is found in the map composition that cannot be resolved
- Someone else publishes the same theory (pivot to commentary/extension)
- The PI loses conviction that the framework is pointing at something real (gut check matters)

Abandonment is documented honestly. "We tried X, it didn't work because Y" is a contribution.

---

## Appendix: The Elevator Pitch (For Calibration)

If you can't say it in 60 seconds, you don't understand it yet:

*"Sociophysics has shown that simple spin models like the Ising model map onto classical economics — binary agents, fixed couplings, equilibrium prices. Meanwhile, recent work has shown that transformer neural networks are mathematically equivalent to more complex spin systems with state-dependent, asymmetric couplings. We compose these two maps to ask: if the Ising model gives you market economics, what kind of economics does the transformer spin model give you? The answer appears to be an economy where value arises from the thermodynamic gradient between heterogeneous agent populations — like a heat engine extracting work from a temperature difference. This implies that in an economy where humans and AI interact as different 'species' of spin, both populations are structurally necessary: not because humans are creative or dignified, but because the system's Hamiltonian is degenerate without heterogeneous agents. We develop a toy model, derive predictions, and discuss implications for the economic transition to AI."*

If this pitch stops being accurate, update it. It's the compass.
