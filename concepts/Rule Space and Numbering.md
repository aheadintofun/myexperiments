# Rule Space and Numbering

## Definition
The complete set of possible rewriting rules for [[Graph Rewriting Automata]], analogous to Wolfram's numbering system for elementary cellular automata. Each rule assigns an outcome (state + topology change) to every [[Local Configuration Space|local configuration]].

## Wolfram Numbering (Cellular Automata)
For elementary CA (binary states, 3-cell neighborhood):
- 8 possible configurations: 000, 001, 010, ..., 111
- Each maps to output: 0 or 1
- Rule = 8-bit string
- **Total rules**: $2^8 = 256$
- **Rule number**: Binary representation (e.g., Rule 110, Rule 30)

## GRA Extension
For binary-state GRA on $d$-regular graphs:
- $2^{d+1}$ possible local configurations
- Each configuration → (next state, topology change)
- State outcomes: 2 choices per configuration
- Topology outcomes: multiple choices (divide, stay, delete edge, etc.)

**Explosion**: Even with binary state/topology outcomes:
$$\text{Total rules} = 4^{2^{d+1}}$$

For $d=2$: $4^8 = 65{,}536$ rules (state + simple topology binary choice)

## Rule Classes

### By Behavior Type
Similar to Wolfram's CA classification:

**Class I: Fixed points**
- All configurations → uniform state
- Topology freezes
- Trivial behavior

**Class II: Periodic patterns**
- Repeating structures
- Stable cyclic growth
- Organized morphologies

**Class III: Chaotic growth**
- Unpredictable expansion
- Fractal-like boundaries
- No apparent structure

**Class IV: Complex/organic**
- **Most interesting for biology**
- Structured but not periodic
- Self-similar patterns
- See [[Organic Structure Emergence]]

### By Topological Operation
Rules classified by primary topology change:
- **Division-dominant**: Frequent vertex division → growth
- **Rewiring-dominant**: Edge addition/removal → reorganization
- **Deletion-dominant**: Vertex removal → pruning
- **Hybrid**: Mixed operations

## Enumeration Challenges
Exhaustive search intractable:
- For $d=3$, binary states: $4^{16} \approx 4.3$ billion rules
- Most rules uninteresting (trivial or explosive)
- Need intelligent sampling or evolutionary search

## Discovering Interesting Rules
Strategies:
1. **Random sampling**: Test random rules, filter by criteria
2. **Evolutionary algorithms**: Evolve rules toward target morphologies
3. **Biologically-inspired**: Encode known developmental programs
4. **Constraint-based**: Rules satisfying conservation laws, symmetries

## Rule Representation
Compact encoding:
```
Configuration → (Next_State, Topology_Action)
(s_v=0, N={0,0}) → (1, divide)
(s_v=0, N={0,1}) → (1, stay)
(s_v=0, N={1,1}) → (0, stay)
...
```

Alternatively: Truth table or Boolean function representation.

## Biological Correspondence
GRA rules ≈ **gene regulatory networks**:
- Configuration = cell state + neighbor signals
- Rule = genetic circuit output
- State change = differentiation
- Topology change = proliferation decision

See [[Developmental Toolkit]] for biological rule libraries.

## Related Concepts
- [[Graph Rewriting Automata]] - Framework using these rules
- [[Local Configuration Space]] - Domain of rules
- [[Cellular Automata Framework]] - Simpler rule systems
- [[Update Rule as Fundamental Unit]] - Algebraic primitive
- [[Organic Structure Emergence]] - Outcome of Class IV rules
- [[Chaotic vs Ordered Growth]] - Rule behavior classification
- [[Developmental Toolkit]] - Biological rule implementations

#graph-rewriting #rule-systems #automata #computational-complexity #classification #wolfram
