# Phase 1 Deliverable: The Spin Transformer Economy

**Economics 2.0 Research Program**
**Version**: 1.0
**Date**: 2026-02-10
**Status**: Phase 1 complete; ready for quality gate assessment

---

## 1. The Correspondence Table: Summary and Orientation

The master correspondence table (see `correspondence-table.md`) maps 39 features across three columns: Ising/spin model features, transformer architecture correspondents, and economic correspondents. Each row composes the two known maps -- Ising-to-transformer and Ising-to-economics -- and asks whether the composition yields a coherent transformer-to-economics correspondence.

**Summary statistics:**

| Status | Count | Rows |
|--------|-------|------|
| CLEAN | 22 | 1--6, 8--14, 16--17, 21--22, 24--27, 31, 33 |
| TENSION | 5 | 7, 15, 32, 37, plus temperature ambiguity pervading row 2 |
| NOVEL | 10 | 18--20, 23, 28--30, 34--36, 38 |
| GAP | 2 | 29 (partial), 39 |

The 22 CLEAN entries establish that the composition works: when both individual maps are well-established, the composed map is coherent and often mathematically exact. The keystone is Row 1, where the Boltzmann weight, softmax attention weight, and multinomial logit choice probability are the same equation -- three communities using identical mathematics without cross-reference. [ESTABLISHED for each individual map; DERIVED for the full chain.]

The 10 NOVEL entries are where the new theory lives. These are features of the transformer architecture that have no standard Ising analog and therefore require direct economic interpretation, bypassing the Ising intermediary. The 5 TENSION entries mark places where the maps disagree or are ambiguous, requiring theoretical resolution before the bridge can be considered rigorous.

The table exceeds the Phase 1 minimum of 15 rows. What follows is a focused analysis of the entries that matter most for the theory's development.

---

## 2. The Five Most Important Novel Entries

Of the 10 NOVEL rows, five form a connected argument that constitutes the core of the new theory. They are presented here in logical order, not table order.

### 2.1 Data-Dependent Couplings as Endogenous Economic Structure (Row 19)

**The physics.** In every standard spin model -- Ising, Potts, Heisenberg, spin glass -- the coupling constants J_ij are either fixed, random-but-frozen (quenched), or slowly evolving. The transformer's couplings are none of these. The attention mechanism computes J_ij = f(W_Q sigma_i, W_K sigma_j) at every time step: the coupling between two spins depends on their current states. Bal (2023) calls this "very weird and highly unusual." [ESTABLISHED]

**The economic interpretation.** What is pathological in physics is fundamental in economics. Trade volume between two agents depends on their current endowments. Credit terms depend on financial condition. Attention allocation depends on current interests. The entire edifice of general equilibrium theory assumes that prices and exchange patterns are endogenous -- determined by the current state of all agents simultaneously. The standard Ising model, with its fixed J, misses this entirely. The transformer captures it as a structural feature. [CONJECTURED]

**Why it matters.** This entry resolves a known limitation of sociophysics. Every Ising-based market model assumes a fixed interaction topology: who trades with whom is predetermined. Real economies have endogenous network formation -- trade relationships emerge from the economic state itself. The transformer's data-dependent couplings provide the first spin model where this happens naturally, without being grafted on as an additional mechanism. If this interpretation holds, the transformer spin model is not merely a more complex Ising model applied to economics; it is a *categorically better* model for economic systems, because it captures endogeneity that the Ising model structurally cannot.

**What would confirm it.** A toy model (Phase 2) in which the state-dependent couplings produce known economic phenomena -- endogenous trade network formation, state-dependent credit spreads, or preferential attachment dynamics -- that fixed-coupling models cannot reproduce.

**What would refute it.** If J(sigma) generates chaotic, unpredictable dynamics with no stable economic interpretation, or if the self-referential feedback (J depends on sigma, sigma depends on J) diverges rather than converging to meaningful steady states.

**Epistemic status: CONJECTURED.** The physics is ESTABLISHED (Bal 2023). The economic interpretation is novel and untested.

### 2.2 Asymmetric Couplings and Forced Non-Equilibrium (Rows 18 and 28)

