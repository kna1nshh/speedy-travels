# Speedy Travels

UK DMC plus travel design and booking platform. Planning stage: no code yet.

## Start here

Read `docs/speedy-travels-brief-and-research.md` before any work.

- Section 3: the owner's full brief. It is the source of truth.
- Section 4: research from chat 1 (Awwwards sites, competitors, Mobbin patterns).
- Section 5: proposed legal checks, stack and build order. Not agreed yet.

## Rules from the brief

- Design around the trip, not hotel search.
- Recommend a few options and explain why. Keep raw scores internal.
- Static data is not proof of live price, availability, opening hours or weather.
- Hierarchy: Country → Region → Destination → Base → Experience → Product → Supplier. UK is Country 001.
- Keep legacy Speedy IDs on imported records. The seed workbook goes in `data/`.
- A trip cannot show "Confirmed" while a critical item is unconfirmed.

## Working style

- Short answers. No em dashes.
- Show the plan before large changes. Ask only when the decision belongs to the owner.
