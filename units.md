### Units conversion

The units of measurement (UOM) apply to the minimum, maximum, observed, normalized, and 
reference quantities. The UOM that are used in this questionnaire must be coded. For 
example:

```
Piece......1
Pair.......2
Pack.......3
Kilogram...11
Gram.......12
Pound......13
```

UOM codes are embedded into the questionnaire in the `UNITS` reusable categories:

![image](https://github.com/user-attachments/assets/0d644feb-25ce-4889-83f8-ef5f90de7ff5)

A conversion table for units must be included into the questionnaire. For every 
item, the interviewers will be able to enter quantity in the reference units, or 
in any other units for which the conversion coefficient is specified. A normalized 
price will be calculated for every item (in reference units).

The conversion table must be embedded as a lookup table with specific name `T`. It must 
be in the following format:

- `rowcode` - code (numeric, integer) of the combination, for example `1317` - conversion
from UOM with code `13` to UOM with code `17`.
- `C10` - coefficient (numeric, double) for direct conversion, for example
`2.204623` (direct for kilograms to pounds conversion).
- `C01` - coefficient (numeric, double) for reverse conversion, for example
`0.453592` (reverse for kilograms to pounds conversion).

If imperial/US units of measurement are not needed, they can be eliminated from the 
list of categories for units of measurement. As long as they are not present there, 
their presence in the lookup table will not be an issue.

If the number of units of measurement is larger than `100` the formula for the 
filtering condition in variable `unit_1` must be updated to accommodate wider 
item codes.

NB: If the questionnaire permits no conversion between the units, it must still 
include the conversion table with unity conversions for every UOM, for example:
```
rowcode C10 C01
0101      1   1
0202      1   1
1212      1   1
1313      1   1
1717      1   1
```

### Demonstration

The specific conversion factors for the demonstration were pulled out from the 
following sources:

- [Wikipedia: Imperial Units](https://en.wikipedia.org/wiki/Imperial_units);
- [Google](https://www.google.com/search?q=convert+1+inch+to+meters).

Always verify the accuracy of the used coefficients across different sources to 
avoid potentially serious mistakes in units conversion!
