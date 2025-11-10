# KiCAD ERC demos

Catastrophic schematics made to demonstrate why ERC exists, and how to use them.

Current KiCAD version used: V8

Also see exemple in [asynthosc](https://github.com/everedero/asynth2osc/tree/broken_erc).

## KiCAD ERC saving the day

* Get to know them!

### Mainstream ERC: the ones people really use
* Unresolved text variables and "software" bugs
* Issues with libraries
* "No connect" and no connect indicator

### Misunderstood ERC: are they really useful?
* Grid: not respecting the grid is a big trap
* 4 connection points: can be legit but can also be a graphical trap
* Footprints and footprints filters

### Really misundesrstood ERC: the connection matrix
* Some external components do not have pin types set: check and repair components

### For people who want several net names per net
KiCAD compiles nets and ends up choosing a single name per net in the netlist, aka internal
 representation of the schematics, the one you will find in PCB view.

This means that it does not like nets with several labels, it will randomly choose one, and
it will complain about that:
* Both uC2\_4 and GPIO35 are attached to the same items, GPIO35 will be used in the netlist

If the net connects to a bus, it will trigger issue because belonging to bus depends on the net.
With previous exemple, if the bus is uC2\_[0..5], uc2\_4 belongs to it but not GPIO35. However,
KiCAD decided to name the net GPIO35.
* GPIO35 graphically connected but not a member of a bus

If you want a diff pair, KiCAD also relies on net names, so the names have to be "toto\_P" and
"toto\_N" (or "toto+" and "toto-").
