Ashley Shearer  
INFO 4617  
Final Project \- Proposal  
25 October 2026  
How do popularity scores for *Spider-Man: Brand New Day* compare with previous Spider-Man movies on TMDB?  
For my project, I want to compare how *Spider-Man: Brand New Day* performed in relation to *Spider-Man: No Way Home*, and *Spider-Man: Far From Home* based on their TMDB daily popularity scores. I am choosing this topic because I helped work on the movie campaign for *Spider-Man: Brand New Day* as an intern for the Sony Pictures Entertainment (SPE) Digital Marketing team this past summer. Since I worked alongside the developers of the Spidey Tracker website ([https\://spideytracker.com/](https://spideytracker.com/)) as well, which gave live updates on tour events and release dates, I want to now reflect on how actual popularity scores were reflected throughout the campaign. Since SPE has strict terms and conditions governing their data, I will be using TMDB to track its progress among the other two movies.   
This question is relevant to SPE and their digital marketing team, along with other entertainment companies for marketing strategies. I expect *Brand New Day* to have higher popularity scores overall because it is the newest movie and seems to be receiving a lot of attention. I would be surprised if an older Spider-Man movie consistently had higher scores.  
I plan to use [https\://www\.themoviedb.org/](https://www.themoviedb.org/). TMDB gives information on a wide range of movies, specifically including *Spider-Man: Brand New Day* and previous Spider-Man movies. My main data source will be TMDB, which gives information such as ratings and release dates, but I plan to specifically focus on [https\://developer.themoviedb.org/docs/daily-id-exports](https://developer.themoviedb.org/docs/daily-id-exports), consisting of popularity scores. The files can be downloaded without an API key and are in a compressed JSON format. Using Python's requests library I will retrieve files and sort/process the JSON data to identify each Spider-Man movie by its TMDB movie ID.  
I plan to narrow my scope to a period of around 30 days in 2026, since it will allow me to compare the popularity of the newest Spider-Man movie with the previous two movies in the series. This means I should end up with around 90 daily popularity score records from *Spider-Man: Brand New Day*, *Spider-Man: No Way Home*, and *Spider-Man: Far From Home combined*. TMDB only keeps its daily files accessible for around three months after the day they are recorded, which might prevent some of the records from being available. Due to this, my first course of action is to check whether the files can be accessed or are archived. If unavailable, the timeframe will be adjusted to focus on a period that does have accessible records.  
For data collection, I will use some of the web request strategies from the textbook to retrieve TMDB's Daily ID Exports. The chapters about using JSON to organize data will also be heavily referenced while I am handling the TMDB popularity scores, as well as Selenium.  
After I have the needed data collected, pandas will help me organize the datasets by date, which will then allow me to compare the popularity scores of *Spider-Man: Brand New Day* with the other two movies. Throughout the 30 day period, the average popularity scores that I have calculated and retrieved will be used to gauge how interest in the movie changed. I plan to use a line graph and bar graph most likely to compare movies and scores. While I can compare and contrast the popularity scores, I cannot actually prove that the newest movie is more popular with all audiences based on just the TMDB data, but my research will still hopefully show how the movies compare in an online recorded sense.  
Since Daily ID Exports are available to the public on TMDB, I will be following their terms of use by only downloading and inspecting needed files for my research, my research is ethical. Since I am collecting movie titles, IDs, dates, and popularity scores, I will not need any personal information about anyone but will record my email in the headers. In addition, data will be pulled from downloadable JSON files and compared through list outputs and visualizations, making the project feasible as well. The biggest risk would be not having accessibility to records from important tour dates or having to adjust my timeframe to a period that is less relevant to the timeline of the campaigns.  
A record I retrieved was through a request that provided me with the list of movies and IDs from a JSON file containing “Spider-Man:”. From there, I was able to identify the IDs of the movies I wanted to focus on and took it a step further by using pandas again with the specified IDs to provide the popularity scores for each of the three movies as of October 20, 2026\.

**HTML URL:**  
file:///Users/ashleyshearer/Downloads/Spider-Man-Copy1.html

**Pasted Code:**  
**import** requests  
**import** pandas **as** pd  
url **\=** "https\://files.tmdb.org/p/exports/movie\_ids\_10\_20\_2026.json.gz"  
df **\=** pd**.**read\_json(url, lines**\=True**)  
response **\=** requests**.**get(  
    url,  
    headers**\=**{"User-Agent": "WebDataScience/1.0 (assh8422@colorado.edu)"},  
    timeout**\=**60  
)  
print("HTTP Status Code:", response**.**status\_code)  
response**.**raise\_for\_status()  
spiderman **\=** df\[df\["original\_title"\]**.**str**.**contains("Spider-Man:")\]  
print(spiderman\[\["id", "original\_title", "popularity"\]\])

**Pasted Output:**  
HTTP Status Code: 200  
              id                                     original\_title  \\  
32941      49131          Spider-Man: The Ultimate Villain Showdown     
33971      50410                         Spider-Man: The Venom Saga     
129211    225938                 Spider-Man: The Dragon's Challenge     
130256    228088  De Superman à Spider-Man: L'aventure des super...     
157820    270764         Spider-Man: The Return of the Green Goblin     
196265    315635                             Spider-Man: Homecoming     
204240    324857                  Spider-Man: Into the Spider-Verse     
264597    399712   The Spectacular Spider-Man: Attack of the Lizard     
287975    429617                          Spider-Man: Far From Home     
365258    528450      Spider-Man: The Mythology of the 21st Century     
395432    569094                Spider-Man: Across the Spider-Verse     
435097    622230             LEGO Marvel Spider-Man: Vexed by Venom     
443689    634649                            Spider-Man: No Way Home     
522751    742218  The Real Spider-Man: The Making of The Green G...     
640262    911916                Spider-Man: Beyond the Spider-Verse     
675486    961651          Spider-Man: All Roads Lead to No Way Home     
680752    969681                          Spider-Man: Brand New Day     
735510   1051708                       Spider-Man: Don't Hide Abuse     
986920   1412329  Spider-Man: Across the Spider-Verse \- Creating...     
1206890  1724187                            Spider-Man: Secret Wars     
1218575  1739008  Spider-Man: Across the Spider-Verse: Across th...     
1218584  1739018  Spider-Man: Across the Spider-Verse: Obscure S...     
1218590  1739026  Spider-Man: Across the Spider-Verse: "I'mma Do...     
1218871  1739374  Spider-Man: Across the Spider-Verse: Your Frie...     
1222015  1743265                               Spider-Man: Syndrome     
1222941  1744836                Spider-Man: Smart Kids Play It Safe     
1222945  1744841                 Spider-Man: What To Do About Drugs     
1234823  1760058  Symbiote Spider-Man: The Saga of the Black Cos...     
1241235  1770142                                  Spider-Man: Lotus   

         popularity    
32941        2.4780    
33971        3.5189    
129211       2.5125    
130256       1.9325    
157820       2.5206    
196265      37.0595    
204240      37.4524    
264597       1.8367    
287975      34.1559    
365258       1.6385    
395432      50.2057    
435097       3.4725    
443689      65.8574    
522751       0.7453    
640262       6.9219    
675486       4.3162    
680752    2343.3622    
735510       1.5820    
986920       1.8669    
1206890      1.1253    
1218575      1.0085    
1218584      1.4410    
1218590      1.7249    
1218871      1.6041    
1222015      1.1437    
1222941      1.3953    
1222945      1.0532    
1234823      2.0867    
1241235      0.8827 

**Pasted Code:**  
**import** pandas **as** pd  
url **\=** "https\://files.tmdb.org/p/exports/movie\_ids\_10\_20\_2026.json.gz"  
df **\=** pd**.**read\_json(url, lines**\=True**)  
movie\_ids **\=** \[969681, 634649, 429617\]  
spiderman\_movies **\=** df\[df\["id"\]**.**isin(movie\_ids)\]  
print(spiderman\_movies\[\["id", "original\_title", "popularity"\]\])

**Pasted Output:**  
           id             original\_title  			popularity  
287975  429617  Spider-Man: Far From Home     34.1559  
443689  634649    Spider-Man: No Way Home     65.8574  
680752  969681  Spider-Man: Brand New Day   2343.3622  
