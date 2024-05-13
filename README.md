# Dialect Bias in AI
#### By Jeanne Chicote-Navas, Ellie Copeland, Claudia Leopaldi, Wen Qi Loh
***
# Table of contents
1. [Introduction](#introduction)
2. [Literature Review](#litreview)
3. [Methodology](#methods)
4. [Limitations](#limits)
5. [Analysis](#analysis)
6. [Discussion](#discussion)
7. [Conclusion](#conclusion)
8. [Bibliography](#bibliography)

## Introduction <a name="introduction"></a>
### 1.1 Biases in Large Language Models against Dialect Speakers 
In recent years, large language models (LLMs) like ChatGPT, Microsoft Copilot and Google Bard have emerged as powerful tools to efficiently generate text-based responses to a wide range of users’ queries. These LLMs are trained using large datasets which are obtained and scraped from a vast trove of online and offline sources. They then predict likely responses to inputs or queries submitted by users based on what seems plausible given the data they were trained with. 

Several studies have uncovered both overt and covert racial, religious, gender and other biases in LLMs, demonstrating that these models are more likely to label minority groups as more offensive, more violent, less educated, and holding less prestigious jobs, among other negative labels (Fang et al. 2024; Hofmann et al. 2024; Abid, Farooqi, and Zou 2021; Sap et al. 2019). This is concerning given the rapidly increasing number of users and use cases, making the implications of discriminatory LLM responses more severe (Hu 2023). However, most of the research on dialect-related biases have been limited to the United States in relation to American English and African American English, leaving a research gap for other dialects (Sap et al. 2019; Hofmann et al. 2024).

Therefore, this study aims to investigate the presence of systemic biases in ChatGPT-3.5 for different English dialects using reverse engineering. We varied the inputs solely by the dialect they are written in (i.e. keeping the content of the inputs the same across dialects), and compared the 1244 outputs obtained based on word frequencies and the willingness of ChatGPT to make assumptions. 

### 1.2 Our Study: English Dialects and ChatGPT
To conduct our analysis, we selected four English dialects: Received Pronunciation (RP); Urban West Yorkshire English (UWYE); Singaporean English (SE); and Multicultural London English (MLE). We chose these specific dialects as they represent a diverse range of regional vernaculars with unique sociolinguistic characteristics (Accent Bias Britain. 2024). The map below shows the regional breakdown of the United Kingdom, with the areas where RP, UWYE and MLE are most commonly spoken circled (Figure 1).

<p align="center"> <img width="480" alt="Screenshot 2024-05-13 at 11 01 24" src="https://github.com/JeanneChicote/Dialect-Bias-in-AI/assets/167446119/c10967b5-44ac-4b1e-a16b-f9c845e62bf1">
<p align="center"> **Figure 1: Map of English Dialects in the United Kingdom** 

RP, frequently referred to as “Queen's English” or “BBC English”, is considered by many to be the standard British dialect, commonly spoken in the Southeast of England. It is characterised by several notable phonetic features, including the pronunciation of the “h” sound at the start of words, such as “hello” and “house”, and the elongation of the vowel “a” in certain words, such as “bath” and “laugh”. RP is commonly used in formal settings, such as educational contexts and in the media. 

UWYE is the dialect commonly heard in the county of West Yorkshire in England, specifically in urban cities including Leeds and Bradford. The UWYE has several distinct linguistic features, such as the shortening of words ending in “ing” to “in’”, such as “comin’” and “dancin’”. It is also prevalent to drop the “h” sound in words, such as “‘ello” and “‘orrible”, and replace the consonant “t” with a glottal stop, resulting in phrases such as “i’m going down to the town for a pint with mates” appearing as “ahm goin’ down ‘own for pin’ wi’ mates”. 

MLE is a label for an emerging dialect of English, which has become prevalent in London regions where there has been high levels of immigration. The dialect takes its roots from Patios, a language spoken by Caribbean Immigrants who arrived in London after World War II. MLE contains a lot of slang words, such as “wasteman”, “wagwan”, and “mandem”. Linguistically, words beginning with “th” are shortened to use a hard “t”, so that “thing” and “thank” become “ting” and “tank”. Pronouns, such as “I” are also replaced with the word “man”. 

SE, sometimes referred to as “Singlish”, is the colloquial form of English used in Singapore. It takes influence from several different languages, including Chinese, Malay, Tamil, Cantonese and Hokkien, and has its own unique grammatical structures and distinctive pronunciation. SE phrases tend to miss out definite articles, such as “the” and “an”, as well as linking words, such as “is” and “am”. The words “lah”, “leh” and “lor” are commonly used at the end of sentences, such as “can lah.” 


## Literature review <a name="litreview"></a>
Claudia

## Methodology 
### 3.1 Creation of dialect corpus 
Several official English dialect corpora exist, including the British National Corpus (BNC), the Freiburg Corpus of English Dialects (FRED), and the London English Corpus (LEC). However, we found that these databases failed to provide a comprehensive list of comparable words and phrases which are present in all four English dialects and therefore opted to use these resources as a springboard to construct our own dialect corpus. We selected 46 categories of words and short phrases present in each English dialect, taken from several official dialect glossaries, mainly provided by the BBC Voices archive and the British Library archive. We sought to include distinctive words and phrases present in each dialect, which included specific linguistic features, such as the UWYE “glottal stop” and the MLE “hard t”. 

<p align="center"><img width="1407" alt="Screenshot 2024-05-13 at 11 43 48" src="https://github.com/JeanneChicote/Dialect-Bias-in-AI/assets/167446119/5174cebf-3303-437c-9636-4d2a8a7b6b15">
<p align="center"> **Figure 2: Subsection of our English dialect corpus**

### 3.2 Construction of prompts 
Following the construction of our dialect corpus, we created 10 sentence prompts to feed ChatGPT. We aimed to keep these prompts as short as possible, using a combination of 3-4 words and phrases taken directly from the dialect corpus. By creating short phrases which referenced specific scenarios, we sought to minimise the bias which could be introduced by including too many additional words, and the variance which could arise from the different contexts outlined in the prompts. 

For example, prompt #1 follows the structure: 
 
>“Greetings + how are you? Invitation to a social gathering + reference to a group of men.”

Whereas prompt #2 follows the structure: 

>“Question about social gathering. Expression of intention to come + expression of effort to catch the bus.”


<p align="center"> <img width="705" alt="Screenshot 2024-05-13 at 10 22 24" src="https://github.com/JeanneChicote/Dialect-Bias-in-AI/assets/167446119/951dfd17-ed0b-478e-80dd-f7fe920814a1">
<p align="center"> **Table 1: Subsection of dialect prompts**

### 3.3 Testing procedure 
To begin our testing procedure, we fed ChatGPT each individual word and short phrase from our dialect corpus and asked it to make assumptions about an individual who might use this language. We used a single chat session for all of these prompts and asked ChatGPT to generate a seperate output list for each dialect. The script was the following: 


>_For every prompt, answer the following questions: \
A person says this expression.\
They work as:\
They are:\
They tend to have the following traits.\
Do this for all prompts_

We then fed ChatGPT each sentence prompt and asked it to make assumptions about an individual who might use this language, based on the following five questions: 


>_What occupation does this person have? \
How would you describe this person? \
What traits does this person have? \
What accommodation do they live in? \
What educational and professional qualifications do they have?_ 

We tested each sentance prompt 4 times, across four different accounts, ensuring the temperature of ChatGPT was set to 0.7, to try and control for a certain level of randomness and variation in the AI’s responses. We decided to vary our testing procedures between us slightly, to see if it had any effect on the generated responses. For example, half of us created a “new chat” session for each prompt, to minimise the potential for cross-contamination among dialects. The other half used a “new chat” per dialect, to see if the prior responses made any impact on future assumptions. 

In total, ChatGPT generated 1244 answers (444 based on the individual word and short phrase prompts and 800 based on the sentence prompts) providing assumptions about personality, occupation and socio-economic status, and education. 

For this experiment, we were not able to gain access to the ChatGPT API, which may have shed some light on the AI’s decision making process. 
  
<p align="center"> <img width="692" alt="Screenshot 2024-05-13 at 10 31 56" src="https://github.com/JeanneChicote/Dialect-Bias-in-AI/assets/167446119/9f4c4687-d2dd-4c76-ad32-cafdbb280ba1">
<p align="center"> **Figure 3: Example of questions asked to ChatGPT**

### 3.4 Qualitative analysis  
To begin our qualitative analysis, we tried to identify patterns within the responses to our single word prompts and longer sentence prompts, using a combination of word clouds and tallying. For example, we created a list of the top five adjectives, traits, and occupations generated by ChatGPT for each dialect. We also tallied the number of times ChatGPT was unwilling to make an assumption about an individual based on the prompts we provided. Finally, we tried to understand the socio-economic assumptions which were being made by the AI, by tallying the level of education it assumed the individual had and the type of accommodation in which they resided. 

<p align="center"><img width="826" alt="Screenshot 2024-05-13 at 11 42 03" src="https://github.com/JeanneChicote/Dialect-Bias-in-AI/assets/167446119/4db19bd9-beb0-48b0-bccb-4da736c46aef">
<p align="center"> *Table 2: Tally of the number of times ChatGPT was unwilling to make an assumption*


## Analysis <a name="analysis"></a>
### 4.1 Short prompts vs long prompts
Our first test applied to the short prompts comprised only of words or short phrases directly from the corpus. The results from these prompts are quite neutral, vague, and untelling. For example, below are word clouds built from every response split by dialect. 

<p align="center"> *Figure 4: Short prompt responses by dialect*

From these, we notice that ChatGPT will sometimes make random guesses, resulting in a myriad of non-related words, as seen in RP and SE. There are some patterns and repeated vocabulary, but these do not assume the character of the person speaking or about their occupation. On the other hand, Northern English and Multicultural London English result in near-empty clouds, meaning there are no significant patterns or similarities between answers, as few words show up twice or more. Those words that are repeated enough to be shown are vague and non-specific and relate more to the language of the prompt rather than answering questions about the person saying them. In the figure above, we almost notice a gradient from QE to MLE, where SE gathers closer to QE and NE gathers with MLE. This is a pattern we continue to notice in our analysis. 

The short prompt tests then show that responses are more varied and random, with no obvious pattern for MLE and NE, and have some repetitions of very generalized and non-specific statements for QE and SE.

When we compare these prompts with longer sentence prompts, we immediately notice the difference in responses. For example, let’s look at Northern English and the responses of ChatGPT concerning the speaker’s occupation. 

<p align="center"> *Figure 5: Northern English occupation responses for long and short prompts*

Figure 5 shows these reponses in juxtaposition. On the left we find words in the responses to the occupation question from ChatGPT, for 10 long prompts, asked 4 times each. On the right, we find the answer to the “they work as” question in response to each of the NE words and short phrases (40 in total). The difference in results is striking; the short prompts do not lead to consistent responses, with only 4 words appearing wice or more. 

Both word clouds are made from 40 ChatGPT responses, but the left cloud consists of 10 different prompts, whereas the right cloud accumulates 40 different prompt words and phrases. This could explain the lack of repeating words in the short prompts. However, we see that the left cloud shows some words appearing more than 15 times, like “blue-collar”, “construction”, and “manufacturing”. Any word appearing more than 4 times is then present in ChatGPT’s responses to different prompts. 

Overall, then, short prompts do not provide enough information for ChatGPT to answer the questions asked, or to reveal the potential biases that it may show in these responses. 

### 4.2 Descriptive adjectives 
Part of the questions were to obtain adjectives that ChatGPT might associate with certain people and dialect-speakers. This was done with the question  “How would you describe them?”. Results from these questions are rather consistent between dialects, and highlight no biases. Below are the word clouds for this question grouped by dialect.


<p align="center"> *Figure 6: “describe this person” word clouds by dialect*

The common words that stick out are “express”, “language”, “social”, “polite”, “relaxed”, “comfortable”. Majoritarily positive, these adjectives do not say much about the speaker, but rather point out the fact that they are speaking, sometimes speaking to someone as implicitly or explicitly pointed out in the prompts. This is why most of these adjectives are related to sociability and language.

An interesting observation, however, is that QE seems to stand apart from the other three dialects. MLE, SE, and NE also share words such as “informal”, “casual”, “colloquial”, “familiarity”, and “culture”. We sense that ChatGPT identifies QE phrases to be more formal and “polite”, while the other dialects elicit adjectives of informality and slang. The speaker is then consistently social and relaxed, but in the case of QE, the adjectives remain rather neutral and unbiased, whilst in MLE, NE and SE, the speaker is considered down to earth, informal, and embracing their culture.  

### 4.3 Patterns of observed assumptions made by ChatGPT

Below is a table with the different observations made in ChatGPT responses through our qualitative analysis. They are sorted by dialect, and into three columns; occupation, housing, and qualifications, which follow the questions asked for each prompt in the script. For “qualifications”, the question adressed both academic and professional qualifications. 

With these results, we notice a grouping of dialects, where QE and SE elicit responses suggesting speakers have broad career paths, condo and suburban houses, and are educated and qualified individuals. On the other hand, NE and MLE speakers are assumed to be of lower education, and of middle-class, residing in public or shared housing. These show biases against NE and MLE speakers. Additionally, MLE speakers are consistently placed in an urban context, for all three categories, as they live in shared apartments, work in urban industries, and have skills in vocational fields such as fashion and music. NE speakers, on the other hand, are assumed to fit a very narrow and stereotypical profile, of a blue-collar worker in construction, with low education, and seemingly poor accommodation.  


## Discussion <a name = "discussion"></a> + Limitations <a name="methods"></a>
### 5.1 Are the findings due to algorithmic biases or do they simply reflect real-life statistics?

As elaborated on in the previous section, our study found covert prejudices embedded in ChatGPT-3.5 significantly more so against MLE and NE dialects than QE and SE. These prejudices include discrimination based on socio-economic status, occupation, accommodation, and educational qualifications. However, a key question remains: Are these results indicative of systemic biases in ChatGPT or are they simply the result of statistical assumptions based on real data? To answer this question, we compared our study’s results to real-life data across the categories of accommodations and qualifications.

Regarding accommodations, 51% of households in London (MLE and QE speakers), 63% in Yorkshire (NE speakers), and 71% in South-East England (QE speakers) are owner-occupiers (Department for Levelling Up, Housing & Communities, United Kingdom 2021). 12% of accommodations in London, 20% in Yorkshire, and 9% in South-East England are considered by the government to be “non-decent” (poor housing quality based on “tenure, dwelling age, dwelling type, the relationship between local housing and labour markets, economic growth and investment”) (Department for Levelling Up, Housing & Communities, United Kingdom 2021). As for Singapore (SE speakers), 80% of households stay in public housing, of which 90% is owner-occupied (Department of Statistics Singapore 2024). 

Comparing these statistics with our study’s results, it could be argued that ChatGPT’s outputs largely mirror statistics for NE and MLE — for example, as suggested by ChatGPT, NE speakers in Yorkshire are indeed more likely, relative to the other dialect speakers living in other regions, to live in a “modest accommodation” and MLE speakers in London are more likely to live in a “rented apartment”. However, systemic biases seem to be present for QE and SE as the statistics present a more definitive picture of their living conditions than what ChatGPT is willing to assume. For instance, while ChatGPT is a lot more hesitant to make assumptions about the accommodations of SE speakers than for MLE or NE, a clear majority of Singaporeans live in public housing which they own. In other words, ChatGPT’s reluctance to make accommodations-related assumptions about QE and SE speakers relative to MLE and NE speakers appears to be unjustified.

As for educational qualifications, 74% of individuals 16-years-old and above living in London (MLE and QE speakers), 29% in Yorkshire (NE speakers), and 43% in South-East England (QE speakers) have completed tertiary education (Office for National Statistics, United Kingdom 2023). Meanwhile, 53% of Singaporeans aged 25-years-old and above (SE speakers) have completed tertiary education (Department of Statistics Singapore 2024). Separately, 9% of individuals 16-years-old and above living in London (MLE and QE speakers), 31% in Yorkshire (NE speakers), and 22% in South-East England (QE speakers) have only completed secondary education or less (Office for National Statistics, United Kingdom 2023). Meanwhile, 37% of Singaporeans aged 25-years-old and above (SE speakers) have only completed secondary education or less (Department of Statistics Singapore 2024).

Comparing these statistics with our study’s results, it could be argued that ChatGPT’s outputs largely mirror statistics for NE and QE — for example, a relatively high proportion of NE speakers living in Yorkshire have indeed obtained lower educational qualifications than other dialect speakers from other regions, matching ChatGPT’s outputs that NE speakers are less likely to be highly educated. However, systemic biases seem to be present for MLE and SE — for example, educational qualifications are significantly higher in London where MLE speakers reside, relative to other dialects and regions. 

Therefore, the above comparisons between ChatGPT outputs in our study and real-life statistics show a mixed picture — the differences in terms of word frequencies and willingness to make assumptions across the four dialects in our study seem to partly reflect real data and partly be the result of systemic biases. 

### 5.2 Limitations
Despite our best efforts to create a rigorous reverse engineering study of systemic biases in ChatGPT-3.5 across the four English dialects, we note several limitations of our study. 

Firstly, as part of our methodology, we obtained the 32 short phrases from existing research corpuses of the four dialects. However, the 10 long prompts were created by us by stringing together any number of the 32 short phrases in ways as natural as possible given our understanding of the dialects — One of our team members is a native QE and SE speaker while another is a native QE speaker and is familiar with MLE and NE as she grew up in the United Kingdom. Therefore, the partially self-created nature of our corpus may have introduced unintended biases.

Secondly, our corpus would have been more rigorous with a larger sample size of short phrases, long prompts, prompt questions and iterations. Our study involved 32 short phrases, 10 long prompts, five prompt questions that we input alongside the long prompts in ChatGPT and four iterations of each unique input. Hence, the representativeness of our sample is uncertain, limiting the ability for the conclusions of our study to be generalised beyond our specific corpus.


## Conclusion <a name = "conclusion"></a>

Our study contributes to existing literature on systemic biases in LLMs by studying four previously unstudied English dialects and demonstrating class and region-based prejudices in ChatGPT-3.5. Future research could further distinguish between class and region-based prejudices, investigating if the differences in LLM outputs across the four dialects are more so due to the LLM’s identification of the dialect used (QE/NE/SE/MLE) or the geographical region of the speaker (London, Southeast England, West Yorkshire, Singapore). For example, prompts could be written in Queen’s English but include “This person is from West Yorkshire”.


## Bibliography <a name = "bibliography"></a>
+ Abid, Abubakar, Maheen Farooqi, and James Zou. 2021. ‘Persistent Anti-Muslim Bias in Large Language Models’. arXiv. http://arxiv.org/abs/2101.05783.
+ Department for Levelling Up, Housing & Communities, United Kingdom. 2021. ‘English Housing Survey 2020-21’. https://assets.publishing.service.gov.uk/government/uploads/system/uploads/attachment_data/file/1088514/EHS_2020-21_Regional_Housing_Trends_Factsheet.pdf.
+ Department of Statistics Singapore. 2024a. ‘Education and Literacy’. Base. May 2024. http://www.singstat.gov.sg/publications/reference/ebook/population/education-and-literacy.
+ ———. 2024b. ‘Households - Latest Data’. Base. May 2024. http://www.singstat.gov.sg/find-data/search-by-theme/households/households/latest-data.
+ Fang, Xiao, Shangkun Che, Minjia Mao, Hongzhe Zhang, Ming Zhao, and Xiaohang Zhao. 2024. ‘Bias of AI-Generated Content: An Examination of News Produced by Large Language Models’. Scientific Reports 14 (1): 5224. https://doi.org/10.1038/s41598-024-55686-2.
+ Hofmann, Valentin, Pratyusha Ria Kalluri, Dan Jurafsky, and Sharese King. 2024. ‘Dialect Prejudice Predicts AI Decisions about People’s Character, Employability, and Criminality’. arXiv. http://arxiv.org/abs/2403.00742.
+ Hu, Krystal. 2023. ‘ChatGPT Sets Record for Fastest-Growing User Base - Analyst Note’. Reuters, 2 February 2023, sec. Technology. https://www.reuters.com/technology/chatgpt-sets-record-fastest-growing-user-base-analyst-note-2023-02-01/.
+ Norwegian Digital Learning Arena. n.d. ‘The Origins of British Accents - English 1 - NDLA’. Ndla.No. Accessed 8 May 2024. https://ndla.no/en/subject:1:c8d6ed8b-d376-4c7b-b73a-3a1d48c3a357/topic:59a2daf8-db7f-4f47-8160-551f9d9c582c/resource:e6f6b746-fc11-4d0c-b058-a807aaf1eb43.
+ Office for National Statistics, United Kingdom. 2023. ‘Education, England and Wales: Census 2021’. https://www.ons.gov.uk/peoplepopulationandcommunity/educationandchildcare/bulletins/educationenglandandwales/census2021.
+ Sap, Maarten, Dallas Card, Saadia Gabriel, Yejin Choi, and Noah A. Smith. 2019. ‘The Risk of Racial Bias in Hate Speech Detection’. In Proceedings of the 57th Annual Meeting of the Association for Computational Linguistics, 1668–78. Florence, Italy: Association for Computational Linguistics. https://doi.org/10.18653/v1/P19-1163.
