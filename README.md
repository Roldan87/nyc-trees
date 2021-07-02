# NYC Street Trees Census - Data Cleaning

![NYC Picture (Image)](https://imgs.6sqft.com/wp-content/uploads/2015/04/21000922/MAPS-by-Jill-Hubley-Explore-NYC-Street-Trees-by-Species-4.png)

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
> `trees_cleaning.ipynb`
>
> `nyc_trees_dataset.csv`

## 1. Data Cleaning

### Missing values (null):

>`health        4993`<br/>
>`spc_latin     4992`<br/>
>`spc_common    4992`<br/>
>`steward       4992`<br/>
>`guards        4992`<br/>
>`sidewalk      4992`<br/>
>`problems      4992`<br/>

The method chosen to deal with this was to fill these empty cells with a new value.
`"Unknown"` was created to prevent the loss of the rest of the data from these rows.

### Columns:

Some columns `labels` were changed for better readability, as well as some `dtype` were changed for better usage.<br/>
Here is the list of the actual columns names and dtypes:

>0   creation_date --> `datetime64[ns]`<br/>
>1   tree_id --> `int64`<br/>
>2   block_id --> `int64`<br/>
>3   breast_diameter --> `int64`<br/>
>4   stump_diameter --> `int64`<br/>
>5   curb_location --> `object`<br/> 
>6   status --> `object`<br/>
>7   health --> `object`<br/>
>8   tree_name --> `object`<br/>
>9   steward --> `object`<br/>
>10  guards --> `object`<br/>
>11  sidewalk --> `object`<br/>
>12  user_type --> `object`<br/>
>13  root_stone --> `bool`<br/>
>14  root_grate --> `bool`<br/>
>15  root_other --> `bool`<br/>
>16  trunk_wire --> `bool`<br/>
>17  trunk_light --> `bool`<br/>
>18  trunk_other --> `bool`<br/>
>19  branch_light  --> `bool`<br/>
>20  branch_shoe --> `bool`<br/>
>21  branch_other --> `bool`<br/>
>22  address --> `object`<br/>
>23  zipcode --> `int64`<br/>
>24  borocode --> `int64`<br/>
>25  nta_code --> `object`<br/>
>26  census_track --> `int64`<br/>
>27  state --> `object`<br/>
>28  latitude --> `float64`<br/>
>29  longitude --> `float64`<br/>



The next columns have been `dropped` for data redundancy:

>the_geom --> `Removed` (overlapping longitude and latitude)
>
>latin_name & common_name --> `Merged` ( "tree_name" = common_name + latin_name)
>
>boroname --> `Removed` (overlapping borocode)
>
>com_board / council_distr / state_assem / state_senate --> `Removed` (Enough Geocodes)
>
>zip_city --> `Removed` (overlapping zipcode)
>
>nta_name --> `Removed` (overlapping nta)
>
> problems --> `Removed` (overlapping root/trunk/branch)
>
>X-Y_sp_coordinates --> `Removed` (Enough Geocodes)

## 2. Final `NYC Trees DataFrame` render:

>`RangeIndex: 100000 entries, 0 to 99999`
>
>`100000 non-null`
>
>`Data columns (total 30 columns)`
>
>`dtypes: bool(9), datetime64[ns](1), float64(2), int64(7), object(11)`
>
>`memory usage: 16.9+ MB`
