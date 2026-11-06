---
name: hardware-design
description: "Rules and a send-checklist for designing physical products a factory will build: structure, joints, fasteners, boards and sheet, CAD, 2D drawings, BOM. Use before and during any hardware design, CAD, drawing or BOM work, and before sending anything to a factory."
---

# Hardware design

These rules come from a factory's senior engineers reviewing our designs, and from their engineering guideline
(`references/engineering-guideline.vi.md`, in Vietnamese; the § numbers below point into it). They hold for every
hardware product. A product's own repo (its AGENTS.md) adds rules for that product only.

## How to work

1. **Before you start**, read the product's own plan and AGENTS.md, then the parts of the guideline that cover what
   you are changing. Answer your own questions from them before asking anyone.
2. **Pick the checklist lines that apply** to the change, and design to them from the start.
3. **Before you send**, go through the whole checklist line by line. Send the filled-in list with the files: for each
   line, say done, not needed (and why), or open (and who decides).
4. **When you ask the engineer about a place on the model**, send a screenshot with that place marked, not only words.
   (2026-11-05, GaragePod: a question asked in words alone wasn't understood.)
5. **After any feedback** from the factory or the team, add the lesson the same day, with its date and the case that
   taught it. A lesson for any product goes into this skill (send a pull request to its repo). A lesson for one
   product goes into that product's AGENTS.md. Post the new line where the feedback came from, so its author can
   fix your wording.

A new session knows only what is written down. A lesson that isn't written here is lost.

## Checklist

### 1. Read before you design

- [ ] Each part answers 7 questions (§1): what it is, where it goes, what it's made of, how it's made, what it joins,
      why it has that shape and those holes, and how it's checked.
- [ ] Work in this order (§1): what it must do, then the assembly, then the joints, then each part, then the cutting
      and checking data. Don't draw parts before the joint is settled.
- [ ] Use the joint the product's plan names. Don't invent another one.
- [ ] Start from the last proven version and change one thing at a time. Ask how it is really built before changing
      it.
- [ ] Keep the plan's design values exact (a 6° pitch, a 400 plate). When a derived position doesn't fit, change
      the part that follows from them, not the design value, and ask if unsure. (2026-11-05, GaragePod: we bent the
      fan-plate hole pitch to 5.96° to meet the bar's tip hole; the engineer kept 6° and moved the plate to follow
      the wood frame.)
- [ ] Before adding part variants, look for one shared datum, such as a common rotation centre, that lets parts be
      common. A design value can give way for that, but only the plan's owner decides. (2026-11-06, GaragePod: the
      engineer set one rotation centre 20 from both edges so all 12 frames and link plates are common, and dropped
      the exact 6° for an even split.)
- [ ] Re-check everything you inherit after each change. A reason that held before may not hold any more. (A wall
      2300 tall needed board joints; split in two, each panel fits one full sheet.)
- [ ] Research bought hardware before you model it (§4.3): the maker's own drawing for the exact model. Never draw
      an imagined part and find a real one later.

### 2. Parts and boards

- [ ] For each part, cut and hole, say why it exists. Use fewer parts, joints and fasteners wherever you can.
- [ ] Use full standard sheets (ply and board: 1220 × 2440) and avoid board joints. Never cut a board you don't need
      to cut.
- [ ] A large frame bay (about 1450 × 1000 or more) needs a middle member. Say which axis it runs on, and why.
- [ ] Wood and board parts (§9): say the board type, grain direction, cut list, jig or CNC step, and the glue and
      press order.
- [ ] Choose each material (wood species, board, glue, fastener) from the properties the part needs: compare the
      options and give the reason. Never just inherit it from the old version or "what the factory uses". (2026-11-05, FocusPod rev E factory review)
- [ ] Size cut parts to stock you can buy (standard timber sections, sheet sizes), to save cost and cut tolerances.
      Every size and spec carries its reason. (2026-11-05, FocusPod rev E factory review)
- [ ] Names follow the pattern assembly - part - position - variant (§4.2). Call a part COMMON only when its shape
      and machining are identical. File names are PARTNO_REV_NAME_DOCTYPE, never final, new or latest.
