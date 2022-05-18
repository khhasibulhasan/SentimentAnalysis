# SentimentAnalysis
Restaurants receive many comments from customers, so analyzing those customers comments can be a great source of information for a restaurant.


#Step 1: Installing packages
install.packages("tm")
install.packages("wordcloud")
install.packages("SnowballC")

#Step 2: Activating Packages
library(tm)
library(wordcloud)
library(SnowballC)

#Step 3: Reading Dataset
Reviews <- read.csv("tourist_accommodation_reviews.csv")

#Step 4: Viewing the dataset
View(Reviews)

#Step 5: Checking the dataset
names(Reviews)
head(Reviews)
tail(Reviews)
summary(Reviews)
str(Reviews)
dim(Reviews)

#Step 06: Restaurant Selection
R001_Thong <- subset(Reviews, Hotel.Restaurant.name=="Thong Dee The Kathu Brasserie")
R002_Odysseus <- subset(Reviews, Hotel.Restaurant.name=="Odysseus Greek Organic Restaurant")
R003_Green <- subset(Reviews, Hotel.Restaurant.name=="Green Tamarind Kitchen")
R004_Dee <- subset(Reviews, Hotel.Restaurant.name=="Dee Plee - Anantara Layan Phuket Resort")
R005_Tavern <- subset(Reviews, Hotel.Restaurant.name=="The Tavern")
R006_EAT <- subset(Reviews, Hotel.Restaurant.name=="EAT. bar & grill")
R007_Surf <- subset(Reviews, Hotel.Restaurant.name=="Surf and Turf by Soul Kitchen")
R008_Siam <- subset(Reviews, Hotel.Restaurant.name=="Siam Supper Club")
R009_Sams <- subset(Reviews, Hotel.Restaurant.name=="Sam's Steaks and Grill")
R010_Istanbul <- subset(Reviews, Hotel.Restaurant.name=="Istanbul Turkish Restaurant")
R011_Corner <- subset(Reviews, Hotel.Restaurant.name=="The Corner Restaurant")
R012_Kataturk <- subset(Reviews, Hotel.Restaurant.name=="Kataturk Turkish Restaurant")
R013_Sawasdee <- subset(Reviews, Hotel.Restaurant.name=="Sala Sawasdee Lobby Bar")
R014_Palm <- subset(Reviews, Hotel.Restaurant.name=="The Palm Cuisine")
R015_Highway <- subset(Reviews, Hotel.Restaurant.name=="Highway Curry Indian & Thai Cuisine")
R016_Tandoori <- subset(Reviews, Hotel.Restaurant.name=="Tandoori Flames")
R017_Pad <- subset(Reviews, Hotel.Restaurant.name=="Pad Thai Shop")
R018_Golden <- subset(Reviews, Hotel.Restaurant.name=="Golden Paradise Restaurant")
R019_Coffee <- subset(Reviews, Hotel.Restaurant.name=="Mr.Coffee")
R020_Flavor <- subset(Reviews, Hotel.Restaurant.name=="Flavor Phuket")
R021_Baan <- subset(Reviews, Hotel.Restaurant.name=="Baan Noy Restaurant")
R022_Chalong <- subset(Reviews, Hotel.Restaurant.name=="Ao Chalong Yacht Club Restaurant")
R023_Naughty <- subset(Reviews, Hotel.Restaurant.name=="Naughty Nuri's Phuket")
R024_Surin <- subset(Reviews, Hotel.Restaurant.name=="Surin Chill House")
R025_Natural <- subset(Reviews, Hotel.Restaurant.name=="Natural Efe Macrobiotic World")
R026_Honeymoon <- subset(Reviews, Hotel.Restaurant.name=="Honeymoon Thai Restaurant by Kenya")
R027_Farm <- subset(Reviews, Hotel.Restaurant.name=="O-OH Farm Ta-Eiad")
R028_Puccio <- subset(Reviews, Hotel.Restaurant.name=="Da Puccio Restaurant")
R029_Sizzle <- subset(Reviews, Hotel.Restaurant.name=="Sizzle Rooftop Restaurant")
R030_American <- subset(Reviews, Hotel.Restaurant.name=="Benny's American Bar & Grill")

#Step 7: FOR CHECKING BY DISPLAYING THE VIEW
View(R030_American)

#Step 8: CHECKING THE HEAD ROWS
head(R001_Thong$Review)
head(R002_Odysseus$Review)
head(R003_Green$Review)
head(R004_Dee$Review)
head(R005_Tavern$Review)
head(R006_EAT$Review)
head(R007_Surf$Review)
head(R008_Siam$Review)
head(R009_Sams$Review)
head(R010_Istanbul$Review)
head(R011_Corner$Review)
head(R012_Kataturk$Review)
head(R013_Sawasdee$Review)
head(R014_Palm$Review)
head(R015_Highway$Review)
head(R016_Tandoori$Review)
head(R017_Pad$Review)
head(R018_Golden$Review)
head(R019_Coffee$Review)
head(R020_Flavor$Review)
head(R021_Baan$Review)
head(R022_Chalong$Review)
head(R023_Naughty$Review)
head(R024_Surin$Review)
head(R025_Natural$Review)
head(R026_Honeymoon$Review)
head(R027_Farm$Review)
head(R028_Puccio$Review)
head(R029_Sizzle$Review)
head(R030_American$Review)

#STEP 9: CREATION OF TEXT VECTOR
Review_R001_Thong <-R001_Thong$Review
Review_R002_Odysseus <- R002_Odysseus$Review
Review_R003_Green <- R003_Green$Review
Review_R004_Dee <- R004_Dee$Review
Review_R005_Tavern <- R005_Tavern$Review
Review_R006_EAT <- R006_EAT$Review
Review_R007_Surf <- R007_Surf$Review
Review_R008_Siam <- R008_Siam$Review
Review_R009_Sams <- R009_Sams$Review
Review_R010_Istanbul<- R010_Istanbul$Review
Review_R011_Corner<- R011_Corner$Review
Review_R012_Kataturk<- R012_Kataturk$Review
Review_R013_Sawasdee<-R013_Sawasdee$Review
Review_R014_Palm<-R014_Palm$Review
Review_R015_Highway<-R015_Highway$Review
Review_R016_Tandoori<-R016_Tandoori$Review
Review_R017_Pad<-R017_Pad$Review
Review_R018_Golden<-R018_Golden$Review
Review_R019_Coffee<-R019_Coffee$Review
Review_R020_Flavor<-R020_Flavor$Review
Review_R021_Baan<-R021_Baan$Review
Review_R022_Chalong<-R022_Chalong$Review
Review_R023_Naughty<-R023_Naughty$Review
Review_R024_Surin<-R024_Surin$Review
Review_R025_Natural<-R025_Natural$Review
Review_R026_Honeymoon<-R026_Honeymoon$Review
Review_R027_Farm<-R027_Farm$Review
Review_R028_Puccio<-R028_Puccio$Review
Review_R029_Sizzle<-R029_Sizzle$Review
Review_R030_American<-R030_American$Review


