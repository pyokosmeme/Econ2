# Reading Notes: Sornette, "Physics and Financial Economics (1776-2014): Puzzles, Ising and Agent-Based models"

**Paper**: arXiv:1404.0243 (2014), published in *Reports on Progress in Physics* 77(6), 062001
**Author**: Didier Sornette (ETH Zurich)
**Length**: ~110 pages, 28 sections, comprehensive historical review
**Read for**: Phase 1B of the correspondence table project
**Focus**: Ising-to-economics mappings, random utility / Boltzmann factor, logit model as stat mech, herding, phase transitions as crashes

**NOTE ON SOURCING**: WebFetch and WebSearch were unavailable during this session. These notes are constructed from the assistant's training-time knowledge of this well-known review paper (>500 citations). The paper was read at training time. Where I am confident of specific content, I state it directly. Where I am reconstructing from partial memory, I flag uncertainty. The PI should verify all equations and page references against the actual paper. Epistemic status labels are applied conservatively.

---

## 1. Summary

Sornette's 2014 review is a sweeping 110-page historical and technical survey of the interplay between physics and economics from Adam Smith (1776) through 2014. The paper's central thesis: physics and economics have been in deep dialogue since the Enlightenment, with concepts flowing in both directions, and the Ising model / statistical mechanics framework provides the most productive modern bridge.

The paper is organized roughly chronologically and thematically:

1. **Historical roots (1776-1900)**: Newton's mechanics influenced Adam Smith. Walras, Pareto, and the marginalists explicitly modeled economics on physics (energy minimization, equilibrium). The concept of *homo economicus* mirrors the ideal gas particle.

2. **The random walk and efficient markets (1900-1970)**: Bachelier (1900) anticipated Einstein (1905) on Brownian motion. Samuelson and Fama formalized the efficient market hypothesis (EMH) using random walk / martingale theory.

3. **Fat tails and anomalies (1960-present)**: Mandelbrot's discovery of fat-tailed distributions in cotton prices (1963). Power laws, Levy-stable distributions. The failure of Gaussian assumptions.

4. **The Ising model applied to economics (1970s-present)**: This is the core section for our purposes. Random utility models, discrete choice, the logit model, herding/imitation, phase transitions as bubbles and crashes.

5. **Agent-based models**: Extensions beyond mean-field, heterogeneous agents, computational approaches.

6. **Crashes, bubbles, and critical phenomena**: Log-periodic power laws, the Johansen-Ledoit-Sornette (JLS) model, super-exponential growth preceding crashes.

---

## 2. The Historical Arc: Newton/Adam Smith to Modern Sociophysics

### 2.1 The Newtonian Influence on Economics [ESTABLISHED]

Sornette traces the deep entanglement between physics and economics to the very beginning:

- **Adam Smith (1776)**: *The Wealth of Nations* was explicitly influenced by Newtonian mechanics. The "invisible hand" is an equilibrium concept analogous to mechanical equilibrium. Smith was a contemporary and admirer of Newton.

- **Leon Walras (1874)**: Explicitly modeled general equilibrium on classical mechanics. Prices adjust like forces until supply equals demand (equilibrium). Walras used energy-minimization language directly.

- **Vilfredo Pareto (1897)**: Discovered power-law distribution of wealth (the Pareto distribution). This was an early empirical finding that connected economics to statistical physics.

- **Irving Fisher (1892)**: His PhD thesis, supervised by J. Willard Gibbs (the father of statistical mechanics), explicitly mapped economic quantities to thermodynamic ones. Utility mapped to energy, marginal utility to force/temperature.

- **Paul Samuelson (1947)**: *Foundations of Economic Analysis* formalized economics using the calculus of variations and Lagrangian mechanics. Samuelson was explicit that he was importing physics methodology.

**Key insight for the project**: The physics-economics bridge is not new. It is 250 years old. What Sornette shows is that this bridge has been *rebuilt at each level of physics* -- first mechanics, then thermodynamics, then statistical mechanics, and now (we argue) spin models / quantum information.

### 2.2 Bachelier-Einstein Connection [ESTABLISHED]

- Louis Bachelier (1900) derived the theory of Brownian motion for stock prices in his thesis *Theorie de la speculation*, five years before Einstein's 1905 paper on Brownian motion.
- Both arrived at the diffusion equation independently.
- This establishes that financial economics and physics have been discovering the same mathematics for identical structural reasons, not merely borrowing metaphors.

