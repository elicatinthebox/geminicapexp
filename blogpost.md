# Capstone Project: "A Wall of Prompt"
## Using Gemini AI for Real Estate Investment Analysis
#### _Author: [Elisa Romondia](https://elisaromondia.it/)_
#### Kaggle notebook public link: https://www.kaggle.com/code/elisaromondia/a-wall-of-prompt-capstone-project

## Introduction

Choosing the right real estate investment, especially for the booming short-term rental market, can feel like navigating a complex maze. Data is scattered, market trends fluctuate, and comparing potential returns across different locations and property types requires significant effort. I wondered: what if Artificial Intelligence could act as my expert analyst, consolidating information, understanding diverse data formats, and providing insightful comparisons?

This curiosity led me to develop my capstone project, **"A Wall of Prompt"**, for the [5-day Generative AI Intensive course](https://rsvp.withgoogle.com/events/google-generative-ai-intensive). My goal was to apply the power of [Gemini AI](https://gemini.google.com/) to a real-world challenge: comparing real estate investment opportunities for short-term rentals, specifically focusing on the popular [Airbnb](https://www.airbnb.com/) platform.

## The Challenge: Comparing Apples and Oranges (or Milanese Studios and Sicilian Sea Views)

To make the project relatable, I focused on a common investment scenario: purchasing a small apartment for short-term letting. The core challenge I set myself was comparing two very different properties in distinct Italian locations:

1.  A luxury studio apartment in the prestigious Brera district of [Milan](https://en.wikipedia.org/wiki/Milan).
2.  An unfurnished, renovation-required apartment with sea views in Giardini Naxos, Sicily, near Taormina (the filming location for season 2 of [The White Lotus](https://en.wikipedia.org/wiki/The_White_Lotus_season_2)).

How could I objectively compare these options, considering factors like purchase price, renovation costs, rental potential, location desirability, and local regulations? This required processing diverse information – property listings (PDFs), renovation price lists (CSV), market data (external CSVs and web searches), property visuals (images), and even video tours.

## My Gemini AI Approach: A "Wall of Prompt" Strategy

My project efficiently employs Gemini AI (specifically, I experimented with the `gemini-1.5-flash-002` and `gemini-2.0-flash` models) as a central analysis engine. I called it "A Wall of Prompt" because my strategy involved iteratively prompting Gemini with various data sources and questions to build a comprehensive comparison.

### Data Sources & Gemini's Multimodality

A key aspect of the project was leveraging Gemini's ability to understand multiple data formats. It's important to note that most input files I used were randomly generated for demonstration purposes to avoid privacy issues, with the exception of external market data.

I fed Gemini:

* **PDF Property Listings:** Details for the [Brera apartment](https://github.com/elicatinthebox/geminicapexp/blob/main/documents/breraapt.pdf) and the [Giardini Naxos apartment](https://github.com/elicatinthebox/geminicapexp/blob/main/documents/naxosapt.pdf). I asked Gemini to extract key details like location, price, size, condition, and features.
* **CSV Renovation Prices:** A [dummy price list](https://github.com/elicatinthebox/geminicapexp/blob/main/documents/dummy_prices.csv) from hypothetical suppliers, which I used to ask Gemini to estimate renovation costs.
* **External CSV Market Data:** Airbnb [listings data for Milan](https://data.insideairbnb.com/italy/lombardy/milan/2025-03-13/visualisations/listings.csv) from the fantastic [Inside Airbnb](https://insideairbnb.com/) project. I used this for data cleaning, analysis (generating the price chart below), and comparing against Gemini's grounded search results.
   ![Data Visualization](https://github.com/elicatinthebox/geminicapexp/raw/refs/heads/main/photos/avg_bnb_plot.jpg)
* **Images:** AI-generated photos simulating the [Giardini Naxos apartment](https://github.com/elicatinthebox/geminicapexp/raw/refs/heads/main/photos/naxosphotoa.jpg) and its [damaged bathroom](https://github.com/elicatinthebox/geminicapexp/raw/refs/heads/main/photos/naxosphotob.jpg). I prompted Gemini to analyze these for condition assessment.
    ![Naxos Apartment Main Room](https://github.com/elicatinthebox/geminicapexp/raw/refs/heads/main/photos/naxosphotoa.jpg)
    ![Naxos Apartment Bathroom](https://github.com/elicatinthebox/geminicapexp/raw/refs/heads/main/photos/naxosphotob.jpg)
* **Video:** An AI-generated [video tour of the Brera apartment](https://github.com/elicatinthebox/geminicapexp/blob/main/videos/breravideo.mp4), which I tasked Gemini with analyzing to describe the layout, style, condition, and even count windows.
  ![Brera Video frame](https://github.com/elicatinthebox/geminicapexp/raw/refs/heads/main/photos/brera_video.jpg)

### Methodology Highlights

In the notebook, I systematically guided Gemini through the comparison process:

1.  **Market Exploration (Grounding):** I used Gemini with Google Search grounding enabled to get initial estimates of Airbnb earnings, profitable areas, and regulations in Milan and the Taormina area (Giardini Naxos). Gemini's responses were impressively detailed, covering occupancy rates, daily rates, taxes, and legal requirements.
2.  **External Data Comparison:** External Data Analysis & Visualization
3 insights are powerful, but validation is key. The notebook incorporates external data – specifically, a listings.csv file for Milan sourced from the public data aggregator insideairbnb.com. Using Python libraries like Pandas, this data was loaded, cleaned (importantly, removing statistical outliers using the Interquartile Range method to avoid skewed results), and analyzed. Matplotlib was then used to visualize the average daily Airbnb prices across different Milan neighborhoods. This step serves as a vital cross-reference, allowing a comparison between Gemini's grounded insights and independent market data.
4.  **Document & Multimodal Understanding:** I uploaded and cached the PDF listings, renovation CSV, images, and video. I then prompted Gemini to describe these documents, analyze the properties' conditions, and assess the coherence of the chosen locations with its earlier profitable area suggestions.
5.  **Cost Estimation & Market Check:** I asked Gemini to estimate the cost of replacing the Brera apartment's three windows with wood, using the provided CSV data (it calculated an average of €800/window for a total of €2400). Then, I used grounding to ask it to check this estimate against the current Milan market. It concluded the estimate was reasonable for materials but likely underestimated the total cost by omitting installation – a valuable sanity check.
6.  **ROI Analysis:** Finally, I prompted Gemini to perform a simplified Return on Investment (ROI) calculation, comparing the high-cost/high-potential-income Brera property (estimated ROI 1.27%) with the lower-cost/needs-renovation Giardini Naxos property (estimated ROI 5.11%). While I acknowledge the limitations (simplified calculation, no financing costs, need for detailed market research), the analysis favoured the Giardini Naxos apartment for potentially higher ROI due to the much lower initial investment. Let's see the final parts of the notebook where the _ROI comparison_ and the _final note_ are shown:
    ![code snippets](https://github.com/elicatinthebox/geminicapexp/raw/refs/heads/main/photos/codesnippets.png)

## Conclusion: My Experience with Gemini as a Real Estate Analyst Assistant

My "A Wall of Prompt" project convinced me that Gemini AI can be a powerful tool for complex comparison tasks like real estate investment analysis. By leveraging its abilities in:

* **Information Retrieval:** Using grounding to access and synthesize web data.
* **Multimodal Understanding:** Processing text (PDF, CSV), images, and video.
* **Data Analysis:** Extracting key information, performing calculations (averages, ROI), and comparing data points.
* **Summarization & Reasoning:** Providing coherent descriptions, comparisons, and conclusions based on multiple inputs.

In my opinion, the project effectively tackled a real-world problem, showcasing how AI can streamline research and provide valuable insights for decision-making. While the data I used was partly illustrative, the methodology provides a strong blueprint for applying generative AI to investment analysis. My experience highlighted the importance of feeding the AI diverse, relevant data (hence, "A Wall of Prompt") and critically evaluating its outputs, especially when dealing with estimations and market variables. 

*Limitations*: Since this is a demonstration project I tried to limit the comparison by not repeating the application of the same functions on both apartments equally, this is because the main purpose is to show the capabilities of Gemini. For the same reason and to save costs the data samples have been limited. Keep in mind that in a real use case the data could be more substantial and require guarantees on their protection. For an in-depth analysis of real data, I strongly recommend including the same set of relevant documents for all properties being compared. Furthermore, considering that you are performing a financial real estate analysis, I strongly recommend having the report supervised by a qualified professional who is licensed to practice in the geographical jurisdiction where you intend to operate.

*Future possibilities*: I would like these features to be integrated into real estate listings. In my opinion, it would be fantastic to be able to integrate the ability to provide personalized requests and review real documents, all using a conversational system in human language. In particular, to be able to estimate renovation costs. This would also open up the possibility of partnerships with building renovation companies that could collaborate by providing estimates on the costs of standard types of work in order to have a match with potential customers on targeted properties even before the consumer actually becomes the owner. 

Furthermore, refining the ROI evaluation and calculation system presents another significant opportunity. By collaborating with short-term rental services and leveraging their data, a scoring system could be developed for real estate listings, indicating a property's potential for short-term rental income. 

Realizing these future possibilities fundamentally requires an investment in data collection and standardization to create optimized datasets and generate highly accurate outputs. Nevertheless, I am confident this investment would provide an excellent return, producing new integrated data that would foster beneficial partnerships across the entire real estate sector and simultaneously create favorable conditions for developing an AI that significantly enhances the consumer experience.

---

*Disclaimer: This project used randomly generated data for some inputs. Investment decisions should always be based on thorough, real-world market research and professional financial advice.*

![Easter Egg Image: AI-generated image inspired by "The White Lotus", featuring a book titled "A Wall of Prompt"](https://github.com/elicatinthebox/geminicapexp/raw/refs/heads/main/photos/easteregg.jpg)
 🪷  _**Easter Egg**: Image generated with [Gemini AI app](https://gemini.google.com/app) inspired by tv series "The White Lotus" where easter eggs are shown as the titles of books being read by the protagonists. In this case the book title is the title of the notebook project._

