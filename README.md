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

>0. creation_date --> `datetime64[ns]`
>1. tree_id --> `int64`
>2. block_id --> `int64`
>3. breast_diameter --> `int64`
>4. stump_diameter --> `int64`
>5. curb_location --> `object`
>6. status  --> `object`
>7. health  --> `object`
>8. latin_name  --> `object`
>9. common_name  --> `object`
>10. steward  --> `object`
>11. guards  --> `object`
>12. sidewalk  --> `object`
>13. user_type --> `object`
>14. problems --> òbject` 

>23. address --> `object`
>24. zipcode --> `int64`
>25. zip_city --> `object`
>26. com_board --> `int64`
>27. borocode --> `int64`
>28. boroname --> `object`
>29. council_distr --> `int64`
>30. state_assem --> `int64`
>31. state_senate --> `int64`
>32. nta_code --> `object`
>33. nta_name --> `object`
>34. census_track --> `int64`
>35. state --> `object`
>36. latitude --> `float64`
>37. longitude --> `float64`
>38. X_sp_coord --> `float64`
>39. Y_sp_coord --> `float64`

The next columns have been removed for data redundancy:

>the_geom --> `Removed` overlapping `longitude` and ´latitude`
>
>root_stone --> `Removed`
>root_grate --> `Removed`
>root_other --> `Removed`
>trunk_wire --> `Removed`
>trunk_light --> `Removed`
>trunk_other --> `Removed`
>branch_light --> `Removed`
>branch_shoe --> `Removed`
>branch_other -->  `Removed`
>
> Kept `problems` to sum up all trees problems in 1 column.

## Final `NYC Trees DataFrame` render:

>`RangeIndex: 100000 entries, 0 to 99999`
>
>`100000 non-null`
>
>`Data columns (total 40 columns)`
>
>`dtypes: bool(9), datetime64[ns](1), float64(4), int64(11), object(15)`
>
>`memory usage: 24.5+ MB`