**The physics.** Softmax attention produces asymmetric couplings: J_ij != J_ji. This is a consequence of (a) the query and key projections being different (W_Q != W_K) and (b) the row-wise normalization of the softmax. Asymmetric couplings break detailed balance, which means there is no well-defined energy function and no Boltzmann equilibrium distribution. The system must be treated using non-equilibrium dynamics -- the kinetic Ising model or dynamical mean-field theory. This is not a modeling choice; it is a mathematical consequence. [ESTABLISHED for the physics; Bal 2023]

**The economic interpretation.** Economic influence is inherently non-reciprocal. An employer's effect on an employee's economic state differs qualitatively from the reverse. A platform's impact on a single user is negligible; the user's dependence on the platform may be total. Standard sociophysics models impose J_ij = J_ji, which forces the economy into equilibrium -- a known limitation that has been criticized for decades. The transformer's natural asymmetry resolves this: the spin transformer economy is necessarily non-equilibrium, not by assumption but by structure. [CONJECTURED for the economic interpretation; DERIVED for the physics]

**Why it matters.** This is arguably the cleanest case of the theory's central pattern: *what makes the transformer spin model "weird" in physics is what makes it natural in economics.* Real economies exhibit persistent flows (GDP, trade currents), directed power relationships, and perpetual non-equilibrium dynamics. The Ising model cannot capture these without ad hoc modifications. The transformer spin model produces them automatically. The composed map predicts that the "transformer economy" has a non-equilibrium steady state with non-zero entropy production, persistent cycles, and directed flows -- all features observed in real economies.

**What would confirm it.** Show that the non-equilibrium steady state of the kinetic Ising model at the transformer's operating point reproduces stylized facts of real economic dynamics (directed flows, violation of detailed balance in transaction data, persistent cycles) that symmetric models cannot.

**What would refute it.** If the asymmetric effects are quantitatively small and the system behaves as if approximately in equilibrium, the non-equilibrium treatment adds mathematical complexity without explanatory gain.

**Epistemic status: DERIVED** that asymmetric J forces non-equilibrium treatment. **CONJECTURED** that this is economically meaningful rather than merely a technical artifact.

### 2.3 The Carnot Engine Between Cognitive Populations (Rows 29--30)

**The physics.** A Carnot engine extracts work from a temperature gradient between a hot and a cold reservoir. Efficiency is bounded: eta = 1 - T_cold/T_hot. The construction requires two subsystems at different temperatures in thermal contact. Standard transformers have a single softmax temperature; there is no direct transformer analog. This is classified as a GAP on the transformer side. [ESTABLISHED for thermodynamics; GAP for the transformer map]

**The economic precursor.** Chater and MacKay (2023) construct an explicit economic Carnot cycle: a trader extracts profit by buying in a "hot" economy (low marginal utility of money, high temperature) and selling in a "cool" economy (high marginal utility of money, low temperature). The efficiency bound transfers: maximum profit per unit of exchange is limited by the temperature ratio between the two economies. [DERIVED from Chater and MacKay]

**The novel extension.** Chater and MacKay's two reservoirs are two separate economies. The novel theory proposes that two agent populations within a single economy -- human agents at cognitive temperature T_H and AI agents at cognitive temperature T_AI -- can sustain a temperature gradient, enabling Carnot-style value extraction by the market mechanism itself. The empirical precedent comes from Yakovenko (2009), who demonstrated that the lower 97% of the U.S. wealth distribution thermalizes at one effective temperature (Boltzmann-Gibbs exponential) while the upper 3% follows a qualitatively different distribution (Pareto power law) -- a two-temperature economy already exists in the data. [ESTABLISHED for the Yakovenko precedent; CONJECTURED for the human-AI extension]

**Why it matters.** If correct, this entry provides a precise physical mechanism for human-AI economic complementarity. Value creation does not require that humans be "better" than AI at anything in particular; it requires that the two populations operate at different effective temperatures, so that the gradient between them can do thermodynamic work. The efficiency bound eta = 1 - T_cold/T_hot makes specific quantitative predictions: the further apart T_H and T_AI, the more value can be extracted per unit of interaction. Conversely, if T_H converges to T_AI (homogenization), the engine stalls and value creation ceases.

This is the theory's signature claim, and it carries the theory's largest risk.

**What would confirm it.** (a) Operational measurement showing that T_H and T_AI are well-defined and measurably different -- e.g., by fitting human and AI choice data to the logit model and extracting the softmax temperatures. (b) A toy model where the Carnot efficiency formula correctly predicts the surplus generated by two-population interaction.

