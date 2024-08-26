
# Pilot Operating Handbook RAG Pipeline

This project provides a simple pipeline to process a Pilot Operating Handbook (POH) for an aircraft. The pipeline enables users to ask questions about the POH by breaking down the text into manageable chunks and preparing it for use in retrieval-augmented generation (RAG) systems.

## Features

- **PDF Download and Parsing**: Automatically download the POH PDF and extract text using `PyMuPDF`.
- **Text Cleaning and Formatting**: Clean and format the extracted text for further processing.
- **Sentence Splitting and Chunking**: Split the text into sentences and further group these into chunks of configurable sizes.
- **Tokenization and Statistics**: Compute statistics such as token counts for each chunk, which can be useful for NLP tasks.

## Requirements

- Python 3.11+
- macOS with Apple Silicon (due to the mlx library)
- Sufficient unified memory to load the large language model locally. Feel free to choose a smaller one if needed.

## Installation

1. **Clone the repository**


2. **Install the required Python packages:**

   These are found in the pyproject.toml file. Either install them using [Poetry](https://python-poetry.org/) or manually using pip.

3. **Set up spaCy:**
   If using poetry spacy may not install properly. Use pip instead:

   ```bash
   pip3 install spacy
   ```

## Usage

1. **Download and process the POH:**

   Place the desired POH PDF in the root directory, or specify its URL in the notebook. The pipeline will handle downloading and text extraction. Note the Cessna 172 POH is there by default.

2. **Run the Jupyter Notebook:**

   Open the notebook `rag_pipeline_mlx.ipynb` and execute the cells. The notebook will:
   - Read the PDF
   - Clean and format the text
   - Split the text into sentences and chunks
   - Calculate statistics for further NLP processing
   - Take a query and run the pipeline to output an answer

3. **Customize the Pipeline:**

   Adjust the chunk size or other parameters directly in the notebook to fit your needs.

## Example

Here's an example of a user query and the answer provided by this RAG pipeline. The language model used is [quantized-gemma-7b-it](https://huggingface.co/mlx-community/quantized-gemma-7b-it) and the sentence embedding model is [bge-base](https://huggingface.co/BAAI/bge-base-en).

**User query**: _What are the standard procedures for operating the fuel selector valve on a Cessna 172S during flight?_

**Answer:**

The standard procedures for operating the fuel selector valve on a Cessna 172S during flight are as follows:

* **Takeoff, climb, landing, and maneuvers:** The fuel selector valve should be in the BOTH position for takeoff, climb, landing, and maneuvers that involve prolonged slips or skids of more than 30 seconds.
* **Cruising flight:** Operation from either LEFT or RIGHT tank is reserved for cruising flight.
* **Unequal fuel flow:** When the fuel selector valve handle is in the BOTH position in cruising flight, unequal fuel flow from each tank may occur if the wings are not maintained exactly level.

Therefore, it is important to ensure that the fuel selector valve is in the correct position for the specific flight maneuver to ensure proper fuel flow and avoid potential engine starvation.

## Contributing

Contributions and suggestions are welcome! This work will benefit from state of the art RAG libraries such langchain. Special attention needs to be paid to handling tables and diagrams in future work.

## Acknowledgements

I'd like to thank Daniel Bourke for his [work](https://www.youtube.com/watch?v=qN_2fnOPY-M). I adapted his nutrition RAG pipeline to work on native Apple Silicon and to be suited for an aircraft manual.