- [ ] Gaps between parts have a job (§7): looks, paint, expansion, seal squeeze, fit tolerance or removal. Give the
      smallest and largest allowed, and how to check it.

### 3. Joints

- [ ] Each joint ties the full frame section, not one face. A plate on one face links only that face, and the load
      path stays open. Put connectors across the full depth, for example on the member end faces.
- [ ] Each joint has a register row (§8): the two parts, its job and load path, the options compared and why this
      one, the exact fastener or glue, assembly order and tool access, how it can fail, and how to check it.
- [ ] Frame corners have a defined joint, for example glue plus screws, with the count and positions.
- [ ] A plate welded to a column sits flush with the column's edge, and the column has a slot as high as the plate
      is thick, to weld in. (2026-11-06, GaragePod base plate: it sat 2 off the edge; the engineer moved it flush and
      cut a 3 high slot.)
- [ ] Glue joints have a spec (§8.2): which glue, both surfaces, surface prep, coverage or bondline thickness,
      pressing and cure time.
- [ ] Name the glue yourself, from the properties the joint needs (load, moisture, heat, cure, the two materials).
      Never write "the factory's usual glue". (2026-11-05, FocusPod rev E factory review)
- [ ] Give each glue joint a quantity budget (grams per panel), and show it still holds: spread or bead pattern,
      not a full gap fill by default. (2026-11-06, FocusPod rev F: a 1 mm full PU layer added 5.3 kg per wall; the
      factory set about 1 kg of glue per wall.)
- [ ] Don't use permanent glue where the joint must come apart for service (§8.2).
- [ ] For a fastening system (Velcro, clips, magnets), say how it attaches to each side and why it is the best
      option: long-term holding force, and no gaps where air or sound leaks. (2026-11-05, FocusPod rev E factory review)
- [ ] Work out the tolerance stack at each important joint, at both limits, not only the nominal size (§6.3).

### 4. Fasteners

- [ ] Show how every board is fixed: screws, glue, pilot holes and positions. A drawing with boards but no fixings
      is incomplete.
- [ ] Show how the product is fixed to the floor or the building, and ask if the plan doesn't say. (2026-11-05,
      GaragePod link plate: the base plate needed Ø7 holes for M6 screws into the floor.)
- [ ] Don't over-fasten. Each extra screw costs labour and parts and adds build error. Start from the proven
      version's counts.
- [ ] Put screws at the board's 4 corners first, 15–20 from the edges, then along the edges. If the corners aren't
      held, they curl.
- [ ] Each screw sits wholly in one board, at least 15 from its edge. A screw split across two boards joins nothing.
- [ ] Each screw is defined exactly (§8.1): standard, diameter × length, head, material and finish. Give the pilot
      hole in wood (diameter and depth), the edge distances and the thread engagement in the base.
- [ ] Model every fastener hole in the 3D at its standard size (ISO clearance or pilot), not only in the tables. (2026-11-05, FocusPod rev E factory review)
- [ ] Screws go into a base that is designed to hold them: wood, a block or an insert. Never into felt, soft lining
      or thin MDF (§8.1).
- [ ] Screws into wood need a pilot hole, the grain direction, edge distance and a pull-out check on the real
      material (§8.1). Torque comes from the joint's weakest base, not a steel bolt table.
- [ ] Each hole is drilled from a side that lets the next panel go on. A counterbore that opens on the next panel's
      mating face blocks it. Check every hole against the assembly order.
- [ ] Each fastener can be reached with the tool, in assembly order. No screw is driven into a closed cavity. A
      rigid joint in CAD doesn't prove a screw can be driven (§8.1).
- [ ] No two fasteners collide. Check tip-to-tip and head-to-head clearance analytically, not only by volume
      overlap.

### 5. Drawings

- [ ] 3D uses X, Y and Z. Each 2D view uses X and Y only, with its origin, positive directions and its mapping to
      the 3D axes written on the view (§3.3).