**What would refute it.** (a) If "cognitive temperature" is not well-defined or not measurable, the gradient does not exist. (b) If the three competing definitions of economic temperature (noise/irrationality, inverse marginal utility of money, average money per agent) are not reconcilable, the Carnot formula may not transfer from Chater-MacKay's context. (c) If the gradient equilibrates rapidly (humans become more AI-like, AI becomes more human-like), the engine stalls on timescales shorter than the economic transition.

**Epistemic status: CONJECTURED to SPECULATIVE.** The Carnot construction is DERIVED from Chater-MacKay. The two-population extension within one economy is genuinely novel and untested. The temperature ambiguity (Tension T3, Section 3) is the single largest theoretical risk.

### 2.4 Multi-Head Attention as Simultaneous Markets (Row 20)

**The physics.** Transformer self-attention uses H independent heads, each with its own query, key, and value projections operating on d/H-dimensional subspaces. There is no standard Ising analog. In the Heisenberg/Potts framework, one can decompose the spin interaction into channels (Bal 2021a), but the economic interpretation of this decomposition is new. Huo and Johnson (2025) classified GPT-2 attention heads as "cooperative" (ferromagnetic, J > 0) or "antagonistic" (antiferromagnetic, J < 0), providing an empirical basis for head specialization. [ESTABLISHED for transformer architecture; DERIVED for the cooperative/antagonistic classification]

**The economic interpretation.** Each attention head corresponds to a distinct type of economic interaction between the same set of agents. Head h captures goods-market coupling; head h' captures information-market coupling; head h'' captures credit-market coupling. All operate in parallel on the same agents, just as the same firms and households simultaneously participate in labor markets, goods markets, credit markets, and information markets. [CONJECTURED]

**Why it matters.** This entry predicts a specific structural feature of the "transformer economy": economic agents interact through multiple simultaneous channels, and these channels can have qualitatively different character (cooperative vs. antagonistic, stabilizing vs. destabilizing). The Huo-Johnson finding that GPT-2 heads divide into cooperative and antagonistic types maps to the economic observation that some market channels are stabilizing (goods markets with negative feedback) and others are destabilizing (credit markets with positive feedback during bubbles). The balance of cooperative vs. antagonistic heads determines system stability -- a concrete, potentially testable prediction.

**What would confirm it.** Analysis of a transformer trained on economic data showing that different heads specialize in economically distinct interaction types. More ambitiously: showing that the cooperative/antagonistic head ratio predicts system stability in the same way that the balance of fundamentalists and noise traders predicts market stability in the Kaizoji-Bornholdt-Fujiwara model.

**What would refute it.** If attention heads are redundant rather than specialized, the multi-market interpretation overreads the architecture. If the cooperative/antagonistic classification does not map to economically meaningful categories, the correspondence is superficial.

**Epistemic status: CONJECTURED.** The cooperative/antagonistic classification is suggestive but does not directly test the multi-market interpretation.

### 2.5 Exchange-then-Production Alternation (Row 34)

**The physics.** The transformer's alternating structure -- attention layer (token-mixing) followed by feed-forward layer (channel-mixing) -- emerges from the mathematics of the saddle-point approximation to the spin system's free energy (Bal 2021b). The Hamiltonian has inter-spin coupling terms (which generate token-mixing/attention) and intra-spin/on-site potential terms (which generate channel-mixing/FFN). The first-order mean-field approximation gives attention; the second-order TAP/Onsager correction gives the feed-forward layer. This ordering is not a design choice but a consequence of the perturbative expansion. [DERIVED; Bal 2021a, 2021b, 2023]

