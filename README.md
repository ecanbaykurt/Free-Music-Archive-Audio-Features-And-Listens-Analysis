Free Music Archive (FMA): Music Features and Listens Analysis

Group Member: Lifu (Leaf) Li, Lujia (Lucia) Yu, Emre Can Baykurt, Pin-Hao (Johnny) Pan, Kuang-Ching (Amanda) Ting



Business Problem Definition

The music industry has undergone significant changes, transitioning from physical albums and CDs to
digital streaming platforms. This shift has not only transformed how music is shared but also 
broadened the range of popular styles, creating a fast-evolving and diverse market where genres 
often blend. Modern hit songs now incorporate elements from various genres like pop, electronic, and 
R&B, with changes in tempo, energy, and melody to cater to audience preferences.
With advancements in data and AI, music companies and artists use audio feature analysis to predict 
what makes a song popular. Our project aims to evaluate the popularity across 14,034 music tracks 
from Free Music Archive (FMA), uncovering the key factors to high listen counts.


Motivation

As the music industry and streaming services have become increasingly competitive, it is important 
to understand what attracts users to listen frequently. By evaluating the correlation between music 
features and listening counts, we can discover elements that encourage users’ engagement. This insight 
can further help the music industry and streaming platforms to enhance their popularity.


Report Summary

This report presents an exploratory analysis of music track popularity using data from the Free Music 
Archive (FMA). We begin by detailing the data cleaning and merging process for the three main datasets: 
tracks, audio features, and genres. Next, we use data visualizations to give an overview of the dataset, 
followed by an analysis of the correlation between audio features and the number of listens. Finally, 
we summarize our findings, discuss challenges encountered, suggest directions for future analysis, 
and conclude with references.


Key findings include:

  -  Pure music (tracks without lyrics) generally received higher listens compared to tracks with vocals,
     indicating a strong audience preference for instrumental tracks
  -  Track duration was found to have no strong correlation with popularity, suggesting that both short
     and long tracks can perform well.
  -  Genre distribution and track characteristics were visualized, revealing distinct patterns between
     different genres, such as high danceability for Electronic and Rock genres.
  -  Analysis of audio features indicated no clear linear correlation with track listens, pointing to the
     need for more sophisticated regression analysis using machine learning techniques.
  -  Social factors, such as artist recognition and song popularity, were positively associated with track
     listens, emphasizing the importance of social engagement in driving track success


Data Description and Data Source

This is a dataset from Free Music Archive (FMA), an open dataset suitable for browsing, searching, 
and organizing music collections of a wide variety. The FMA provides 917 GB of 106,574 tracks from 
16,341 artists and 14,854 albums, arranged in a hierarchical taxonomy of 161 genres. Specifically, 
this dataset can be found at this line: https://github.com/mdeff/fma?tab=readme-ov-file


Basic information

There are 109,727 rows with 39 columns in raw_track dataset, and 14,515 rows with 250 columns in 
raw_echonest dataset, and 165 rows with 5 columns in raw_genres dataset.


Overview of the Analysis

The analysis began with three main datasets: raw_tracks, raw_echonest, and raw_genres. After filtering
and merging raw_tracks and raw_echonest into df_merged, we discovered over 160 music subgenres, which 
complicated our ability to gain a broader overview of the dataset. Each genre in raw_genres is linked to a 
parent genre, with some parent genres encompassing multiple subgenres (e.g., "International" contains 30 
subgenres, "Rock" has 29, and "Electronic" has 19). Therefore, we decided to use only the 17 ultimate parent
genres as the labels for each track. After merging df_merged with raw_genres into df_merged_genre, we 
addressed three main challenges:


Missing Values:
A significant 56.31% of entries in the language field were missing. For instrumental tracks without lyrics, 
these were replaced with the label "Pure."

Random Missing Values:
Missing values in Echonest features were removed from the dataset.

