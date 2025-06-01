# Protoype for askNEU
This is the prototype model of askNEU . 

### Final product has been released , check it out below !   

Try it here : https://askneu.com/

(If the site is down, it may be undergoing updates or maintenance. Please check back in a little while)

Technical Breakdown : https://drive.google.com/file/d/1-MkJ1w56oQ56rsKOPjB9l2fk9EhrPkGX/view

Key Features : 

• 𝐒𝐞𝐚𝐫𝐜𝐡 𝐚𝐜𝐫𝐨𝐬𝐬 𝟏𝟎𝟎+ 𝐍ortheastern University 𝐰𝐞𝐛𝐬𝐢𝐭𝐞𝐬, 𝟐𝟎,𝟎𝟎𝟎+ 𝐰𝐞𝐛 𝐩𝐚𝐠𝐞𝐬, 𝐚𝐧𝐝 𝟐,𝟎𝟎𝟎+ 𝐏𝐃𝐅𝐬


• 𝐀𝐜𝐜𝐞𝐬𝐬 𝐝𝐞𝐞𝐩 𝐬𝐞𝐚𝐫𝐜𝐡 powered by AI Agents 𝐟𝐨𝐫 𝐜𝐨𝐦𝐩𝐥𝐞𝐱 𝐪𝐮𝐞𝐫𝐢𝐞𝐬 𝐭𝐡𝐚𝐭 𝐬𝐩𝐚𝐧 𝐦𝐮𝐥𝐭𝐢𝐩𝐥𝐞 𝐬𝐨𝐮𝐫𝐜𝐞𝐬


• 𝐅𝐢𝐧𝐝 𝐬𝐭𝐮𝐝𝐲 𝐬𝐩𝐚𝐜𝐞𝐬 𝐢𝐧 𝐮𝐧𝐨𝐜𝐜𝐮𝐩𝐢𝐞𝐝 𝐜𝐥𝐚𝐬𝐬𝐫𝐨𝐨𝐦𝐬


• 𝐐𝐮𝐞𝐫𝐲 𝐜𝐨𝐮𝐫𝐬𝐞 𝐨𝐟𝐟𝐞𝐫𝐢𝐧𝐠𝐬 𝐮𝐬𝐢𝐧𝐠 𝐧𝐚𝐭𝐮𝐫𝐚𝐥 𝐥𝐚𝐧𝐠𝐮𝐚𝐠𝐞


https://github.com/user-attachments/assets/28d26136-0b5e-44cd-a34d-17e2b3ad5f82

## Prototype

AskNEU is a conversational Retrieval-Augmented Generation (RAG)  designed to provide Q&A functionality based on Northeastern University website data. By leveraging RAG techniques combined with GPT-based language models, the application enables users to ask questions and receive contextually accurate answers derived from university information.


## Data

Dataset aggregation can be seen as two phase such as data extraction and data processing :

Data Extraction : The data was sourced from publicly accessible Northeastern University websites, covering various domains such as admissions and alumni resources.
Key sources include:

* Office of Global Services (OGS)
* Student Financial Services (SFS)
* NEU Marino
* Student Catalogue
* Admissions (Graduate and Undergraduate,Phd’s)
* University Health and Counselling Services (UCHS)
* University Website Content: Pages from the official Northeastern University website, including academic catalogs, student handbooks, and faculty directories.
* Frequently Asked Questions (FAQs): A compilation of common questions and answers across these websites.

**Only publicly available data was utilized**

## Technical Details
- **Embedding Model:**
  - snowflake-arctic-embed-m-v1.5 model is used for embedding generation.

- **Vector Store:**
  - Pinecone is employed to store and retrieve vectorized data efficiently.

- **Chunking Process:**
  - Data is split into manageable chunks using Recursive Character Splitter to ensure meaningful context retrieval.

- **LLM Integration:**
  - One LLM rephrases queries to make them self-contained.
  - Another LLM generates final answers based on the rephrased queries and retrieved context.
    
- **Hydrid Retreival** Hybrid retriever combines multiple retrieval techniques, typically integrating both semantic search (vector-based) and lexical search (keyword-based), to maximize the relevance and 
  accuracy of retrieved information
  
  ![image](https://github.com/user-attachments/assets/13271e32-49cd-4911-abea-d9cddc05b2df)


## System Workflow

![image](https://github.com/user-attachments/assets/43bafedd-1797-496b-a840-c89c0401c459)

# Evaluation of RAG LLM Architecture for Hybrid and Vector RAG

![image](https://github.com/user-attachments/assets/9d001b48-2242-498f-a68d-2a3671b5b7b4)

The evaluation of the RAG LLM architecture for both hybrid and vector RAG is conducted in two phases: first, the generation of synthetic data, followed by the application of evaluation metrics.

**Synthetic Dataset Generation:**
We use state-of-the-art models to generate questions and answers (ground truth) based on context from the dataset. This synthetic data serves as test data for evaluating the models.
The generated questions fall into three categories:

1) Simple: Basic factual queries.
2) Reasoning: Queries that require logical deduction.
3) Multicontext: Queries that involve understanding multiple pieces of information from various contexts.

**Evaluation Metrics:**

Qualitative Evaluation: Assesses the model's performance on specific aspects to gain a deep understanding of its capabilities.

Relevance: Does the response directly address the query and stay on-topic?
Accuracy: Is the provided information correct and aligned with the ground truth?
Completeness: Does the response cover all key aspects of the question, without omitting any important details?
Clarity: Is the response easy to understand with clear and effective language?
Conciseness: Is the response free of unnecessary details and overly verbose explanations?

Quantitative Evaluation: Measures the model's performance using metrics like average ROUGE scores (ROUGE-1, ROUGE-2, ROUGE-L) to assess similarity between the generated responses and the ground truth.


## API Keys
- Pinecone API key (for vector storage)
- OpenAI API key  


## Project Structure
```plaintext
askneu/
├── Ask_Neu-Final.ipynb          # Main application script
├── data.txt                     # Google Drive link containing files after scrapping webpages
├── requirements.txt             # Python dependencies
├── README.md                    # Project documentation
└── synthetic_data_evaluated.csv # results on syntethic data
```

Feel free to explore, contribute, and improve AskNEU to make university data more accessible and insightful!