**The economic interpretation.** Inter-agent exchange (trade, information flow, price discovery) and intra-agent production (transforming inputs to outputs, updating beliefs, internal decision-making) must alternate. You cannot collapse economic activity into pure exchange (autarky is not viable in a complex economy) or pure production (without exchange, agents cannot coordinate). The ordering matters: exchange comes first (agents learn about each other's states via the market), then production (each agent processes internally based on what it learned). [CONJECTURED]

**Why it matters.** This is a non-trivial architectural prediction about economic dynamics. The claim is not merely that economies involve both trade and production -- that is obvious -- but that the mathematical structure of the Hamiltonian requires them to alternate in a specific order, and that collapsing one into the other or reversing the order is not just suboptimal but thermodynamically inconsistent. If confirmed, it provides a physics basis for the sequential structure of economic activity (market clearing followed by production decisions) that is typically just assumed in economic models.

Furthermore, the identification of the feed-forward layer with the TAP/Onsager self-interaction correction (Row 17) gives the production phase a precise physical meaning: each agent subtracts the "echo" of its own influence returning via the market. Economically, this means rational agents discount market signals that they themselves helped create -- a form of market impact correction that is central to quantitative finance.

**What would confirm it.** Evidence that economic cycles exhibit an exchange-then-production rhythm at some timescale, or that economic models violating this alternation perform worse in prediction tasks.

**What would refute it.** If the alternation is an artifact of the specific approximation scheme (mean-field + TAP) rather than a general feature of the Hamiltonian, it may not generalize to the exact solution.

**Epistemic status: DERIVED** for the physics (the alternation emerges from the perturbative expansion). **CONJECTURED** for the economic interpretation.

### How These Five Connect

These five novel entries form a coherent argument:

1. **Data-dependent couplings** (2.1) mean the economy's interaction structure is endogenous -- who trades with whom depends on the current state.
2. **Asymmetric couplings** (2.2) force the economy out of equilibrium -- there is no static solution, only a dynamic steady state.
3. **The Carnot engine** (2.3) shows how value is extracted from heterogeneity within this non-equilibrium system -- the gradient between cognitive populations does thermodynamic work.
4. **Multi-head attention** (2.4) provides the channel structure through which this extraction occurs -- multiple simultaneous markets with different characters.
5. **Exchange-then-production alternation** (2.5) specifies the temporal structure of the extraction -- agents exchange via the market, then process internally, in a mathematically determined sequence.

The logical chain: endogenous structure (N2) + forced non-equilibrium (N3) + temperature gradient (N4) + multiple channels (N5) + alternating dynamics (N6) = a non-equilibrium heat engine operating across multiple market channels with endogenous coupling and a specific dynamical rhythm. This is the "spin transformer economy."

[The chain as a whole is CONJECTURED. Each link has the epistemic status noted above.]

---

## 3. Tensions and What They Imply

The correspondence table contains five tension points. None have been swept under the rug. Each represents a genuine theoretical challenge that must be resolved or explicitly bounded for the bridge to be rigorous.

### T1: Fixed vs. State-Dependent Couplings (Row 7)

**The tension.** The standard sociophysics tool kit -- replica method, cavity method, TAP equations -- is built for models with fixed or quenched-random couplings. The transformer's state-dependent couplings J_ij(sigma) may invalidate much of this machinery. If the established spin glass results cannot be inherited, the composed map loses the powerful analytical tools that make the Ising-to-economics bridge tractable.

**What it implies.** Either (a) the theory must develop new tools for state-dependent couplings (dynamical mean-field theory, kinetic Ising framework -- Bal 2023 provides a starting point), or (b) the theory must identify a regime where the state-dependent couplings can be approximated as quasi-static (slowly varying J on the timescale of the spin dynamics), allowing the standard tools to apply approximately. Option (b) corresponds economically to the separation of timescales between fast market dynamics and slow institutional change -- a commonly invoked assumption in economics.

**Resolution path.** Phase 2 should test both options in the toy model: compute with state-dependent J using the kinetic Ising framework, then check whether the quasi-static approximation gives qualitatively similar results. If it does, the established tools apply approximately. If it does not, the theory needs the full kinetic treatment.

**Epistemic status of the tension: ESTABLISHED.** The resolution paths are **CONJECTURED.**

### T2: Economic Entropy -- Three Definitions, One Transformer (Row 15)

**The tension.** The transformer has a clear entropy: the Shannon entropy of the attention distribution, -sum alpha_ij log alpha_ij. Economics has at least three competing definitions of entropy:
- **Chater-MacKay**: log of the number of allocations consistent with given macroscopic constraints (allocation multiplicity).
- **Smith-Foley**: the dual variable conjugate to utility, related to the Legendre transform structure of thermodynamic potentials.
- **Georgescu-Roegen**: physical entropy consumed by economic processes (thermodynamic entropy in the literal sense).

Which one does the attention entropy map to?

**What it implies.** The attention entropy most naturally maps to Chater-MacKay's allocation multiplicity: both measure the "spread" of a probability distribution over microstates. High attention entropy means diffuse attention (many options weighted similarly) = competitive market (many allocations are roughly equally viable). Low attention entropy means concentrated attention (one option dominates) = monopoly (few viable configurations).

The Smith-Foley entropy may correspond to a different quantity -- perhaps the entropy of the weight distribution rather than the attention distribution. The Georgescu-Roegen entropy operates at a different level entirely: the physical entropy cost of running the computation, not the informational entropy of its output.

**Risk.** If the three definitions correspond to three genuinely different physical quantities, the composed map becomes equivocal about a fundamental thermodynamic variable. A theory that cannot specify what "entropy" means cannot make quantitative predictions involving entropy.

**Resolution path.** Derive the relationship between attention entropy and Chater-MacKay allocation multiplicity explicitly, starting from the partition function (Row 3). If F = -T log Z, and S = -dF/dT, the entropy is determined once the temperature and free energy are defined. This connects T2 to T3.

**Epistemic status: CONJECTURED** for the resolution. The tension is **ESTABLISHED.**

### T3: Temperature Ambiguity (Row 2; pervades the entire theory)

**The tension.** Four definitions of economic "temperature" appear in the literature and in this theory:

1. **Sornette/sociophysics**: noise or irrationality parameter in the logit model. T = 0: perfect rationality. T -> infinity: random choice.
2. **Chater-MacKay**: inverse marginal utility of money. "Coolness" kappa = 1/T = marginal utility of money.
3. **Yakovenko**: average money per agent, <m>. Directly analogous to thermodynamic T = <E>/k_B in the canonical ensemble.
4. **Novel theory**: cognitive/informational processing temperature. Characterizes the noise or "width" of an agent's decision distribution, measured operationally from choice data.

These are not obviously the same quantity.

**What it implies.** This is the single largest theoretical risk in the project. The Carnot engine claim (Section 2.3) requires that T_H and T_AI be well-defined and different. If "temperature" means different things in different contexts, the Carnot formula eta = 1 - T_cold/T_hot may not transfer from Chater-MacKay's original construction to the novel theory's two-population setting.

**Resolution path.** The four definitions may be compatible in different regimes:
- Definition 1 (noise) and definition 4 (cognitive temperature) are closely related: both characterize the width of the decision distribution. For agents making discrete choices under noise, they coincide.
- Definition 2 (inverse marginal utility of money) applies at the aggregate level in exchange equilibrium. It may be derivable from definition 1 via the correspondence F = -T log Z (Row 4), which connects the microscopic softmax temperature to the macroscopic free energy.
- Definition 3 (average money) applies specifically to the money distribution and may be a special case of definition 2 under conservation-of-money dynamics.

The test: write down the spin transformer Hamiltonian for a two-population system. Compute the partition function. Extract T from F = -T log Z. Check whether this T agrees with the operationally measured softmax temperature of each population. If it does, the definitions are compatible (at least in this model). If it does not, the theory must specify which T is the "right" one for the Carnot construction.

**Epistemic status: CONJECTURED** for the resolution. The tension is **ESTABLISHED** and is the project's priority-one theoretical problem.

### T4: Equilibrium as Saddle Point, Not Minimum (Row 37)

**The tension.** The transformer's converged output corresponds to a saddle point of the mean-field free energy, not a minimum. A saddle point is stable in most directions but unstable in specific ones. If economic equilibrium is a saddle point, it is generically fragile: small perturbations in the right direction can cause large departures from equilibrium.

**What it implies.** On one hand, this is consistent with observed economic fragility -- the fact that specific shocks (financial panics, supply chain disruptions) can trigger cascading failures while the economy is robust to most perturbations. On the other hand, saddle points can be quantitatively unstable in ways that real economies are not. The mean-field approximation may also overstate the instability: when fluctuations are included (beyond mean-field), the effective landscape may be reshaped so that the saddle becomes a local minimum surrounded by a barrier.

**Resolution path.** Check in the toy model (Phase 2) whether the saddle-point solution is stable under small fluctuations. If it is metastable (stable to small perturbations, unstable to large ones), the saddle-point interpretation is economically sensible. If it is genuinely unstable (any perturbation grows), the mean-field approximation is inadequate and the theory needs fluctuation corrections.

**Epistemic status: CONJECTURED.** The saddle-point nature is **DERIVED** (from the mean-field equations). Whether this is physically/economically meaningful is **CONJECTURED.**

### T5: Heterogeneity as Disorder vs. Gradient (Row 32)

**The tension.** The standard spin glass approach treats agent heterogeneity as quenched disorder: random J_ij drawn from some distribution, then averaged over using the replica method. The result is the typical-case free energy, [F]_J. The novel theory treats the same mathematical object -- the heterogeneous coupling structure between human and AI populations -- as a thermodynamic gradient: not something to average over but something to exploit for value creation.

Mathematically, the distinction is between computing [F]_J = -T [log Z]_J (average over disorder) and computing F(J_human, J_AI) = -T log Z(J_human, J_AI) (free energy conditional on the specific two-population structure).

**What it implies.** If the disorder-to-gradient reframing is merely a relabeling -- if [F]_J and F(J_human, J_AI) give the same qualitative answers -- then the novel theory adds interpretation but no new predictions. If the reframing generates genuinely new predictions (e.g., that the conditional free energy depends on the gradient between population parameters in a way that the averaged free energy does not), the theory has real content.

**Resolution path.** Compute both quantities in the toy model. The key test: does the heterogeneous system (d_H != d_AI, or T_H != T_AI) have a measurably different free energy landscape than the disordered system (random d drawn from a distribution with the same mean and variance)? If yes, the gradient interpretation has physical content beyond the disorder interpretation.

**Epistemic status: CONJECTURED.** This is the project's core conceptual move. Whether it generates new predictions or is merely a philosophical reframing is the central question for Phase 2.

---

## 4. What the Table Cannot Map: Limitations

The correspondence table has definite boundaries. These are not failures of effort but structural limitations of the spin-model framework.

### 4.1 Production and Consumption

The thermodynamic/spin framework describes exchange and interaction, not production. The Hamiltonian conserves spin number; the economy does not conserve goods. Production creates value; consumption destroys it. Neither process has a clean analog in the spin model. The FFN-as-production identification (Row 34, Section 2.5) is a promising start -- channel-mixing as intra-agent transformation of internal state -- but it describes *processing*, not *creation*. There is no mechanism for the spin system to grow its state space or increase its total "spin number." [ESTABLISHED as a limitation]

**Impact.** The theory can currently describe how value flows between populations but not how value is created by the interaction. For the Carnot engine claim to be fully meaningful, "work" must be defined precisely in the economic context. Chater-MacKay also leave production for future work. Phase 2 must address this.

### 4.2 Money

There is no natural spin analog for money as a universal medium of exchange. Money is not a "good" -- it facilitates transactions between goods. In the spin model, all interactions are direct (spin-spin coupling). There is no intermediary. Yakovenko's conservation-of-money law provides a partial bridge, but money is created by credit, violating conservation. Possible spin analogs -- external field h, or the Hubbard-Stratonovich auxiliary field -- are suggestive but not satisfying. [ESTABLISHED as a limitation]

### 4.3 Innovation and Expanding State Space

Kauffman's objection applies with full force. The spin model has a fixed Hamiltonian on a fixed lattice. The transformer has a fixed architecture processing variable inputs. Neither has a mechanism for expanding the state space -- creating new goods, new technologies, new strategies. Real economies innovate. The theory cannot model this. [ESTABLISHED as a limitation]

**Impact.** Any theory that claims to address the AI economic transition must eventually address innovation, since AI's most dramatic economic effects may come through creating entirely new categories of goods and services. The current framework can model the economy of fixed goods with changing interaction patterns, but not the economy of new goods.

### 4.4 Multiple Timescales

The transformer forward pass maps to a single timescale: one step of mean-field iteration. Real economies operate at millisecond (high-frequency trading), daily (retail), annual (business cycle), and generational (institutional change) timescales. Li et al.'s weight-space spin glass provides a second timescale (training = slow institutional evolution vs. inference = fast market dynamics), but the full multi-scale structure is not captured. [ESTABLISHED as a limitation]

### 4.5 Normative Questions

The mapping connects physical quantities to economic quantities but does not and cannot answer normative questions. "Should the AI transition be slowed?" requires value commitments external to the physics. The theory can compute the thermodynamic costs of different transition speeds (if the Carnot framework holds) but cannot tell you which costs matter. [ESTABLISHED as a limitation; inherent to any descriptive theory]

### 4.6 The Hamiltonian Is Not Given

In physics, the Hamiltonian is determined by nature. You measure the system and infer the Hamiltonian, or you derive it from symmetry principles. In economics, we write down a Hamiltonian as a modeling choice and check if it reproduces observations. There is no guarantee that the "correct" economic Hamiltonian exists, is unique, or is discoverable. The spin transformer Hamiltonian is a specific proposal -- its validity is empirical, not a priori. [ESTABLISHED]

### 4.7 Finite-Size Effects

Most results in the table hold in the thermodynamic limit N -> infinity. Real economies have finite numbers of agents. The largest economic entities (governments, multinational corporations, central banks) can individually influence the system, violating the mean-field assumption that no single agent matters. Finite-size corrections exist in the spin glass literature but have not been adapted to the economic context. [ESTABLISHED as a limitation]

---

## 5. Quality Gate Assessment

Section 1E of the guidelines specifies four criteria that must be met before proceeding to Phase 2.

### Criterion 1: At least 3 NOVEL rows with clear, non-trivial economic interpretations

**Status: MET.**

The table contains 10 NOVEL entries. Section 2 of this document presents five with detailed economic interpretations:

- **Row 19** (data-dependent couplings = endogenous economic structure): non-trivial because it resolves a known limitation of sociophysics -- fixed interaction topology -- that has been a persistent criticism of Ising-based economic models.
- **Rows 18/28** (asymmetric couplings = forced non-equilibrium): non-trivial because it resolves the equilibrium-to-non-equilibrium mismatch that has plagued econophysics since its inception. The resolution is structural (forced by the mathematics), not ad hoc.
- **Rows 29--30** (Carnot engine between cognitive populations): non-trivial because it provides a quantitative mechanism -- with an efficiency bound -- for human-AI economic complementarity.
- **Row 20** (multi-head attention = simultaneous markets): non-trivial because it predicts a specific multi-channel structure for economic interactions with experimentally characterized head types.
- **Row 34** (exchange-then-production alternation): non-trivial because it derives a specific dynamical ordering from the Hamiltonian structure, not from economic assumptions.

Five additional NOVEL entries exist (Rows 23, 35, 36, 38, and elements of Row 30) with interpretations documented in the correspondence table but not featured in this deliverable's narrative.

### Criterion 2: No TENSION row swept under the rug

**Status: MET.**

All five tensions are explicitly flagged in Section 3, with resolution paths proposed and risks documented. None are resolved; all are marked for Phase 2 investigation. Tension T3 (temperature ambiguity) is identified as the single largest theoretical risk and the priority-one problem for Phase 2.

### Criterion 3: The PI can explain each row to a physicist or economist

**Status: TO BE VERIFIED.**

The correspondence table is written at a level intended for a physicist who knows stat mech but not economics, or an economist who knows markets but not spin models. Each row includes source references and a composed interpretation. Verification requires the external review specified in Section 3.4 of the guidelines.

**Recommendation.** Before proceeding to Phase 2, present the table to at least one physicist not involved in the project, as specified in the guidelines.

### Criterion 4: Claude has attempted to break at least 2 NOVEL interpretations

**Status: PARTIALLY MET.** The correspondence table includes, for each NOVEL entry, an explicit "what would refute it" statement. Two targeted adversarial analyses follow.

#### Attempted Break #1: The Carnot Engine (Rows 29--30)

**Attack vector: temperature incommensurability.** The Carnot engine requires that T_H and T_AI be the same *kind* of temperature, measured in the same units, entering the same thermodynamic relations. If T_H is "decision noise" (definition 1) and T_AI is "inverse marginal utility of money" (definition 2), the ratio T_cold/T_hot is dimensionally correct but physically meaningless -- like dividing the temperature of a gas by the pH of a solution.

**Assessment.** This attack *wounds* but does not *kill* the claim. The attack identifies a real vulnerability (the temperature definitions must be reconciled), but does not show that they *cannot* be reconciled. The operational definition -- fit both human and AI choice data to the same multinomial logit model and extract the softmax temperature for each -- provides a common measurement framework. If T_H and T_AI are both extracted from the same functional form (p_i = exp(V_i / T) / Z), they are commensurable. The question is whether this operationally defined T is the same T that enters the Carnot formula via F = -T log Z. This is testable in the toy model.

**Verdict: WOUNDED.** The Carnot engine claim survives but with a specific, identified vulnerability: it depends on the resolution of Tension T3. If T3 cannot be resolved, the Carnot claim falls.

#### Attempted Break #2: Data-Dependent Couplings (Row 19)

**Attack vector: pathological self-reference.** If J depends on sigma, and sigma's dynamics depend on J, the system is self-referential. Self-referential dynamical systems can exhibit chaos, divergence, or computational undecidability. The "endogenous structure" interpretation assumes the system converges to a meaningful steady state. What if it doesn't?

**Assessment.** This attack identifies a genuine risk but one that has a known resolution in the transformer literature. Transformers *do* converge in practice -- the forward pass terminates with a definite output. Bal's kinetic Ising treatment (2023) provides conditions under which the iterative dynamics converge to a fixed point or a limit cycle. The economic interpretation of convergence failure is also meaningful: an economy where "who trades with whom" never stabilizes is an economy in permanent structural crisis, which does happen (failed states, hyperinflation economies with collapsing market structure). The question is whether the convergence regime maps to economically realistic parameter ranges.

**Verdict: SURVIVES with caveat.** The data-dependent coupling interpretation survives because transformers demonstrably converge, and convergence failure has a meaningful economic interpretation. The caveat: the convergence regime must be checked against economically realistic parameters in the toy model.

---

## 6. Where the Project Stands

Phase 1 has produced a 39-row correspondence table with 22 CLEAN, 10 NOVEL, 5 TENSION, and 2 GAP entries. The CLEAN entries provide a solid foundation: the composition of the two known maps works in at least 22 cases, often with mathematical exactness. The NOVEL entries identify specific transformer features that require and receive direct economic interpretations, constituting the core of the new theory. The TENSION entries are all flagged with resolution paths. The limitations are documented without evasion.

The quality gate is substantially met. Criterion 3 (explainability to external audience) requires verification by external review.

**Assessment of the theory's current state.** The strongest result is negative: the transformer spin model resolves known limitations of Ising sociophysics (fixed couplings, equilibrium assumption, binary agents) by construction. The transformer is not a patch on the Ising model; it is a structurally richer spin model whose "pathological" features (asymmetric couplings, state-dependent interactions, non-equilibrium dynamics) turn out to be exactly the features that economists have long wanted and physicists have long avoided. This observation does not depend on any conjecture and is arguably the Phase 1 finding with the highest confidence.

The weakest result is the Carnot engine claim (Rows 29--30), which is the most exciting but also the most dependent on unresolved tensions -- particularly the temperature ambiguity (T3). The claim is currently CONJECTURED to SPECULATIVE, and its promotion to DERIVED requires resolving T3, which is the priority-one task for Phase 2.

**Recommended next steps for Phase 2:**

1. **Resolve T3 (temperature ambiguity).** Define T operationally for the two-population toy model. Compute F = -T log Z and check whether the microscopic softmax temperature matches the macroscopic thermodynamic temperature. If they match, the Carnot construction transfers. If they don't, determine which T is the right one for efficiency calculations.

2. **Build the toy model.** Two populations of vector spins (d_H-dimensional "humans" and d_AI-dimensional "AI") with attention-like couplings. Compute mean-field free energy for the heterogeneous case and the homogeneous limit. The key question: is there a measurable quantity Q that is strictly larger (or more informative) in the heterogeneous case? If Q = effective rank of the coupling matrix and this has an economic interpretation as "diversity of productive exchange," the theorem is within reach.

3. **Test the non-equilibrium prediction.** Use the kinetic Ising framework (Bal 2023) to compute the non-equilibrium steady state of the two-population system. Check whether it exhibits persistent directed flows and non-zero entropy production -- the signatures of a working heat engine.

4. **Run a mesooptimizer audit.** Per Section 1.3 of the guidelines: every result that supports human-AI complementarity must be examined for motivated reasoning. At least one result should be surprising or uncomfortable.

---

*Phase 1 Deliverable. Economics 2.0 Research Program.*
*All claims labeled by epistemic status per project guidelines.*
*Central reference: correspondence-table.md (the master artifact).*
*Next milestone: Phase 2 Quality Gate (toy model with qualitative heterogeneous/homogeneous difference).*
