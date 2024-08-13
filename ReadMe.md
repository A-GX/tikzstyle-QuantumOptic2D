# Tikzstyle: Quantum Optic 2D

## Abstract
-   This style has originally been thought to draw schemas of QKD implementations, it will thus likely lack symbols for other uses (even for QKD, it probably is not complete). Feel free to propose new Nodes that you feel are missing (see "How can you help?" section), I will try to react reasonably fast.
-   This style is inspired by FIG. 1. in [Preparing a commercial quantum key
distribution system for certification against implementation loopholes, Vadim Makarov et al](https://arxiv.org/abs/2310.20107). (In particular, the example picture is a copy of the above-mentioned schema).
- Feel free to use WITHOUT giving credits, it might however slow down the development process
(I am not planning to work full-time on it)
- If you know of other open-source/collaborative tikzstyles like this one (independently of the field), please let me know. I will happily reference them.

## Documentation
You can see all nodes (out of context and with default argument values) in `List-Nodes/list.pdf`. In use example can be found in `Example/fig-alone.pdf` and `Example/scale-fig.pdf`.
### Calling Nodes
- normal calling: 

        \pic at (x,y) {name_node={arguments}};
- if you want to change line color in node (to get a PBS from a BS for example) : 

        \draw[red] (x,y) pic {name_node={arguments}};
- if you want only on of, say 3, arguments, use : 

        \pic at (x,y) {name_node={arg1,,}};
### Position on wire
Given (x,y) the position of the end (or start) of your wire, the nodes need to be placed as follows:
- Laser : (x+.5,y) -> (x-.5,y)
- IM, PM, VOA, Att : (x+.5,y) -> (x-.5,y)
- connector, rotator: (x+.1) -> (x-.1)
- DWDM: (x+.85,y±1) -> (x-.5,y±1)
- DWDdM: (x+.5,y±1) -> (x-.85,y±1)
- BS: (x+.6,y±1) -> (x-.6,y±1)
- half-mirror, faraday-mirror: (x+.05,y) -> (x-.05,y)
- isolator: (x+.2,y) -> (x-.2,y)
- terminator: (x+.1,y) -> (x-.1,y)
- symbols for *Quantum Canal* and *polarisation controllers* needs to be placed **on** a wire. The coordinates given when printing those nodes are the middle of the nodes, that are both of length `.8`.

### Node Invocation and Arguments
You can pass arguments to specify the name of the node or specify the settings of your devices. Here, we detail the arguments for all defined nodes. If you want to let the default arguments, call using the name of the Node only.
- Laser: `laser={laser,1548.51mm,(ch. 36)}`
- Detectors: `detector={$d_1$,$d_2$}`
- Special Detectors: `spe-detect={Pwm,SD}`
- Intensity Modulator: `im={IM}`
- Phase Modulator: `pm={PM}`
- Variable Optical Modulator: `voa={VOA}`
- Attenuator: `att={Att,20 dB}`
- Connector: `connector`
- Rotator: `rotator={R,$45^\circ$}`
- Multiplexer: `multiplex={DWDM,Ch. 36,Ch. 26}`
- De-Multiplexer: `de-multiplex={DWDdM,Ch. 36,Ch. 26}`
- Half-mirror: `half-mirror={$\frac{1}{2}-mirror$,R}`
- faraday-mirror: `faraday-mirror={FM}`
- Beam Splitter: `bs={BS,R}`
- Isolator: `isolator={Iso,28 dB}`
- Terminator: `terminator={T}`
- Quantum Canal: `qc={QC}`
- Polarisation Contoller: `pc={PC}`

## Advices
- Using the default node size might output a picture a bit too big for your needs, in this cas scale **The whole tikz picture** using 
    
        \begin{tikzpicture}[scale=.65, every node/.style={scale=.65}]
        
- When using with beamer, do not forget to use a `fragile` frame environment!

## How can you help ?
### Missing Nodes
1. Open an "enhancement" issue, describing the node that is missing Node
2. Submit the tikz code for a missing node in its dedicated issue. Please specify its positioning on the wire, as well as its arguments so that I can add it easily to the documentation.
    -   Requirements for new symbols/nodes: Except for devices acting on multiple beams, the name has to be placed above the symbol `node[above] at (0,.35) {#name}` and the properties (when needed) below as `node[below] at (0,-.35) {#properties}`.
    - Ideally, let most of the text of your node be a parameter with default value.
    - Try to keep a graphical coherence when introducing new nodes  
3. Your git-hub username will be added to the list of collaborators

### Missing functionalities
1. Open a "functionality" issue, describing what node is missing what.
2. Submit a tikz code solving the issue. If needed, specify new positioning and arguments as well.
3. Your git-hub username will be added to the list of collaborators.

### Better Documentation
1. Submit change by opening a "Documentation" issue