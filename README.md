import pandas as pd

# define the dictionary of parallel lists

dictAQI = {

        "North America", "North America", "Europe", "Europe", "Asia", "Asia",
        "North America", "North America", "Europe", "Europe", "Asia", "Asia",
        "North America", "North America", "Europe", "Europe", "Asia", "Asia",
        "North America", "North America", "Europe", "Europe", "Asia", "Asia",
        "North America", "North America", "Europe", "Europe", "Asia", "Asia",
        "North America"
    ],
    "product": [
        "widgets", "bobbles", "widgets", "bobbles", "widgets", "bobbles",
        "widgets", "bobbles", "widgets", "bobbles", "widgets", "bobbles",
        "widgets", "bobbles", "widgets", "bobbles", "widgets", "bobbles",
        "widgets", "bobbles", "widgets", "bobbles", "widgets", "bobbles",
        "widgets", "bobbles", "widgets", "bobbles", "widgets", "bobbles",
        "widgets"
    ],
    "sales": [
        150, 200, 120, 180, 300, 250,
        175, 220, 130, 190, 310, 260,
        160, 210, 140, 200, 320, 270,
        155, 215, 135, 205, 330, 280,
        165, 225, 145, 210, 340, 290,
        170
    ]
}

# create a DataFrame from the dictionary

dfAQI = pd.DataFrame(dictAQI)

# display the DataFrame

print(dfAQI)