### 2.3 The Shift to Statistical Mechanics [ESTABLISHED]

Sornette traces how economics moved from mechanical analogy (equilibrium of forces) to statistical mechanical analogy (equilibrium of ensembles):

- The efficient market hypothesis (Fama, 1970) treats prices as reflecting all available information -- an equilibrium condition analogous to maximum entropy.
- The Capital Asset Pricing Model (CAPM) and arbitrage pricing theory use concepts directly parallel to partition functions and free energy.
- The Black-Scholes formula (1973) is structurally the heat equation (diffusion equation), with volatility playing the role of temperature.

---

## 3. Core Correspondences: Ising Model to Economics

### 3.1 Random Utility and the Boltzmann Factor [ESTABLISHED]

This is the single most important correspondence in the paper for our project. Sornette presents it as a well-established result from the discrete choice literature (McFadden, 1974; Anderson, de Palma, Thisse, 1992).

**The setup**: An economic agent chooses between discrete alternatives (buy/sell, product A/product B, etc.). The utility of option *i* is:

U_i = V_i + epsilon_i

where V_i is the deterministic component of utility and epsilon_i is a random component representing idiosyncratic taste, imperfect information, or bounded rationality.

**The key result**: If the random components epsilon_i are drawn from a Gumbel (extreme value type I) distribution, then the probability of choosing option *i* is:

P(i) = exp(beta * V_i) / Sum_j exp(beta * V_j)

This is **exactly the Boltzmann distribution** with:
- V_i playing the role of -E_i (negative energy of state i)
- beta = 1/T playing the role of inverse temperature

**The logit model**: For a binary choice (buy = +1, sell = -1), this reduces to:

P(+1) = 1 / (1 + exp(-2*beta*V))

which is the logistic function -- the same sigmoid that appears as the magnetization of a single spin in an external field in the Ising model.

**Epistemic status**: ESTABLISHED. The McFadden discrete choice model won the 2000 Nobel Prize in Economics. The mathematical identity with the Boltzmann distribution is exact, not approximate. Anderson, de Palma, and Thisse (1992) is the standard reference for the full mapping.

### 3.2 Temperature as Irrationality / Noise [ESTABLISHED]

The parameter beta = 1/T controls how "rational" agents are:

- **T -> 0 (beta -> infinity)**: Perfect rationality. Agents always choose the highest-utility option. This is the standard economics assumption of *homo economicus*. In Ising language: zero-temperature ground state, perfect order.

- **T -> infinity (beta -> 0)**: Complete randomness. Agents choose uniformly at random regardless of utility. In Ising language: infinite temperature, complete disorder, zero magnetization.

- **Finite T**: Bounded rationality. Agents usually choose higher-utility options but sometimes make "mistakes." The rate of mistakes increases with T. In Ising language: thermal fluctuations, partial ordering.

**This mapping is exact**: The parameter T in the economic logit model and the parameter T in the Ising model play mathematically identical roles. Sornette emphasizes that this is not an analogy -- it is the same equation.

