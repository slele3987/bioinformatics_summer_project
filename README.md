Distribution Graph
This is code for a distribution graph from the USDA Food Central database. I followed https://github.com/r-flores/Ingredient_CoOccurrence to create a hash file, and then created a csv file using the file, which is in the folder. This distribution graph shows the top 20 ingredients with the most occurrences in the csv file. This is to visualize the ingredients that occur the most in this database and to then compare the top 20 ingredients with other databases.

Installation
I installed (technically imported) matplotlib, which is a plotting library for python that creates visual distributions, and pandas, which is a python software for data manipulation & analysis.

# Import
import matplotlib.pyplot as plt; plt.rcdefaults()
import pandas as pd
# Import
import matplotlib.pyplot as plt; plt.rcdefaults()
import pandas as pd
I opened the csv file and named it "graph."

# Name the csv file 
graph = pd.read_csv("foodcentral.hashfile.csv")
Usage
I created a bar graph using the top 20 ingredients, sinc the csv file has many ingredients. I labeled the axes and titled it.

# Use top 20 ingredients
ing = graph.nlargest(20,['Occurrence'])

# Create horizontal bar graph
plt.barh(ing.Ingredient, ing.Occurrence)
# Label the axes
plt.xlabel("Occurrence", fontsize = 12)
plt.ylabel("Ingredient", fontsize = 12)
# Title the scatter plot
plt.title("Ingredient Occurrence Bar Graph")

# Display the scatter plot
plt.show()
