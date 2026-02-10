# Master Correspondence Table: Ising / Spin Models <-> Transformers <-> Economics

**Version**: 1.0 (Phase 1 synthesis)
**Date**: 2026-02-10
**Status**: Central artifact of the Economics 2.0 research program
**Sources synthesized**: Bal (2020, 2021a, 2021b, 2023), Rende et al. (2024), Huo & Johnson (2025), Bouchaud, Marsili & Nadal (2023), Sornette (2014), Yakovenko & Rosser (2009), Chater & MacKay (2023), Ramsauer et al. (2021), Li et al. (2025), Smith & Foley (2008), bg.md landscape survey

---

## Status Key

- **CLEAN**: Both maps (Ising->Transformer and Ising->Economy) are established or well-derived; the composition Transformer->Economy is straightforward. All three columns agree.
- **TENSION**: The maps disagree, are ambiguous, or compose in a non-obvious way. Requires theoretical resolution.
- **NOVEL**: The transformer has a feature with no standard Ising analog, requiring *direct* economic interpretation that bypasses the Ising intermediary. **This is where the new theory lives.**
- **GAP**: An economic feature with no clear transformer analog, or a transformer feature with no clear economic interpretation.

## Epistemic Status Labels

All claims are labeled:
- **ESTABLISHED**: Published, peer-reviewed, independently replicated or widely accepted.
- **DERIVED**: Follows logically from established results; the derivation has been published but not independently replicated.
- **CONJECTURED**: Plausible inference from established/derived results, but not proven; this project's interpretive contribution.
- **SPECULATIVE**: Suggestive but with weak evidentiary support; requires significant further work.

---

## The Master Table

