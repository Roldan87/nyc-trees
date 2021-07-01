# NYC Street Trees Census - Tree Data

## The Mission

The Department of Environmental Conservation, from New York City, has recently made the news by telling the people that they needed their help. 
Indeed, their request is simple: They needed the people of New York City, whether young or old, to go to the nearest tree in their street and gather information about that tree.
This is all in an effort to make the population aware that nature is important, even in big Metropolis like NYC. Now that they have heard back from the people, the DEC noticed that they missed a crucial step. 
They forgot to give the people a data collection guide, and so the data they received back is a bit messy.

My mission, should I choose to accept it, is to help them clean the data so that they can begin to raise awareness to ecological issues, such as climate change.

## Files included

>
>`Readme.md`
>
> `nyc_trees_dataset.csv`

## Data Cleaning

### Missing values (null):

>`health        4993`
>`spc_latin     4992`
>`spc_common    4992`
>`steward       4992`
>`guards        4992`
>`sidewalk      4992`
>`problems      4992`

The method chosen to deal with this was to fill these empty cells with a new value;
`"Unknown"` was created to prevent the loss of the rest of the data from these rows.

### DataTypes

Most of the columns had the correct `dtype`, but the following were changed:






`RangeIndex: 100000 entries, 0 to 99999`

`Data columns (total 40 columns)`
