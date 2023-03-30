# Client Report - Daniel Dominguez
__Course CSE 250__

In this project, we explored how certain names have been used over time by analyzing a given dataset. We investigated four different questions related to the popularity and trends of specific names in different time periods.

For example, in question 1, we examined the popularity of the name "Daniel" over the years and noticed that the maximum number of people named "Daniel" was in 1990, which may explain why the person conducting the analysis was given this name, as it was quite trendy in the early 90s.

In question 2, we focused on the popularity of the name "Brittany" and observed that it reached its peak in the 1990s, which suggests that most women named Brittany may be in their 20s or 40s.

In question 3, we looked at the trends in popularity of several Christian names (Martha, Mary, Paul, and Peter) and found that they have become less popular over time.

Finally, in question 4, we analyzed the popularity of the first names of the main and secondary characters in the movie "Back to the Future" (Marty, Jennifer, Emmett, Lorraine, and George) and created a chart showing how their usage has changed over time.

Overall, our project aimed to explore the changes in popularity of certain names over time and present the findings in a simplified, easy-to-understand manner.

#### Question 1

For question 1 as my name being Daniel and I was born on 1994 I marked on the graph with a line my year of birth. Something that I noticed is a that the maximum of more people named "Daniel" was in 1990 so pretty sure my mother picked the name with that being so trendy in the early 90's.

![](question1.png)

```python 
#Question 1 
daniel = names.query("name == 'Daniel'")
dan_chart = (alt.Chart(daniel, title = "Usage of the name Daniel along the years")
    .mark_bar(color= 'red')
    .encode(x=  alt.X('year', axis = alt.Axis(format = 'd', title = "Year")),
            y= 'Total'
    ))

line_d = alt.Chart(names).mark_rule(color="red").encode(x = "year")
daniel96 = names.query("name == 'Daniel' & year == 1994")
dan_chart_f = dan_chart + line_d
dan_chart_f.save("Question1.png")
```



#### Question 2
We can probably see in the chart that Brittany was quite popular in the 80's-90's. Reaching it's peak in the 1990. So by observing this, we might find most of the Women named Brittany between their 40's or 20's


![](question2.png)  

```python 
britt = names.query("name == 'Brittany'")

britt_chart = (alt.Chart(britt, title = "How old would Brittany be...?")
    .mark_bar()
    .encode(x=  alt.X('year', axis = alt.Axis(format = 'd', title = "Year")),
            y= 'Total'
    ))
britt_chart.save("question2.png")britt = names.query("name == 'Brittany'")

```

#### Question 3
For the this question an important relationship that we can find between the different names given to search about. You can see that this christian names are getting less used with the pass of the years. It would be interesting to find if this is happening with more christian names.

![](question3.png)

```python 
names_trends =(alt.Chart(q3, title = "Popularity of the names Martha, Mary, Paul, and Peter from 1920 to 2000")
    .mark_line(point=True)
    .encode( x = alt.X('year', axis = alt.Axis(format = 'd', title = "Year")), 
            y= alt.Y('Total', axis = alt.Axis(title = "People")), 
            color = alt.Color('name', scale=alt.Scale(scheme='category10')))
).interactive()
names_trends.save("question3.png")
```

#### Question 4

I picked the movie "Back to the Future" I really like that movie, I picked the first names of the principal and secondary characters of the movie like: Marty, Lorraine, Emmett, George, and Jennifer. I also tried the name Biff, but there is no data about someone named Biff in the given dataset.

![](question4.png)

```python 
back2future = ["Marty", "Jennifer", "Emmett", "Lorraine", "George"]
back2future_q = names.query('name == @back2future')

b2f_chart = (alt.Chart(back2future_q, title = "How big were the names of the Back to the Future movie characters")
    .mark_line()
    .encode(x=  alt.X('year', axis = alt.Axis(format = 'd', title = "Year")) ,
            y= 'Total',
            color = alt.Color('name', scale=alt.Scale(scheme='dark2')
    )))
line_df = pd.DataFrame({'year': [1985]})
line = alt.Chart(line_df).mark_rule(color="red").encode(x = "year")

b2f_final_chart = b2f_chart + line
b2f_final_chart.save("question4.png")
```

