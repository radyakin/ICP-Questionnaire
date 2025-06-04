### Item information preloading in the assignment

`itemCode_1` - mandatory! Any item for which the price needs to be collected must be assigned a unique code that is determining the rest of the characteristics below. Example, *CONS1234812394*. This code is not processed by the software by itself, and the accompanying information must be supplied along with it. It is exported with the final data to allow absorption of the collected data to storage and processing/aggregation. The code is handled as a string to prevent loss of leading zeroes or truncation/rounding of values due to precision, and the supplying and consuming subsystems must account for this.

`itemDescription_1` - mandatory!  Every item must be described by supplying a text line that describes the item in sufficient precision. Example: "_Pork shoulder, for roasting, fresh, without bones_". If the description is structured in the supplying system, it must serialize all the individual attributes into a single description line.

`itemSpecify_1` - (optional). A text list of up to `10` attributes to be acquired by interviewers upon encountering an instance of the item for pricing to help supervisors understand what item was located. For example, "brand | quality | imported status" will request three questions (The answers to each will be *string* inputs):

- specify brand;
- specify quality;
- specify imported status.

`minQuantity_1` - (optional). If specified, the normalized quantity will be compared with this minimum to check that the interviewer has picked the item of an appropriate size. For example: *2.250*.

`maxQuantity_1` - (optional). If specified, the normalized quantity will be compared with this maximum to check that the interviewer has picked the item of an appropriate size. For example: *4.500*.

`referenceQuantity_1` - (mandatory). For every item the observed price and observed amount will be used to calculate the price of this amount. For example: *1.5*. This quantity specifically is **not** constrained to be between the `minQuantity_1` and `maxQuantity_1`.

`referenceUnit_1` - (mandatory). For every item determines the measurement units in which the `minQuantity_1`, `maxQuantity_1`, and `referenceQuantity_1` are expressed. For example: 7. (Units of measurement are **coded**.)

`referencePrice_1` - (optional). If specified, the normalized price will be compared with this reference price and the interviewer will be alerted if the observed price deviates from the reference price by a large margin. Reference price allows for 2 decimals.

`tolerancePercent_1` - (optional).  This is percent (e.g. `25` for *25%*, not `0.25` for *25%*) by which the observed standardized price is permitted to deviate from the reference price `referencePrice_1` meaning a constraint for the price ratio as follows:

$$ 1 - \frac{t}{100} <= \frac{p}{r} <= 1 + \frac{t}{100} $$

where *p* is observed price, *r* is reference price and *t* is tolerance.

`itemObs_1` - (mandatory). For every item, the minimal number of observations of that item to be collected. This value is expected to be protected in the preloading file, so that the interviewers can't reduce it below the specified value (but they can increase it to a larger one if needed). For example: `5`.

Note: It is an error of misspecification if `minQuantity_1` is larger than `maxQuantity_1` for any item.

### Other information that may be preloaded in the assignment:

1. **List of the shops** - if the list is known by the agency it can be supplied for the interviewer to minimize time on recording the location and to minimize errors in coding of shop types. In general, it is expected that the interviewer will need to be able to introduce other shops as needed to fulfill the assignment. Each list may contain up to 200 shops and their associated information (title, address, location coordinates, and shop type). 

2. `aisleName_1` - (optional). Name of the aisle in case the questionnaire is expanded to multiple aisles. For example: "*Groceries*" or "*Electronics*".

### Use of images

As of now the images of items may not be preloaded dynamically. Instead, they must be embedded into the questionnaire. Use of images is optional, but if they are included into the questionnaire, they must be named specifically as "***i_{itemcode}***". Where the code of the item is to be substituted in place of `{itemcode}`. For example, "*i_11011130199*".

### Units conversion
Units of measurement that are used in this collection are coded. For example:
```
Piece......1
Pair.......2
Pack.......3
Kilogram...11
Gram.......12
Pound......13
```
The UOM codes apply to the minimum, maximum, observed, normalized, and reference quantities.
UOM codes are embedded into the questionnaire in the `UNITS` reusable categories.
![image](https://github.com/user-attachments/assets/0d644feb-25ce-4889-83f8-ef5f90de7ff5)


A conversion table for units must be included into the questionnaire. For every item, the interviewers will be able to enter quantity in the reference units, or in any other units for which the conversion coefficient is specified.
