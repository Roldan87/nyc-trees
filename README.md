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

>0   creation_date    		100000 non-null  	datetime64[ns]
>1   tree_id          		100000 non-null  	int64         
>2   block_id      		100000 non-null  	int64         
>3   breast_diameter  	100000 non-null  	int64         
>4   stump_diameter   	100000 non-null  	int64         
>5   curb_location    		100000 non-null  	object        
>6   status           		100000 non-null  	object        
>7   health           		100000 non-null  	object        
>8   tree_name        		100000 non-null  	object        
>9   steward          		100000 non-null  	object        
>10  guards           		100000 non-null  	object        
>11  sidewalk         		100000 non-null  	object        
>12  user_type        		100000 non-null  	object        
>13  problems         		100000 non-null  	object        
>14  address          		100000 non-null  	object        
>15  zipcode          		100000 non-null  	int64         
>16  com_board        		100000 non-null  	int64         
>17  borocode         		100000 non-null  	int64         
>18  council_distr    		100000 non-null 	int64         
>19  state_assem      		100000 non-null  	int64         
>20  state_senate     		100000 non-null  	int64         
>21  nta_code         		100000 non-null  	object        
>22  census_track     		100000 non-null  	int64         
>23  state            		100000 non-null  	object        
>24  latitude         		100000 non-null  	float64       
>25  longitude        		100000 non-null  	float64       
>26  X_sp_coord      		100000 non-null  	float64       
>27  Y_sp_coord       		100000 non-null  	float64 

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
