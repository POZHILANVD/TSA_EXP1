# Ex.No: 01 A PLOT A TIME SERIES DATA
###  Date: 26-08-2025

# AIM:
To Develop a python program to Plot a time series data (population/ market price of a commodity
/temperature.
# ALGORITHM:
1. Import the required packages like pandas and matplot
2. Read the dataset using the pandas
3. Calculate the mean for the respective column.
4. Plot the data according to need and can be altered monthly, or yearly.
5. Display the graph.
# PROGRAM:

### NAME: POZHILAN V D
### REG NO: 212223240118
```

import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns

df = pd.read_excel('Coffe_sales.xlsx')
df.head()


sns.countplot(data=df, x='Mes', hue='Tipo de cafe')
plt.title('Consumo por mes')
plt.xlabel('Mes')
plt.ylabel('Cantidad de cafe consumido')
plt.grid(True)
plt.show()

import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
months = sorted(df['Mes'].unique())
coffee_types = sorted(df['Tipo de cafe'].unique())

counts = []
for coffee in coffee_types:
    counts.append([df[(df['Mes'] == month) & (df['Tipo de cafe'] == coffee)].shape[0] for month in months])

bar_width = 0.8 / len(coffee_types)
x = np.arange(len(months))

for i, (coffee, coffee_count) in enumerate(zip(coffee_types, counts)):
    plt.bar(x + i * bar_width, coffee_count, width=bar_width, label=coffee)

plt.title('Consumo por mes')
plt.xlabel('Mes')
plt.ylabel('Cantidad de cafe consumido')
plt.xticks(x + bar_width * (len(coffee_types) - 1) / 2, months)
plt.grid(True, axis='y', linestyle='--', alpha=0.7)
plt.legend(title='Tipo de cafe')
plt.tight_layout()
plt.show()
1

import matplotlib.pyplot as plt

# Count the values for each ('Mes', 'Tipo de cafe') pair
counts = df.groupby(['Mes', 'Tipo de cafe']).size().unstack(fill_value=0)

# Plot a line for each coffee type
for coffee_type in counts.columns:
    plt.plot(counts.index, counts[coffee_type], marker='o', label=coffee_type)

plt.title('Consumo por mes')
plt.xlabel('Mes')
plt.ylabel('Cantidad de cafe consumido')
plt.grid(True, axis='y', linestyle='--', alpha=0.7)
plt.legend(title='Tipo de cafe')
plt.tight_layout()
plt.show()



```
# OUTPUT:


<img width="736" height="533" alt="image" src="https://github.com/user-attachments/assets/78ab0145-d01a-4c77-8cdf-e28e802405f5" />


<img width="823" height="572" alt="image" src="https://github.com/user-attachments/assets/4847e58f-1920-41e3-b10d-c36ab78fc0e9" />

<img width="786" height="544" alt="image" src="https://github.com/user-attachments/assets/22584a74-3604-4e92-82fc-34038ec4ae09" />


# RESULT:
Thus we have created the python code for plotting the time series of given data.
