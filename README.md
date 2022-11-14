# How to Kobo


## variable and choice naming

Pertains to the column `name` in _'survey'_ and _'choices'_ tabs

- as a general rule, please pick names that are human-readable and give a hint as to what this variable is representing

    e.g. `"hh_num_girls_under_18"` and not: `"abahh_u18f"`

- the name needs to contain at least one letter

    e.g. ` "25_50_percent" `, not: `"25_50" `

- do not use any whitespaces, use underscores instead
- do not include any other special characters (diacritics, apostrophes, hyphens, dashes, other symbols) - it's best to stick to lowercase letters, numbers and underscores!

    e.g. ` "kraj_kosice" `, not: `"Košický kraj"`

- consistent naming of similar choices in different questions:

    e.g. `dnk`, `pns` or `dont_know`, `prefer_not_to_say` and not mixing them.
   
## Others

This section is by far the most important with regards to compatibility with our cleaning procedures!

### Survey Tab

- For all other (text) questions 'name' should end with `_other`. 

    e.g. If you want to add a text question for a select_one: humanitarian_assisance, than the other variable should be: humanitarian_assistance_other. 

### Choices Tab

- For all other choices should be only `other` and nothing else. 
 
    e.g. `Other`, `Other_please_specify`, `info_other`, `other_info` will not be accepted

## constraints

### select_one

In most cases, there is no constraints usually needed for a select_one as most of the cases is solved in choice_filter. However, if you are trying to set a select_one in a loop with a constraint related to main :

    e.g. if(${ind_pos} = 1,  selected(. , 'respondent'),  not(selected(. , 'respondent') ))

### select_multiple

- setting a maximum number of choices that can be selected for this question:
    e.g. Top 5: if(selected(. , 'idnk') or selected(. ,'none') or selected(. , 'prefer_not_to_answer'), count-selected(.)=1, count-selected(.)<=5)
    
- setting a constraint to not select a choice with other choices:
    e.g. if(selected(. , 'idnk') or selected(. , 'nowhere'), count-selected(.)=1, 1)

### text

Constraints for text questions are usually reserved for cases when the question asks for the respondent's phone number or e-mail address.

### integer

Constraints for integer are usually used to set limits and thresholds on depending on another variable or an integer:
    e.g. . >= 0 or .<= ${hh_family_size}

## audits

Set parameter track-changes in order to track changes.

    e.g. Add track-changes=TRUE to the audit row in a field called parameter

## Logbook

Please keep track of all changes done in the tool during data collection (If really a change is necessary to be done)