#Rule 10: Convert all text to lower case
Review_R001_Thong <- tolower(Review_R001_Thong)
Review_R002_Odysseus <- tolower(Review_R002_Odysseus)
Review_R003_Green <- tolower(Review_R003_Green)
Review_R004_Dee <- tolower(Review_R004_Dee)
Review_R005_Tavern <- tolower(Review_R005_Tavern)
Review_R006_EAT <- tolower(Review_R006_EAT)
Review_R007_Surf <- tolower(Review_R007_Surf)
Review_R008_Siam <- tolower(Review_R008_Siam)
Review_R009_Sams <- tolower(Review_R009_Sams)
Review_R010_Istanbul<- tolower(Review_R010_Istanbul)
Review_R011_Corner<- tolower(Review_R011_Corner)
Review_R012_Kataturk<- tolower(Review_R012_Kataturk)
Review_R013_Sawasdee<-tolower(Review_R013_Sawasdee)
Review_R014_Palm<-tolower(Review_R014_Palm)
Review_R015_Highway<-tolower(Review_R015_Highway)
Review_R016_Tandoori<-tolower(Review_R016_Tandoori)
Review_R017_Pad<-tolower(Review_R017_Pad)
Review_R018_Golden<-tolower(Review_R018_Golden)
Review_R019_Coffee<-tolower(Review_R019_Coffee)
Review_R020_Flavor<-tolower(Review_R020_Flavor)
Review_R021_Baan<-tolower(Review_R021_Baan)
Review_R022_Chalong<-tolower(Review_R022_Chalong)
Review_R023_Naughty<-tolower(Review_R023_Naughty)
Review_R024_Surin<-tolower(Review_R024_Surin)
Review_R025_Natural<-tolower(Review_R025_Natural)
Review_R026_Honeymoon<-tolower(Review_R026_Honeymoon)
Review_R027_Farm<-tolower(Review_R027_Farm)
Review_R028_Puccio<-tolower(Review_R028_Puccio)
Review_R029_Sizzle<-tolower(Review_R029_Sizzle)
Review_R030_American<-tolower(Review_R030_American)

#Rule 11: Remove links from the rewiews
Review_R001_Thong <- gsub("http\\S+\\s*", "", Review_R001_Thong)
Review_R002_Odysseus <- gsub("http\\S+\\s*", "", Review_R002_Odysseus)
Review_R003_Green <- gsub("http\\S+\\s*", "", Review_R003_Green)
Review_R004_Dee <- gsub("http\\S+\\s*", "", Review_R004_Dee)
Review_R005_Tavern <- gsub("http\\S+\\s*", "", Review_R005_Tavern)
Review_R006_EAT <- gsub("http\\S+\\s*", "", Review_R006_EAT)
Review_R007_Surf <- gsub("http\\S+\\s*", "", Review_R007_Surf)
Review_R008_Siam <- gsub("http\\S+\\s*", "", Review_R008_Siam)
Review_R009_Sams <- gsub("http\\S+\\s*", "", Review_R009_Sams)
Review_R010_Istanbul<- gsub("http\\S+\\s*", "", Review_R010_Istanbul)
Review_R011_Corner<- gsub("http\\S+\\s*", "", Review_R011_Corner)
Review_R012_Kataturk<- gsub("http\\S+\\s*", "", Review_R012_Kataturk)
Review_R013_Sawasdee<- gsub("http\\S+\\s*", "", Review_R013_Sawasdee)
Review_R014_Palm<- gsub("http\\S+\\s*", "", Review_R014_Palm)
Review_R015_Highway<- gsub("http\\S+\\s*", "", Review_R015_Highway)
Review_R016_Tandoori<- gsub("http\\S+\\s*", "", Review_R016_Tandoori)
Review_R017_Pad<- gsub("http\\S+\\s*", "", Review_R017_Pad)
Review_R018_Golden<- gsub("http\\S+\\s*", "", Review_R018_Golden)
Review_R019_Coffee<- gsub("http\\S+\\s*", "", Review_R019_Coffee)
Review_R020_Flavor<- gsub("http\\S+\\s*", "", Review_R020_Flavor)
Review_R021_Baan<- gsub("http\\S+\\s*", "", Review_R021_Baan)
Review_R022_Chalong<- gsub("http\\S+\\s*", "", Review_R022_Chalong)
Review_R023_Naughty<- gsub("http\\S+\\s*", "", Review_R023_Naughty)
Review_R024_Surin<- gsub("http\\S+\\s*", "", Review_R024_Surin)
Review_R025_Natural<- gsub("http\\S+\\s*", "", Review_R025_Natural)
Review_R026_Honeymoon<- gsub("http\\S+\\s*", "", Review_R026_Honeymoon)
Review_R027_Farm<- gsub("http\\S+\\s*", "", Review_R027_Farm)
Review_R028_Puccio<- gsub("http\\S+\\s*", "", Review_R028_Puccio)
Review_R029_Sizzle<- gsub("http\\S+\\s*", "", Review_R029_Sizzle)
Review_R030_American<- gsub("http\\S+\\s*", "", Review_R030_American)

