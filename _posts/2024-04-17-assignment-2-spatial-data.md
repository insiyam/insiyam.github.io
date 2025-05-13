---
markdown: kramdown
title: "Assignment 2"
categories:
  - Blog
tags:
  - link
  - Post Formats
---
# Commercial Licences in 1914 Zanzibar
##  By Fatima and Insiya
# Introduction
For this assignment, we focused on extracting data from the Zanzibar Gazette published in 1914. Our selected dataset centres on Commercial Licences Issued in Zanzibar, a recurring section in the Gazette that lists individuals, their place of residence, and the type of business licence they were granted. We chose this dataset because it offers a unique glimpse into the economic landscape of colonial Zanzibar—what kinds of trades were being practised, where economic activity was concentrated, and who was participating in this commercial ecosystem.  
Our curiosity was particularly piqued by the relationship between residences and license types, as it could reveal spatial patterns of labour, class, or ethnic organisation in Zanzibar’s society at the time. By mapping out these relationships, we hoped to uncover not just individual data points but a more layered understanding of the island’s economic geography.

# Source Material and Data Selection
To identify relevant entries for our dataset, we began by using the search function in the PDF version of the Zanzibar Gazette, searching specifically for the keyword “license”. This approach allowed us to efficiently locate all instances where licences were listed in tabular form. We focused on Gazette pages 84 to 173, which included license records from January and February 1914.  
The entries we extracted typically appeared in a standardised format. Each section began with a licence issue date, followed by the type or category of licence (e.g., Money Lender's Licence, Broker's Licences, Hawker’s Licences), and then a table listing the licence holders. These tables generally had three columns: the name of the person or entity to whom the licence was issued, their place of residence, and their nationality. The structured nature of these entries made them suitable for data extraction, analysis, and visualisation. 

# Data Modelling and Structure
The most time-consuming and challenging part of this assignment was the data extraction process. We experimented with multiple tools, primarily ChatGPT, Gemini, and Transkribus, to convert the scanned license listings into structured data.

## Tools Used and Workflow - Fatima
I started by taking screenshots of the relevant pages from the Zanzibar Gazette, then compiled those screenshots into a single PDF. This file was uploaded to ChatGPT, where I used the prompt:

> “Please extract all commercial license information from these pages and format it into a structured table with the following columns: License Type, Issued To, Residence, and Nationality. Ensure no entries are skipped, and preserve the order as it appears in the original document.”

At first, this seemed effective—ChatGPT returned clean tables. However, upon closer inspection, I realised that it only extracted partial data from the document, skipping over certain rows or tables altogether.  
To improve the results, I switched to a more manual method by uploading the screenshots one by one and using image input with the following prompt:

> “From this image, extract all visible commercial license data into a clear table with columns for License Type, Issued To, Residence, and Nationality. Double-check for missing or unclear entries and preserve the format as seen in the original”

This approach proved more accurate, though it was significantly more tedious. ChatGPT handled image-based extraction better and produced usable tables that we could paste into a spreadsheet with minimal corrections.  
I also tried using Gemini, but it performed poorly in comparison. The results included a lot of “NaN” entries, missing values, and repeated errors, even after revision prompts like:

> “Extract all license-related tables from this document and organize them into a clean, analysis-ready spreadsheet format. The final table should include consistent headers, well-aligned rows, and no missing or fabricated data.”

Gemini also hallucinated location names and inserted entries that didn’t exist in the original text, so I eventually discontinued using it.    
<p align="center">
  <img src="https://raw.githubusercontent.com/fatimakazim/fatimakazim.github.io/master/assets/images/Gemini.png" width="45%" alt="Gemini Table"/>
  <img src="https://raw.githubusercontent.com/fatimakazim/fatimakazim.github.io/master/assets/images/GPT.png" width="45%" alt="ChatGPT Table"/>
</p>

<p align="center">
  <em>Left: Gemini output | Right: ChatGPT-4 output</em>
</p>

