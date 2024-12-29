# LangChain Assignment: Extracting Structured Information

## Objective
This project extracts structured information about characters from a dataset of stories and outputs the details in JSON format. The implementation leverages LangChain, FAISS vector database, and MistralAI (or an alternative embedding provider) to process unstructured narrative data into structured data.

---

## Prerequisites
Ensure the following are installed and configured:

1. **Python** (Version 3.8 or higher)
2. **Required Libraries**:
   ```bash
   pip install langchain faiss-cpu python-dotenv requests
   ```
3. **API Key**: Obtain your API key for MistralAI or an alternative embedding provider.
4. **Dataset**: A folder named `stories` containing text files, where each file represents a single story.

---

## Features
The script provides two main CLI commands:

1. **`compute-embeddings`**:
   - Reads all stories in the dataset.
   - Computes embeddings for the stories.
   - Stores the embeddings in a FAISS vector database.

2. **`get-character-info`**:
   - Takes a character name as input.
   - Searches the vector database for relevant story details.
   - Outputs structured details about the character in JSON format.

---

## Installation and Setup

1. **Clone the Repository**
   ```bash
   git clone https://github.com/your-username/langchain-assignment.git
   cd langchain-assignment
   ```

2. **Set Up Environment Variables**
   Create a `.env` file to store your API key:
   ```
   MISTRAL_API_KEY=your_mistral_api_key
   ```

3. **Run the Script**
   Ensure all dependencies are installed and the dataset is placed in the `stories` folder.

---

## Usage

### 1. Compute Embeddings
   ```bash
   python script.py compute-embeddings
   ```
   - Reads all `.txt` files in the `stories` folder.
   - Computes embeddings and saves them in the FAISS database.

### 2. Get Character Information
   ```bash
   python script.py get-character-info --character_name "Jon Snow"
   ```
   - Searches for the character in the processed stories.
   - Outputs details in the following JSON format:
     ```json
     {
       "name": "Jon Snow",
       "storyTitle": "A Song of Ice and Fire",
       "summary": "Jon Snow is a brave and honorable leader who serves as the Lord Commander of the Night's Watch and later unites the Free Folk and Westeros against the threat of the White Walkers.",
       "relations": [
         { "name": "Arya Stark", "relation": "Sister" },
         { "name": "Eddard Stark", "relation": "Father" }
       ],
       "characterType": "Protagonist"
     }
     ```

---

## Edge Case Handling

- If a character is not found in the dataset, the script will return an error message:
  ```json
  {
    "error": "Character not found in the dataset."
  }
  ```

---

## Extensibility

- **Additional Embedding Providers**: You can replace MistralAI with OpenAI or Hugging Face embeddings by updating the embedding class.
- **Improved JSON Outputs**: Enhance the structured JSON format to include additional details like location or events.
- **Web Interface**: Extend the script to a Flask or FastAPI-based web interface for easier interaction.

---

## Example Outputs

**Command**:
```bash
python script.py get-character-info --character_name "Jon Snow"
```

**JSON Output**:
```json
{
  "name": "Jon Snow",
  "storyTitle": "A Song of Ice and Fire",
  "summary": "Jon Snow is a brave and honorable leader who serves as the Lord Commander of the Night's Watch and later unites the Free Folk and Westeros against the threat of the White Walkers.",
  "relations": [
    { "name": "Arya Stark", "relation": "Sister" },
    { "name": "Eddard Stark", "relation": "Father" }
  ],
  "characterType": "Protagonist"
}
```