#rule no 12: Remove Punctuation
Review_R001_Thong <- gsub("[[:punct:]]", "", Review_R001_Thong)
Review_R002_Odysseus <- gsub("[[:punct:]]", "", Review_R002_Odysseus)
Review_R003_Green <- gsub("[[:punct:]]", "", Review_R003_Green)
Review_R004_Dee <- gsub("[[:punct:]]", "", Review_R004_Dee)
Review_R005_Tavern <- gsub("[[:punct:]]", "", Review_R005_Tavern)
Review_R006_EAT <- gsub("[[:punct:]]", "", Review_R006_EAT)
Review_R007_Surf <- gsub("[[:punct:]]", "", Review_R007_Surf)
Review_R008_Siam <- gsub("[[:punct:]]", "", Review_R008_Siam)
Review_R009_Sams <- gsub("[[:punct:]]", "", Review_R009_Sams)
Review_R010_Istanbul<- gsub("[[:punct:]]", "", Review_R010_Istanbul)
Review_R011_Corner<- gsub("[[:punct:]]", "", Review_R011_Corner)
Review_R012_Kataturk<- gsub("[[:punct:]]", "", Review_R012_Kataturk)
Review_R013_Sawasdee<- gsub("[[:punct:]]", "", Review_R013_Sawasdee)
Review_R014_Palm<- gsub("[[:punct:]]", "", Review_R014_Palm)
Review_R015_Highway<- gsub("[[:punct:]]", "", Review_R015_Highway)
Review_R016_Tandoori<- gsub("[[:punct:]]", "", Review_R016_Tandoori)
Review_R017_Pad<- gsub("[[:punct:]]", "", Review_R017_Pad)
Review_R018_Golden<- gsub("[[:punct:]]", "", Review_R018_Golden)
Review_R019_Coffee<- gsub("[[:punct:]]", "", Review_R019_Coffee)
Review_R020_Flavor<- gsub("[[:punct:]]", "", Review_R020_Flavor)
Review_R021_Baan<- gsub("[[:punct:]]", "", Review_R021_Baan)
Review_R022_Chalong<- gsub("[[:punct:]]", "", Review_R022_Chalong)
Review_R023_Naughty<- gsub("[[:punct:]]", "", Review_R023_Naughty)
Review_R024_Surin<- gsub("[[:punct:]]", "", Review_R024_Surin)
Review_R025_Natural<- gsub("[[:punct:]]", "", Review_R025_Natural)
Review_R026_Honeymoon<- gsub("[[:punct:]]", "", Review_R026_Honeymoon)
Review_R027_Farm<- gsub("[[:punct:]]", "", Review_R027_Farm)
Review_R028_Puccio<- gsub("[[:punct:]]", "", Review_R028_Puccio)
Review_R029_Sizzle<- gsub("[[:punct:]]", "", Review_R029_Sizzle)
Review_R030_American<- gsub("[[:punct:]]", "", Review_R030_American)
  
#rule no 13: Remove digits from the reviews
Review_R001_Thong <- gsub("[[:digit:]]", "", Review_R001_Thong)
Review_R002_Odysseus <- gsub("[[:digit:]]", "", Review_R002_Odysseus)
Review_R003_Green <- gsub("[[:digit:]]", "", Review_R003_Green)
Review_R004_Dee <- gsub("[[:digit:]]", "", Review_R004_Dee)
Review_R005_Tavern <- gsub("[[:digit:]]", "", Review_R005_Tavern)
Review_R006_EAT <- gsub("[[:digit:]]", "", Review_R006_EAT)
Review_R007_Surf <- gsub("[[:digit:]]", "", Review_R007_Surf)
Review_R008_Siam <- gsub("[[:digit:]]", "", Review_R008_Siam)
Review_R009_Sams <- gsub("[[:digit:]]", "", Review_R009_Sams)
Review_R010_Istanbul<- gsub("[[:digit:]]", "", Review_R010_Istanbul)
Review_R011_Corner<- gsub("[[:digit:]]", "", Review_R011_Corner)
Review_R012_Kataturk<- gsub("[[:digit:]]", "", Review_R012_Kataturk)
Review_R013_Sawasdee<- gsub("[[:digit:]]", "", Review_R013_Sawasdee)
Review_R014_Palm<- gsub("[[:digit:]]", "", Review_R014_Palm)
Review_R015_Highway<- gsub("[[:digit:]]", "", Review_R015_Highway)
Review_R016_Tandoori<- gsub("[[:digit:]]", "", Review_R016_Tandoori)
Review_R017_Pad<- gsub("[[:digit:]]", "", Review_R017_Pad)
Review_R018_Golden<- gsub("[[:digit:]]", "", Review_R018_Golden)
Review_R019_Coffee<- gsub("[[:digit:]]", "", Review_R019_Coffee)
Review_R020_Flavor<- gsub("[[:digit:]]", "", Review_R020_Flavor)
Review_R021_Baan<- gsub("[[:digit:]]", "", Review_R021_Baan)
Review_R022_Chalong<- gsub("[[:digit:]]", "", Review_R022_Chalong)
Review_R023_Naughty<- gsub("[[:digit:]]", "", Review_R023_Naughty)
Review_R024_Surin<- gsub("[[:digit:]]", "", Review_R024_Surin)
Review_R025_Natural<- gsub("[[:digit:]]", "", Review_R025_Natural)
Review_R026_Honeymoon<- gsub("[[:digit:]]", "", Review_R026_Honeymoon)
Review_R027_Farm<- gsub("[[:digit:]]", "", Review_R027_Farm)
Review_R028_Puccio<- gsub("[[:digit:]]", "", Review_R028_Puccio)
Review_R029_Sizzle<- gsub("[[:digit:]]", "", Review_R029_Sizzle)
Review_R030_American<- gsub("[[:digit:]]", "", Review_R030_American)