## Tools Used and Workflow – Insiya
While working on the data from February licenses in Zanzibar, we used Transkribus. Originally, I attempted to use Perplexity, which tends to hallucinate less, but it does not support image detection, so I decided to use Transkribus, a software I worked with before. By using the free Transkribus Print M1 model, I was able to get a very accurate reading of the text. There were almost no errors in letter transcription, but there were a few challenges with the detection of text in general. For example, many sections would not be recognised, and for many words, the beginning or ending would be cut off. Using the section and pen tool, I was able to mark up where the text was in the document. I also tried to make use of the table tool, but it was very finicky, so I decided to just keep it as regular text detection.
<p align="center">
  <img src="https://raw.githubusercontent.com/fatimakazim/fatimakazim.github.io/master/assets/images/transkribus.png" width="50%" alt="Transkribus Screenshot"/>
</p>


Example of marked-up text in Transkribus.  
The output from Transkribus was very accurate in terms of letters; I had to make only minor edits to get exact matches. To organise this information into table data, I used Perplexity AI. I sent the following prompt with the data from each section (which was organised in regions from Transkribus).

> I am giving you some data that needs to be organised into a table. The columns are name, residence, and nationality; every line will correspond with a new cell, falling into each category every 3 lines. Do not change or add any new words.

After it rearranged the data, it also highlighted some inconsistencies, which I allowed it to correct, but still without changing any spellings or ‘correcting’. I continued to do this for 5 licence types and just manually added the transcriptions for licences with fewer than two rows. The paid Ngoma licenses were trickier because there were two columns of names and residences, so the AI was less able to pair them accurately since the Transkribus text output order was not consistent. I reviewed the text file to notice when the name-residence order shifted and tried to give Perplexity more guidance.

> Kassum Jaffer is a name with Mlandege as residence. After Vikokotoni, the order is shifted to residence first, then name. Please adjust this table accordingly without changing spellings and leaving blanks for issues.

After this output, I manually edited the table in Excel while looking at the original document to make sure all the data was lined up. Since Perplexity left the confusing cells blank, I was able to cut/paste all the data into the right spots.

# Accuracy and AI Limitations
One of the major challenges in using AI tools was the low image quality of the Gazette—although the scan quality is decent, the original print isn’t very clear, which makes it difficult to decipher some of the words, especially in the column listing residence names. The OCR models frequently misread text, resulting in garbled or fictional place names. None of the tools, including Transkribus, were able to accurately interpret these locations.  
As a result, we had to manually cross-check and correct every residence name. We relied on visual inspection and Google searches to confirm whether a location existed in Zanzibar or the surrounding region.

# Reflections on Prompt Engineering
We found that specific and image-based prompts worked better than generic ones. Uploading individual images gave us better control and accuracy, though at the cost of time. General prompts like “extract all data from this PDF” often led to partial or inconsistent extractions, regardless of the platform used.

# Metadata Enrichment and Geocoding
The three main types of metadata we added were location, date, and coordinates. The first two were based on the headings in the article. We also created a category tag based on the type of licences. The most time-consuming was the geocoding, as we completed it manually. There were many difficulties, as many of the residences were not listed online, perhaps because they are now archaic terms for these places. We also noticed that many of the spellings used in the publication had changed to their modern, standardised spellings. There were also some residences that had similar names with only slight spelling variations (Mwebeni vs Mwembeni) that we were not sure were spelling errors in the publication or just names that are less common. https://www.mindat.org/ was a helpful source for some of the residences, but they did not have highly specific coordinates for all locations. Google Maps was also used heavily since it provides coordinates for all districts or locations that we could manually copy and paste.

#  Data Cleaning and Manual Corrections
One of the main struggles we had was matching up geocodes for residences that showed up in both of our data samples, since we found the codes independently of each other. We manually adjusted these residences so that they all matched up. We chose to keep ‘unique’ spellings of locations even if they have the same coordinates so that the data text would still match the original source material, as there were few instances, and it would not skew the data significantly. Using simple Excel techniques, we were able to organise the data. Since the sample was also relatively small, only 230 lines, we did not need to use any functions, and just manually checking after filtering and sorting was enough.

## Visualisation Layers and Techniques

