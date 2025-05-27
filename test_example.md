Test example.
===============

The survey intends to collect the price of ***RICE*** when sold in bags `2kg` to `5kg` range, and standardize it to a price per `1kg`.
It is anticipated that the price per kilo is around `25LCUs` (local currency units), with deviations plus/minus `30%`.
This price is supplied as a reference price and deviation as tolerance.

The interviewer observes ***RICE***

SCENARIO 1:
---------------

**INPUT:** 2 pounds cost 30 LCUs.

**OUTPUT:** Error. Observed quantity is out of range.

**EXPLAIN:** 2 LBS=0.907kg, which is less than 2kg minimum.

SCENARIO 2:
---------------

**INPUT:** 20 pounds cost 300 LCUs

**OUTPUT:** Error. Observed quantity is out of range.

**EXPLAIN:** 

- Determine conversion coefficient from LBS to KG: `0.453`
- 20 LBS is `(20*0.453)=9.07kg`
- Verify: 9.07kg is more than 5kg maximum.

SCENARIO 3:
---------------
**INPUT:** 10 pounds cost 150 LCUs

**OUTPUT:** warning that the price observed is too large.

**EXPLAIN:**

- Determine conversion coefficient from LBS to KG: `0.453`
- Normalize quantity to kg: 10 pounds is `10*0.453=4.536kg`
- Calculate price per normalized unit: `150/4.536=33.07 LCU per kg`
- Calculate the price ratio of observed vs reference price: `33.07/25=132.28%`
- Verify: `132.28%>(100%+30%)`

SCENARIO 4:
---------------

**INPUT:** 10 pounds cost 120 LCUs

**OUTPUT:** price accepted without any error or warning messages

**EXPLAIN:**

- Determine conversion coefficient from LBS to KG: `0.453`
- Normalize quantity to kg: 10 pounds is `10*0.453=4.536kg`
- Calculate price per normalized unit: `120/4.563=26.30 LCUs per kg`
- Calculate the price ratio of observed vs reference price: `26.30/25=105.20%`
- Verify: `(100%-30%)<=105.20%<=(100%+30%)`