#rule no 14: Remove blank spaces at the beginning
Review_R001_Thong <- gsub("^ ", "", Review_R001_Thong)
Review_R002_Odysseus <- gsub("^ ", "", Review_R002_Odysseus)
Review_R003_Green <- gsub("^ ", "", Review_R003_Green)
Review_R004_Dee <- gsub("^ ", "", Review_R004_Dee)
Review_R005_Tavern <- gsub("^ ", "", Review_R005_Tavern)
Review_R006_EAT <- gsub("^ ", "", Review_R006_EAT)
Review_R007_Surf <- gsub("^ ", "", Review_R007_Surf)
Review_R008_Siam <- gsub("^ ", "", Review_R008_Siam)
Review_R009_Sams <- gsub("^ ", "", Review_R009_Sams)
Review_R010_Istanbul<- gsub("^ ", "", Review_R010_Istanbul)
Review_R011_Corner<- gsub("^ ", "", Review_R011_Corner)
Review_R012_Kataturk<- gsub("^ ", "", Review_R012_Kataturk)
Review_R013_Sawasdee<- gsub("^ ", "", Review_R013_Sawasdee)
Review_R014_Palm<- gsub("^ ", "", Review_R014_Palm)
Review_R015_Highway<- gsub("^ ", "", Review_R015_Highway)
Review_R016_Tandoori<- gsub("^ ", "", Review_R016_Tandoori)
Review_R017_Pad<- gsub("^ ", "", Review_R017_Pad)
Review_R018_Golden<- gsub("^ ", "", Review_R018_Golden)
Review_R019_Coffee<- gsub("^ ", "", Review_R019_Coffee)
Review_R020_Flavor<- gsub("^ ", "", Review_R020_Flavor)
Review_R021_Baan<- gsub("^ ", "", Review_R021_Baan)
Review_R022_Chalong<- gsub("^ ", "", Review_R022_Chalong)
Review_R023_Naughty<- gsub("^ ", "", Review_R023_Naughty)
Review_R024_Surin<- gsub("^ ", "", Review_R024_Surin)
Review_R025_Natural<- gsub("^ ", "", Review_R025_Natural)
Review_R026_Honeymoon<- gsub("^ ", "", Review_R026_Honeymoon)
Review_R027_Farm<- gsub("^ ", "", Review_R027_Farm)
Review_R028_Puccio<- gsub("^ ", "", Review_R028_Puccio)
Review_R029_Sizzle<- gsub("^ ", "", Review_R029_Sizzle)
Review_R030_American<- gsub("^ ", "", Review_R030_American)

#Rule 15: Remove blank spaces from the end point
Review_R001_Thong <- gsub(" $", "", Review_R001_Thong)
Review_R002_Odysseus <- gsub(" $", "", Review_R002_Odysseus)
Review_R003_Green <- gsub(" $", "", Review_R003_Green)
Review_R004_Dee <- gsub(" $", "", Review_R004_Dee)
Review_R005_Tavern <- gsub(" $", "", Review_R005_Tavern)
Review_R006_EAT <- gsub(" $", "", Review_R006_EAT)
Review_R007_Surf <- gsub(" $", "", Review_R007_Surf)
Review_R008_Siam <- gsub(" $", "", Review_R008_Siam)
Review_R009_Sams <- gsub(" $", "", Review_R009_Sams)
Review_R010_Istanbul<- gsub(" $", "", Review_R010_Istanbul)
Review_R011_Corner<- gsub(" $", "", Review_R011_Corner)
Review_R012_Kataturk<- gsub(" $", "", Review_R012_Kataturk)
Review_R013_Sawasdee<- gsub(" $", "", Review_R013_Sawasdee)
Review_R014_Palm<- gsub(" $", "", Review_R014_Palm)
Review_R015_Highway<- gsub(" $", "", Review_R015_Highway)
Review_R016_Tandoori<- gsub(" $", "", Review_R016_Tandoori)
Review_R017_Pad<- gsub(" $", "", Review_R017_Pad)
Review_R018_Golden<- gsub(" $", "", Review_R018_Golden)
Review_R019_Coffee<- gsub(" $", "", Review_R019_Coffee)
Review_R020_Flavor<- gsub(" $", "", Review_R020_Flavor)
Review_R021_Baan<- gsub(" $", "", Review_R021_Baan)
Review_R022_Chalong<- gsub(" $", "", Review_R022_Chalong)
Review_R023_Naughty<- gsub(" $", "", Review_R023_Naughty)
Review_R024_Surin<- gsub(" $", "", Review_R024_Surin)
Review_R025_Natural<- gsub(" $", "", Review_R025_Natural)
Review_R026_Honeymoon<- gsub(" $", "", Review_R026_Honeymoon)
Review_R027_Farm<- gsub(" $", "", Review_R027_Farm)
Review_R028_Puccio<- gsub(" $", "", Review_R028_Puccio)
Review_R029_Sizzle<- gsub(" $", "", Review_R029_Sizzle)
Review_R030_American<- gsub(" $", "", Review_R030_American)

#Rule no 16A: Remove Restaurant word from reviews:
Review_R001_Thong <- gsub("restaurant", "", Review_R001_Thong)
Review_R002_Odysseus <- gsub("restaurant", "", Review_R002_Odysseus)
Review_R003_Green <- gsub("restaurant", "", Review_R003_Green)
Review_R004_Dee <- gsub("restaurant", "", Review_R004_Dee)
Review_R005_Tavern <- gsub("restaurant", "", Review_R005_Tavern)
Review_R006_EAT <- gsub("restaurant", "", Review_R006_EAT)
Review_R007_Surf <- gsub("restaurant", "", Review_R007_Surf)
Review_R008_Siam <- gsub("restaurant", "", Review_R008_Siam)
Review_R009_Sams <- gsub("restaurant", "", Review_R009_Sams)
Review_R010_Istanbul<- gsub("restaurant", "", Review_R010_Istanbul)
Review_R011_Corner<- gsub("restaurant", "", Review_R011_Corner)
Review_R012_Kataturk<- gsub("restaurant", "", Review_R012_Kataturk)
Review_R013_Sawasdee<- gsub("restaurant", "", Review_R013_Sawasdee)
Review_R014_Palm<- gsub("restaurant", "", Review_R014_Palm)
Review_R015_Highway<- gsub("restaurant", "", Review_R015_Highway)
Review_R016_Tandoori<- gsub("restaurant", "", Review_R016_Tandoori)
Review_R017_Pad<- gsub("restaurant", "", Review_R017_Pad)
Review_R018_Golden<- gsub("restaurant", "", Review_R018_Golden)
Review_R019_Coffee<- gsub("restaurant", "", Review_R019_Coffee)
Review_R020_Flavor<- gsub("restaurant", "", Review_R020_Flavor)
Review_R021_Baan<- gsub("restaurant", "", Review_R021_Baan)
Review_R022_Chalong<- gsub("restaurant", "", Review_R022_Chalong)
Review_R023_Naughty<- gsub("restaurant", "", Review_R023_Naughty)
Review_R024_Surin<- gsub("restaurant", "", Review_R024_Surin)
Review_R025_Natural<- gsub("restaurant", "", Review_R025_Natural)
Review_R026_Honeymoon<- gsub("restaurant", "", Review_R026_Honeymoon)
Review_R027_Farm<- gsub("restaurant", "", Review_R027_Farm)
Review_R028_Puccio<- gsub("restaurant", "", Review_R028_Puccio)
Review_R029_Sizzle<- gsub("restaurant", "", Review_R029_Sizzle)
Review_R030_American<- gsub("restaurant", "", Review_R030_American)

