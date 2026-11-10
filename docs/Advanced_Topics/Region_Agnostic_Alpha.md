# Region Agnostic Alpha

_Section: Advanced Topics | page id: region-agnostic-alpha_

# Introduction

Region Agnostic Alpha (RAA) is a new Alpha research methodology that involves simulating an Alpha across multiple regions in a **single simulation** (GLB, USA, ASI, EUR). The primary benefits are:

- **Robustness**: If a signal demonstrates efficacy across multiple regions, it indicates strong statistical significance and broad coverage, thereby enhancing robustness and reducing the likelihood of overfitting.
- **Flexibility**: Should a signal prove effective only in specific regions, the Alpha can be adjusted accordingly to target those regions.

The expression structure is identical to standard fast expressions; the principal distinction is that data fields in a Region Agnostic Alpha are translated into GLB, USA, EUR, and ASI Alphas. A Region Agnostic Alpha may be submitted if it performs acceptably in **two or more regions**.

## Parent / child structure

A single RA simulation produces one **RA Parent** Alpha and up to 4 **RA Child** Alphas (one per region: Alpha (USA, EUR, ASI, GLB) → RAAlpha):

- Alpha properties (name, description, etc.) are held at the parent level; RA Child Alphas inherit the parent's description (updating the parent's description updates all children).
- Individual RA Child Alphas can still be cloned and worked on as regular Alphas.
- RA Child Alphas can be used in super Alphas (treated like regular Alphas).
- We suggest submitting through RAA instead of submitting the regions separately as individual Alphas, where possible.

To simulate a RAAlpha, on Simulation page use the '+' button and choose 'New Region-Agnostic Simulation':

![image]({"title": "Region Agnostic Simulation", "width": 1699, "height": 597, "fileSize": 49518, "url": "https://api.worldquantbrain.com/content/images/9gdVoL-8DfD_r71igBl540RdAus=/464/original/region-agnostic-simulation.png"})

# Simulation Settings

## Compatibility constraints

- **Delay**: D1 only.
- **Universe**: requires the special RA universes — SMALL, MEDIUM, **LARGE** (see mapping below).
- **Max-trade / max-pos** (max-pos and max-trade cannot both be ON simultaneously): - If max-trade OFF, max-pos OFF → ASI automatically runs with max-trade ON. - If max-trade ON, max-pos OFF → ASI stays max-trade ON. - If max-trade OFF, max-pos ON → ASI uses max-pos ON and max-trade OFF.

Rationale: max-pos also captures an investibility constraint, which is sufficient for the original purpose of ASI's max-trade test.

## Universe mapping

The RA universe setting maps to the following per-region universes:

```json
{
  "type": "TABLE",
  "value": {
    "data": [
      [
        "RA Universe",
        "ASI",
        "EUR",
        "GLOBAL",
        "USA"
      ],
      [
        "LARGE",
        "MINVOL1M",
        "TOP2500",
        "MINVOL1M",
        "TOP3000"
      ],
      [
        "MEDIUM",
        "MINVOL10M",
        "TOP1200",
        "MINVOL10M",
        "TOP2000"
      ],
      [
        "SMALL",
        "TOP500",
        "TOP800",
        "TOPDIV3000",
        "TOP1000"
      ]
    ],
    "cell": [],
    "firstRowIsTableHeader": true,
    "firstColIsHeader": true,
    "tableCaption": ""
  },
  "id": "ce067ad4-90a9-4bb4-b49c-e02a86553112"
}
```

## Data field rules

An expression may reference fields whose region coverage does not fully overlap; the simulation runs on the **intersection** of the regions: - abc_usa_asi * xyz_glb_eur → fails: no intersecting regions ("Region agnostic simulations must have more than one region"). - abc_usa_asi * xyz_usa_eur → would produce only a USA simulation, so it also cannot run as RA (RA requires more than one region). It is recommended to work on fields that are present in multiple regions, and preferably to focus on one dataset at a time.

