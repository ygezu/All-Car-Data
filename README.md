# All-Car-Data
## Contributors
Summer Chalmers, Yanet Gezu, and Patrick Mayer

## Introduction
Data Cruisers and seven other groups collected data from a speed detection radar located on 30th St and 24th Avenue in Rock Island IL. This data included speed, time, weather, temperature, type of car, and who collected the data. Our group found that the best three variables in common within all the groups were speed, time, and temperature. Using these variables we conducted the same analysis as we did with our own data, finding the maximum and minimum speed as well as the average speed of every group that collected data. The times of the data being collected range from early morning times to late into the evening. We will finish off our analysis by correlating these results with our scholarly research. 

## Data Dictionary
1. Group One = CarData(2)
2. Group Two = IRL_Car_Data
3. Group Three = Car_Data
4. Group Four = Car
5. Group Five = counting_cars
6. Group Six = MergedCarData
7. Group Seven = Speed analyst 332 Car Data
8. Group Eight = Updated Car Tracking

None of these groups are in any particular order

## Data Cleaning

This is all the code used to clean the data and make variables usable for our shiny application, such as changing names to Name or the speed to Speed instead of mph. 


1. Adding "Type" and "Group" variables with default values "NA" and "G1" respectively.

        cars1 <- cars1[, c(2,4,5,8)] #No type recorded

        cars1$Type <- "NA"

        cars1$Group <- "G1"
 
2. Removing unnecessary columns, adding "Type" and "Group" with default values, and renaming columns.
        #cars2 No Car type
   
        cars2 <- cars2[, -c(4,5)] #No type recorded
        cars2$Type <- "NA" 
        cars2$Group <- "G2"
        names(cars2)[names(cars2) == "Collector"] <- "Name"
        names(cars2)[names(cars2) == "Time.of.Day"] <- "Time"
        names(cars2)[names(cars2) == "MPH"] <- "Speed"


`#cars3`

`cars3 <- cars3[, -c(1,4,7)]`

`cars3$Group <- "G3"`

`#cars4`

`cars4 <- cars4[, c(1, 5,7,9,10)]`


`cars4$Group <- "G4"`

`names(cars4)[names(cars4) == "Collector.Name"] <- "Name"`

`names(cars4)[names(cars4) == "Vehicle.Type"] <- "Type"`

`names(cars4)[names(cars4) == "Speed.MPH"] <- "Speed"`


`#cars5`

`cars5 <- cars5[, c(2, 3, 4)] #NO type recorded`


`cars5$Group <- "G5"`

`names(cars5)[names(cars5) == "MPH"] <- "Speed"`

`names(cars5)[names(cars5) == "Temp"] <- "Temperature"`


`cars5$Name <- "NA"`

`cars5$Type <- "NA"`


`#cars6`

`cars6 <- cars6[, c(2,3,7,8)] #NO type recorded`


`cars6$Type <- "NA"`

`cars6$Group <- "G6"`


`#cars7`

`cars7 <- cars7[, c(1,3,4,5,7)]`


`cars7$Group <- "G7"`

`names(cars7)[names(cars7) == "Student"] <- "Name"`

`names(cars7)[names(cars7) == "MPH"] <- "Speed"`

`names(cars7)[names(cars7) == "Type.of.se"] <- "Type"`

`names(cars7)[names(cars7) == "Time.of.Day"] <- "Time"`


`#cars8`

`cars8 <- cars8[, -c(1)]`


`cars8$Group <- "G8"`

`names(cars8)[names(cars8) == "Time.of.Day"] <- "Time"`

`names(cars8)[names(cars8) == "Type.of.Car"] <- "Type"`

`names(cars8)[names(cars8) == "Speed..mph."] <- "Speed"`

`names(cars8)[names(cars8) == "Weather"] <- "Temperature"`




#FIX TIME

`cars1$Time <- strptime(cars1$Time, format = "%H:%M")`

`cars1$Time <- format(cars1$Time, format = "%I:%M %p")`

`cars1$Time <- sub("AM", "PM", cars1$Time)`

`#cars2$Time <- strptime(cars2$Time, format = "%H:%M")`

`#cars2$Time <- format(cars2$Time, format = "%I:%M %p")`

`cars4$Time <- strptime(cars4$Time, format = "%H:%M")`

`cars4$Time <- format(cars4$Time, format = "%I:%M %p")`

`cars3$Time <- strptime(cars3$Time, format = "%H:%M")`

`cars3$Time <- format(cars3$Time, format = "%I:%M %p")`

`cars5$Time <- format(as.POSIXct(cars5$Time, format = "%I:%M:%S %p"), format = "%I:%M %p")`

`cars6$Time <- strptime(cars6$Time, format = "%H:%M")`

`cars6$Time <- format(cars6$Time, format = "%I:%M %p")`

`to_change_indices <- as.numeric(substring(cars6$Time, 1, 2)) >= 1 & as.numeric(substring(cars6$Time, 1, 2)) <= 7`

`cars6$Time[to_change_indices] <- sub("AM", "PM", cars6$Time[to_change_indices])`

`cars7$Time <- strptime(cars7$Time, format = "%H:%M")`

`cars7$Time <- format(cars7$Time, format = "%I:%M %p")`

`cars7$Time <- sub("AM", "PM", cars7$Time)`

`cars8$Time <- strptime(cars8$Time, format = "%H:%M")`

`cars8$Time <- format(cars8$Time, format = "%I:%M %p")`



`#REMOVING NULL`

`cars1 <- head(cars1, -2)`

`cars3 <- head(cars3 , -8)`

`cars5 <- head(cars5, -53)`

## Maximum

Presented is the graph of the fastest car recorded out of all groups which was 50 miles per hour
<div align = "center">
<img src ="https://github.com/ygezu/All-Car-Data/blob/main/MaxAllData.png" width = "700">
</div>

## Minimum

Presented is the graph of the slowest car recorded out of all groups which was 12 miles per hour
<div align = "center">
<img src ="https://github.com/ygezu/All-Car-Data/blob/main/MinAllData.png" width = "700">
</div>

## Average

We took the average speed of each car type and found that every cars speed was over the speed limit of 30 miles per hour. If car type was not recorded it was labeled as NA.
<div align = "center">
<img src ="https://github.com/ygezu/All-Car-Data/blob/main/AverageByCarAll.png" width = "700">
</div>

## Bigger Picture

Here we plotted everyone's data with the different colors corresponding to different groups. The x-axis is time(in miliary time) and the y-axis is the speed (in miles per hour).
<div align = "center">
<img src ="https://github.com/ygezu/All-Car-Data/blob/main/EveryonesData.png" width = "700">
</div>

## Analysis

As shown in the previous picture all the data is one place presented by time and speed. This data still supports our orginal theory that cars speed more in the PM rather than in the AM as scholarly reseach stated. Yes most of the cars go over the speed limit of 30 miles per hour, but the majority of the points that do are in the later hours of the day. Every car's average speed was over 30 miles per hour, roughly at 33 miles per hour. 

