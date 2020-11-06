# Prevalence Script

We will be a creating a prevalence script to find out the prevalence of ingredients from the USDA FoodCentral database. The hash file was created from https://github.com/r-flores/Ingredient_CoOccurrence. I created a csv file after obtaining the hash, which is what I will be using for this code. Prevalence is the number of occurrences of an ingredient divided by the total number of occurrences. One occurrence is how many times an ingredient shows up on a label.

## Import


```python
# Import
import pandas as pd
from spellchecker import SpellChecker
```

## File


```python
# Name csv file
data = pd.read_csv('foodcentral.hashfile.csv')

```

## Spellchecker

Because so many terms are misspelled in this database, spellchecker will be used to allow for occurrences that are misspelled to be counted in the prevalence of certain ingredients.


```python
ing = input('Please enter your ingredient: ')

# Spell Check
spell = SpellChecker()
while True:
    if ing != spell.correction(ing): # If not spelled correctly
        print('We cannot find your ingredient; here is what we think you meant to put:', spell.candidates(ing))
        ing = input('Please enter your ingredient again: ')
    else: 
        break;
```

    Please enter your ingredient: citric acid


## Prevalence

Now it is time to calculate the prevalence of the ingredient. After entering your ingredient, the prevalence will be presented. 


```python
#Calculate prevalence 
ingredient = data[data.Ingredient == str(ing)]
total_occurrences = sum(data.Occurrence)
prevalence = max(ingredient.Occurrence)/total_occurrences

# Print prevalence
print('The prevalence of ' + ing + ' is ' + str(prevalence))

```

    The prevalence of citric acid is 0.015264153476763655



```python

```
