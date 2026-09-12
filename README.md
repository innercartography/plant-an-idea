# Plant an Idea

A way to stand in front of a vacant storefront, say what it should become,
and find out which ideas other people actually agree with.

Built at **Building for SF**, a civic buildathon hosted by Abundant Leaders SF
with the Office of Economic and Workforce Development, SITELAB urban studio,
Vacant to Vibrant (SF New Deal), and the Civic Joy Fund — September 11–12, 2026.

Demo parcel: **225 Bush Street**, the ground-floor retail of the old Standard
Oil Building.

## The claim

Ideas are not the bottleneck. OEWD said so directly: vacancy taxes, incentives
and public acquisition do not move the needle. What stops activation is lease
execution, insurance, permitting, code upgrades, and owners who are cautious
about an unfamiliar tenant.

So this produces something different — **evidence that a block will welcome an
unusual use**, so an owner or broker can stop treating it as a risk.

## How it works

1. **Identify the parcel** — scan a QR in the window, type an address, or
   upload a spatial scan.
2. **Plant an idea** on a real surface in the space.
3. **Agree, disagree, or plant your own.** No replies. Taken from Polis, the
   tool behind Taiwan's vTaiwan process. What rises is what several people
   wanted across different groups, not what one person argued hardest for.
4. **Online before you call.** Every constraint carries two steps — what you
   can look up yourself, and who to ring once the public record runs out. The
   call only unlocks when the online questions are done.
5. **Tend it.** Answers go on the record with your name. The next person
   planting something similar starts from your answer.

## Design rules

- **Never invent a rule.** If a constraint cannot be cited to the parcel
  record, the response returns `unknown` and routes to a human.
- **No verified number, no number.** Agencies without a confirmed contact say
  so and link to a lookup. This tool does not guess phone numbers.
- **No motive inference.** The system never tries to work out *why* someone
  said what they said. Agreement does the sorting.
- **Every fact carries where it came from and when.**

## Accessibility

The spatial view is one representation, not the data. The same record renders
as a plain list, and entries can be relayed by someone with a tablet or a paper
form — marked `relayed` on the record. No account, no residency test.

## Running it

It's a single static HTML file. Open `index.html`. No build step, no server.

### Optional: Supabase

Set two constants near the top of the script:

```js
var SUPABASE_URL = "https://xxxx.supabase.co";
var SUPABASE_ANON_KEY = "<publishable anon key>";
```

Use the **publishable/anon key only** — never the service role key. Leave blank
to run fully in memory. Schema is in the Agent view.

## Agent surface

```js
PlantAnIdea.match("food access and community kitchens")  // ranked repos
PlantAnIdea.state()                                      // full graph as JSON
PlantAnIdea.plant("an idea", { by: "me" })               // returns a repo id
PlantAnIdea.schema()                                     // Supabase DDL
```

Repos are addressed as `parcel/225-bush/idea/<n>`. A JSON-LD manifest in the
document head points at this API.

## Modes

- **Step view** — one section at a time, arrow keys or the bar at the bottom.
- **Present** — a twelve-slide deck, three slides live from current state.
- **3D graph** — the knowledge graph in three topologies. Loads Three.js from a
  CDN; falls back to the offline plan view if that fails.
- **Agent view** — the machine-readable state and the interest matcher.

## Data sources

- SF Property Information Map — https://sfplanninggis.org/pim/
- DataSF — https://datasf.org/opendata/
- CivLab Republic — https://republic.civlab.org/

## Status

Prototype. Parcel facts marked `VERIFY` still need confirming against the
Property Information Map.

---

Michael Lopez · [innercartography.one](https://innercartography.one) ·
[linkedin.com/in/miiike415](https://www.linkedin.com/in/miiike415)
