
# Mario Kart 8 Deluxe Build Statistics #

This repository consists of Jupyter notebooks and CSV files relating to
character/kart builds in
Mario Kart for the Nintendo Switch (Mario Kart 8 Deluxe).
The included CSV files contain all the in-game stats
(as well as some derived stats) for every possible combination of character,
vehicle, tires, and glider.

## Getting Started #

If you clone this repository, you can use the CSVs for reference or add
your own Jupyter notebooks for do additional analysis.

### Prerequisites #

If you want to use this repository for more than just getting the CSVs, you
should install
[Jupyter Notebook](http://jupyter.readthedocs.io/en/latest/content-quickstart.html).

### Installation #

Clone this repository:

`git clone https://github.com/jfmario/mario-kart-8-deluxe-builds`

If you want to run the Jupyter environment, run `jupyter notebook` from the
root of this repository and then in a browser visit the localhost URL printed
on the terminal.

### Usage #

The data files are all present and included with this repository. However,
if something changes in an update or you notice a mistake in the source data,
these are the steps to rebuild the data.

1. Edit the files in `src-data` so that they are correct.
1. Run the notebook [MakeCombos](./MakeCombos.ipynb). It will take a long time as it is building every possible combination (over 400,000 possibilities).
1. Run the notebook [AdditionalScores](./AdditionalScores.ipynb). This adds several derived stats to the data.
1. Run the notebook [Minimize](./Minimize.ipynb). This reduces the data from 400,000 records to just 9,000 records, because there are many combinations that have identical stats. The filtered version reduces identical combinations based on my personal favorite characters out of every identity grouping, then randomly selecting vehicle, tire, and glider.
1. Run the notebook [Samples](./Samples.ipynb). This displays a 5-row random sample of every source and output file. The exceptions is `WINNERS.csv`, which is displayed in full.

**Source Files**

* `src-data/DRIVERS.csv`: Base stats for all characters.
* `src-data/VEHICLES.csv`: Stats for all vehicles.
* `src-data/TIRES.csv`: Stats for all tires.
* `src-data/GLIDERS.csv`: Stats for all gliders.

**Output Files**

* `output/COMBOS.csv`: Basic stats for all combinations.
* `output/COMBOS_EXTRA.csv`: Basic and derived stats for all combinations.
* `output/MINIFIED.csv`: Basic and derived stats with stat duplicates filtered out.
* `output/WINNERS.csv`: The best combination according to each basic and derived stat.

**Stats**

*Basic Stats*

These are the basic in-game stats.

* `GroundSpeed`: Maximum speed on ground.
* `WaterSpeed`: Maximum speed in the water.
* `AirSpeed`: Maximum speed in the air.
* `AntiGravitySpeed`: Maximum speed in anti-gravity.
* `Acceleration`: Ability to speed up quickly.
* `Weight`
* `GroundHandling`: Ability to maneuver on the ground.
* `WaterHandling`: Ability to maneuver in the water.
* `AirHandling`: Ability to maneuver in the air.
* `AntiGravityHandling`: Ability to maneuver in anti-gravity.
* `Traction`: Grip power.
* `MiniTurbo`: Power of turbo boosts.

*Derived Stats*

These are stats that do not exist in `COMBOS.csv` or any source files
but do exist in the other output files. They are calculated based on the basic
stats listed above. Some are rather subjective and they are all calculated
in [AdditionalScores.ipynb](./AdditionalScores.ipynb).

* `Total`: The total of all basic stats.
* `Balance`: The well-roundedness of the combination. Defined currently as 5 minus the Standard Deviation of the basic stats.
* `AverageSpeed`: Average of Ground, Water, Air, and Anti-Gravity speed values.
* `WeightedSpeed`: Average of speed values with double-weight to Water speed, triple weight to AntiGravity speed, and quadruple weight to Ground speed.
* `AverageHandling`: Average of all the handling values.
* `WeightedHandling`: Average of all the handling values weighted in the same way as `WeightedSpeed`.
* `GroundMastery`: Average of Ground speed and handling values.
* `WaterMastery`: Average of Water speed and handling values.
* `AirMastery`: Average of Air speed and handling values.
* `AntiGravityMastery`: Average of Anti-Gravity speed and handling values.
* `DriftMastery`: Average of handling, traction, and mini-turbo values.
* `CollisionMastery`: Average of weight and ground handling values.

## Files #

### Jupyter Notebooks #

**[MakeCombos.ipynb](./MakeCombos.ipynb)**

This notebook reads the source files and writes all the combinations by
summing the stat values for every possible driver, vehicle, tires, and glider
permutation. It creates the output file `COMBOS.csv`.

**[AdditionalScores.ipynb](./AdditionalScores.ipynb)**

This notebook calculates all derived stats listed above. It creates the
output file `COMBOS_EXTRA.csv`.

**[Minimize.ipynb](./Minimize.ipynb)**

This notebook filters the stats down to a smaller output, where no two combinations
with identical stats will be present. Some randomness is involved in
selected the combo to show among competing possibilities. This notebook
also records the best combination according to each stat value, both basic
and derived. It creates the output files `MINIFIED.csv` and `WINNERS.csv`.

**[Samples.ipynb](./Samples.ipynb)**

This notebook reads all source and output files and presents 5-line samples of
each. `WINNERS.csv` is rendered in its entirety at the bottom.

### CSV Files #

See above for a description of each CSV file.

### Winners #

Winners are listed here for convenience.

| Stat | Driver | Vehicle | Tire | Glider | Value |
| --- | --- | --- | --- | --- | --- |
| GroundSpeed | Bowser | Standard Quad | Metal | Waddle Wing | 5.75 |
| WaterSpeed | Bowser | Landship | Off-Road | Cloud Glider | 5.75 |
| AirSpeed | Dry Bowser | Cat Cruiser | Sponge | Wario Wing | 5.75 |
| AntiGravitySpeed | Bowser | Sports Coupé | Cyber Slick | Flower Glider | 5.75 |
| Acceleration | Baby Rosalina | Buggybud | Azure Roller | Parafoil | 5.75 |
| Weight | Bowser | Steel Driver | Metal | Gold Glider | 5.75 |
| GroundHandling | Baby Daisy | Buggybud | Azure Roller | Bowser Kite | 5.75 |
| WaterHandling | Baby Daisy | Landship | Wooden | Gold Glider | 5.75 |
| AirHandling | Baby Daisy | Buggybud | Azure Roller | Bowser Kite | 5.75 |
| AntiGravityHandling | Baby Daisy | Blue Falcon | Azure Roller | Flower Glider | 5.75 |
| Traction | Koopa Troopa | Koopa Clown | Monster | Flower Glider | 5.75 |
| MiniTurbo | Baby Daisy | Buggybud | Azure Roller | Bowser Kite | 5.75 |
| Total | Metal Mario | Koopa Clown | Roller | Paper Glider | 46.0 |
| Balance | Luigi | Standard Quad | Roller | Bowser Kite | 4.8694417580332265 |
| AverageSpeed | Dry Bowser | Mach 8 | Wooden | Hylian Kite | 5.125 |
| WeightedSpeed | Dry Bowser | Sports Coupé | Wooden | Plane Glider | 5.15 |
| AverageHandling | Baby Daisy | Buggybud | Azure Roller | Bowser Kite | 5.625 |
| WeightedHandling | Baby Daisy | Buggybud | Azure Roller | Paper Glider | 5.65 |
| GroundMastery | Luigi | Sport Bike+ | Crimson Slim | Waddle Wing | 4.125 |
| WaterMastery | Dry Bowser | Landship | Roller | Parafoil | 4.375 |
| AirMastery | Metal Mario | Comet+ | Azure Roller | Flower Glider | 4.375 |
| AntiGravityMastery | Metal Mario | Inkstriker | Wooden | Paper Glider | 4.375 |
| DriftMastery | Baby Daisy | Buggybud | Azure Roller | Paper Glider | 5.208333333333333 |
| CollisionMastery | Metal Mario | Tanooki Kart | Gold Wheels | Gold Glider | 4.375 |

## Contributing #

### Welcome Contributions #

The following types of contributions are welcome:

* Fixing errors (ie, one of my stats is wrong).
* Improving or adding new useful derived stats by altering or adding cells in `AdditionalScores.ipynb`.
* Adding notebooks that do other calculations.
* Adding notebooks that show nice displays.

### Guidelines #

* Any new notebooks should either present data or write data to a new output file.
* Notebooks that write data should have their outputs cleared before a commit.
* Notebooks that display data should have been run once and completed before commit.
* What the notebook does should be documented in this README and optionally in the notebook itself.

## Acknowledgements #

### Authors #

* John F Marion

### Built With #

* [Jupyter](https://github.com/jupyter/jupyter)

### Other #

* Mario Kart 8 Deluxe is a game for the [Nintendo Switch](http://nintendo.com).
* Stats were pulled from the [Super Mario Wiki](https://www.mariowiki.com/Mario_Kart_8_Deluxe).