| # | Ising Feature | Transformer Correspondent | Trans. Source | Economic Correspondent | Econ. Source | Composed: Transformer -> Economy | Status | Notes |
|---|---|---|---|---|---|---|---|---|
| 1 | **Boltzmann weight** exp(-beta E) / Z | **Softmax attention weight** exp(q.k / T) / Z | Bal 2020; Ramsauer+ 2021; Rende+ 2024 | **Logit choice probability** exp(beta V_i) / sum exp(beta V_j) | McFadden 1974; Sornette 2014; Brock & Durlauf 2001 | Softmax attention = logit choice probability. The mathematical identity is exact: softmax IS the Boltzmann distribution IS the multinomial logit. [ESTABLISHED for each link; DERIVED for the full chain] | **CLEAN** | Keystone of the entire bridge. Three communities use the same equation without cross-reference. |
| 2 | **Temperature T** (inverse beta = 1/T controls thermal fluctuations) | **Softmax scaling** 1/sqrt(d_k) or learnable tau | Bal 2020-2023; Ramsauer+ 2021 | **Decision noise / bounded rationality** (T->0: homo economicus; T->inf: random) | Sornette 2014 (logit model); Bal 2020-2023 (softmax) | Softmax temperature tau = logit rationality parameter. This is the PREFERRED DEFINITION: tau is the scaling parameter in the Boltzmann/softmax/logit distribution, established independently by Bal (physics) and Sornette (econophysics) as the same mathematical object. Low tau: sharp attention = rational agents = winner-take-all. High tau: uniform attention = random choice = competitive markets. Chater-MacKay's "inverse marginal utility of money" and Yakovenko's "average money per agent" are macroscopic/proxy quantities whose relationship to the microscopic tau is a derivable consistency check, not a competing definition. | **CLEAN** | The spin transformer Hamiltonian defines T = tau (softmax). This is identical to Sornette's logit noise parameter. Chater-MacKay's macro-T should be derivable from micro-tau in the thermodynamic limit (as in standard stat mech). Yakovenko's <m> is an observable proxy. Standard transformers fix tau = sqrt(d_k); learnable tau = endogenous rationality. T_H and T_AI are measurable from choice data. |
| 3 | **Partition function Z** = sum exp(-beta E) | **Softmax normalization** (log-sum-exp) | Bal 2020; Rende+ 2024 | **Inclusive value / social surplus** (McFadden); aggregate expected welfare | McFadden 1978; Sornette 2014; Smith & Foley 2008 | Log-sum-exp of attention scores = consumer surplus = generating function for all equilibrium quantities. | **CLEAN** | LSE, ubiquitous in ML, is literally the free energy. Numerically stable softmax = free energy computation. |
| 4 | **Free energy F** = -T log Z | **Log-partition function** of attention layer (implicit in forward pass) | Bal 2021a; Bal 2021b | **Negative aggregate welfare** or **economic potential**; Helmholtz free energy F = U - TS; "extractable wealth" | Smith & Foley 2008; Chater & MacKay 2023 | Transformer free energy = negative economic welfare. Minimizing F (physics) = maximizing welfare (economics), modulo sign convention. | **CLEAN** | The sign flip (minimize energy vs. maximize utility) must be tracked carefully. V_i = -E_i throughout. |
| 5 | **Magnetization m** = -dF/dh = thermal average of spins | **Attention output** = softmax(QK^T/T) V = weighted sum of values | Bal 2020; Bal 2021a | **Aggregate demand / excess demand / market sentiment** | Sornette 2014; Bouchaud+ 2023 | Attention output = expected economic choice = aggregate demand. The master equation: output_i = dF/dh_i (layer output is a thermodynamic response function). [DERIVED] | **CLEAN** | When V=K, output is literally the magnetization. General V case: generalized order parameter. Economic response functions (multipliers, elasticities) derive from this. |
| 6 | **External field h_i** (biases spin toward alignment) | **Input embedding / residual connection** (additive signal persisting through layers) | Bal 2021a; Bal 2023 | **Exogenous fundamentals**: endowments, policy signals, private information, real-economy conditions | Sornette 2014; Bouchaud+ 2023 | Residual connection = persistent exogenous signal. Economy always "remembers" external conditions; internal dynamics (attention) add corrections but never overwrite fundamentals. [DERIVED] | **CLEAN** | Residual connections are not engineering tricks but thermodynamic necessity. Removing them = setting h=0 = economy with no fundamentals (pure speculation). |
| 7 | **Coupling constant J_ij** (fixed or quenched random; interaction strength between spins) | **Attention weight alpha_ij** derived from QK dot product (data-dependent, asymmetric) | Bal 2020-2023; Rende+ 2024 | **Economic interaction strength**: trade volume, influence, imitation, supply-chain coupling (typically symmetric in sociophysics) | Bouchaud+ 2023; Sornette 2014 | Attention weights = economic coupling. But transformer J is data-dependent and asymmetric; standard Ising J is fixed and symmetric. The composed map predicts context-dependent, directional economic influence -- more realistic than standard sociophysics. | **TENSION** | Central tension of the bridge. See rows 18-19 for the decomposed analysis. |
| 8 | **Stored patterns** xi_mu in Hopfield network | **Key-value pairs** (k_mu, v_mu) at sequence positions | Bal 2020; Ramsauer+ 2021 | **Available options / goods / market configurations** | [Standard econ] | Key-value pairs = menu of economic options. Attention retrieves the option best matching the query (agent's needs). Exponential storage capacity (Ramsauer) = economy can maintain exponentially many configurations. [CONJECTURED] | **CLEAN** | Classical Hopfield stores O(d) patterns; modern continuous Hopfield stores exp(d/2). Economic implication: richer representational spaces = richer economies. |
| 9 | **Phase transition at T_c** (spontaneous magnetization, divergent susceptibility, power-law correlations) | **Behavioral regime change** in attention: transition between averaging, clustered, and sharp retrieval modes | Ramsauer+ 2021; Huo & Johnson 2025 | **Market crash / bubble / regime change**: below T_c, spontaneous herding; at T_c, excess volatility, system-wide correlation, power-law fluctuations | Sornette 2014; Bouchaud+ 2023 | Attention regime transition = market phase transition. The composed map predicts new universality classes for "transformer economy" phase transitions (Heisenberg/O(d) rather than Ising/Z_2). [CONJECTURED] | **CLEAN** | Universality class question: does the transformer economy have Ising exponents, Heisenberg exponents, or something new? Testable prediction. |
| 10 | **Susceptibility chi** = dm/dh (diverges at T_c) | **Sensitivity of attention** output to input perturbation | [Implicit in Bal framework] | **Excess volatility / market sensitivity to news** chi ~ \|T - T_c\|^{-gamma} | Sornette 2014; Bouchaud+ 2023 | Attention sensitivity = market volatility amplification. Near phase boundary: small input changes cause large output shifts = small news causes large price movements. Fluctuation-dissipation: chi = beta * Var(m) * N. [ESTABLISHED on both sides] | **CLEAN** | The FDT connects response (susceptibility) to spontaneous fluctuations. Economic version: market sensitivity ~ volatility. Non-trivial quantitative prediction. |
| 11 | **Ferromagnetic coupling J > 0** (spins tend to align) | **Cooperative attention heads** (tokens reinforce each other's representations) | Huo & Johnson 2025 | **Herding / imitation / bandwagon effect** (agents copy neighbors) | Sornette 2014; Bouchaud+ 2023; Vilela+ 2019 | Cooperative heads = herding agents. The three-way correspondence is the cleanest in the table: ferromagnetic coupling = cooperative attention = herding behavior. Experimentally validated in GPT-2. [DERIVED for the full chain] | **CLEAN** | Huo & Johnson classify GPT-2 heads as cooperative/antagonistic. Vilela et al. model noise traders with ferromagnetic coupling. The parallel is structural. |
| 12 | **Antiferromagnetic coupling J < 0** (spins tend to anti-align) | **Antagonistic attention heads** (tokens compete/contrast) | Huo & Johnson 2025 | **Contrarian / arbitrage behavior** (agents oppose majority) | Vilela+ 2019; Bouchaud+ 2023 | Antagonistic heads = contrarian agents. Antiferromagnetic attention = stabilizing market force (mean reversion). Balance of cooperative vs. antagonistic heads determines system stability. [DERIVED] | **CLEAN** | Kaizoji, Bornholdt & Fujiwara (2002) modeled fundamentalists as anti-aligned with noise traders. Same structure in GPT-2 heads. |
| 13 | **Frustration** (competing interactions in a loop; not all bonds satisfiable) | **Attention head conflict** (different heads "want" different outputs for the same token) | [Implicit in multi-head attention] | **Conflicting economic interests** (agents cannot all be simultaneously satisfied); underpins spin glass economics | Bouchaud+ 2023 | Multi-head disagreement = market frustration. Frustrated economies develop spin-glass-like properties: many near-degenerate equilibria, path dependence, slow dynamics. [CONJECTURED] | **CLEAN** | Frustration is what makes economics non-trivial. Trade-offs and prices emerge as attempts to minimize frustration. Transformer multi-head structure naturally produces frustration. |
| 14 | **Energy gap Delta E** (between ground state and first excited state) | **Logit gap** (difference between top-1 and top-2 next-token logits) | Huo & Johnson 2025 | **Price spread / bid-ask spread / choice confidence**; utility gap in discrete choice | Sornette 2014; [Standard econ] | Logit gap = energy gap = economic confidence margin. Validated experimentally at p < 10^-3 in GPT-2. The Boltzmann suppression exp(-beta * Delta E) gives the probability ratio between top choices. [ESTABLISHED for Ising-Transformer; DERIVED for full chain] | **CLEAN** | One of the strongest three-way correspondences. Energy gap -> logit gap is experimentally validated. Logit gap -> utility gap is standard in discrete choice theory. |
| 15 | **Entropy S** = -sum p_i log p_i (of spin configuration) | **Entropy of attention distribution** (-sum alpha_ij log alpha_ij) | [Standard information theory] | **Economic entropy**: allocation multiplicity (Chater-MacKay); social surplus-related (Smith-Foley); or information entropy of price distribution | Chater & MacKay 2023; Smith & Foley 2008 | Attention entropy = economic entropy. High entropy: diffuse attention = competitive market = many possible allocations. Low entropy: concentrated attention = monopoly = few possible allocations. [DERIVED] | **TENSION** | Three competing definitions of economic entropy (Chater-MacKay, Smith-Foley, Georgescu-Roegen). Transformer side is clear. Economic side requires choosing a definition. |
| 16 | **Mean-field approximation** (replace spin-spin interactions with average field; exact on complete graphs) | **Self-attention** (each token interacts with the average of all others, weighted by coupling) | Bal 2021a | **Representative agent / rational expectations** (all agents face the same "average" conditions) | Sornette 2014; Bouchaud+ 2023 | Self-attention = market mechanism. Mean-field = representative agent. Going beyond mean-field (TAP, cavity, RSB) = going beyond representative-agent economics. The transformer is inherently beyond mean-field due to structured, asymmetric couplings. [ESTABLISHED for each link] | **CLEAN** | Powerful structural insight. Standard economics IS mean-field theory. Known failures of mean-field = known failures of representative-agent models. |
| 17 | **Onsager / TAP self-interaction correction** (subtracts the "echo" of a spin's own influence returning via neighbors) | **Feed-forward / MLP layer** (position-wise, single-site nonlinear transformation) | Bal 2021a; Bal 2023 | **Market impact correction**: agents accounting for the fact that their own actions move prices; rational expectations feedback | Bouchaud+ 2023 | FFN layer = self-impact correction. Each agent adjusts for its own market influence. The TAP correction subtracts the spurious self-reinforcing feedback from naive mean-field. Economically: rational agents discount market signals that they themselves helped create. [DERIVED for Ising-Transformer; CONJECTURED for economic interpretation] | **CLEAN** | One of the deepest correspondences. The FFN's role has always been somewhat mysterious. The TAP identification gives it precise economic content. Alternating structure (attention then FFN) = alternating exchange then self-assessment. |
| 18 | **Asymmetric couplings J_ij != J_ji** (breaks detailed balance; no equilibrium energy function; requires non-equilibrium / kinetic treatment) | **Standard softmax attention** (Q != K projections; row-wise normalization breaks symmetry) | Bal 2023 | **Non-reciprocal economic power**: employer/employee, producer/consumer, platform/participant, informed/uninformed trader -- economic influence is inherently directional | [Standard econ; novel interpretation] | Asymmetric attention = asymmetric economic power. Standard sociophysics imposes J_ij = J_ji (unrealistic). The transformer's natural asymmetry is more realistic for economics. Non-reciprocal couplings force non-equilibrium treatment, which is also more realistic (real economies never reach equilibrium). [DERIVED for transformer-physics; CONJECTURED for economic interpretation] | **NOVEL** | The feature that makes transformer spin models "weird" in physics is the feature that makes them "natural" in economics. This is the first NOVEL entry: the transformer resolves a known limitation of sociophysics. |
| 19 | **Data-dependent couplings J_ij(sigma)** (coupling depends on current spin configuration; "very weird and highly unusual" in physics -- Bal) | **Q-K attention mechanism** where J_ij = f(W_Q sigma_i, W_K sigma_j) | Bal 2023 | **State-dependent terms of trade**: "who trades with whom" and "at what rate" depends on agents' current states (endowments, preferences, information) | [Novel interpretation; connects to temporary equilibrium theory] | Data-dependent attention = endogenous interaction structure. In standard Ising economies, J is fixed (institutions are static). In the transformer economy, J changes with the economic state -- institutions, terms of trade, and market structure are endogenous. [ESTABLISHED for transformer-physics; CONJECTURED for economic interpretation] | **NOVEL** | Second key NOVEL entry. What is "pathological" in physics is fundamental in economics. Trade depends on endowments; network effects are state-dependent; credit depends on financial state. The Ising model misses this; the transformer captures it. |
| 20 | **Multi-head attention** (H independent coupling channels operating in parallel on d/H-dimensional subspaces) | **Multi-head self-attention**: each head has its own Q^h, K^h, V^h | Bal 2021a; Huo & Johnson 2025 | **Multiple simultaneous interaction channels**: trade, information exchange, social influence, financial coupling -- all operating in parallel between the same agents | [Novel interpretation] | Multi-head attention = multiple simultaneous markets. Each head captures a different type of economic interaction (goods market, labor market, credit market, information market) operating simultaneously between the same agents. [CONJECTURED] | **NOVEL** | No standard Ising analog. In the Potts/Heisenberg framework, decomposition into channels exists (Bal), but the economic interpretation is novel. Huo & Johnson find cooperative vs. antagonistic heads -- these map to stabilizing vs. destabilizing market channels. |
| 21 | **Layer normalization** / extensive energy (J -> J/N to keep energy per spin O(1)) | **LayerNorm / RMSNorm** ensuring activations have bounded magnitude; 1/sqrt(d_k) scaling | Bal 2021a | **Bounded rationality / resource constraints** ensuring per-agent economic quantities remain finite as economy grows | [Novel interpretation; connects to extensivity in macro] | LayerNorm = extensivity constraint. Per-capita GDP (intensive quantity) must remain finite as population (N) grows. Without normalization, the "temperature" effectively goes to zero as the system grows, freezing the economy. [DERIVED for transformer-physics; CONJECTURED for economic interpretation] | **CLEAN** | Thermodynamic necessity, not engineering trick. Explains why transformers without LayerNorm fail: thermodynamically pathological regime. |
| 22 | **Depth / number of layers L** (iterations of mean-field self-consistency equation) | **L transformer layers** (each layer = one step of mean-field iteration or one time step of kinetic dynamics) | Bal 2021b; Bal 2023 | **Number of market rounds / tatonnement steps** to reach equilibrium; depth of economic processing for complex economies | [Novel interpretation; connects to Walrasian tatonnement] | Transformer depth = economic processing time. Deeper transformers = more rounds of market clearing = closer to true equilibrium. Diminishing returns from depth once convergence is reached. Complex economies (strong coupling) need more layers. [DERIVED for physics-transformer; CONJECTURED for economic interpretation] | **CLEAN** | Depth is a precision parameter (how close to true equilibrium), not capacity (how complex the economy). Consistent with DEQ finding that one implicit layer can replace many explicit layers. |
| 23 | **Vector spin sigma_i in R^d** (d internal degrees of freedom per spin; Heisenberg model) | **Token embedding x_i in R^d** (d-dimensional representation per token) | Bal 2021a; Huo & Johnson 2025 | **Multi-attribute economic agent**: preferences over many goods, multi-dimensional strategy/capability space, rich internal state | [Novel interpretation; improves on binary Ising agents] | d-dimensional token = d-dimensional economic agent. Classical sociophysics uses binary spins (buy/sell); the transformer gives agents continuous, high-dimensional state spaces. Heisenberg symmetry implies Goldstone modes (costless collective reorientations of economic activity). [DERIVED for physics-transformer; CONJECTURED for economic interpretation; SPECULATIVE for Goldstone modes] | **NOVEL** | Upgrade from Ising (Z_2 symmetry) to Heisenberg (O(d) symmetry) changes universality class. Economic implication: the transformer economy has qualitatively different phase transitions than the binary sociophysics economy. |
| 24 | **Potts spin sigma_i in {1,...,q}** (q discrete states per spin) | **Token from vocabulary of size q** (one-hot encoded) | Rende+ 2024 | **Agent choosing among q discrete strategies** (multi-option market, not just buy/sell) | Bornholdt 2022; Diep 2021 | Token = economic choice among q options. The Potts bridge is tighter than the Ising bridge: exact mapping (Rende+) with q > 2 naturally accommodates real economic choice sets. Potts transition is first-order for q > 4, predicting abrupt crashes in markets with many options. [ESTABLISHED for physics-transformer; ESTABLISHED for physics-economy; CONJECTURED for composition] | **CLEAN** | The Potts model appears on both sides independently. Rende et al. map transformers to Potts; Bornholdt maps Potts to markets. The coincidence strengthens the bridge. |
| 25 | **Training = inverse problem** (infer Hamiltonian couplings from observed configurations) | **Cross-entropy training** = pseudolikelihood maximization of inverse Potts problem | Rende+ 2024 | **Econometric inference**: inferring interaction structure from observed market behavior | [Standard econometrics; novel composition] | Training a transformer on economic data = performing inverse statistical mechanics on the economic system = econometric inference of the economy's "Hamiltonian." [DERIVED for physics-transformer; CONJECTURED for composed economic interpretation] | **CLEAN** | Rende et al.'s deepest result. The ML community's training procedure and the physics community's inverse problem are the same algorithm. Neither designed it that way. |
| 26 | **Replica symmetry breaking** (multiple equilibria organized ultrametrically; exponentially many nearly-degenerate states) | **Multiple qualitatively different solutions** to the same prediction task; training-dependent outputs | Rende+ 2024; Li+ 2025 | **Multiple economic equilibria**: the economy has many viable configurations; small perturbations can cause jumps between them; path dependence; economic crises as transitions between RSB states | Bouchaud+ 2023 | RSB in transformer = multiple economic equilibria. An economy in the RSB phase has many "modes" it can be in. Crises are not departures from equilibrium but jumps between degenerate equilibria in a rugged landscape. [ESTABLISHED for physics-economy; CONJECTURED for the transformer link] | **CLEAN** | BMN's treatment of RSB in economics is their strongest contribution. The transformer side (Li et al.) provides a new pathway to the same structure via weight-space spin glasses. |
| 27 | **SAT-UNSAT transition** (critical ratio alpha_c of constraints to variables; above alpha_c, no satisfying assignment exists) | **Phase transition in learning** at critical dataset size alpha_c; sharp onset of generalization | Rende+ 2024 | **Economic viability boundary**: when constraints (budget, regulation, market-clearing) exceed degrees of freedom (prices, quantities), no viable allocation exists. Market completeness pushes alpha toward alpha_c. | Bouchaud+ 2023 | Learning threshold = economic viability threshold. Below alpha_c: system cannot find solutions (economy fails, model cannot generalize). Near alpha_c: solutions exist but are hard to find (fragile economy, slow learning). Above alpha_c: no solutions (unsatisfiable economy). BMN show market completeness increases alpha toward alpha_c, explaining financial instability from over-engineering. [ESTABLISHED for each link; DERIVED for composition] | **CLEAN** | Striking policy prediction: more complete markets = closer to SAT-UNSAT boundary = more fragile. Validated qualitatively by 2008 financial crisis. |
| 28 | **Kinetic Ising / non-equilibrium steady state** (dynamics without a well-defined energy function; master equation replaces Boltzmann distribution) | **Transformer forward pass = one time step of kinetic mean-field dynamics** | Bal 2023 | **Out-of-equilibrium economic dynamics**: real economies never reach equilibrium; constant flow of goods/money/information in a non-equilibrium steady state | [Connects to post-Keynesian, complexity economics] | Transformer dynamics = non-equilibrium economic dynamics. The shift from equilibrium Ising to kinetic Ising is not a choice but a consequence of asymmetric couplings. This resolves a long-standing tension in econophysics: physicists mapped equilibrium models to inherently non-equilibrium economies. The transformer mapping forces the correct (non-equilibrium) treatment. [DERIVED] | **NOVEL** | Third key NOVEL entry. Non-equilibrium is forced by asymmetric J, not assumed. The transformer economy is necessarily non-equilibrium -- not by choice but by structure. |
| 29 | **Carnot cycle** (work extraction from temperature gradient between hot and cold reservoirs; efficiency eta = 1 - T_cold/T_hot) | **[No direct transformer analog]** -- temperature is fixed in standard transformers | [GAP on transformer side] | **Economic Carnot cycle**: trader extracts profit from temperature difference between populations | Chater & MacKay 2023; Sornette 2014 (for T definition) | The Carnot construction requires TWO temperatures. Standard transformers have one. The novel theory proposes: tau_human != tau_AI within the same economy, where tau is the softmax/logit temperature (Bal + Sornette definition). T_H and T_AI are operationally measurable from choice behavior. The market mechanism extracts value from this gradient. Efficiency bound eta = 1 - tau_cold/tau_hot is a specific, testable prediction. [CONJECTURED for the two-population Carnot; the temperature definition itself is ESTABLISHED via Bal + Sornette] | **NOVEL** | Fourth key NOVEL entry. Chater-MacKay construct the Carnot cycle between two economies using macro-T. The novel theory internalizes it using micro-tau (Bal + Sornette) applied to two agent populations. Whether the Carnot formula transfers from macro-T to micro-tau is consistency check 1 for Phase 2. |
| 30 | **Two spin species at different T** (driven two-temperature system; or two populations with different statistical laws) | **[No standard transformer analog]** -- all tokens share the same softmax temperature | [GAP on transformer side] | **Yakovenko's two-class structure**: lower 97% thermalizes at tau_lower (Boltzmann-Gibbs); upper 3% follows Pareto law at effectively different tau | Yakovenko 2009 | The novel theory maps: human agents at tau_H (measurable softmax/logit temperature from choice data) and AI agents at tau_AI (measurable from AI choice behavior — typically much lower, sharper). The gradient |tau_H - tau_AI| enables Carnot-style value extraction. Empirical precedent: Yakovenko proves two-temperature economies already exist. Operational test: fit logit models to human and AI choice data separately; if tau_H >> tau_AI, the gradient exists. [ESTABLISHED for physics-economy; ESTABLISHED for the temperature definition via Bal + Sornette; CONJECTURED for the human-AI Carnot extension] | **NOVEL** | Fifth key NOVEL entry. Yakovenko provides empirical precedent. Key question: what sustains the gradient? Yakovenko: different income processes (additive vs. multiplicative). Novel theory: different computational substrates. The Bal + Sornette temperature definition makes tau_H and tau_AI measurable, converting this from speculation to testable claim. |
| 31 | **Cavity field** = effective field on a marginal spin from all others; method for adding/removing one spin | **[Implicit in attention]** -- each token "sees" the field from all others via attention | Bouchaud+ 2023 | **Price as cavity field**: the price vector a marginal agent faces = the cavity field from all other agents. Adding one agent and computing the economy's response. | Bouchaud+ 2023 | The cavity method gives a microscopic derivation of prices. In the transformer: each token's attention-weighted input IS the cavity field. Economic prices emerge as cavity fields in the attention economy. [ESTABLISHED for physics-economy; DERIVED for physics-transformer; CONJECTURED for full composition] | **CLEAN** | Beautiful correspondence: price discovery = cavity method = attention computation. All three are computing "what does the rest of the system look like from one agent's perspective?" |
| 32 | **Quenched disorder** (random J_ij frozen on slow timescale; averaged via replicas) | **Learned parameters** (trained weights, fixed at inference time) | Li+ 2025 | **Structural heterogeneity** (endowments, skills, institutions -- slow-changing) vs. **transient heterogeneity** (current positions -- fast-changing) | Bouchaud+ 2023 | Trained weights = institutional structure. Quenched disorder = frozen heterogeneity. The novel theory reframes: standard spin glass treats heterogeneity as disorder (to be averaged over). The novel theory treats it as gradient (to be exploited). Same math, different interpretation. [ESTABLISHED for each link; the reinterpretation is the project's core conceptual contribution -- CONJECTURED] | **TENSION** | The disorder-vs-gradient reframing is the theory's strongest move. Mathematical content is identical. The question is whether the gradient interpretation is physically/economically justified or merely a relabeling. |
| 33 | **Token mixing** (inter-spin coupling terms in H; sums over spin sites) | **Attention mechanism** (aggregation across token positions) | Bal 2021b | **Inter-agent exchange / trade** (information, goods, money flowing between agents) | [Standard econ] | Attention = market mechanism for inter-agent coordination. The Hamiltonian demands token mixing; the economy demands exchange. Neither can be eliminated without destroying the system. [DERIVED] | **CLEAN** | Part of the fundamental decomposition: token mixing (exchange) + channel mixing (production). |
| 34 | **Channel mixing** (intra-spin / on-site potential terms in H; operations on a single spin's internal degrees of freedom) | **MLP / feed-forward layer** (position-wise operation on d-dimensional representation) | Bal 2021b | **Intra-agent production / internal processing** (transforming inputs to outputs, making decisions, updating beliefs) | [Novel interpretation] | FFN = internal production function of each agent. Each agent processes its own state independently of inter-agent interactions. The alternation (attention then FFN, exchange then production) is structurally required by the Hamiltonian -- you cannot collapse all economic activity into pure exchange or pure autarky. [DERIVED for physics-transformer; CONJECTURED for economic interpretation] | **NOVEL** | Sixth key NOVEL entry. The attention-then-FFN alternation predicts that economies must alternate between trading and producing. This is a non-trivial architectural prediction for economic dynamics. |
| 35 | **Q-K-V factored structure** (query = "what am I looking for"; key = "what am I advertising"; value = "what I actually provide") | **Factored self-attention**: QK pathway (where to attend) separate from V pathway (what to extract) | Rende+ 2024 | **Demand-supply-transaction decomposition**: Q = demand signal; K = supply signal; V = actual economic content transacted | [Novel interpretation] | The factored structure predicts that "who you interact with" (QK/network topology) is separable from "what you exchange" (V/content). Economically: network structure and preference structure factorize. If this fails (who you trade with depends on what you trade), the exact Potts mapping breaks down. [DERIVED for physics-transformer; CONJECTURED for economic interpretation] | **NOVEL** | Seventh key NOVEL entry. This structural claim about the economy is testable. If violated, the exact mapping (Rende+) becomes approximate. |
| 36 | **Pseudolikelihood** approximation (local conditionals, not global joint distribution) | **Per-token cross-entropy loss** (predict one token given all others; never compute joint probability) | Rende+ 2024 | **Bounded rationality in a precise sense**: agents optimize locally (conditioning on neighbors' current states) rather than globally (computing full equilibrium) | [Novel interpretation; connects to Herbert Simon] | Pseudolikelihood = bounded rationality. Agents who use local conditional information rather than global joint information are performing pseudolikelihood estimation. Unlike Simon's verbal description, this version comes with exact error bounds (from the replica calculation). [DERIVED for physics-transformer; CONJECTURED for economic interpretation] | **NOVEL** | Eighth key NOVEL entry. Gives a mathematically precise, calculable model of bounded rationality with known generalization error. |
| 37 | **Saddle point of mean-field free energy** (dF_MF/dm = 0; self-consistent magnetizations; may be unstable) | **Converged transformer output** (fixed point of layer-wise iteration) | Bal 2021b | **Economic equilibrium as saddle point** (marginally stable, not globally optimal; multiple nearby equilibria) | [Novel interpretation; connects to Nash equilibrium] | Transformer convergence = economic equilibrium. But equilibrium is a saddle point (some directions unstable), not a minimum. This predicts that economic equilibria are generically fragile -- stable to most perturbations but unstable to specific ones. More complex economies (stronger coupling) need more layers/rounds to find the saddle. [DERIVED for physics-transformer; CONJECTURED for economic interpretation] | **TENSION** | The saddle-vs-minimum distinction matters: saddle points can be escaped; minima cannot. If the economy sits at a saddle, there always exist directions of instability. This is consistent with observed economic fragility. |
| 38 | **Work W** = energy extracted via macroscopic degrees of freedom | **[No direct transformer analog]** | [GAP] | **Profit** = surplus extracted by a trader operating between reservoirs at different T | Chater & MacKay 2023 | In the novel theory: economic value created by the human-AI interaction. W = Q_hot - Q_cold. Maximum efficiency eta = 1 - T_cold/T_hot. The gradient between human and AI cognitive temperatures is the source of economic value. [CONJECTURED] | **NOVEL** | Ninth key NOVEL entry. Central to the Carnot engine claim. Requires precise definition of what "work" means in the transformer-economy context. |
| 39 | **Ground state degeneracy** (multiple spin configurations minimize energy; exponential in N for frustrated systems) | **Multiple attention patterns** producing equivalent outputs; multiple valid next-token predictions | [Implicit in transformer behavior] | **Multiple Pareto optima** (many allocations are equally "efficient"; which one is selected depends on history) | Bouchaud+ 2023 | Degeneracy = economic indeterminacy. The economy has many equally good configurations, and which one is realized is path-dependent. The novel theory's claim: without heterogeneous spin species (human + AI), the ground state becomes MORE degenerate, losing productive capacity. [ESTABLISHED for physics-economy; CONJECTURED for the novel degeneracy-heterogeneity claim] | **GAP** | The novel theory claims degeneracy without heterogeneity. This is a specific, testable prediction from the two-species Hamiltonian. Needs toy model verification (Phase 2). |

---

## NOVEL Entries Analysis

These are the rows where the transformer has features that bypass the standard Ising intermediary, requiring direct economic interpretation. **This is where the new theory lives.**

### N1: Asymmetric Couplings (Row 18)

**Why it is novel**: Standard sociophysics assumes J_ij = J_ji, which guarantees detailed balance and equilibrium thermodynamics. Transformers have J_ij != J_ji as a structural feature (W_Q != W_K, plus row-wise softmax normalization). No existing sociophysics model accounts for this.

**Proposed economic interpretation**: Economic interactions are inherently non-reciprocal. An employer's influence on an employee differs from the employee's influence on the employer. A platform's impact on its users is vastly larger than any single user's impact on the platform. The transformer's asymmetric couplings are therefore *more realistic* than the symmetric Ising model for economic applications.

**What would confirm it**: Show that the non-equilibrium steady state of the asymmetric kinetic Ising model (Bal 2023) reproduces known features of real economic dynamics (persistent cycles, directed flows, power asymmetries) that symmetric models cannot capture.

**What would refute it**: If symmetrizing the attention matrix (W_Q = W_K) produces equally good economic predictions, the asymmetry is not economically meaningful. Alternatively, if the asymmetry leads to pathological economic predictions (unstable divergences, non-physical states), the mapping is defective.

**Epistemic status**: CONJECTURED. The physics is ESTABLISHED (Bal 2023). The economic interpretation is novel and untested.

### N2: Data-Dependent Couplings (Row 19)

**Why it is novel**: In all standard spin models, J_ij is either fixed (Ising), random-but-frozen (spin glass), or slowly evolving (adaptive networks). The transformer's J_ij = f(W_Q sigma_i, W_K sigma_j) depends on the current spin states at every time step. Bal calls this "very weird and highly unusual."

**Proposed economic interpretation**: The strength of economic interaction between agents depends on their current states -- this is not weird in economics; it is fundamental. Trade volume depends on endowments. Credit depends on financial condition. Attention allocation depends on current interests. The feature that makes the model pathological in physics makes it natural in economics.

**What would confirm it**: Construct a toy model showing that the transformer's data-dependent couplings reproduce known economic phenomena (e.g., endogenous network formation, state-dependent trade patterns) that fixed-coupling models cannot.

**What would refute it**: If data-dependent couplings produce chaotic, unpredictable dynamics with no stable economic interpretation, the mapping breaks down. The self-referential nature of J(sigma) could generate pathological feedback loops.

**Epistemic status**: CONJECTURED. The strongest observation for the project: what is weird in physics is natural in economics.

### N3: Non-Equilibrium as Structural Consequence (Row 28)

**Why it is novel**: The shift to non-equilibrium is not a modeling choice but a mathematical consequence of asymmetric J. You cannot use equilibrium statistical mechanics for the transformer spin model. This resolves a long-standing tension: econophysics has mapped equilibrium models to non-equilibrium economies, which was always a mismatch.

**Proposed economic interpretation**: The transformer economy is necessarily non-equilibrium. This is more realistic than equilibrium models and resolves the known limitation of Ising sociophysics. Non-equilibrium steady states (constant GDP growth with persistent flows) replace static equilibria.

**What would confirm it**: Show that the non-equilibrium steady state of the kinetic Ising model at the transformer's operating point reproduces stylized facts of real economies (persistence of flows, non-zero entropy production, violation of detailed balance in transaction data).

**What would refute it**: If the asymmetric effects are quantitatively small and the system behaves as if nearly in equilibrium, the non-equilibrium treatment adds complexity without explanatory power.

**Epistemic status**: DERIVED (the physics is forced). The economic interpretation is CONJECTURED.

### N4: The Carnot Engine Between Agent Populations (Rows 29-30)

**Why it is novel**: Chater and MacKay construct a Carnot cycle between two *separate economies* using macroscopic temperature. No one has identified a temperature gradient between two *agent populations within the same economy* or proposed that value arises from this gradient using microscopic (softmax/logit) temperature.

**Proposed economic interpretation**: Human agents operate at softmax/logit temperature tau_H (high — noisy, exploratory, entropic choice behavior). AI agents operate at tau_AI (low — sharp, concentrated, exploitative choice behavior). Both temperatures are operationally defined via the Bal + Sornette identification: tau is the scaling parameter in the Boltzmann/softmax/logit distribution, measurable from choice data. The gradient |tau_H - tau_AI| enables Carnot-style value extraction. The efficiency bound eta = 1 - tau_cold/tau_hot is a specific, testable prediction.

**What would confirm it**: (a) Fit logit models to human and AI choice data; demonstrate tau_H >> tau_AI empirically. (b) Show that the Carnot efficiency formula correctly predicts value creation in a toy model with two agent populations at different tau. (c) Derive Chater-MacKay's macroscopic temperature from the microscopic tau in the thermodynamic limit (consistency check 1).

**What would refute it**: (a) If tau_H and tau_AI are not measurably different from choice data, the gradient does not exist. (b) If the Carnot formula gives quantitatively wrong predictions even when tau is well-measured — indicating that the softmax temperature does not play the thermodynamic role the theory assigns it. (c) If the gradient equilibrates rapidly (AI learns to mimic human noise, or human choice sharpens through AI tools) and cannot be maintained.

**Epistemic status**: CONJECTURED. The temperature definition is ESTABLISHED (Bal + Sornette, independently). The Carnot construction for separate economies is DERIVED (Chater-MacKay). The application to two populations within one economy using microscopic tau is the novel, untested extension. The adversarial review (R-001) wounded the claim under the old three-definition framing; the resolution via Bal + Sornette addresses the definitional concern but the T_H = T_AI limiting case and the micro-to-macro consistency check remain open.

### N5: Multi-Head Attention as Multiple Markets (Row 20)

**Why it is novel**: The Ising model has one coupling. Transformers have H attention heads, each with its own QK and V projections. There is no standard Ising analog of multiple independent coupling channels operating simultaneously between the same spins.

**Proposed economic interpretation**: Each attention head corresponds to a different type of economic interaction. Head h captures goods-market coupling; head h' captures information-market coupling; head h'' captures credit-market coupling. All operate in parallel on the same agents.

**What would confirm it**: Analyze a trained transformer's heads and show they specialize in different types of pattern (analogous to how GPT-2 heads specialize in syntactic vs. semantic roles). If these specializations map to economically meaningful categories, the interpretation holds.

**What would refute it**: If heads are redundant (all doing roughly the same thing) rather than specialized, the multi-market interpretation is too generous.

**Epistemic status**: CONJECTURED. Huo & Johnson's cooperative/antagonistic classification is suggestive but does not directly test the multi-market interpretation.

### N6: Attention-then-FFN Alternation as Exchange-then-Production (Row 34)

**Why it is novel**: The transformer's alternating attention-then-MLP structure emerges from the mathematical structure of the saddle-point equations (Bal 2021b). It is not a design choice but a consequence of the Hamiltonian having both inter-spin and intra-spin terms. No one has interpreted this alternation economically.

**Proposed economic interpretation**: Inter-agent exchange (attention/token-mixing) and intra-agent production (FFN/channel-mixing) must alternate. You cannot collapse the economy into pure exchange or pure autarky. The ordering matters: exchange comes first (agents learn about each other's states), then production (each agent processes internally). This is a non-trivial prediction about economic dynamics.

**What would confirm it**: Find empirical evidence that economic cycles have an exchange-then-production rhythm at some timescale. Or show that models violating this order perform worse in economic simulations.

**What would refute it**: If the alternation is an artifact of the specific approximation scheme (mean-field + TAP) rather than a general feature, it may not generalize.

**Epistemic status**: DERIVED for the physics; CONJECTURED for the economic interpretation.

### N7: QKV Factored Structure as Demand-Supply-Transaction (Row 35)

**Why it is novel**: The decomposition of attention into Query (what am I looking for), Key (what am I offering), and Value (what I actually provide when attended to) has no Ising analog. The factored structure corresponds to separability of position-couplings and state-couplings in the Potts model (Rende et al.).

**Proposed economic interpretation**: Q = demand signal, K = supply signal, V = actual transacted content. The attention weight Q_i . K_j measures the match between i's demand and j's supply. The separation of "who interacts" (QK) from "what is exchanged" (V) is a specific structural claim: economic network topology is separable from preference structure.

**What would confirm it**: Test the factorizability assumption against real economic data. If trade patterns factorize into a network part and a commodity part, the assumption holds.

**What would refute it**: If "who you trade with" depends strongly on "what you're trading" (obviously true for many goods -- you buy bread from a baker, not a banker), the factored structure breaks. This would mean the exact Potts mapping (Rende+) becomes approximate for realistic economies.

**Epistemic status**: CONJECTURED. This is a strong structural assumption with clear testable implications.

### N8: Pseudolikelihood as Bounded Rationality (Row 36)

**Why it is novel**: Rende et al. show that transformer training is mathematically identical to pseudolikelihood estimation. Pseudolikelihood uses local conditional distributions rather than the intractable global joint distribution. No one has interpreted this as a formal model of bounded rationality.

**Proposed economic interpretation**: Economic agents who condition on their neighbors' current states (rather than computing full general equilibrium) are performing pseudolikelihood estimation. This gives a precise, calculable model of bounded rationality: agents are optimal given their information constraints, and the generalization error from the replica calculation quantifies the cost of bounded rationality.

**What would confirm it**: Show that the pseudolikelihood estimator's generalization error (from Rende et al.'s replica calculation) matches the efficiency loss from bounded rationality in known economic models.

**What would refute it**: If the pseudolikelihood approximation produces qualitatively wrong economic predictions (e.g., fails to find equilibria that exist), the mapping is not economically useful.

**Epistemic status**: CONJECTURED. Mathematically grounded but economically untested.

---

## TENSION Entries Analysis

### T1: Coupling Constants -- Fixed vs. State-Dependent (Row 7)

**The tension**: In sociophysics, J_ij is fixed (Ising), random-frozen (spin glass), or slowly evolving (adaptive networks). In transformers, J_ij depends on the current state at every time step. The composition requires explaining why this difference is either (a) economically irrelevant or (b) economically meaningful.

**Resolution path**: Argue that state-dependent couplings are more economically realistic. The sociophysics assumption of fixed J was a simplification that the transformer mapping corrects. This is the resolution proposed in Row 19 (NOVEL entry).

**Risk**: If we adopt state-dependent J, much of the established spin glass machinery (replica method, cavity method) may not directly apply. New tools (dynamical mean-field theory, kinetic Ising) are needed.

**Epistemic status**: ESTABLISHED as a tension. Resolution via the NOVEL interpretation is CONJECTURED.

### T2: Entropy Definition (Row 15)

**The tension**: Three competing definitions of economic entropy exist in the literature:
- Chater-MacKay: allocation multiplicity (log of number of microstates consistent with macrostate)
- Smith-Foley: dual of utility, related to the Legendre structure of potentials
- Georgescu-Roegen: physical entropy as consumed by economic processes

The transformer has a clear entropy (of the attention distribution). Which economic entropy does it map to?

**Resolution path**: The attention entropy most naturally maps to Chater-MacKay's allocation multiplicity, since both measure the "spread" of a probability distribution. The Smith-Foley entropy may correspond to a different quantity (the entropy of the weight/coupling distribution rather than the attention distribution). Georgescu-Roegen's entropy is the physical entropy consumed by computation -- relevant but on a different level.

**Risk**: If the definitions cannot be reconciled, the bridge becomes equivocal about a fundamental quantity.

**Epistemic status**: CONJECTURED. The reconciliation requires careful mathematical work.

### T3: Temperature Definition — RESOLVED by methodological commitment; two consistency checks remain

**The resolution**: The spin transformer Hamiltonian defines the microscopic temperature. Following the project's core methodology — the Hamiltonian is the source, the economy is the target — temperature is the softmax/Boltzmann scaling parameter tau:

P(i) = exp(x_i / tau) / Sigma_j exp(x_j / tau)

This definition is established independently on both sides of the bridge:
- **Bal (2020-2023)**: tau is the thermodynamic temperature of the spin system implemented by the transformer. [ESTABLISHED]
- **Sornette (2014)**: The identical parameter appears as the rationality/noise parameter in the logit discrete choice model, which IS the Boltzmann distribution applied to economic choice. [ESTABLISHED]

Bal and Sornette arrive at the same equation from different starting points (spin physics and econophysics respectively). The definition is microscopic, operational, and measurable from choice data for any agent population.

**The hierarchy** (not three competing definitions, but one definition and two consistency checks):
1. **DEFINITION**: tau from the softmax/Boltzmann/logit (Bal + Sornette). Microscopic, operational, measurable.
2. **CONSISTENCY CHECK 1 (Phase 2)**: Does Chater-MacKay's macroscopic "inverse marginal utility of money" reduce to tau in the thermodynamic limit? In standard stat mech, micro-T and macro-T are provably identical (content of the zeroth law). If this holds for the economic setting, consistency. If not, Chater-MacKay describes an Ising-class economy with different thermodynamics — itself a prediction.
3. **CONSISTENCY CHECK 2 (Phase 2)**: Is Yakovenko's <m> (average money per agent) proportional to tau under appropriate assumptions? This is analogous to <KE> ~ T in the ideal gas — an observable proxy, not the definition.

**Remaining risk**: If consistency check 1 fails, the Carnot efficiency formula from Chater-MacKay does not transfer directly to the novel theory's context. The Carnot claim would then need to be re-derived from the microscopic tau rather than inherited from the macroscopic framework. This is a significant but well-posed task for Phase 2.

**What this resolves for the Carnot engine (Rows 29-30)**: T_H and T_AI are now well-defined as the softmax/logit temperatures measurable from human and AI choice behavior respectively. The Carnot formula eta = 1 - tau_cold/tau_hot becomes a specific, testable prediction. The mesooptimizer audit's concern about "three incommensurable definitions" is addressed: there is one definition (with established precedent in both physics and econophysics) and two open consistency checks.

**Epistemic status**: DERIVED (the definition follows from the Hamiltonian and has independent support from Sornette). The consistency checks are CONJECTURED and scheduled for Phase 2.

### T4: Saddle Point vs. Minimum (Row 37)

**The tension**: The transformer converges to a saddle point of the mean-field free energy, not necessarily a minimum. Physical equilibrium is a free energy minimum. If the economy sits at a saddle point, it is stable in most directions but unstable in some -- a fundamentally different stability profile.

**Resolution path**: Argue that real economic equilibria ARE saddle points: stable to most perturbations but unstable to specific ones (financial crises, technological disruptions). The saddle-point interpretation may be a feature, providing a physics basis for observed economic fragility.

**Risk**: Saddle points may be quantitatively unstable in ways that real economies are not. Or the saddle-point interpretation may be an artifact of the mean-field approximation (the true equilibrium may be a minimum when fluctuations are included).

**Epistemic status**: CONJECTURED.

### T5: Heterogeneity as Disorder vs. Gradient (Row 32)

**The tension**: Bouchaud et al. treat agent heterogeneity as quenched disorder -- something to be averaged over using replicas. The novel theory treats the same mathematical structure as a thermodynamic gradient -- something to exploit for value creation. These are different uses of the same math.

**Resolution path**: The distinction is between averaging over and conditioning on the heterogeneity. The standard spin glass approach computes [F] = -T[log Z]_J (average free energy over disorder realizations). The novel theory needs to compute F(J_human, J_AI) -- the free energy conditional on the specific two-population structure, not averaged over it.

**Risk**: If the gradient interpretation requires a new calculation (not just a reinterpretation), the established spin glass results cannot be directly inherited. New derivations are needed.

**Epistemic status**: CONJECTURED. The reinterpretation is the project's core conceptual move. Whether it generates new predictions (beyond what the standard disorder framework already provides) is the key test.

---

## What the Table Cannot Map: Explicit Limitations

### 1. Production, Consumption, and Labor

The entire thermodynamic/spin framework -- on both the Ising and transformer sides -- describes exchange and interaction, not production. The Hamiltonian conserves spin number; the economy does not conserve goods (production creates, consumption destroys). Chater and MacKay explicitly leave production for future work. The FFN-as-production identification (Row 34) is a promising start but remains CONJECTURED.

**Impact**: The theory cannot currently answer "what economic value does human-AI interaction CREATE?" -- only "how does value FLOW between populations." This is a fundamental limitation that Phase 2 must address.

### 2. Money as a Medium of Exchange

There is no natural spin analog for money -- a universal medium of exchange that is not a "good" itself but facilitates transactions. Yakovenko's conservation-of-money law provides a bridge, but it is approximate (money is created by credit) and does not appear in the spin transformer mapping.

**Possible resolution**: Money may correspond to the external field h or to the "auxiliary field" introduced by the Hubbard-Stratonovich transformation. Neither is fully satisfactory.

### 3. Innovation and the Expanding State Space

Kauffman's objection: the economic state space is not fixed. New goods, new technologies, new strategies are continually created. The spin model has a fixed Hamiltonian on a fixed lattice. The transformer has a fixed architecture processing variable inputs, but the architecture itself does not change. There is no natural mechanism for expanding the state space within the mapping.

**Impact**: The theory can model economies with a fixed set of goods/strategies but not economies that innovate. This is a serious limitation for any theory that claims to address the AI transition.

### 4. Time and Dynamics at Multiple Scales

The transformer forward pass maps to a single timescale (mean-field iteration). Real economies operate at multiple timescales: high-frequency trading (milliseconds), business cycles (years), institutional change (decades), technological paradigm shifts (centuries). Li et al.'s weight-space spin glass provides a second timescale (training = institutional evolution), but the full multi-scale structure is not captured.

### 5. Welfare Normative Claims

The mapping connects physical quantities (energy, entropy, temperature) to economic quantities (wealth, allocation multiplicity, marginal utility). But physics is descriptive; economics is also normative. The theory cannot, by itself, answer "should we slow the AI transition?" -- it can only compute the thermodynamic costs and benefits under specific definitions. The choice of which "temperature" matters, and whether Carnot efficiency is the right optimization target, requires normative commitments external to the physics.

### 6. The Hamiltonian Is Not Given

In physics, the Hamiltonian is determined by nature. In economics, we write down a Hamiltonian and check if it reproduces observations. There is no guarantee that the "correct" economic Hamiltonian exists, is unique, or is discoverable. The spin transformer Hamiltonian is a specific proposal whose validity is empirical, not a priori.

### 7. Finite-Size Effects

Most results in the table hold in the thermodynamic limit (N -> infinity). Real economies have finite numbers of agents, and the largest economic entities (governments, multinational corporations, central banks) can individually influence the system -- violating the mean-field assumption. The theory of finite-size corrections in spin systems exists but has not been adapted to the economic context.

---

## Summary Statistics

- **Total rows**: 39
- **CLEAN**: 22 (rows 1-6, 8-14, 16-17, 21-22, 24-27, 31, 33)
- **TENSION**: 5 (rows 7, 15, 32, 37, plus temperature ambiguity pervading row 2)
- **NOVEL**: 10 (rows 18-20, 23, 28-30, 34-36, 38)
- **GAP**: 2 (rows 29 partially, 39)

The 22 CLEAN entries provide a solid foundation. The 10 NOVEL entries are where the new theory lives -- each represents a feature of the transformer that has no standard Ising analog and requires a direct economic interpretation that this project must develop. The 5 TENSION entries are the theoretical challenges that must be resolved for the bridge to be rigorous.

---

*Compiled from Phase 1 reading notes. All claims labeled by epistemic status per project guidelines.*
*Central artifact of the Economics 2.0 Research Program.*
*Next step: Phase 2 toy model should test the NOVEL entries, starting with rows 29-30 (Carnot engine between two spin populations).*