#Rule no 16B: Removing the word hotel
Review_R001_Thong <- gsub("hotel", "", Review_R001_Thong)
Review_R002_Odysseus <- gsub("hotel", "", Review_R002_Odysseus)
Review_R003_Green <- gsub("hotel", "", Review_R003_Green)
Review_R004_Dee <- gsub("hotel", "", Review_R004_Dee)
Review_R005_Tavern <- gsub("hotel", "", Review_R005_Tavern)
Review_R006_EAT <- gsub("hotel", "", Review_R006_EAT)
Review_R007_Surf <- gsub("hotel", "", Review_R007_Surf)
Review_R008_Siam <- gsub("hotel", "", Review_R008_Siam)
Review_R009_Sams <- gsub("hotel", "", Review_R009_Sams)
Review_R010_Istanbul<- gsub("hotel", "", Review_R010_Istanbul)
Review_R011_Corner<- gsub("hotel", "", Review_R011_Corner)
Review_R012_Kataturk<- gsub("hotel", "", Review_R012_Kataturk)
Review_R013_Sawasdee<- gsub("hotel", "", Review_R013_Sawasdee)
Review_R014_Palm<- gsub("hotel", "", Review_R014_Palm)
Review_R015_Highway<- gsub("hotel", "", Review_R015_Highway)
Review_R016_Tandoori<- gsub("hotel", "", Review_R016_Tandoori)
Review_R017_Pad<- gsub("hotel", "", Review_R017_Pad)
Review_R018_Golden<- gsub("hotel", "", Review_R018_Golden)
Review_R019_Coffee<- gsub("hotel", "", Review_R019_Coffee)
Review_R020_Flavor<- gsub("hotel", "", Review_R020_Flavor)
Review_R021_Baan<- gsub("hotel", "", Review_R021_Baan)
Review_R022_Chalong<- gsub("hotel", "", Review_R022_Chalong)
Review_R023_Naughty<- gsub("hotel", "", Review_R023_Naughty)
Review_R024_Surin<- gsub("hotel", "", Review_R024_Surin)
Review_R025_Natural<- gsub("hotel", "", Review_R025_Natural)
Review_R026_Honeymoon<- gsub("hotel", "", Review_R026_Honeymoon)
Review_R027_Farm<- gsub("hotel", "", Review_R027_Farm)
Review_R028_Puccio<- gsub("hotel", "", Review_R028_Puccio)
Review_R029_Sizzle<- gsub("hotel", "", Review_R029_Sizzle)
Review_R030_American<- gsub("hotel", "", Review_R030_American)

#Rule no 17: Inspect the vector after cleaning
head(Review_R001_Thong)
head(Review_R002_Odysseus)
head(Review_R003_Green)
head(Review_R004_Dee)
head(Review_R005_Tavern)
head(Review_R006_EAT)
head(Review_R007_Surf)
head(Review_R008_Siam)
head(Review_R009_Sams)
head(Review_R010_Istanbul)
head(Review_R011_Corner)
head(Review_R012_Kataturk)
head(Review_R013_Sawasdee)
head(Review_R014_Palm)
head(Review_R015_Highway)
head(Review_R016_Tandoori)
head(Review_R017_Pad)
head(Review_R018_Golden)
head(Review_R019_Coffee)
head(Review_R020_Flavor)
head(Review_R021_Baan)
head(Review_R022_Chalong)
head(Review_R023_Naughty)
head(Review_R024_Surin)
head(Review_R025_Natural)
head(Review_R026_Honeymoon)
head(Review_R027_Farm)
head(Review_R028_Puccio)
head(Review_R029_Sizzle)
head(Review_R030_American)

#Rule no 18:
Corpus_Review_R001_Thong <- Corpus(VectorSource(Review_R001_Thong))
Corpus_Review_R002_Odysseus <- Corpus(VectorSource(Review_R002_Odysseus))
Corpus_Review_R003_Green <- Corpus(VectorSource(Review_R003_Green))
Corpus_Review_R004_Dee <- Corpus(VectorSource(Review_R004_Dee))
Corpus_Review_R005_Tavern <- Corpus(VectorSource(Review_R005_Tavern))
Corpus_Review_R006_EAT <- Corpus(VectorSource(Review_R006_EAT))
Corpus_Review_R007_Surf <- Corpus(VectorSource(Review_R007_Surf))
Corpus_Review_R008_Siam <- Corpus(VectorSource(Review_R008_Siam))
Corpus_Review_R009_Sams <- Corpus(VectorSource(Review_R009_Sams))
Corpus_Review_R010_Istanbul <- Corpus(VectorSource(Review_R010_Istanbul))
Corpus_Review_R011_Corner <- Corpus(VectorSource(Review_R011_Corner))
Corpus_Review_R012_Kataturk <- Corpus(VectorSource(Review_R012_Kataturk))
Corpus_Review_R013_Sawasdee <- Corpus(VectorSource(Review_R013_Sawasdee))
Corpus_Review_R014_Palm <- Corpus(VectorSource(Review_R014_Palm))
Corpus_Review_R015_Highway <- Corpus(VectorSource(Review_R015_Highway))
Corpus_Review_R016_Tandoori <- Corpus(VectorSource(Review_R016_Tandoori))
Corpus_Review_R017_Pad <- Corpus(VectorSource(Review_R017_Pad))
Corpus_Review_R018_Golden <- Corpus(VectorSource(Review_R018_Golden))
Corpus_Review_R019_Coffee <- Corpus(VectorSource(Review_R019_Coffee))
Corpus_Review_R020_Flavor <- Corpus(VectorSource(Review_R020_Flavor))
Corpus_Review_R021_Baan <- Corpus(VectorSource(Review_R021_Baan))
Corpus_Review_R022_Chalong <- Corpus(VectorSource(Review_R022_Chalong))
Corpus_Review_R023_Naughty <- Corpus(VectorSource(Review_R023_Naughty))
Corpus_Review_R024_Surin <- Corpus(VectorSource(Review_R024_Surin))
Corpus_Review_R025_Natural <- Corpus(VectorSource(Review_R025_Natural))
Corpus_Review_R026_Honeymoon <- Corpus(VectorSource(Review_R026_Honeymoon))
Corpus_Review_R027_Farm <- Corpus(VectorSource(Review_R027_Farm))
Corpus_Review_R028_Puccio <- Corpus(VectorSource(Review_R028_Puccio))
Corpus_Review_R029_Sizzle <- Corpus(VectorSource(Review_R029_Sizzle))
Corpus_Review_R030_American <- Corpus(VectorSource(Review_R030_American))

