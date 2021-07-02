# NYC Street Trees Census - Data Cleaning

![NYC Picture (Image)](https://viajes.nationalgeographic.com.es/medio/2018/11/07/figuras-geometricas-en-central-park_59ddbc26_794x447.jpg)

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

>`health        4993`<br/>
>`spc_latin     4992`<br/>
>`spc_common    4992`<br/>
>`steward       4992`<br/>
>`guards        4992`<br/>
>`sidewalk      4992`<br/>
>`problems      4992`<br/>

The method chosen to deal with this was to fill these empty cells with a new value.
`"Unknown"` was created to prevent the loss of the rest of the data from these rows.

### Columns Names & DataTypes

Some names were changed for better readability, as well as some `dtype` were changed for better usage.<br/>
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
>13  problems --> `object`<br/>     
>14  address --> `object`<br/> 
>15  zipcode --> `int64`<br/>
>16  com_board --> `int64`<br/>   
>17  borocode --> `int64`<br/>
>18  council_distr --> `int64`<br/>
>19  state_assem --> `int64`<br/>
>20  state_senate --> `int64`<br/>
>21  nta_code --> `object`<br/>
>22  census_track --> `int64`<br/>
>23  state --> `object`<br/>
>24  latitude --> `float64`<br/>
>25  longitude --> `float64`<br/>
>26  X_sp_coord --> `float64`<br/>
>27  Y_sp_coord --> `float64`<br/>

The next columns have been removed for data redundancy:

>the_geom --> `Removed` (overlapping longitude and latitude)
>
>latin_name --> `Merged` ( "tree_name" = common_name + latin_name)
>
>boroname --> `Removed` (overlapping borocode)
>
>zip_city --> `Removed` (overlapping zipcode)
>
>nta_name --> `Removed`(overlapping nta)
>
>root_stone / root_grate / root_other -->  `Removed` <br/>
>trunk_wire / trunk_light / trunk_other -->  `Removed` <br/>
>branch_light / branch_shoe / branch_other -->  `Removed`<br/>
>
> (problems --> Kept to sum up all trees problems in 1 column)

## Final `NYC Trees DataFrame` render:

>`RangeIndex: 100000 entries, 0 to 99999`
>
>`100000 non-null`
>
>`Data columns (total 28 columns)`
>
>`dtypes: datetime64[ns](1), float64(4), int64(11), object(12)`
>
>`memory usage: 21.4+ MB`
