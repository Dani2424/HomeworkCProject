# HomeworkCProject
tareas


library(readr)
library(lubridate)

household_power_consumption <- read_csv("household_power_consumption.csv")
household_power_consumption$Date<-dmy(household_power_consumption$Date)
fe<-household_power_consumption[household_power_consumption$Date>="2007-02-01",]
feb<-fe[fe$Date<="2007-02-02",]
feb = feb[!is.na(feb$Date),]  

#ready date 

#plot1
hist(feb$Global_active_power,col="red", main="Global active Power" , xlab="Global Active Power (kilowatts)",breaks=200)

#plot2

feb= feb[order(feb$Date),]  #order
plot(feb$Time,feb$Global_active_power,pch=19,ty="s",xlab=NA, ylab="Global Active Power (kilowatts)", ylim=c(0,8))
```
#plot3
library(ggplot2)
ggplot(feb, aes(x=Time,y=Sub_metering_1))+ geom_line()+ geom_line(y=feb$Sub_metering_2, color="red")+ geom_line(y=feb$Sub_metering_3, color="blue")

#plot4

par(mfrow=c(2,2),mar=c(4,4,2,1),oma=c(0,0,2,0))

plot(feb$Time,feb$Global_active_power,pch=19,ty="s",xlab=NA, ylab="Global Active Power (kilowatts)", ylim=c(0,8))
ggplot(feb, aes(x=Time,y=Sub_metering_1))+ geom_line()+ geom_line(y=feb$Sub_metering_2, color="red")+ geom_line(y=feb$Sub_metering_3, color="blue")
plot(feb$Time,feb$Voltage,pch=19,ty="s", xlab="datetime", ylab = "Voltage")
plot(feb$Time,feb$Global_reactive_power,pch=19,ty="s", xlab="datetime")