#Rule no 19: Inspect the corpus
Corpus_Review_R001_Thong
Corpus_Review_R002_Odysseus
Corpus_Review_R003_Green
Corpus_Review_R004_Dee
Corpus_Review_R005_Tavern
Corpus_Review_R006_EAT
Corpus_Review_R007_Surf
Corpus_Review_R008_Siam
Corpus_Review_R009_Sams
Corpus_Review_R010_Istanbul
Corpus_Review_R011_Corner
Corpus_Review_R012_Kataturk
Corpus_Review_R013_Sawasdee
Corpus_Review_R014_Palm
Corpus_Review_R015_Highway
Corpus_Review_R016_Tandoori
Corpus_Review_R017_Pad
Corpus_Review_R018_Golden
Corpus_Review_R019_Coffee
Corpus_Review_R020_Flavor
Corpus_Review_R021_Baan
Corpus_Review_R022_Chalong
Corpus_Review_R023_Naughty
Corpus_Review_R024_Surin
Corpus_Review_R025_Natural
Corpus_Review_R026_Honeymoon
Corpus_Review_R027_Farm
Corpus_Review_R028_Puccio
Corpus_Review_R029_Sizzle
Corpus_Review_R030_American

#Rule No 20: Remove Stopwatch and whitespace
Corpus_Review_R001_Thong <- tm_map(Corpus_Review_R001_Thong, removeWords,stopwords("english"))
Corpus_Review_R001_Thong <- tm_map(Corpus_Review_R001_Thong, stripWhitespace)
inspect(Corpus_Review_R001_Thong)

Corpus_Review_R002_Odysseus <- tm_map(Corpus_Review_R002_Odysseus, removeWords,stopwords("english"))
Corpus_Review_R002_Odysseus <- tm_map(Corpus_Review_R002_Odysseus, stripWhitespace)
inspect(Corpus_Review_R002_Odysseus)

Corpus_Review_R003_Green <- tm_map(Corpus_Review_R003_Green, removeWords,stopwords("english"))
Corpus_Review_R003_Green <- tm_map(Corpus_Review_R003_Green, stripWhitespace)
inspect(Corpus_Review_R003_Green)

Corpus_Review_R004_Dee <- tm_map(Corpus_Review_R004_Dee, removeWords,stopwords("english"))
Corpus_Review_R004_Dee <- tm_map(Corpus_Review_R004_Dee, stripWhitespace)
inspect(Corpus_Review_R004_Dee)

Corpus_Review_R005_Tavern <- tm_map(Corpus_Review_R005_Tavern, removeWords,stopwords("english"))
Corpus_Review_R005_Tavern <- tm_map(Corpus_Review_R005_Tavern, stripWhitespace)
inspect(Corpus_Review_R005_Tavern)

Corpus_Review_R006_EAT<- tm_map(Corpus_Review_R006_EAT, removeWords,stopwords("english"))
Corpus_Review_R006_EAT<- tm_map(Corpus_Review_R006_EAT, stripWhitespace)
inspect(Corpus_Review_R006_EAT)

Corpus_Review_R007_Surf<- tm_map(Corpus_Review_R007_Surf, removeWords,stopwords("english"))
Corpus_Review_R007_Surf <- tm_map(Corpus_Review_R007_Surf, stripWhitespace)
inspect(Corpus_Review_R007_Surf)

Corpus_Review_R008_Siam <- tm_map(Corpus_Review_R008_Siam, removeWords,stopwords("english"))
Corpus_Review_R008_Siam <- tm_map(Corpus_Review_R008_Siam, stripWhitespace)
inspect(Corpus_Review_R008_Siam)

Corpus_Review_R009_Sams <- tm_map(Corpus_Review_R009_Sams, removeWords,stopwords("english"))
Corpus_Review_R009_Sams <- tm_map(Corpus_Review_R009_Sams, stripWhitespace)
inspect(Corpus_Review_R009_Sams)

Corpus_Review_R010_Istanbul <- tm_map(Corpus_Review_R010_Istanbul, removeWords,stopwords("english"))
Corpus_Review_R010_Istanbul <- tm_map(Corpus_Review_R010_Istanbul, stripWhitespace)
inspect(Corpus_Review_R010_Istanbul)

Corpus_Review_R011_Corner <- tm_map(Corpus_Review_R011_Corner, removeWords,stopwords("english"))
Corpus_Review_R011_Corner <- tm_map(Corpus_Review_R011_Corner, stripWhitespace)
inspect(Corpus_Review_R011_Corner)

Corpus_Review_R012_Kataturk <- tm_map(Corpus_Review_R012_Kataturk, removeWords,stopwords("english"))
Corpus_Review_R012_Kataturk <- tm_map(Corpus_Review_R012_Kataturk, stripWhitespace)
inspect(Corpus_Review_R012_Kataturk)

Corpus_Review_R013_Sawasdee <- tm_map(Corpus_Review_R013_Sawasdee, removeWords,stopwords("english"))
Corpus_Review_R013_Sawasdee <- tm_map(Corpus_Review_R013_Sawasdee, stripWhitespace)
inspect(Corpus_Review_R013_Sawasdee)

Corpus_Review_R014_Palm <- tm_map(Corpus_Review_R014_Palm, removeWords,stopwords("english"))
Corpus_Review_R014_Palm <- tm_map(Corpus_Review_R014_Palm, stripWhitespace)
inspect(Corpus_Review_R014_Palm)