Data Type Corrections: 
We corrected incorrect data types, such as converting track duration into seconds and ensuring that Echonest 
features were in float format. The final cleaned dataset was named df_master_tidy.

Analysis Focus

The analysis focuses on understanding the factors that potentially impact track listens. We hypothesized that 
four main influencing factors would be examined: track language (verbal or non-verbal), track duration, track 
genre, and track social features.

Part One: Track Language Analysis
In the first part of the analysis, we evaluated the influence of track language on listens. Graph 2.1 revealed 
that 56.3% of tracks are non-verbal ("Pure" music), while 41.9% feature English lyrics, and only 1.8% are in 
other languages. Further analysis of non-English tracks in Graph 2.2 indicated that Spanish, Portuguese,
French, and Turkish are the most prevalent. Comparing verbal and non-verbal tracks, Graph 3 (box plot analysis) 
showed that listens for pure tracks are more variable, with a longer right tail compared to verbal tracks. 
Despite several prominent outliers in the verbal category, pure tracks generally achieved higher overall listen 
counts.

Part Two: Track Duration Analysis
In the second part of the analysis, we examined track duration. Graph 4 illustrated a right-skewed distribution, 
indicating that most tracks are relatively short (peaking at 0:12 - 8:20 minutes). The scatter plot in Graph 5, 
titled "Track Duration vs. Listens (Excluding Outliers)," suggested a weak positive correlation between duration 
and listens, indicating that track duration alone is not a strong predictor of popularity; both short and long 
tracks can achieve high listen counts.

Part Three: Track Genre Analysis
The third part of the analysis focused on the impact of track genre on listens. Due to tracks often having 
multiple genres, a new dataset was created with each genre listed separately for clearer analysis. Radar 
charts in Graph 6 revealed that most genres exhibit high instrumentalness and low speechiness, except for Spoken 
tracks. Genres like Electronic, Hip-Hop, and Rock demonstrated high danceability and energy, while Classical, 
Instrumental, and Jazz were more acoustic.

Graph 7.1 (donut chart) indicated that 70% of tracks belong to a single genre, while only 23% span two genres. 
Graph 7.2 showcased that Rock and Electronic are the dominant genres, each featuring over 4,000 tracks, while 
other genres have fewer than 1,000. To assess genre popularity, a weighted average of listens was employed in G
raph 8, highlighting Electronic and Rock as leaders, followed by Instrumental and Classical.

Graph 9 displayed the top 10 tracks by listens, revealing that the top three exceed 300,000 listens, with the 
Electronic genre dominating the list with four tracks in the top 10. This suggests its widespread popularity. 
The next step is to analyze how the audio features of these popular Electronic tracks differ from the genre 
average to gain further insights into their success.

Part Four: Correlation Analysis of Audio Features
Graph 11.2 presented a correlation heatmap indicating that most audio features exhibit weak correlations with 
"track_listens," suggesting limited linear relationships. However, "danceability" and "valence" displayed 
relatively stronger positive correlations with listens, implying that tracks with higher values in these 
features tend to be more popular. Conversely, "acousticness" and "speechiness" were negatively correlated 
with popularity. Graph 12 reinforced this relationship, with a red regression line indicating that higher 
"danceability" is associated with a more positive tone.

In the fourth part, Graph 13 examined the correlation between social features and track listens for the top 5 
artists. It found that artists like Broke For Free, who have high Discovery and Familiarity scores, tend to 
garner more listens, highlighting the significance of social engagement in driving popularity. Graph 14.1
revealed a positive nonlinear relationship between Song Hotness and Song Currency, where increased popularity 
leads to disproportionately higher currency. Graph 14.2 (3D scatter plot) illustrated that both Song Hotness 
and Song Currency positively contribute to Artist Hotness, showcasing the influence of individual track success 
on an artist's overall popularity. Graph 15, a bubble chart, visualized the relationship between Song Hotness, 
Song Currency, and track listens, indicating connections but no clear trends suggesting a significant impact of 
these features on listens.


Suggestions

