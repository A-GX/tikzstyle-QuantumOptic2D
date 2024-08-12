# Tikzstyle: Quantum Optic 2D

## Abstract
Style inspired by FIG. 1. in "Preparing a commercial quantum key
distribution system for certification against implementation loopholes" by
Vadim Makarov et al. (In particular, the example picture is a copy of the above-mentioned schema).

If you want to participate in the development of this tikzstyle, please open
an issue describing what is missing, I will try to open a development branch
as fast as I can (and see the issue).

Feel free to use WITHOUT giving credits, it might however slow the development
(I am not planning to work full-time on it)

## Documentation
You can see all nodes (out of context and with default argument values) in `List-Nodes/list.pdf`. In use example can be found in `Example/fig-alone.pdf` and `Example/scale-fig.pdf`.
### Calling Nodes
- normal calling: `\pic at (x,y) {name_node={arguments}};`
- if you want to change line color in node (to get a PBS from a BS for example) : 
    `\draw[red] (x,y) pic {name_node={arguments}};`
- if you want only on of, say 3, arguments, use : `\pic at (x,y) {name_node={arg1,,}};`
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

### Arguments
You can pass arguments to specify the name of the node or specify the settings of your devices. Here, we detail the arguments for all defined nodes.
    
    **TO DO**

## Advices
- Using the default node size might output a picture a bit too big for your needs, in this cas scale **The whole tikz picture** using 
    -   `\begin{tikzpicture}[... local style ..., scale=1, every node/.style={scale=...}]`

