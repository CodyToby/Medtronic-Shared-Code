# Medtronic-Shared-Code
# LOADING DATA
data <- read.csv('data.csv', sep = ',', header=TRUE)

#Split Year variable
data$year <- substr(data$Fiscal.Year, start=3, stop=6)

#exclude index
data <- data[,-1]
data$month <- ifelse(data$Fiscal.Month  =="DEC", "12", ifelse(data$Fiscal.Month  =='NOV', "11", ifelse(data$Fiscal.Month  =='OCT', "10", ifelse(data$Fiscal.Month =='SEP', "9", ifelse(data$Fiscal.Month  =='AUG', "8", ifelse(data$Fiscal.Month  =='JUN', "7", ifelse(data$Fiscal.Month =='JUL', "6", ifelse(data$Fiscal.Month  =='MAY', "5", ifelse(data$Fiscal.Month  =='APR',"4", ifelse(data$Fiscal.Month  =='MAR', "3", ifelse(data$Fiscal.Month  =='FEB', "2", ifelse(data$Fiscal.Month  =='JAN', "1", data$Fiscal.Month))))))))))))


data$Date <- paste0(as.numeric(data$year),'-', as.numeric(data$month))
data$Date <- as.yearmon(data$Date, "%Y-%m")

#NAMING VARIABLES
names(data)
names(data) <- c('FYEAR',  'FQUARTER', 'FMONTH', 'GEO_NAME', 'GEO_REGION', 'COUNTRY_CLUSTER', 'COUNTRY_NAME', 'L1', "L2", 'PRODUCT_ID', 'CUSTOMER', 'SALES_QTY','YEAR', 'MONTH', 'DATE')

