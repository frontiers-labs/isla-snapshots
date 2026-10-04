# Isla snapshots

Sail models compiled to Isla IR, pinned by commit from
[TIR](https://github.com/frontiers-labs/tir)'s `xtask/verify/<isa>.toml`.

## x86.ir

Translated from the ACL2-derived `sail-x86-from-acl2` model: the `x86.ir`
target of its `model/Makefile`, spliced with
`test-generation-patches/isla_footprint.sail`.

The IR differs from that translation where the model disagrees with the
Intel SDM:

- `ror_spec_8/16/32/64`: for a count above 1, CF is the top bit of the
  result. The model took bit 0.
- `x86_cmps`: the flags come from `[RSI] - [RDI]`. The model subtracted in
  the other order.