Corpus_Review_R015_Highway <- tm_map(Corpus_Review_R015_Highway, removeWords,stopwords("english"))
Corpus_Review_R015_Highway <- tm_map(Corpus_Review_R015_Highway, stripWhitespace)
inspect(Corpus_Review_R015_Highway)

Corpus_Review_R016_Tandoori <- tm_map(Corpus_Review_R016_Tandoori, removeWords,stopwords("english"))
Corpus_Review_R016_Tandoori <- tm_map(Corpus_Review_R016_Tandoori, stripWhitespace)
inspect(Corpus_Review_R016_Tandoori)

Corpus_Review_R017_Pad <- tm_map(Corpus_Review_R017_Pad, removeWords,stopwords("english"))
Corpus_Review_R017_Pad <- tm_map(Corpus_Review_R017_Pad, stripWhitespace)
inspect(Corpus_Review_R017_Pad)

Corpus_Review_R018_Golden <- tm_map(Corpus_Review_R018_Golden, removeWords,stopwords("english"))
Corpus_Review_R018_Golden <- tm_map(Corpus_Review_R018_Golden, stripWhitespace)
inspect(Corpus_Review_R018_Golden)

Corpus_Review_R019_Coffee <- tm_map(Corpus_Review_R019_Coffee, removeWords,stopwords("english"))
Corpus_Review_R019_Coffee <- tm_map(Corpus_Review_R019_Coffee, stripWhitespace)
inspect(Corpus_Review_R019_Coffee)

Corpus_Review_R020_Flavor <- tm_map(Corpus_Review_R020_Flavor, removeWords,stopwords("english"))
Corpus_Review_R020_Flavor <- tm_map(Corpus_Review_R020_Flavor, stripWhitespace)
inspect(Corpus_Review_R020_Flavor)

Corpus_Review_R021_Baan <- tm_map(Corpus_Review_R021_Baan, removeWords,stopwords("english"))
Corpus_Review_R021_Baan <- tm_map(Corpus_Review_R021_Baan, stripWhitespace)
inspect(Corpus_Review_R021_Baan)

Corpus_Review_R022_Chalong <- tm_map(Corpus_Review_R022_Chalong, removeWords,stopwords("english"))
Corpus_Review_R022_Chalong <- tm_map(Corpus_Review_R022_Chalong, stripWhitespace)
inspect(Corpus_Review_R022_Chalong)

Corpus_Review_R023_Naughty<- tm_map(Corpus_Review_R023_Naughty, removeWords,stopwords("english"))
Corpus_Review_R023_Naughty <- tm_map(Corpus_Review_R023_Naughty, stripWhitespace)
inspect(Corpus_Review_R023_Naughty)

Corpus_Review_R024_Surin <- tm_map(Corpus_Review_R024_Surin, removeWords,stopwords("english"))
Corpus_Review_R024_Surin <- tm_map(Corpus_Review_R024_Surin, stripWhitespace)
inspect(Corpus_Review_R024_Surin)

Corpus_Review_R025_Natural <- tm_map(Corpus_Review_R025_Natural, removeWords,stopwords("english"))
Corpus_Review_R025_Natural <- tm_map(Corpus_Review_R025_Natural, stripWhitespace)
inspect(Corpus_Review_R025_Natural)

Corpus_Review_R026_Honeymoon <- tm_map(Corpus_Review_R026_Honeymoon, removeWords,stopwords("english"))
Corpus_Review_R026_Honeymoon <- tm_map(Corpus_Review_R026_Honeymoon, stripWhitespace)
inspect(Corpus_Review_R026_Honeymoon)

Corpus_Review_R027_Farm <- tm_map(Corpus_Review_R027_Farm, removeWords,stopwords("english"))
Corpus_Review_R027_Farm <- tm_map(Corpus_Review_R027_Farm, stripWhitespace)
inspect(Corpus_Review_R027_Farm)

Corpus_Review_R028_Puccio <- tm_map(Corpus_Review_R028_Puccio, removeWords,stopwords("english"))
Corpus_Review_R028_Puccio <- tm_map(Corpus_Review_R028_Puccio, stripWhitespace)
inspect(Corpus_Review_R028_Puccio)

Corpus_Review_R029_Sizzle <- tm_map(Corpus_Review_R029_Sizzle, removeWords,stopwords("english"))
Corpus_Review_R029_Sizzle <- tm_map(Corpus_Review_R029_Sizzle, stripWhitespace)
inspect(Corpus_Review_R029_Sizzle)

Corpus_Review_R030_American <- tm_map(Corpus_Review_R030_American, removeWords,stopwords("english"))
Corpus_Review_R030_American <- tm_map(Corpus_Review_R030_American, stripWhitespace)
inspect(Corpus_Review_R030_American)

