# "A Wall of Prompt"
### _Using Gemini AI to compare real-estate investment for short-term rentals_
**Author:** [Elisa Romondia](https://elisaromondia.it)

## Abstract
This project was created as a **Capstone Project** for the [5-day Generative AI Intensive course](https://rsvp.withgoogle.com/events/google-generative-ai-intensive). The goal is to apply [Gemini AI](https://gemini.google.com/) capabilities to a real-world project. To make the project more understandable to a wider audience, I looked for a real-world problem that was common today. A real estate investment intended as the purchase of a property to be rented out through short-term rentals. To make the use case more familiar to a wider audience, I chose to focus on small apartments, well-known locations and a well-known service for short-term rentals, in this case, [airbnb](https://www.airbnb.com/). As locations, I chose to take two starting points (gemini will then help me refine the search on specific areas based on my requests in the prompts) in the same country (Italy): [Milano](https://en.wikipedia.org/wiki/Milan), because it is one of the most visited cities in Italy and the Italian location of one of the most successful TV series of this period: [The White Lotus (second 2)](https://en.wikipedia.org/wiki/The_White_Lotus_season_2). We know from Wikipedia that Taormina is the main location but to demonstrate the AI's capabilities (in this specific case, grounding), I will base the initial prompt on the reference to the second season of the TV series.

### Disclaimer about the data used in the notebook
Given the demonstrative purpose of this project, all files used must be public, therefore to avoid any violation of privacy, they were all previously generated randomly except the external database _(listings.csv)_ used as a comparison and the files generated within the notebook itself _(example: avg_bnb_plot.jpg)_. _**Any reference to real people or companies in those files is to be considered purely coincidental.**_

Let's see in detail each of the files used in this notebook:

* **[breraapt.pdf](https://github.com/elicatinthebox/geminicapexp/blob/main/documents/breraapt.pdf)**: .pdf file randomly generated to present a sample of a hypothetical advertisement for the sale of an apartment in the Brera area of ​​Milan. File hosted on GitHub.
* **[naxosapt.pdf](https://github.com/elicatinthebox/geminicapexp/blob/main/documents/naxosapt.pdf)**: .pdf file randomly generated to present a sample of a hypothetical advertisement for the sale of an apartment in Giardini Naxos (Taormina). File hosted on GitHub.
* **[dummy_prices.csv](https://github.com/elicatinthebox/geminicapexp/blob/main/documents/dummy_prices.csv)**: .csv file randomly generated to simulate a database of hypothetical supplier partners for renovation work with prices and type of renovation. File hosted on GitHub.
* **[naxosphotoa.jpg](https://github.com/elicatinthebox/geminicapexp/blob/main/photos/naxosphotoa.jpg)** and **[naxosphotob.jpg](https://github.com/elicatinthebox/geminicapexp/blob/main/photos/naxosphotob.jpg)**: All photos were randomly generated with AI to simulate an apartment in Giardini Naxos (Taormina), with a very damaged bathroom and not furnished. Files hosted on GitHub. Format .jpg
* **[breravideo.mp4](https://github.com/elicatinthebox/geminicapexp/blob/main/videos/breravideo.mp4)**: Randomly generated with AI to simulate a home video tour of the apartment in the Brera area of ​​Milan, based on the related .pdf document previously generated. File hosted on github. Format .mp4




* **[listings.csv](https://data.insideairbnb.com/italy/lombardy/milan/2025-03-13/visualisations/listings.csv)**: .csv file from [insideairbnb](https://insideairbnb.com/) a mission driven project that provides data publicly accessible about Airbnb. The .csv selected contains specifically summary information and metrics for listings in Milan, as it mentioned on [this page ](https://insideairbnb.com/get-the-data/)under the section about Milan. The main dataset can be interactively explored at [this page](https://insideairbnb.com/milan/). To know more about the data, please refer to their [Data dictionary](https://docs.google.com/spreadsheets/d/1iWCNJcSutYqpULSQHlNyGInUvHg2BoUGoNRIGa6Szc4/edit?gid=1322284596#gid=1322284596). Please keep in mind that the file is downloaded via url in the notebook and that it may differ over time as it is periodically updated by the maintainers of the insideairbnb project.

## Notebook Overview

The notebook walks through a comparative analysis of two hypothetical properties:

1.  A small apartment in the **Brera district, Milan**.
2.  A fixer-upper apartment near the sea in **Giardini Naxos, Sicily** (near Taormina, the location of "The White Lotus" season 2, used to test AI grounding).

It utilizes a series of prompts ("a wall of prompts") to interact with the Gemini API, performing tasks such as:

* Gathering initial market insights (potential earnings, regulations) using Gemini grounded with Google Search.
* Analyzing external Airbnb market data for Milan (`listings.csv`).
* Processing information from hypothetical documents (property PDFs, renovation cost CSVs).
* Interpreting simulated visual data (a video tour of the Milan apartment, photos of the Sicily apartment).
* Estimating potential renovation costs based on the analyzed data.

## Environment & Setup

This notebook is designed to run in the **Kaggle environment**.

* **Language:** Python 3 (specifically tested with Python 3.10.12)
* **Internet:** Must be enabled in Kaggle settings for Gemini API calls and grounding.
* **API Key:** Requires a Google AI API key. Add your key to **Kaggle Secrets** with the label `GEMINI_API_KEY`. The notebook is configured to retrieve the key from there.
* **Libraries:** The notebook installs and imports the following key libraries:
    * `google-generativeai`
    * `pandas`
    * `matplotlib`
    * (and other standard Python libraries)

## Data Sources

The analysis relies on a combination of data sources:

1.  **Gemini AI with Grounding:** Leverages Gemini's ability to access and process information from Google Search for real-time insights.
2.  **External Data:** Uses `listings.csv` for Milan from [insideairbnb.com](http://insideairbnb.com/) (specifically a publicly available dataset from March 2024) for market price analysis.
3.  **Hypothetical/Generated Data:** Includes sample/dummy data created for demonstration purposes due to privacy considerations:
    * PDF documents representing property listings.
    * A CSV file with sample renovation costs.
    * Links to simulated video/image files representing the properties.

**Note:** The use of generated data means the final investment comparison is illustrative rather than based on actual properties.

## How to Use

1.  Ensure you have added your `GEMINI_API_KEY` to Kaggle Secrets.
2.  Enable Internet access in the notebook settings.
3.  Run the cells sequentially to follow the analysis workflow.
4.  Modify prompts or input data (if desired) to explore different scenarios.

## Project Demonstration

The primary goal of this notebook is to **demonstrate the versatile capabilities of Gemini AI** in a complex, multi-faceted analysis task. It shows how AI can integrate and reason over text, structured data, web search results, documents, video, and images.

While it performs a comparative analysis, the conclusions regarding the specific properties are illustrative due to the use of generated data. Users are encouraged to adapt the methods shown here to their own real-world data and scenarios.

---

*Feel free to explore and adapt this notebook!*