- [ ] Use first-angle projection, with its symbol on the sheet, and say which way each view looks (§3.2).
- [ ] Dimension edge to edge or centre to centre, from one datum, so each feature's start and end are defined.
- [ ] Dimension straight to hole centres on the view itself. Use no coordinate tables in place of dimensions, and
      no floating numbers.
- [ ] Measure from datums with baseline or ordinate dimensions, not chains that add up errors (§6.2). Don't give
      the same size twice as two controls.
- [ ] Each hole has a tag (H01 …), the face it is drilled from, its type (through, blind, counterbore, pilot), its
      size and depth, and the part it mates with (§6.2).
- [ ] Each hole position has a reason (§7): the mating part, load, edge distance or tool access. "Even spacing" or
      "as in the old model" is not a reason.
- [ ] A row with more holes than the parts it holds may be there for adjustment, so a part can move along it. Ask
      the hole row's job before you call it a drawing error or remove holes. (2026-11-05, GaragePod corner column: the
      15-hole rows on the fan plates let the slats change position.)
- [ ] Datums A/B/C are real faces you can clamp and measure (§6.3). Each controlled size has a tolerance, either its
      own or a stated general rule.
- [ ] Don't put ISO 2768-m on everything (§3.2). Wood, felt, glass and bonded panels need their own tolerances.
- [ ] Give true sizes, never bounding-box sizes (§6.1). For a bent sheet, give thickness, inside radius, angle and
      flange sizes.
- [ ] Draw real circles, centre marks, centre lines, hidden lines and hatching (§6.1).
- [ ] General rules go on a notes sheet; keep short notes next to their feature. Never shrink the font to fit: add
      a sheet (§6.1).
- [ ] For a change, send only the changed part's drawing pages and BOM rows, unless asked otherwise.

### 6. Files and checks

- [ ] Send an editable native CAD file with real sketches and parameters, plus the STEP exported from the same
      revision (§4.4). A STEP alone is not enough. Send it with every STEP, a resend
      included. (2026-11-05, FocusPod rev E: a STEP-only resend left the factory engineer with no sketches to edit.)
- [ ] CAD, drawings and BOM are the same revision and agree (§2.5). If they disagree, stop and fix the source. Never
      leave the factory to pick a file.
- [ ] The BOM matches the model part by part (§2.6). Check the counts, sizes and materials.
- [ ] Mark each number's status: confirmed, source, calculation, assumption or unverified (§10).
- [ ] Never write PASS without the method, conditions, file revision and result (§10). Physical tests stay PLANNED
      until they are done.
- [ ] A volume clash check can miss small clashes (§10). Add a minimum-clearance check, and check parts can go in
      and come out.
- [ ] Open the PDF at print size and check it: no overlapping text, nothing running off the sheet, and every
      dimension readable.
- [ ] Check file metadata (STEP author and organisation, PDF author) against the product's rules. Keep supplier
      quotes, margins and personal data out of anything public.
- [ ] Report short (§14): result and file links first, then what changed, what is on hold, and exactly what you
      need approved.

## Lessons log

New lessons go into the checklist above, each with its date and the case that taught it.

- 2026-11-02, FocusPod side wall split (rev A to rev D): the 14 lines on board fixings, full-section joints, drill
  direction, dimensions to centres, fastener counts, middle member, re-checking inherited sizes, full sheets, corner
  screws, screws inside one board, a reason for each part, answering from the plan first, and using the planned
  joint.
- 2026-11-05, GaragePod corner column: the line on adjustment hole rows.
- 2026-11-05, FocusPod rev E resend: the native file goes with every STEP.
- 2026-11-05, GaragePod wood frames: keep the plan's design values exact.
- 2026-11-05, GaragePod link plate: floor fixing, and marked screenshots with questions.
- 2026-11-05, FocusPod rev E factory review: materials chosen by analysis, stock sizes, glue named by properties,
  fastening systems on both sides, ISO holes in the 3D.
- 2026-11-06, GaragePod frames: a shared datum for common parts.
- 2026-11-06, FocusPod rev F: a glue quantity budget per panel.
- 2026-11-06, GaragePod base plate: flush plate and weld slot.
