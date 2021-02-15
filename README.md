# Statistics for Corrently hourly tariff

*based on https://github.com/keisentraut/awattar-statistics*

There is a new, very interesting offer in Germany for a dynamic power contract.
The company is called [STROMDAO](https://www.stromdao.de/) with their product [Corrently](https://www.corrently.de/home.html).
They offer an [HOURLY tariff](https://www.corrently.de/gruenstromerlebnis/gruenstromindex.html) based on the available green electricity.

This Project is about getting a rough idea about the expected costs of the Corrently HOURLY tariff without having a smart meter.

# Data Source

The source of this data is the official [Corrently API](https://corrently.io/).
**Please note that this price is without VAT.**
So you will need to add 19% in order to get the actual prices for customers.

All data is only collected once and then cached.
For convenience, this repository comes with the pre-downloaded data from ```2013-12-22``` until ```2020-09-21```.

# Usage

In order to get the latest daily data, please run ```./corrently-statistics.py update``` first.
This will download and append the missing data to the file ```historical-data.txt```.

Then run ```./corrently-statistics.py calculate``` which will create all the files and visualizations.
This will take a few minutes of generation.

# Output

This script outputs a few CSV files which you can use for further processing, for instance Libreoffice Calc or Excel.
The following three outputs are created:

* **daily prices** (```data/daily/2020-04-22.txt```): prices per hour, format is ```{hour};{price}```. Please note that there might be 25 or 23 hours on days where daylight saving changes, i.e. there might be no hour ```02``` or two hours ```02a``` and ```02b```.
* **monthly minimum, average, median and maximum prices** (```data/monthly/2020-08-*.txt```): Those files contain the hourly minimum, average, median or maximum prices for the whole month.
* **yearly minimum, average, median and maximum prices** (```data/yearly/2020-*.txt```): Those files contain the hourly minimum, average, median or maximum prices for the whole year.

There are three types of visualizations:

* **daily charts** (```plot/daily/2020-04-22.png```): bar chart for a single day
* **monthly percentile charts** (```out/plot/monthly/2020-08.png```): percentile chart for a month
* **yearly percentile charts** (```out/plot/yearly/2020.png```): percentile chart for a complete year

I find the monthly percentile charts the most interesting. Those look like the following:
![Visualization for July 2020](plot_monthly_2020-07.png)

# Contributing

If you want to have another visualization, please feel free to open an issue or - if you can - a pull request.