To succeed in today’s music industry, artists and professionals should prioritize a deep understanding of their
audience while strategically leveraging social media. Engaging with fans on platforms like TikTok, Instagram, 
and YouTube is crucial for building a loyal following. By analyzing audience preferences and behaviors, 
artists can create content that resonates, such as music videos or relatable behind-the-scenes glimpses. 
Embracing viral trends and collaborating with influencers can further amplify reach. Tailoring promotions 
based on audience insights and monitoring engagement analytics will enable artists to refine their strategies. 
This audience-centric approach will enhance market presence, drive listens, and boost revenue in an increasingly 
competitive landscape.


Future Research Directions. The next phase of the analysis involves examining the impact of lyrics on market 
dynamics using advanced NLP techniques, such as sentiment analysis, thematic clustering, and trend analysis.

Sentiment Analysis: 
  - This will determine the emotional tone of lyrics (e.g., love, sadness, rebellion) and their influence on audience
     engagement.

Thematic Clustering: 
  - This will identify common lyrical themes, providing insights into what resonates with listeners.

Time-Series Analysis: 
  - This will track the evolution of these themes over time, helping to correlate lyrical data with market features,
     such as genre popularity and social media metrics.

By correlating lyrical content with track performance and audience engagement, we aim to gain deeper insights into how 
lyrics influence track popularity in the context of the evolving music landscape.


Challenges

During this project, we faced several data challenges that impacted our analysis. After merging Tracks and Echonest datasets, 
we encountered issues with the hierarchy of music genres. Another major issue was missing values for language information, 
affecting 56% of the data, especially for tracks without lyrics, which limited language-based analysis. We also had to handle 
random missing values in features by dropping NA rows, reducing our sample size to 15,000 tracks from over 100,000. Additionally, 
incorrect data types for features like track duration required standardization for accurate analysis. These steps resulted in 
a df_master_tidy, but missing temporal data limited trend analysis. Linear regression also proved insufficient for capturing 
complex relationships, highlighting the need for machine learning models. Despite these challenges, our systematic data cleaning 
ensured a reliable dataset for meaningful insights.

References

Michaël Defferrard, Kirell Benzi, Pierre Vandergheynst, Xavier Bresson. FMA: A Dataset For Music Analysis, 2017.
Get track’s audio features. Web API Reference | Spotify for Developers. (n.d.). https://developer.spotify.com/documentation/web-api/reference/get-audio-features
Admin. “The Impact of Social Media on Music Discovery.” Novecore Blog, 17 Aug. 2023, blog.novecore.com/impact-of-social-on-music-discovery/.
How song characteristics can affect song popularity. (n.d.). https://pages.github.coecis.cornell.edu/info2950-s23/project-skillful-starmie/eda.html
The impact of Music Distribution Services. Kami Records. (2023, June 24). https://kamirecords.co/the-impact-of-music-distribution-services/#:~:text=In%20the%20digital%20age%2C%20music,reach%20new%20heights%20of%20success.
Artist similarity, familiarity and Hotness. Music Machinery. (2009, May 25). https://musicmachinery.com/2009/05/25/artist-similarity-familiarity-and-hotness/


Generative AI disclosure statement:


In completing this project, we have utilized Generative AI tools to assist with various aspects of our work. Below is a detailed account of how these tools were used: 

Content Generation: We used ChatGPT to brainstorm ideas for plot choices and leverage the code content for specific problems we met, including taking genre_id information from the dictionary within pandas columns, dropping duplicated genre information in each row, and drawing the circle graphic indicating the parent genre with each subgenres.
Code Review and Debugging: We used ChatGPT to improve our Python code, including optimizing algorithms and resolving potential errors.
Proofreading and Grammar Checks: We used Grammarly to refine our writing, improve readability, and ensure grammatical accuracy.
Our team has reviewed, edited, and validated all AI-generated content to ensure its accuracy, relevance, and originality in accordance with academic integrity guidelines.
