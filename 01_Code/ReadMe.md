# 01_KG_Creation_Pipeline.ipynb

This jupyter notebook is designed to create and update a Knowledge Graph (KG) based on a provided list of entities located in the `02_Input` directory. The notebook includes pipelines to update entities and relations files, as well as an optional pipeline to identify and rectify any missing relations due to model errors.

## How to Use the Notebook

### Initialization
1. **Run all the initialization cells at the start:**
    - These cells set up the necessary environment variables, import required libraries, and configure the OpenAI API.

### Pipeline to Update Entities and Relations
2. **Run the `01: Pipeline to update the entities and relations files` located in `03_Output/00_GPT KGs`:**
    - This pipeline reads the entity list, generates metadata and relations for new entities, and updates the respective files.

### Optional Pipeline for Missing Relations
3. **Run the `02: Optional pipeline to identify any missing relations` in the created KG due to model errors, and update them:**
    - This pipeline identifies any files with missing relations and fills them.



# 02_Generate_KG_JSON.ipynb

This Jupyter notebook is designed to update the JSON files for the Knowledge Graph (KG) in the `00_Current Versions` and `01_Archived Versions` directories. The notebook includes steps to merge entities and relations, update the current KG, archive it for record, and push the updated JSON files to the `00_API` folder.

## How to Use the Notebook

### Initialization
1. **Import necessary libraries:**
    - Ensure all the required libraries such as `pandas`, `json`, `datetime`, `os`, and `shutil` are imported.

### Read Current Entities and Relations
2. **Read current entities and relations:**
    - Load the existing entities from `Entities.json`.
    - Load the relations from `Relations_replaced.csv`.

### Merge Entities and Relations
3. **Merge the entities and relations into JSON objects:**
    - Iterate over the entities and create a knowledge graph object for each entity.
    - Merge the corresponding relations for each entity into the knowledge graph object.

### Update the Current KG and Archive for Record
4. **Update the current KG and add it to the archive:**
    - Create a timestamp for the current update.
    - Write the updated knowledge graph to `knowledge_graph.json` in the `00_Current Versions` folder.
    - Archive the updated knowledge graph by writing it to the `01_Archived Versions` folder with the timestamp.

5. **Save individual JSON files for each entity:**
    - Save each entity's knowledge graph as a separate JSON file in the `00_Current Versions` folder.

### Push JSON Files to API Folder
6. **Run the cells to push JSON files from `00_Current Versions` folder to `00_API` folder:**
    - Use the `update_files_in_API` function to delete all initial files in the destination directory and copy all files from the source directory to the destination directory.


## Additional Notes
- **Dependencies:**
    - Ensure that all required libraries (`pandas`, `json`, `datetime`, `os`, `shutil`) are installed.
- **Environment Setup:**
    - Make sure the directories `../03_Output/00_GPT KGs/`, `../03_Output/01_Auto KGs/`, and `../00_API/` exist and have the necessary read/write permissions.
- **Environment Variables:**
    - Make sure the `.env` file is properly set up with the necessary API keys and endpoints for OpenAI.
