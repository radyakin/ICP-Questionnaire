# Questionnaire Customization

Anyone who intends to edit or import a Survey Solutions questionnaire must have an 
account and do such edits in the [Designer](https://designer.mysurvey.solutions) tool. 

The access to the Designer tool is open to public and free (no cost). Users must 
self-register.

The particular template described here is not *editable* by the public. It is 
accessible in read-only mode. If there is a customization needed, users must 
perform it on own copy. If there is a bug in the template, raise an issue in 
the [issues tracker at GitHub](https://github.com/radyakin/ICP-Questionnaire/issues).

### Identifying information
The questionnaire template contains no identification fields. While the system will
know which interviewer is sending the information and when it was recorded it still
makes sense to introduce some sort of identification, such as an island code, town
or village name, etc for locating where the interviewer is working to collect the
prices. (alternatively, target area bounds can be supplied to the interviewer during
assignment creation).

### Use of images

As of now the images of items may not be preloaded dynamically (this is a Survey 
Solutions' limitation). Instead, they must be embedded into the questionnaire. 
The use of images is optional, but if they are included into the questionnaire, 
they must be named specifically as "***i_{itemcode}***". Where the code of the 
item is to be substituted in place of `{itemcode}`. 

For example, "*i_11011130199*".

### Units conversion
Units of measurement that are used in this collection must be coded. For example:

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


A conversion table for units must be included into the questionnaire. For every 
item, the interviewers will be able to enter quantity in the reference units, or 
in any other units for which the conversion coefficient is specified. A normalized 
price will be calculated for every item (in reference units).

The conversion table must be embedded as a lookup table with specific name `T`. It must be in 
the following format:

- `rowcode` - code (numeric, integer) of the combination, for example `1317` - conversion
from UOM with code `13` to UOM with code `17`.
- `C10` - coefficient (numeric, double) for direct conversion, for example `2.204623` (direct for kilograms to pounds conversion).
- `C01` - coefficient (numeric, double) for reverse conversion, for example `0.453592` (reverse for kilograms to pounds conversion).

If imperial/US units of measurement are not needed, they can be eliminated from the 
list of categories for units of measurement. As long as they are not present there, 
their presence in the lookup table will not be an issue.

If the number of units of measurement is larger than `100` the formula for the 
filtering condition in variable `unit_1` must be updated to accommodate wider 
item codes.

The specific conversion factors for the demonstration were pulled out from the 
following sources:

- [Wikipedia: Imperial Units](https://en.wikipedia.org/wiki/Imperial_units);
- [Google](https://www.google.com/search?q=convert+1+inch+to+meters).
