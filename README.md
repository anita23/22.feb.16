# 22.feb.16
library(foreign)
require(foreign)
baseinegi <- read.dbf("C:\\Users\\SALA-C9\\Downloads\\SDEMT215.dbf")
baseinegi<-data.frame(baseinegi)### hacemos la base data
help(str)
str(baseinegi)
attach(baseinegi)
table(SEX)
table(EDA)
EDA1<- as.numeric(as.character(EDA))###CAMBIA NUMERICO
table(EDA1)
install.packages("memisc")
install.packages("lattice")
install.packages("MASS")
install.packages("car")
require(car)
require(memisc)
require(lattice)
require(MASS)


### PONderar casos###
install.packages("questionr")
require("questionr")
c1<-wtd.table(baseinegi$SEX, weights=baseinegi$FAC)#### para expandir las diferentes variables
table(c1)
c0<- table(baseinegi$SEX)
c0
write.csv(c1,file= 'C:\\Users\\SALA-C9\\Desktop\\practicaseries.csv')### para salvar en excel 
###porcentajes#####
tabrama<-wtd.table(baseinegi$SEX, weights = baseinegi$fac)
c1.1<-round((tabrama/margin.table(tabrama))*100, 2)
c1.1
write.csv(c1.1,file= 'C:\\Users\\SALA-C9\\Desktop\\practicaseries1.csv')
### ocupados y no ocupados###
baseinegi$SEX<- ordered(baseinegi$SEX, levels = c(1,2), labels = c("hombres", "mujeres"))
c2<- wtd.table(baseinegi$SEX, weights = baseinegi$Fac)
c2

baseinegi$NAC_MES<- ordered(baseinegi$NAC_MES, levels = c("01","02","03","04","05","06","07","08","09","10","11","12","99"), labels = c("enero", "febrero","marzo","abril", "mayo", "junio", "julio", "agosto","septiembre", "octubre", "noviembre", "diciembre", "noespecificado"))
c3<- wtd.table(baseinegi$NAC_MES, weights = baseinegi$FAC)
View(baseinegi)
table(baseinegi$NAC_MES)
c3