#Rule No 21: Stemming words to their root
Stem_Corpus_Review_R001_Thong <- tm_map(Corpus_Review_R001_Thong, stemDocument)
Stem_Corpus_Review_R002_Odysseus <- tm_map(Corpus_Review_R002_Odysseus, stemDocument)
Stem_Corpus_Review_R003_Green <- tm_map(Corpus_Review_R003_Green, stemDocument)
Stem_Corpus_Review_R004_Dee <- tm_map(Corpus_Review_R004_Dee, stemDocument)
Stem_Corpus_Review_R005_Tavern <- tm_map(Corpus_Review_R005_Tavern, stemDocument)
Stem_Corpus_Review_R006_EAT <- tm_map(Corpus_Review_R006_EAT, stemDocument)
Stem_Corpus_Review_R007_Surf <- tm_map(Corpus_Review_R007_Surf, stemDocument)
Stem_Corpus_Review_R008_Siam <- tm_map(Corpus_Review_R008_Siam, stemDocument)
Stem_Corpus_Review_R009_Sams <- tm_map(Corpus_Review_R009_Sams, stemDocument)
Stem_Corpus_Review_R010_Istanbul <- tm_map(Corpus_Review_R010_Istanbul, stemDocument)
Stem_Corpus_Review_R011_Corner <- tm_map(Corpus_Review_R011_Corner, stemDocument)
Stem_Corpus_Review_R012_Kataturk <- tm_map(Corpus_Review_R012_Kataturk, stemDocument)
Stem_Corpus_Review_R013_Sawasdee <- tm_map(Corpus_Review_R013_Sawasdee, stemDocument)
Stem_Corpus_Review_R014_Palm <- tm_map(Corpus_Review_R014_Palm, stemDocument)
Stem_Corpus_Review_R015_Highway <- tm_map(Corpus_Review_R015_Highway, stemDocument)
Stem_Corpus_Review_R016_Tandoori <- tm_map(Corpus_Review_R016_Tandoori, stemDocument)
Stem_Corpus_Review_R017_Pad <- tm_map(Corpus_Review_R017_Pad, stemDocument)
Stem_Corpus_Review_R018_Golden <- tm_map(Corpus_Review_R018_Golden, stemDocument)
Stem_Corpus_Review_R019_Coffee <- tm_map(Corpus_Review_R019_Coffee, stemDocument)
Stem_Corpus_Review_R020_Flavor <- tm_map(Corpus_Review_R020_Flavor, stemDocument)
Stem_Corpus_Review_R021_Baan <- tm_map(Corpus_Review_R021_Baan, stemDocument)
Stem_Corpus_Review_R022_Chalong <- tm_map(Corpus_Review_R022_Chalong, stemDocument)
Stem_Corpus_Review_R023_Naughty <- tm_map(Corpus_Review_R023_Naughty, stemDocument)
Stem_Corpus_Review_R024_Surin <- tm_map(Corpus_Review_R024_Surin, stemDocument)
Stem_Corpus_Review_R025_Natural <- tm_map(Corpus_Review_R025_Natural, stemDocument)
Stem_Corpus_Review_R026_Honeymoon <- tm_map(Corpus_Review_R026_Honeymoon, stemDocument)
Stem_Corpus_Review_R027_Farm <- tm_map(Corpus_Review_R027_Farm, stemDocument)
Stem_Corpus_Review_R028_Puccio <- tm_map(Corpus_Review_R028_Puccio, stemDocument)
Stem_Corpus_Review_R029_Sizzle <- tm_map(Corpus_Review_R029_Sizzle, stemDocument)
Stem_Corpus_Review_R030_American <- tm_map(Corpus_Review_R030_American, stemDocument)

#Rule No 22
load_positive_lexicon <- read.csv("positive-lexicon.txt")
load_negative_lexicon <- read.csv("negative-lexicon.txt")

#Rule No 23
head(load_positive_lexicon)
tail(load_positive_lexicon)
head(load_negative_lexicon)
tail(load_negative_lexicon)

#Rule No 24
sentiment <- function(stem_corpus)
{
  #generate wordclouds
  wordcloud(stem_corpus,
            min.freq = 3,
            colors=brewer.pal(8, "Dark2"),
            random.color = TRUE,
            max.words = 100)
  #Calculating the count of total positive and negative words in each review
  #Create variables and vectors
  total_pos_count <- 0
  total_neg_count <- 0
  pos_count_vector <- c()
  neg_count_vector <- c()
  #Calculate the size of the corpus
  size <- length(stem_corpus)
  for(i in 1:size)
  {
    #All the words in current review
    corpus_words<- list(strsplit(stem_corpus[[i]]$content, split = " "))
    #positive words in current review
    pos_count <-length(intersect(unlist(corpus_words), unlist(load_positive_lexicon)))
    #negative words in current review
    neg_count <- length(intersect(unlist(corpus_words), unlist(load_negative_lexicon)))
    total_pos_countA <- total_pos_count + pos_count ## overall positive count
    total_neg_countA <- total_neg_count + neg_count ## overall negative count
  }
  #Calculating overall percentage of positive and negative words of all the reviews
  total_pos_countA ## overall positive count
  total_neg_countA ## overall negative count
  total_countA <- total_pos_countA + total_neg_countA
  overall_positive_percentageB <- (total_pos_countA*100)/total_countA
  overall_negative_percentageB <- (total_neg_countA*100)/total_countA
  overall_positive_percentageB ## overall positive percentage
  #Create a dataframe with all the positive and negative reviews
  df<-data.frame(Review_Type=c("Postive","Negitive"),
                 Count=c(total_pos_countA ,total_neg_countA ))
  print(df) #Print
  overall_positive_percentageB<-paste("Percentage of Positive Reviews:",
                                     round(overall_positive_percentageB,2),"%")
  return(overall_positive_percentageB)
}


#Step 25:
sentiment(Stem_Corpus_Review_R001_Thong)
sentiment(Stem_Corpus_Review_R002_Odysseus)
sentiment(Stem_Corpus_Review_R003_Green)
sentiment(Stem_Corpus_Review_R004_Dee)
sentiment(Stem_Corpus_Review_R005_Tavern)
sentiment(Stem_Corpus_Review_R006_EAT)
sentiment(Stem_Corpus_Review_R007_Surf)
sentiment(Stem_Corpus_Review_R008_Siam)
sentiment(Stem_Corpus_Review_R009_Sams)
sentiment(Stem_Corpus_Review_R010_Istanbul)
sentiment(Stem_Corpus_Review_R011_Corner)
sentiment(Stem_Corpus_Review_R012_Kataturk)
sentiment(Stem_Corpus_Review_R013_Sawasdee)
sentiment(Stem_Corpus_Review_R014_Palm)
sentiment(Stem_Corpus_Review_R015_Highway)
sentiment(Stem_Corpus_Review_R016_Tandoori)
sentiment(Stem_Corpus_Review_R017_Pad)
sentiment(Stem_Corpus_Review_R018_Golden)
sentiment(Stem_Corpus_Review_R019_Coffee)
sentiment(Stem_Corpus_Review_R020_Flavor)
sentiment(Stem_Corpus_Review_R021_Baan)
sentiment(Stem_Corpus_Review_R022_Chalong)
sentiment(Stem_Corpus_Review_R023_Naughty)
sentiment(Stem_Corpus_Review_R024_Surin)
sentiment(Stem_Corpus_Review_R025_Natural)
sentiment(Stem_Corpus_Review_R026_Honeymoon)
sentiment(Stem_Corpus_Review_R027_Farm)
sentiment(Stem_Corpus_Review_R028_Puccio)
sentiment(Stem_Corpus_Review_R029_Sizzle)
sentiment(Stem_Corpus_Review_R030_American)

#Application of Shiny Dashboard
install.packages("shiny")
install.packages("shinydashboard")
library(shiny)
library(shinydashboard)
