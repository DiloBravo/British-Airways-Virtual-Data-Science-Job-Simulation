# Task 1: Lounge Eligibility Model

Forage BA Data Science task. The brief: BA needs to plan lounge capacity at Heathrow Terminal 3, but wants a model that works for future schedules, not one tied to specific flight numbers or aircraft.

## Approach

I grouped flights by three things that don't depend on a specific flight: haul length (Short/Long), arrival region (Europe, North America, Middle East, Asia), and time of day (Peak: Morning/Evening, or Off-peak: Lunchtime/Afternoon). That gave 8 categories, each with an assumed eligibility percentage for BA's three lounge tiers:

- **Concorde Room** – First Class, Premier cardholders, Gold Guest List
- **First Lounge** – Gold members
- **Club Lounge** – Silver cardholders, Club World passengers

Short-haul European hub routes score highest overall, since they're high-frequency business commuter routes. Peak-time flights score higher than off-peak within every region. Tier 1 stays small everywhere, since Concorde Room doesn't exist at T3 yet and its eligibility criteria are rare regardless of route.

## Files

- `Lounge_Eligibility_Lookup_Template_-_Task_1.xlsx` – the actual submission: lookup table + written justification
- `British_Airways_Summer_Schedule_Dataset.xlsx` – the flight schedule (10,000 flights) used to test the model
- `Task_1.ipynb` – applies the same lookup table to the full schedule in pandas, going beyond the sample the Excel task required

Note: GitHub's preview doesn't render this Excel file reliably. Download it to view both sheets properly.

## What the notebook found

Applying the model to all 10,000 flights showed two things:

- **Total demand is driven by flight volume, not route type.** Short-haul Europe Peak has the highest total estimated demand mainly because it has the most flights. Per flight, it's nearly identical to Long-haul North America Peak.
- **The model held up well against ground truth.** Built without looking at the dataset's actual eligibility figures, the estimates landed within roughly 10–20% of the real numbers across every category.
