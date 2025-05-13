---
title: "Assignment 1 - Analyzing ROR Corpus with Voyant and R"
categories:
  - Assignments
  - Blog
tags:
  - Assignments
  - Voyant
---

# Working with a Corpus

## Introduction
How do we understand the student body of our campus, their questions, their fears and their connection to social media? For assignment one, we chose a corpus from a relatively unusual place. Foregoing Project Gutenberg, we chose a corpus that was institutionally and geographically relevant to us here at NYUAD, the Facebook group known as ROR. We chose to compare posts from ROR, Female ROR, and Male ROR, to bring a new understanding of our student body, especially looking at dynamics between gendered and non-gendered spaces. By using tools like R and Voyant Tools, our exploratory data analysis allowed us to draw conclusions about the language used in these forums, and how they might reflect larger societal and institutional principles.  

## Background
Since the start of New York University’s Abu Dhabi campus in 2010, there has been a need for an online space solely for students. In the following year, on July 29th 2011, ROR was born. Officially titled “NYUAD's Room of Requirement,” this forum reflects its founding class’s interest in Harry Potter but has now become an integral part of campus community. ROR is a space for all sorts of promotions, and inquiries, from freshman nervously debating their schedules and asking for Professor reviews, to heated posts about frustrations with admin behavior and a call action for the Student Government. Its popularity, with an average 20.6 posts per day, solidifies its importance within our student body, even when Facebook as a platform has declined in our generation. As the number of students and campus activity has increased, more Facebook groups have been created, targeting things like exchanging money, sharing rides, confessions and more. Within the past five years, a Female and Male ROR have also gained popularity, creating a gendered space, when the general ROR feels too public. These subsidiary groups also have an extra feature of anonymous posts, allowing students to post more sensitive information, in addition to engaging in gender-specific social behaviours. To account for the restrictions on the gendered RORs we will also reflect on our previous experiences with these forums. 

###### Victor - Male ROR
What I noticed from the male ROR group is that the average post length is very short, not to mention that the group does not see a lot of participation since most posts are from months/years ago, as well as a lot of the more recent ones coming from anonymous members (for reference, the option of posting anonymously on Facebook was introduced in April 2022). This makes sense because a significant amount of posts have topics that could be seen as “taboo” by some people, such as questions related to sex and mental health, and romantic relationships. Still, a lot of the posts seem to be related to academic and institutional matters, such as advice on which classes to choose or requests to change rooms with others. Nonetheless, most of the posts tend to be short and straightforward, albeit much more intimate than ROR.

###### Insiya - Female ROR
The Female ROR community, officially titled R♀R,  is a very active group, with frequent posts that I would categorize within two types: gendered activities, and vulnerable. The first category would be posts that refer to historical ‘feminine’ topics; on Female ROR these are most commonly female students selling clothes or items, but can also be self promotion about a nail service, questions on where to buy certain items or reviews of salons etc. The anonymous posts of Female ROR predate the official introduction in Facebook and it was managed through a Google Forms link where posts were collected and then posted by a separate “Anonymous Post” user account.  Nowadays, the in-built anonymous feature allows for quicker posts and features many different types of questions, from asking about internship stress to providing support for complex familial or romantic relationships. Since this feature was added to Facebook (during my freshman year), these anonymous posts have become more common and now I would say more than half of the posts are anonymous questions, even those that do not tie into traditional gender norms. I suspect this is because the general ROR does not have anonymous posts and the separate “NYUAD Confessions” page is not a private group and posts can be seen by anyone. It is also interesting that Female ROR utilizes the group rules feature which helps make the community feel more safe. I myself have used Female ROR for inquiries that I feel “don’t belong” in the general ROR, despite them being relatively impersonal and not anonymous. 

## Methodology

After deciding on our initial idea, we faced challenges early on, struggling to actually collect the data for our corpus. We had a very difficult time trying to use a social platform like Facebook, where scrolling pages and algorithms made it difficult to mass collect text, especially without sensitive information like peoples names and facebook profiles. Even online scrapers were locked behind paywalls or not applicable since RORs are private groups. We were initially aiming for an extensive ‘distant reading’ hoping “to shift focus away from the established canon, allowing for a broader insight into cultural patterns.” Not unlike the lost texts in major repositories or other challenges that Drucker mentions, we also had to limit our scope due to these technical issues. 

Our solution to this problem was to manually collect texts from posts to create our corpus. However, as Ama Bemma Adwetewa-Badu said, “data is not neutral,” making us aware of how our own biases and algorithms can affect our corpus. The parameters chosen were searching “anyone” within each forum and collecting the first 20 posts. With general ROR, we each collected 10 posts, as we had different search results due to our unique algorithms which are influenced by who our Facebook friends are or what posts we interacted with.  The final corpus consists of 60 posts across the three groups, totalling to 3,960 words. After preparing these texts in .txt files, we ran them through Voyant Tools and a notebook in R (Posit Cloud) to discover patterns within these spaces, and reflect on the larger NYUAD student body.

## Findings
By distant reading through Voyant Tools and R, we found that although all three groups revolve around student life, there are distinct linguistic nuances, highlighting  how group identity or membership can subtly shape the topics and tone of these spaces.
###### Voyant Tools 
After uploading the corpus to Voyant Tools, we chose to highlight the following three visualizations:
<iframe style='width: 600px; height: 450px;' src='https://voyant-tools.org/tool/Summary/?palette=Observable10&corpus=0b1c51ab1ec7e776f72dde8453907618'></iframe>
The ‘Summary’ tool confirmed some general trends that we knew from experience (Female ROR tends to have lengthier posts) while also revealing some distinctions between each text. Its interesting to note how Female ROR and Male ROR have an almost inverse relationship, while general ROR acts as a middle ground within the corpus. Specific distinctive words like "nails' play into gender stereoptypes but "thanks" also shows how the community feels stronger and has more appreciative words.