# Submission Tests

At least 2 RA Child Alphas need to pass all of the following tests:

- Standard Sharpe test: Sharpe >= 1.58
- Standard Fitness test: Fitness >= 1.0
- 2Y ladder Sharpe test: 2Y ladder Sharpe >= 1.58
- Sub-universe Sharpe test
- Self correlation test
- ASI-specific: - Max-trade forced ON

**Prod correlation** is tested at the RA Parent level: assuming >= 2 RA Child Alphas already pass the criteria above, if **all** of them fail prod correlation, the RA Parent is un-submittable; otherwise, all passing RA Children are submitted

## Alpha Classification

- An RAA can be an **Atom** and a **Power Pool** Alpha.
- Some RA Children might pass and some fail the IS ladder test, leading to different classifications across children — this is expected.

## Quota Management

```json
{
  "type": "TABLE",
  "value": {
    "data": [
      [
        "Quota",
        "Treatment"
      ],
      [
        "Submission quota",
        "Treated as 1 regular Alpha (consumes only the RA Parent submission, not\n  the children)"
      ],
      [
        "Concurrent simulation quota",
        "Counts the sum of RA Child Alphas' concurrent quota"
      ],
      [
        "Daily simulation quota",
        "Counts the number simulated RA Child Alphas"
      ]
    ],
    "cell": [],
    "firstRowIsTableHeader": true,
    "firstColIsHeader": false,
    "tableCaption": ""
  },
  "id": "856459cb-c685-4326-b2e6-1e2150efd479"
}
```

## Genius Stats

```json
{
  "type": "TABLE",
  "value": {
    "data": [
      [
        "Stat",
        "Treatment"
      ],
      [
        "Signals",
        "Counts RA Child Alphas"
      ],
      [
        "Combined Alpha performance",
        "Counts submitted RA Child Alphas"
      ],
      [
        "Operators and fields per Alpha",
        "1 Alpha (considers only the RA Parent Alpha)"
      ],
      [
        "Signal and pyramid count",
        "Considers submitted RA Child Alphas only"
      ]
    ],
    "cell": [],
    "firstRowIsTableHeader": true,
    "firstColIsHeader": false,
    "tableCaption": ""
  },
  "id": "3d1ab85e-26d6-4462-8d3e-2d91ec1efc9e"
}
```

## Pyramids

- **Pyramid Alpha distribution**: on submission, each submitted RA Child is added to its pyramid.
- **Alpha distribution**: each submitted RA Child is added to the distribution.
- **Pyramid theme multiplier**: the RA Parent takes the **max of** **submitted all RA Children**. Viewing the parent's submission check shows the max child multiplier if a child cannot be submitted, the max over submittable children is shown. On submission, the max of the submitted children's theme multipliers is recorded against the parent, and each child's multiplier is recorded against that child.

## Theme multiplier combination

- **Regular themes (non-pyramid)**: all submitted RA Child theme multipliers are combined, and the standard formula is then applied:
(**sum**(**multipliers**) - len(**multipliers**) + 1)
- **Pyramid theme multiplier**: the max child pyramid multiplier is added to the formula as one more multiplier. For example, if RAAlpha-USA matches a pyramid with multiplier 1 and RAAlpha-ASI matches a pyramid with multiplier 1.5, then 1.5 is added into the formula's multipliers.

## Osmosis Points

- Osmosis points apply to submitted **RA Children only** — the RA Parent cannot be combined into a combo, so points cannot be allocated to the parent.

# Tips for Success

- Exercise caution when conducting cross-sectional data comparisons, as inconsistencies may arise in currency units, market capitalization scales, and stock face values. Resolve these either by normalizing values by their respective scales or by using time-series comparison operations to standardize units.
- If a Region Agnostic Alpha proves difficult to satisfy submission criteria across two or more regions, optimization on individual regions remains a viable alternative.
- Signals discovered in the GLB region can serve as an effective starting point.
