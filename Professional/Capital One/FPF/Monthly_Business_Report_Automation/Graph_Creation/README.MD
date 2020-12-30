# Graph Creation

The two scripts in this repository are samples containing the general structure and logic in pulling data from the tables created in the Data Creation folder.

From there the Spark dataframe is converted to Pandas for data wrangling and formatting. 

After that, the
    
    ppt.createChart(), 
    ppt.createTable(),
    ppt.createSlide(),
    ppt.createDeck(),
    
functions are called.

As you will see in the script, the functions take a dataframe, and organize it into the chart type of your choice or a table. To create our slides, we have our core data in the graph, with a table that has month-over-month percent difference of the key metrics to help layer context onto the raw data itself.

## Example output can be found as the jpg file in the earlier folder (FPF)
