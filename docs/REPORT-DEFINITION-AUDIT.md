# Report-definition audit — 3 November 2026

Inspected the published reviewed PBIX archive directly, including all 14 visual definitions. This is a static configuration audit, not a new execution of the data model.

- Five slicers reference Age, ChestPain, Cholesterol_Level, Resting Blood Pressure and Gender.
- The count card counts non-null Age values. It must not be interpreted as a distinct patient count without a unique patient identifier and missing-value checks.
- The age card uses the Median aggregation, despite a legacy queryRef containing Sum. Native query labels and field expressions must be considered together.
- The resting-BP gauge uses Median and has a minimum visual calculation fixed to 94. That lower bound needs validation against the intended range and filter context; it is not a verified clinical threshold.
- The cholesterol gauge uses Median, with model measures supplying its bounds.
- The chest-pain donut counts non-null ChestPainType entries. Missing labels could change its denominator.

The raw source, data dictionary and reproducible model exports remain unavailable in this repository. No new population statistics or clinical findings can be responsibly added from visual configuration alone. Full DAX execution, source reconciliation and interaction testing remain open.
