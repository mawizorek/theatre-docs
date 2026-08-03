---
id: oph-circuits
title: Circuits and dimmers
type: reference
status: public
parent: ogunquit-playhouse
order: 10
maintainer: Master electrician
revised: 2026-08
data:
  - circuits-and-dimmers.tsv
---

# Circuits and dimmers

The rack schedule: every soca run out of the three dimmer racks and the two ML
panels, what it is called, and where it lands.

This is the reference you trace backwards from a dead fixture. Find the circuit
number, read the rack letter, and the colour column tells you which loom to
follow in the rack itself.

## Reading it

**The rack rows are section breaks, not records.** `RACK 1`, `ML PANEL 2` and
so on divide the sheet; everything under one belongs to it until the next.

The first column stays put when you scroll sideways, and so does the header, so
a value eight columns to the right still tells you what it is and which circuit
it belongs to. On a phone, swipe the table rather than turning it.

!!! warning "Blanks mean unknown, not empty"

    A blank destination is a run nobody has traced, not a run that goes
    nowhere. `No Soca` in the notes column is different and does mean what it
    says: the dimmer exists in the rack with no soca run out of it.

<!-- dr:table circuits-and-dimmers.tsv -->

## Related

- [Where the dimmers run](@oph-dimmer-runs), the field survey that checks this
  schedule against what is actually patched