<div style="max-width: 900px; margin: auto;">
  <iframe src="/assets/kepler-map.html" width="100%" height="600px" style="border:none;"></iframe>
</div>

For this map, I chose a clustered point layer, grouping nearby licence points into single bubbles whose size reflects the number of licences in that locale. I set the colour based on the string field license type, so each cluster’s hue tells you the dominant license category there. Opacity was dialled back (∼27 %) to avoid over‑saturation, and I used subtractive blending so overlapping circles darken rather than simply pile on top of one another. Although this map doesn’t show it, I also added a category filter dropdown (Retail, Trade, Finance, Craft, Entertainment) so I can toggle layers on and off.

# Observed Patterns & Clusters
The heaviest concentrations sit squarely in Unguja’s Stone Town area (Zanzibar City), where virtually every licence type overlaps—trade brokers, money‑lenders, hawkers, silversmiths, and even theatrical and Ngoma licences—forming a multi‑coloured bullseye. A secondary cluster appears in Pemba’s Weti–Chake‑Chake–Mkoani corridor, but here the palette is dominated by Finance (Money‑Lender’s) and Trade (Broker’s), with very few Craft or Entertainment points. Beyond those two hubs, points thin out dramatically; a lone moneylender bubble near Mvomero and an isolated paid Ngoma licence on the mainland stand out as outliers.  
As we examined the map, we noticed that Zanzibar City stood out as the island’s commercial nucleus—almost every license type clustered there, from brokers and moneylenders to silversmiths, hawkers, and entertainment venues, suggesting a highly diversified urban economy. What also caught our attention were the smaller clusters in port towns like Weti, Chake-Chake, and Mkoani, which seemed more narrowly focused on trade and finance, indicating their role as local exchange points rather than full commercial centres. We were also struck by how empty the interior regions of both islands were; the lack of licensed activity there suggests either limited economic formalisation or perhaps informal economies that didn’t require licensing. Interestingly, we saw that hawker licences appeared in a wide radius around almost every settlement, hinting at the importance of mobile, small-scale retail in everyday life. Finally, a few scattered points on the mainland and deep inland on Pemba made us wonder about isolated or temporary commercial ventures—perhaps a lone theatrical group or a moneylender serving a dispersed population. Overall, the map reveals a strongly urban and coastal commercial structure, with highly localised exceptions.

# Reflection on the Use of AI Tools
The article “Provocations from the Humanities for Generative AI” emphasizes that “AI requires an understanding of culture”—not just language fluency but recognition of historical depth and specificity. In our project, even seemingly small choices—like correctly identifying a license holder’s residence—required human contextual judgment. This experience reinforced that AI can be a helpful tool, but not a replacement for the kind of critical, interpretive thinking that humanities scholarship values and that historical data demands.  
As we analyze the data on license issuance, a key quote from the article stands out:  
> "Humanities researchers track these complex meanings across time and place, and we share a commitment to protecting the stories of the few over the many".

This quote underscores the importance of examining the nuances and complexities within historical datasets, rather than simply focusing on broad trends. In the case of the Zanzibar Gazette, the license data likely reflects not just economic activity, but also the power dynamics and social hierarchies of the colonial era. The quote encourages us to look beyond the surface-level statistics and consider how this dataset may privilege certain narratives or perspectives over others. For example, the spatial distribution of licenses could reveal patterns of marginalization, with certain regions or communities having more limited access to economic opportunities.

# Conclusion
Overall, this assignment helped us uncover spatial and economic patterns in colonial Zanzibar through data extraction and visualization. Despite challenges, the process offered valuable insights into how historical records can be analyzed using digital tools.

### Data and Source Files
- [Jan-license-section](https://fatimakazim.github.io/assets/jan-license.pdf)
- [Feb-license-section](https://fatimakazim.github.io/assets/feb-license.pdf)
- [zanzibar-licenses-dataset-1914](https://fatimakazim.github.io/assets/zanzibar.csv)

# Resources
Klein, Lauren, et al. “Provocations from the humanities for generative ai research.” *arXiv preprint* arXiv:2502.19190 (2025).

☑️READY FOR GRADING☑️