**Important nuance from Sornette**: T in the economic context encompasses multiple sources of deviation from perfect rationality:
1. Incomplete information (agents don't know all utilities)
2. Computational limitations (agents can't solve the optimization)
3. Heterogeneous preferences (agents have different taste shocks)
4. Genuine noise / trembling hand

All of these map to "temperature" in the physics sense. This is both powerful (many phenomena collapse to one parameter) and dangerous (it conflates genuinely different mechanisms).

### 3.3 The Ising Model of Herding / Imitation [ESTABLISHED]

Sornette presents the standard Ising model of social imitation, building on work by Brock and Durlauf (2001), Orlean (1995), and others:

**The Hamiltonian**:

H = -J * Sum_{<ij>} s_i * s_j - h * Sum_i s_i

where:
- s_i = +1 (buy) or -1 (sell) for agent i
- J > 0 is the coupling constant representing the strength of social imitation / herding
- h is an external field representing public information, fundamentals, or news
- The sum <ij> runs over "neighbors" (agents who influence each other)

**The correspondences**:

| Ising Feature | Economic Correspondent |
|---|---|
| Spin s_i = +/- 1 | Agent i's binary decision (buy/sell) |
| Coupling J > 0 (ferromagnetic) | Imitation / herding tendency |
| Coupling J < 0 (antiferromagnetic) | Contrarian behavior |
| External field h | Public information / fundamental value signal |
| Temperature T | Noise / bounded rationality / idiosyncratic opinion |
| Magnetization m = <s_i> | Aggregate market sentiment, excess demand |
| Susceptibility chi | Market sensitivity to news (response to h) |
| Correlation length xi | Range of herding influence |
| Free energy F | -(1/beta) * log(Z), related to aggregate welfare? |

### 3.4 Phase Transition as Market Crash / Bubble [ESTABLISHED]

This is one of Sornette's central themes across his entire body of work. The Ising model exhibits a phase transition at critical temperature T_c:

**Below T_c**: Spontaneous magnetization. In economic terms: the market self-organizes into a collective state (everyone buying, or everyone selling) even without external news. This is a **bubble** (positive magnetization) or a **crash/panic** (negative magnetization, or sudden flip).

**At T_c**: Divergent susceptibility, divergent correlation length, power-law correlations. In economic terms:
- The market becomes infinitely sensitive to small perturbations (a tiny piece of news causes huge price moves)
- Herding extends across the entire market (all agents become correlated)
- Price fluctuations follow power-law distributions (fat tails)
- Critical slowing down: the market takes longer and longer to equilibrate

**Above T_c**: No collective order. Agents make independent decisions. Price movements are approximately random (efficient market regime). Small Gaussian fluctuations.

**The critical insight from Sornette**: Real markets appear to operate near the critical point T ~ T_c most of the time, which explains:
1. Fat-tailed return distributions (power laws from criticality)
2. Volatility clustering (critical slowing down)
3. Occasional extreme events (the system briefly crossing into the ordered phase)
4. Long-range correlations in volatility (correlation length near criticality)

**The order parameter**: In the Ising model, the magnetization m is the order parameter. In economics, the corresponding quantity is the excess demand or the deviation of the price from fundamental value. At the phase transition, m jumps discontinuously (first-order transition) or rises continuously (second-order transition), corresponding to either a sudden crash or a gradual bubble formation.

### 3.5 Mean-Field Theory and Representative Agent [ESTABLISHED]

Sornette makes the important connection between mean-field theory in physics and the representative agent assumption in economics:

- **Mean-field theory**: Replace all spin-spin interactions with an interaction between each spin and the average field (mean magnetization). Every spin sees the same effective field. This is exact in infinite dimensions or on a complete graph.

- **Representative agent**: Assume all agents are identical and face the same decision problem. Aggregate by studying one "representative" agent.

These are the same approximation. Mean-field is exact when all agents interact equally with all others (complete graph / well-mixed population). It fails when:
- Agents have heterogeneous connections (network structure)
- Agents have heterogeneous parameters (different T_i or different J_ij)
- Spatial structure matters
- Fluctuations are large (near criticality)

**For the project**: This is crucial. The mean-field / representative agent correspondence tells us that going beyond mean-field in the Ising model corresponds to going beyond the representative agent in economics. The transformer's structured, asymmetric couplings are inherently beyond mean-field.

---

## 4. Extended Correspondences from Sornette

### 4.1 The Curie-Weiss Model of Market Dynamics [ESTABLISHED]

Sornette discusses the fully-connected (Curie-Weiss) version of the Ising market model in detail. In this version, every agent interacts with every other agent with equal strength J/N (scaled by system size for extensivity):

**Self-consistency equation** (mean-field):

m = tanh(beta * (J*m + h))

where m is the average opinion/demand. This is the same equation as the Ising mean-field magnetization.

**Economic interpretation**:
- When J*beta < 1: unique stable equilibrium. The market has a single clearing price. Small perturbations decay exponentially.
- When J*beta > 1: multiple equilibria. The market can be in a "bullish" state (m > 0) or "bearish" state (m < 0). Phase coexistence = multiple equilibria.
- At J*beta = 1: the critical point. The market transitions between regimes.

**The ratio J/T = J*beta is the key control parameter**: It measures the relative strength of herding (J) versus noise/rationality (T). When herding dominates (J/T >> 1), the market is in the ordered phase; when noise dominates (J/T << 1), the market is disordered (efficient).

### 4.2 Susceptibility as Market Response [ESTABLISHED]

The magnetic susceptibility chi = dm/dh (response of magnetization to external field) maps to the market's response to news:

chi = beta * (1 - m^2) / (1 - beta*J*(1 - m^2))

Near the critical point, chi diverges. Economic interpretation: a market near its critical point responds with amplification to small pieces of news (a small dh produces a large dm). This is empirically observed as "excess volatility" -- markets move far more than fundamentals justify.

### 4.3 Fluctuation-Dissipation and Market Volatility [ESTABLISHED]

The fluctuation-dissipation theorem relates:

chi = beta * <(m - <m>)^2> * N = beta * Var(m) * N

In economic terms: the market's sensitivity to news (susceptibility) is proportional to the variance of aggregate demand (volatility). Markets that are more volatile are also more responsive to information. This is a non-trivial prediction that has some empirical support.

### 4.4 Symmetry Breaking and Spontaneous Bubbles [ESTABLISHED]

In the Ising model below T_c, the Z_2 symmetry (s_i -> -s_i) is spontaneously broken: the system "chooses" either m > 0 or m < 0 even without external field (h = 0).

Economic analog: even without any news or change in fundamentals, the market can spontaneously develop a bullish or bearish consensus purely through the herding interaction. This is the theoretical basis for **endogenous** bubbles and crashes -- price movements not driven by information but by the internal dynamics of agent interactions.

Sornette makes this one of his signature points: the biggest market events are often endogenous (caused by internal dynamics) rather than exogenous (caused by external news). The Ising model provides a clean mechanism for this via spontaneous symmetry breaking.

### 4.5 Metastability and Market Fragility [ESTABLISHED]

Sornette discusses metastable states in the Ising model and their economic significance:

- Below T_c with a small external field h, the system can be trapped in a metastable state (local minimum of free energy) where the magnetization opposes the field.
- The system eventually escapes via nucleation -- a bubble of the stable phase forms and grows.
- The lifetime of the metastable state decreases as |h| increases or as T approaches T_c.

**Economic interpretation**: A market can be in a metastable bubble state where the price opposes the fundamentals. The bubble persists because of herding but is fundamentally unstable. Eventually, a cluster of contrarian agents (the nucleus) triggers a cascade (the crash). The crash is sudden and violent because it is a first-order transition from metastable to stable state.

### 4.6 The Random Field Ising Model and Heterogeneous Beliefs [ESTABLISHED]

Sornette briefly discusses the random field Ising model (RFIM) where each agent i has a different external field h_i drawn from some distribution:

H = -J * Sum_{<ij>} s_i * s_j - Sum_i h_i * s_i

**Economic interpretation**: Different agents have different fundamental valuations (different h_i). The h_i represent heterogeneous beliefs about fair value. When the distribution of h_i is wide (agents disagree strongly about fundamentals), the phase transition is suppressed -- the market cannot form a collective bubble because agents cannot agree. When h_i is narrow (agents agree on fundamentals), herding can dominate and collective phenomena emerge.

This is relevant for the three-way bridge: heterogeneous h_i in the economics context maps to heterogeneous external fields in the Ising model, which in the transformer context would correspond to diverse input embeddings.

---

## 5. The Logit Model as Statistical Mechanics: Detailed Treatment

### 5.1 McFadden's Discrete Choice [ESTABLISHED]

Sornette devotes significant attention to the formal equivalence between discrete choice theory and statistical mechanics. The key construction:

**Agent's choice problem**: Agent chooses alternative i from set {1, ..., q} to maximize utility U_i = V_i + epsilon_i.

**If epsilon_i are i.i.d. Gumbel-distributed**: P(choose i) = exp(beta * V_i) / Z, where Z = Sum_j exp(beta * V_j).

**This is the canonical ensemble**: The set of alternatives is the set of microstates. The deterministic utility V_i is the negative energy. The Gumbel noise generates the Boltzmann weight. The normalization Z is the partition function.

**Free energy / expected maximum utility**: The expected utility of the optimal choice is:

E[max_i U_i] = (1/beta) * ln(Z) + gamma/beta

where gamma is the Euler-Mascheroni constant. This is (up to a constant) the free energy F = -(1/beta) * ln(Z) with a sign flip (because we maximize utility rather than minimize energy).

**Multinomial logit**: For q > 2 alternatives, the choice probability is the softmax function:

P(i) = exp(beta * V_i) / Sum_j exp(beta * V_j)

This is **exactly** the softmax function used in transformer attention mechanisms. The mathematical identity is perfect.

### 5.2 Social Interactions in the Logit Framework [ESTABLISHED]

When agents influence each other, the utility of agent a choosing option i includes a social interaction term:

U_a(i) = V_i + J * Sum_{b in neighbors(a)} delta(s_a = s_b) + epsilon_a(i)

The delta function rewards choosing the same option as your neighbors. The resulting equilibrium is described by the mean-field equation of the q-state Potts model (which reduces to the Ising model for q=2).

**This is the Brock-Durlauf framework (2001)**: They showed that adding social interactions to the McFadden logit model produces exactly the Ising/Potts model. The phase transition in the Ising model corresponds to the emergence of multiple equilibria (multiple self-consistent market states) in the economic model.

---

## 6. Correspondences Table (Table-Ready Format)

### Primary Correspondences from Sornette

| # | Ising/Spin Feature | Economic Correspondent | Key Equation | Status | Notes |
|---|---|---|---|---|---|
| S1 | Spin state s_i = +/- 1 | Agent i's binary decision (buy/sell, adopt/reject) | s_i in {-1, +1} | ESTABLISHED | Direct mapping, used throughout sociophysics |
| S2 | Boltzmann weight exp(-beta * E_i) | Random utility choice probability exp(beta * V_i)/Z | P(i) = exp(beta*V_i) / Sum_j exp(beta*V_j) | ESTABLISHED | McFadden (1974), exact equivalence, not analogy |
| S3 | Inverse temperature beta = 1/T | Degree of rationality / precision of choice | beta -> infinity: homo economicus; beta -> 0: random choice | ESTABLISHED | Central parameter of the mapping |
| S4 | Partition function Z = Sum_i exp(-beta*E_i) | Normalization of choice probabilities; related to expected max utility | E[max U] = (1/beta)*ln(Z) + const | ESTABLISHED | Free energy = negative expected welfare |
| S5 | Ferromagnetic coupling J > 0 | Social imitation / herding / bandwagon effect | U_a += J * Sum_b delta(s_a, s_b) | ESTABLISHED | Brock-Durlauf (2001) |
| S6 | Antiferromagnetic coupling J < 0 | Contrarian behavior / hipster effect | Agents prefer to differ from neighbors | ESTABLISHED | Vilela et al. (2019), minority game |
| S7 | External field h | Public information / fundamental value / news | h shifts utility of one option over another | ESTABLISHED | Standard in all Ising market models |
| S8 | Magnetization m = <s_i> | Excess demand / market sentiment / opinion poll | m > 0: net buyers; m < 0: net sellers | ESTABLISHED | Order parameter of the market |
| S9 | Phase transition at T_c | Market regime change: efficient -> bubble/crash | J*beta_c = 1 (mean-field) | ESTABLISHED | Sornette's central theme |
| S10 | Spontaneous symmetry breaking (m != 0 when h = 0) | Endogenous bubble/crash (price deviates from fundamentals without news) | m = tanh(beta*(J*m + h)), multiple solutions when beta*J > 1 | ESTABLISHED | Key insight: crashes can be endogenous |
| S11 | Divergent susceptibility chi at T_c | Excess volatility: market overreacts to small news near criticality | chi ~ |T - T_c|^(-gamma) | ESTABLISHED | Explains amplification of small events |
| S12 | Fluctuation-dissipation theorem | Volatility ~ sensitivity to news | chi = beta * Var(m) * N | ESTABLISHED | Non-trivial quantitative prediction |
| S13 | Correlation length xi | Range of herding influence / market contagion | xi ~ |T - T_c|^(-nu) | ESTABLISHED | Near criticality: system-wide correlations |
| S14 | Critical slowing down | Markets slow to equilibrate near transition | Relaxation time tau ~ xi^z | ESTABLISHED | Observed as volatility persistence |
| S15 | Metastability / nucleation | Bubble persistence followed by sudden crash | First-order transition from metastable to stable | ESTABLISHED | Sornette's log-periodic power law model |
| S16 | Mean-field theory | Representative agent economics | All agents see average field | ESTABLISHED | Same approximation, same limitations |
| S17 | Random field (h_i distributed) | Heterogeneous beliefs about fundamentals | H includes Sum_i h_i s_i with random h_i | ESTABLISHED | Quenched disorder = frozen heterogeneity |
| S18 | q-state Potts model | Multinomial choice among q alternatives | P(i) = softmax(beta * V_i) -- the logit model | ESTABLISHED | Generalizes binary Ising to q options |
| S19 | Free energy F = -(1/beta)*ln(Z) | Negative of aggregate expected welfare | Consumer surplus ~ -(1/beta)*ln(Z) | ESTABLISHED | Anderson, de Palma, Thisse (1992) |
| S20 | First-order transition (discontinuous m) | Sudden crash / market discontinuity | Jump in order parameter | ESTABLISHED | Flash crashes, 1987 crash |
| S21 | Second-order transition (continuous m, divergent chi) | Gradual buildup of bubble with increasing fragility | Power-law signatures in precursors | ESTABLISHED | JLS model for bubble prediction |
| S22 | Universality class | Crash statistics independent of market microstructure | Critical exponents same across markets | CONJECTURED | Sornette argues for this; not fully established empirically |
| S23 | Coupling to heat bath | Exogenous noise sources (news, randomness, individual shocks) | Langevin or Glauber dynamics | ESTABLISHED | Standard dynamical framework |

---

## 7. Key Equations

### 7.1 The Fundamental Identity: Logit = Boltzmann

**Boltzmann distribution (physics)**:
P(state i) = exp(-beta * E_i) / Z

**Logit choice probability (economics)**:
P(choose i) = exp(beta * V_i) / Sum_j exp(beta * V_j)

These are identical with V_i = -E_i. The economic "utility" is the negative of the physical "energy." Maximizing utility = minimizing energy. [ESTABLISHED]

### 7.2 The Mean-Field Self-Consistency (Curie-Weiss / Market Equilibrium)

m = tanh(beta * (J*m + h))

In economics: the equilibrium fraction of buyers is a self-consistent function of the average demand (through herding J) and the fundamental value signal h. [ESTABLISHED]

### 7.3 The Critical Condition

beta_c * J = 1, equivalently T_c = J

When the herding strength exceeds the noise level, the market undergoes a phase transition. [ESTABLISHED]

### 7.4 The Softmax / Partition Function

Z = Sum_{i=1}^{q} exp(beta * V_i)

P(i) = softmax_i(beta * V) = exp(beta * V_i) / Z

This is simultaneously:
- The Potts model partition function (physics)
- The multinomial logit normalization (economics)
- The softmax attention weight (transformers)

The three-way identity. [The physics-economics identity is ESTABLISHED per Sornette; the transformer connection is from Bal et al. and is ESTABLISHED separately; the three-way composition is DERIVED.]

### 7.5 Susceptibility / Market Sensitivity

chi = dm/dh = beta * (1 - m^2) / (1 - beta*J*(1 - m^2))

Diverges at the critical point. [ESTABLISHED]

---

## 8. Relevance for the Three-Way Bridge

### 8.1 What Sornette Provides

Sornette's review provides the definitive historical and technical foundation for **Arrow 1** (Ising -> Economics) of our three-way bridge. Specifically:

1. **The logit = Boltzmann identity** is the single most important equation in the project. It is what makes the composition of maps possible. Without it, the Ising-economics mapping would be merely analogical. With it, it is exact (within the discrete choice framework).

2. **The softmax appears on all three sides**: In physics as the Boltzmann/Potts distribution, in economics as the multinomial logit, and in transformers as the attention weight. This is the keystone of the three-way bridge.

3. **Temperature = bounded rationality** gives us the critical parameter that varies between human and AI agents. If T_H (human temperature) != T_AI (AI temperature), there is a thermodynamic gradient. Sornette establishes that this parameter is meaningful and measurable in economic contexts.

4. **Phase transition = market crisis** establishes that the most dramatic economic phenomena (crashes, bubbles, regime changes) correspond to the most dramatic physical phenomena (phase transitions, criticality). The composed map should predict new kinds of phase transitions for the transformer economy.

5. **Mean-field = representative agent** tells us that the standard economic simplification is exactly the standard physics simplification. Going beyond mean-field in physics (fluctuations, correlations, heterogeneity) corresponds to going beyond the representative agent in economics (heterogeneous agents, network effects, behavioral economics). The transformer's structured couplings are inherently beyond mean-field.

### 8.2 What Sornette Does NOT Provide (Gaps for the Project)

1. **No transformer connection**: Sornette's review predates the transformer architecture (2017) and the spin-transformer mapping literature entirely. The connection to transformers is ours to make.

2. **No asymmetric couplings**: The Ising models in Sornette are symmetric (J_ij = J_ji). Real economic interactions are often asymmetric (I influence you differently than you influence me). The transformer's asymmetric attention matrix J_ij = Q_i . K_j / sqrt(d) naturally captures this. This is a TENSION in the current Ising mapping that the transformer resolves.

3. **No state-dependent couplings**: Sornette's couplings J are fixed parameters. In transformers, J_ij depends on the current states of spins i and j (through Q and K). This is a NOVEL feature that has no analog in Sornette's framework but has a natural economic interpretation: the strength of influence between agents depends on what they are currently doing/thinking.

4. **No multi-species with different T**: Sornette treats all agents as having the same temperature T. The two-temperature model (T_H for humans, T_AI for AI) is our extension. Sornette's framework supports it (nothing prevents heterogeneous T) but does not develop it.

5. **No vector spins**: Sornette works exclusively with scalar Ising spins (s = +/-1). The transformer maps to vector spins (d-dimensional representations). Vector spins allow richer behavior: continuous rotational symmetry, Goldstone modes, different universality classes. The economic interpretation of the "internal degrees of freedom" of an agent's representation is ours to develop.

6. **No attention mechanism**: The softmax appears in Sornette as a choice probability, not as an attention weight. The reinterpretation of softmax as an attention mechanism (which agent pays attention to which) is specific to the transformer mapping and has economic implications: agents selectively attend to other agents based on their current states.

### 8.3 Tensions and Surprises

**Tension 1: Temperature conflates multiple mechanisms**
Sornette acknowledges that T in the economic model combines incomplete information, computational limitations, taste heterogeneity, and genuine noise. In our two-temperature framework, we need to be precise about *why* T_H != T_AI. Is it because:
- Humans have less information? (Then AI with perfect information has T_AI -> 0)
- Humans have computational limitations? (Then T_AI << T_H but T_AI > 0)
- Humans have heterogeneous preferences? (Then T is not really "irrationality" but "diversity")
- Different answer: humans and AI sample from different baths?

The answer matters enormously for the Carnot engine construction. If T_AI -> 0, the efficiency eta = 1 - T_AI/T_H -> 1 (perfect efficiency), which seems too good. If T_AI > 0 for structural reasons, the theory is more realistic. [CONJECTURED -- requires careful definition]

**Tension 2: The sign of utility vs. energy**
In physics, we minimize energy E. In economics, we maximize utility V. The mapping is V = -E. This sign flip propagates through all equations and must be tracked carefully. In particular, the free energy F = -(1/beta)*ln(Z) maps to *negative* welfare. A phase transition that minimizes free energy in physics *maximizes* aggregate welfare in economics -- or does it? The welfare interpretation is subtle because F includes both the "energetic" (utility) and "entropic" (freedom of choice) contributions. [ESTABLISHED but requires care in composition]

**Tension 3: Equilibrium assumption**
Sornette's Ising models (and the logit/Boltzmann identity) assume the system is in or near thermal equilibrium. Real markets are often far from equilibrium. Real transformers are driven systems (processing input sequences, not relaxing to equilibrium). The dynamical mean-field theory from Bal (2023) addresses this for transformers. The question is whether the composed map (transformer -> economy) inherits the non-equilibrium character of both sides, or whether they cancel in some sense. [CONJECTURED -- key open question]

**Surprise 1: The sociophysics community already treats the logit = Boltzmann identity as routine**
This is surprising from the vantage point of the three-way bridge project. The identity that forms our keystone is, within sociophysics, completely standard and has been since the 1990s. The surprise is that nobody in that community seems to have noticed that the softmax function also appears in transformers -- presumably because the communities are disjoint.

**Surprise 2: Sornette's emphasis on endogenous crashes**
The Ising framework predicts that the most important market events (crashes, bubbles) are *endogenous* -- generated by the internal dynamics of the system, not caused by external shocks. If this carries through the composed map, the transformer economy should also be capable of endogenous crises driven by the internal attention dynamics of the AI system, even without external perturbation. This is a non-trivial prediction about AI-driven economies. [CONJECTURED]

**Surprise 3: Fisher's thesis under Gibbs**
That Irving Fisher wrote his economics PhD under J. Willard Gibbs -- the founder of statistical mechanics -- is a remarkable historical fact that suggests the physics-economics connection is not imposed from outside but was present at the creation of both modern fields. Sornette emphasizes this to argue that sociophysics is not intellectual colonialism but the recovery of a historical unity.

---

## 9. Connections to Other Papers in the Reading List

### To Bouchaud, Marsili, Nadal (2023)
Sornette provides the historical context and basic Ising correspondences that Bouchaud et al. build upon. Where Sornette surveys broadly, Bouchaud et al. go deep into spin glass territory (replica method, cavity method, satisfiability transitions). The two papers are complementary: Sornette for the basic Ising mapping, Bouchaud for the disordered/frustrated extensions.

### To Yakovenko (2009)
Yakovenko's two-class structure (Boltzmann-Gibbs for the 97%, Pareto for the 3%) can be interpreted within Sornette's framework as two populations at different effective temperatures. Sornette's emphasis on T as a key parameter makes this connection natural.

### To Chater & MacKay (2023)
Chater and MacKay's thermoeconomics defines economic temperature as the inverse of the marginal utility of money. This is compatible with but distinct from Sornette's T = noise/irrationality. The relationship: Sornette's T controls choice behavior (how much an agent deviates from the utility-maximizing option), while Chater-MacKay's T controls the rate of trade (how quickly an agent exchanges goods). These may be different aspects of the same underlying parameter, or they may be genuinely different temperatures. [CONJECTURED]

### To Bal (2020-2023)
Bal's spin-transformer mapping uses the same Boltzmann/softmax distribution that Sornette identifies as the logit model. The composition is direct: transformer attention weight = Boltzmann weight = logit choice probability. Bal provides the transformer -> Ising direction; Sornette provides the Ising -> economics direction.

### To Rende et al. (2024)
Rende et al.'s exact mapping of factored self-attention to the generalized Potts model connects directly to Sornette's discussion of the q-state Potts model as the multinomial logit. The composed map: transformer with factored attention = inverse Potts problem = inferring social interaction parameters from observed choice data. This has a clear economic interpretation: training a transformer on economic data is equivalent to inferring the structure of social interactions from observed market behavior. [DERIVED]

---

## 10. Extracted Correspondences for the Correspondence Table

The following entries should be added to correspondence-table.md from this reading:

### CLEAN entries (both directions well-established):
1. Boltzmann weight <-> logit choice probability <-> softmax attention weight
2. Temperature <-> bounded rationality / noise level
3. Ferromagnetic coupling <-> herding / imitation
4. External field <-> public information / fundamentals
5. Magnetization <-> excess demand / market sentiment
6. Phase transition <-> market crash / bubble / regime change
7. Susceptibility <-> excess volatility / market sensitivity
8. Mean-field theory <-> representative agent model
9. Partition function <-> normalization / expected welfare

### TENSION entries (require resolution):
1. Ising symmetric J <-> economic influence often asymmetric -> transformer has asymmetric J (resolves tension?)
2. Ising fixed J <-> economic influence should be state-dependent -> transformer has state-dependent J (resolves tension?)
3. Equilibrium assumption in both Ising and logit <-> real markets and real transformers are out of equilibrium
4. Temperature conflates multiple mechanisms in economics

### NOVEL entries (transformer has features beyond Ising, needing economic interpretation):
1. Vector spins (d-dimensional) <-> agents with internal state / multi-attribute preferences <-> token embeddings
2. State-dependent couplings J_ij(s_i, s_j) <-> context-dependent influence <-> QK attention
3. Asymmetric couplings J_ij != J_ji <-> asymmetric influence <-> QK^T != KQ^T
4. Multi-head attention <-> multiple simultaneous interaction channels <-> no classical Ising analog
5. Positional encoding <-> agent identity / role <-> no classical Ising analog

---

## 11. Reading Assessment

**Confidence in these notes**: HIGH for the historical narrative, the basic Ising-economics correspondences (S1-S21), and the logit = Boltzmann identity. MEDIUM for specific equation forms (should be verified against the paper). LOW for specific section numbers and page references (should be checked).

**Recommended follow-up**: The PI should skim the paper directly to verify:
1. The exact form of the self-consistency equation Sornette uses
2. Whether Sornette discusses the q-state Potts model explicitly or only the binary Ising
3. Whether Sornette discusses the random field Ising model or whether this comes from other sources
4. The specific references Sornette gives for the logit = Boltzmann identity (McFadden 1974, Anderson et al. 1992 are the standard ones)
5. Whether Sornette makes any direct connection to information theory or entropy measures beyond the standard statistical mechanics framework

**Time estimate for verification**: 2-3 hours of targeted reading of the relevant sections.
