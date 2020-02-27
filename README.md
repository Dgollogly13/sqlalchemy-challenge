# SQL Alchemy Challenge

The goal of this challenge was to master advanced data storage and retrieval using a variety of programming language libraries and applications. I was tasked with querying the necessary data, transforming it into a digestible format, and then creating a flask server where the transformed data would be called and displayed for the user. 

### Analysis and Coding 

I started this challenge by connecting to my sqlite database in order to pull the necessary information for transforming. I queried the data and plotted it with matplotlib to get a better picture of what the data was describing. 

```
Results = session.query(Measurement.date, Measurement.prcp).filter(Measurement.date >= dt.date(2016, 8, 23)).all()
prec_df = pd.DataFrame(Results, columns=['Year', 'Precipitation'])
prec_df.set_index(prec_df['Year'], inplace=True)
prec_sort = prec_df.sort_index()
prec_sort

Year	Precipitation	
2016-08-23	0.00
2016-08-23	NaN
2016-08-23	1.79
2016-08-23	0.05
2016-08-23	0.15
```
This process was repeated a few times to pull average temperature, weather station total rainfall, and a few other variables. Once the queries were completed, I started work on my flask application. I created an API app with python that allowed the user to click through various pages to see the queried data. 

```
@app.route("/api/v1.0/stations")
def stations():
    results = session.query(Station.name).all()
    all_stations = list(np.ravel(results))
    return jsonify(all_stations)
```

### Challenges or Additional Opportunities

The main challenges throughout this project were mastering sqlalchemy versus the native SQL language, mapping the routes correctly using flask, and calling the information correctly in flask. It was a fantastic project to work on as I learned a variety of new skills and got some real expereince with object-related mapping.

Some additional opportunities include querying the data in other unique ways to get an even more comprehensible view of the dataset and other weather specifics as well as fine-tuning the user interface in the API app. The user interface was fairly basic as I spent much more time on mastering sqlalchemy and creating my app routes correctly. 

### Built With

* Numpy 
* Pandas
* Datetime 
* Sqlalchemy
* Flask
* Matplotlib

### Authors

* **Dallas Gollogly** - [dgollogly13](https://github.com/dgollogly13)

### Acknowledgments

* Denver University Data Analytics Bootcamp 
