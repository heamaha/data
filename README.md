# data

---


```
heamaha@redington MINGW64 ~

$ pwd

/c/Users/heamaha

heamaha@redington MINGW64 ~

$ cd Documents/General\ Assembly/Data\ Sets/
```

**1. Look at the head and the tail of chipotle.tsv in the data subdirectory of this repo. Think for a minute about how the data is structured.**

`$ head chipotle.tsv`

|order_id        |quantity        |item_name       |choice_description      |item_price|
|----------------|----------------|----------------|------------------------|----------|
|1       |1       |Chips and Fresh Tomato Salsa    |NULL    |$2.39|
|1       |1       |Izze    |[Clementine]    |$3.39|
|1       |1       |Nantucket Nectar        |[Apple] |$3.39|
|1       |1       |Chips and Tomatillo-Green Chili Salsa   |NULL    |$2.39|
|2       |2       |Chicken Bowl    |[Tomatillo-Red Chili Salsa (Hot), [Black Beans, Rice, Cheese, Sour Cream]]     |$16.98|
|3       |1       |Chicken Bowl    |[Fresh Tomato Salsa (Mild), [Rice, Cheese, Sour Cream, Guacamole, Lettuce]]    |$10.98|
|3       |1       |Side of Chips   |NULL    |$1.69|
|4       |1       |Steak Burrito   |[Tomatillo Red Chili Salsa, [Fajita Vegetables, Black Beans, Pinto Beans, Cheese, Sour Cream, Guacamole, Lettuce]]     |$11.75|
|4       |1       |Steak Soft Tacos        |[Tomatillo Green Chili Salsa, [Pinto Beans, Cheese, Sour Cream, Lettuce]]      |$9.25|

```
heamaha@redington MINGW64 ~/Documents/General Assembly/Data Sets

$ tail chipotle.tsv
```

|        |        |       |      |      |
|--------|--------|-------|------|------|
|1831    |1       |Carnitas Bowl   |[Fresh Tomato Salsa, [Fajita Vegetables, Rice, Black Beans, Cheese, Sour Cream, Lettuce]]      |$9.25|
|1831    |1       |Chips   |NULL    |$2.15|
|1831    |1       |Bottled Water   |NULL    |$1.50|
|1832    |1       |Chicken Soft Tacos      |[Fresh Tomato Salsa, [Rice, Cheese, Sour Cream]]        |$8.75|
|1832    |1       |Chips and Guacamole     |NULL    |$4.45|
|1833    |1       |Steak Burrito   |[Fresh Tomato Salsa, [Rice, Black Beans, Sour Cream, Cheese, Lettuce, Guacamole]]      |$11.75|
|1833    |1       |Steak Burrito   |[Fresh Tomato Salsa, [Rice, Sour Cream, Cheese, Lettuce, Guacamole]]  |$11.75|
|1834    |1       |Chicken Salad Bowl      |[Fresh Tomato Salsa, [Fajita Vegetables, Pinto Beans, Guacamole, Lettuce]]     |$11.25|
|1834    |1       |Chicken Salad Bowl      |[Fresh Tomato Salsa, [Fajita Vegetables, Lettuce]]      |$8.75|
|1834    |1       |Chicken Salad Bowl      |[Fresh Tomato Salsa, [Fajita Vegetables, Pinto Beans, Lettuce]]|$8.75|


**1. (cont'd) What do you think each column means?**

* The first column is labeled order_id.  It is a positive integer that respresents a unique identifier for each order.
* The second column is labeled quantity.  It is a positive integer that represents the number of items ordered in the next column, item_name.
* The third column is labeled item_name.  It is a text string that describes of the item on the menu that is ordered
* The fourth column is labeled choice_description.  It is a text string that describes details and options for the item_name.
* The fifth column is labeled item_price.  It is likely stored as a text string with a dollar sign and text representation of a float number with 2 decimal places to represent the cost of the item_name.

---

**1. (cont'd) What do you think each row means?**

Each row represents a specific and unique item on an order.  In relational database terms, the "primary key" for a row would be comprised of both the order_id and item_name.

---

**2. How many orders do there appear to be?**

The order_id appreas to start at "1" and go to "1834", which gives the impression there are 1834 orders.  This could be confirmed by using the unique command on that column to report the number of unique values in that column in this dataset.

---

**3. How many lines are in this file?**

```
$ wc chipotle.tsv

  4623  55837 364975 chipotle.tsv
  ```

There are 4,623 lines in this file.

---

**4. Which burrito is more popular, steak or chicken?**

```
heamaha@redington MINGW64 ~/Documents/General Assembly/Data Sets

$ grep -i 'Steak Burrito' chipotle.tsv  | wc

    368    5621   38547

```

There are 368 'Steak Burrito' item_name rows, which seems to indicate 368 steak burrito orders.

Note:  I used the -i option for grep to ensure that both upper case and lower case entries were included in the counts.

```
heamaha@redington MINGW64 ~/Documents/General Assembly/Data Sets

$ grep -i 'Chicken Burrito' chipotle.tsv | wc

    553    8168   56987
```

There are 553 'Chicken Burrito' item_name rows, which seems to indicate 368 steak burrito orders.

Note:  I used the -i option for grep to ensure that both upper case and lower case entries were included in the counts.

It appears that the chicken burrito is more popular, with 553 chicken burritos ordered as compared to 368 steak burritos.

---

**5. Do chicken burritos more often have black beans or pinto beans?**

```
heamaha@redington MINGW64 ~/Documents/General Assembly/Data Sets

$ grep -i 'Chicken Burrito' chipotle.tsv | grep -i 'Black Beans' | wc

    282    4416   30725
```

There are 282 'Chicken Burrito' item_name rows, which also have 'Black Beans' listed in the choice_description of that row.

Note:  I used the -i option for grep to ensure that both upper case and lower case entries were included in the counts.

```
heamaha@redington MINGW64 ~/Documents/General Assembly/Data Sets

$ grep -i 'Chicken Burrito' chipotle.tsv | grep -i 'Pinto Beans' | wc

    105    1745   12304
```

There are 105 'Chicken Burrito' item_name rows, which also have 'Pinto Beans' listed in the choice_description of that row.

Note:  I used the -i option for grep to ensure that both upper case and lower case entries were included in the counts.

It appears that the chicken burritos have black beans more often than pinto beans.

---

**6. Make a list of all of the CSV or TSV files in the GA-SEA-DAT1 repo (using a single command). You will be working on your local repo on your laptop. Think about how wildcard characters can help you with this task.**

```
heamaha@redington MINGW64 ~/Documents/General Assembly/Data Sets

$ ls *.*sv

Airline_on_time_west_coast.csv  chipotle.tsv
```

---

**7. Count the approximate number of occurrences of the word "dictionary" (regardless of case) across all files in the GA-SEA-DAT1 repo.**

```
heamaha@redington MINGW64 ~/Documents/General Assembly/Data Sets

$ cat * | grep -i dictionary | wc

      0       0       0
```

---

**8. Optional: Use the the command line to discover something "interesting" about the Chipotle data. Try using the commands from the "advanced" section!**

How many people ordered plain chips with no salsa or guacamole?

```
heamaha@redington MINGW64 ~/Documents/General Assembly/Data Sets

$ grep -i chips chipotle.tsv | grep -i -v tomatillo | grep -i -v guacamole | grep -i -v fresh | grep -i -v corn | wc

    312    1762    8427
```

