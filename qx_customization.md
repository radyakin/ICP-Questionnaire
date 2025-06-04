# Questionnaire customization
Anyone who intends to edit or import a Survey Solutions questionnaire must have an 
account and do such edits in the [Designer](https://designer.mysurvey.solutions) tool. 

The access to the Designer tool is open to public and free (no cost). Users must 
self-register.

The particular template described here is not *editable* by the public. It is 
accessible in read-only mode. If there is a customization needed, users must 
perform it on own copy. 

If there is a bug in the template, raise an issue in the 
[issues tracker at GitHub](https://github.com/radyakin/ICP-Questionnaire/issues).

### Identifying information
The questionnaire template contains no identification fields. While the system will
know which interviewer is sending the information and when it was recorded it still
makes sense to introduce some sort of identification, such as an island code, town
or village name, etc for locating where the interviewer is working to collect the
prices. (alternatively, 
[target area bounds](https://github.com/user-attachments/assets/6c496f7f-3785-4278-a1aa-88730c6a1255) 
can be supplied to the interviewer during assignment creation).


### Use of images
As of now the images of items may not be preloaded dynamically (this is a Survey 
Solutions' limitation). Instead, they must be embedded into the questionnaire. 
The use of images is optional, but if they are included into the questionnaire, 
they must be named specifically as "***i_{itemcode}***". Where the code of the 
item is to be substituted in place of `{itemcode}`. 

For example, "*i_11011130199*".

### Units conversion
See [Units conversion](units.md)