<iframe style='width: 600px; height: 450px;' src='https://voyant-tools.org/tool/Cirrus/?palette=Observable10&corpus=0b1c51ab1ec7e776f72dde8453907618'></iframe>
The word cloud indicates the most common words in the entire corpus, but since there are significant differences in the length of each text, this analysis is more heavily influenced by the Female ROR. However, words like "just" and "like" and the overall cloud indicate the more casual tone of these forums, which makes sense as this is a space only among the students, where people can be more comfortable with each other. 

<iframe style='width: 600px; height: 450px;' src='https://voyant-tools.org/tool/Topics/?palette=Observable10&termsPerTopic=8&corpus=0b1c51ab1ec7e776f72dde8453907618'></iframe>
The "Topics" tool is an interesting way to conceptualize the different themes of posts. It can also be seen that while many words are common throughout the three text, most of these topics are highly present in only one text e.g. visas are only mentioned in general ROR. This reflects how students can choose to post in specific ROR spaces based on the breadth of responses they might get.

###### R Observations
	
The decision of using R and tools like Voyant or the tidyverse came from the ability to quickly identify trends in word usage and frequency. With a linear reading of 60 separate posts (and thousands of words), it would be challenging to systematically notice which words appear uniquely or more frequently in one group versus another.
 
By utilizing the “MostDistinctiveWords” R code provided by the Professor, we were able to upload the three collections of text (ROR, Male ROR, and Female ROR), clean and tokenize their contents, and then compare word frequencies across the corpora. This is achieved by importing each text as a single string, breaking it into sentences, and then further splitting those sentences into individual words using the tidytext function unnest_tokens(). Next, it removes common stopwords (e.g., “the,” “of,” “and”) to focus on the most meaningful terms. By binding the three datasets together and labeling each one (“ROR,” “Male_ROR,” “Female_ROR”), the code can then compute the relative frequency (proportion) of each word in each corpus. Finally, the script uses ggplot2 to create a scatterplot that highlights the differences in word usage between ROR and the other two groups, making it easy to spot which words appear disproportionately in one corpus versus the others. 

###### Plot made with R - Large version
![Plot made with R - Large version](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/plot.png)

###### Plot made with R - Small version
![Plot made with R - Small version](https://raw.githubusercontent.com/vicnadu/digital-humanities/refs/heads/master/assets/images/plot2.png)

Looking at the plot comparing word frequencies, we can notice several patterns in the corpus:
* Words Appearing More Frequently in Female ROR: Certain terms related to personal experiences, feelings, or interpersonal dynamics (for instance, “feel,” “experience,” “appreciated”) appear more often in the Female ROR group than in the main ROR corpus. This might suggest that discussions in the Female ROR group have a more emotional tone and more intimate support.
* Words Appearing More Frequently in Male ROR: By contrast, words such as “campus,” “students,” “voice,” or “uncomfortable” appeared more often in the Male ROR group. This suggests that users in the Male ROR group might share more concerns on personal issues or questions based on institutional issues (e.g., campus policies).
* Shared Vocabulary: Many words in each corpus lie near the diagonal in the scatterplots, indicating that some topics (such as references to “everyone,” “people,” or “students”) are common across all three groups. This makes sense, as these groups are all part of the broader NYUAD student community.

## Conclusion
This assignment attempts to analyze how three distinct NYUAD Facebook groups—ROR (open to all students), Male ROR, and Female ROR—use language when discussing campus life, with a focus on posts containing the word “everyone.” Motivated by the need to see patterns not easily captured in a manual reading, the analysis employs computational methods in R to tokenize text, remove stopwords, and compare word frequencies across the three corpora, making it possible to quickly spot trends that would be difficult to notice through a purely linear reading. The results reveal that each group exhibits unique linguistic characteristics: the Female ROR group appears to use more emotionally charged words, while the Male ROR group includes more institution-oriented vocabulary, while the general ROR group contains a blend of both. These findings highlight not only surprising differences (such as the prevalence of certain personal or organizational terms in specific groups) but also the value of digital tools in displaying such distinctions. 

## Work breakdown
In the first meeting, we both worked together to brainstorm the initial idea, which was suggested by Insiya. In the second meeting, we brainstormed the methodology of selecting the posts and collected all of them equally, making sure to replace any duplicated posts that we collected from ROR. In the third and final meeting, we divided each other’s roles and began the process of using the tools and writing the analysis, which resulted in the following breakdown:

##### Insiya
* Came up with the initial idea during the brainstorming
* Used Voyant to analyze the corpus
* Formatted the Markdown code
* Wrote the following sections:
    * Introduction
    * Background
    * Methodology
    * Voyant Tools
    * Citations

##### Victor
* Separated the corpus into three different text files
* Used the R code in the Posit Cloud to analyze the corpus
* Formatted the Markdown code
* Wrote the following sections:
    * Background
    * R observations
    * Conclusion
    * Work breakdown

## Citations
Drucker, J. (2021). The Digital Humanities Coursebook: An Introduction to Digital Methods for Research and Scholarship (1st ed.). Routledge. https://doi.org/10.4324/9781003106531

Kim Adams and Saronik Bosu (2022). High Theory Podcast Episode: Distant Reading
A Discussion with Ama Bemma Adwetewa-Badu

<!-- This assignment is ready to be graded. -->