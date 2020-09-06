HSYNC Re-generation circuit

This circuit is based on (and very close to being a 100% copy of) Renesas Technical Brief 476
(tb476) associated with the ISL59885 sync-separator IC.

The basic idea is that some sync signals (looking at you SEGA Master System) do not adhere to
"proper" sync waveform, mainly meaning that during VSYNC, HSYNC is completely missing. This
will usually show itself as a "skew" in the top (or even more) of the video image, as the PLL
circuit of the monitor loses lock to the horizontal sync, and has to re-acquire it after each
vertical sync. To avoid this, creating a re-generated horizontal sync signal, derived from
the original, but ever-present, is the key. This circuit does this completely through discrete
components, and at the same time allows for HVSYNC, as the ISL59885 outputs both HSYNC and
VSYNC as separate signals. Should work for both CSYNC and Sync-on-Green (Y of YPbPr) signals
(latter untested).

This should be especially useful for monitors that show (excessive) flagging (like Sony BVM-A,
BVM D9/D14 or JVC DT-V monitors).

Jumper descriptions (looking at component side, BNC outputs to right):

JP2 Input is 75 Ohm terminated (down) or not (up).

JP3 Source signal is passed directly to the output (up) or the sync stripped version (down).

JP4 HSYNC output is HSYNC (right) or CSYNC (including the regenerated HSYNC) (left).

For a complete description, read the technical brief, which is available on Renesas' website
under "Documents" section for the ISL59885.

Attach CSYNC (or Y/G) to the input, and connect HSYNC and VSYNC to monitor (or JP4 set to CSYNC
and then HSYNC (now CSYNC) to monitor sync input). Board needs to powered by 5V from USB or
through J6.

(2020) Martin Hejnfelt (martin@hejnfelt.com)
