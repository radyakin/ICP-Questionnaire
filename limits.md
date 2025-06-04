# Limits

The following limits stem directly from the [Survey Solutions limits](https://docs.mysurvey.solutions/questionnaire-designer/limits/survey-solutions-limits/):

- number of shops recorded: `200`;
- number of items recorded: `200`;

The questionnaire template is designed in anticipation that a larger number of items may be needed 
in practice, hence the items' prices section is indexed (all variables end in `_1`). If it is
determined that a larger number of items are to be preloaded into a single assignment, then the
questionnaire must be modified (replicas of the items section must be created with indices `_2`, 
`_3`, and so on as necessary). Correspondingly, the calculation of statistics by shop types must
iterate over all such replicas.

It can be more practical, however, to create multiple assignments, each limited to no more than 
`200` items. This allows to stay close to the original questionnaire template and simplifies
the preloading requirements.

If the number of shops is expected to be more than `200` to fulfil one assignment, the designer may 
replicate the shops section as well as replicate the linked question in the items section, and
include a switch question to activate only one such replica.
