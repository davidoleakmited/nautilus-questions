# Nautilus Questions

This repository contains structured JSON files to organize questions and dialogues for the Nautilus dataset.

## File Structure

The project contains two types of files:

1. **`questions_fr.json`** : Contains main questions organized by difficulty levels
2. **`dialogue_fr.json`** : Contains dialogues and follow-up questions in a conversational context

## JSON File Structure

Each JSON file follows this structure:

```json
{
  "twin": {
    "author": "Author Name",
    "title": "Dataset Title",
    "description": "Dataset Description",
    "version": "1.0.0",
    "date": "YYYY-MM-DD",
    "license": "MIT",
    "tags": ["tag1", "tag2", "tag3"],
    "playablePlaylist": ["N00B", "EASY"],
    "levels": {
      "N00B": [...],
      "EASY": [...],
      ...
    }
  }
}
```

## Difficulty Levels

Questions are organized into difficulty levels:

- **N00B** : Basic questions, beginner level
- **EASY** : Easy questions
- **AVG_HYDRAULIC_MC** : Intermediate level questions on hydraulics
- **JUNIOR_HYDRAULIC_MC** : Junior level questions on hydraulics
- **LEAKMITED_EXPERT** : Expert questions

## Question Structure

Each question must have the following structure:

```json
{
  "id": "N00B_01",
  "intent": "lecture",
  "type": "attributaire",
  "question": "Question text"
}
```

### Required Fields

- **`id`** : Unique question identifier (format: `LEVEL_NUMBER`, e.g., `N00B_01`, `EASY_02`)
- **`intent`** : Question intent. Possible values:
  - `lecture` : Simple data reading
  - `agrégation` : Data aggregation
  - `statistique` : Statistical analysis
  - `spatial` : Spatial/geographical question
  - `corrélation` : Correlation between data
  - `diagnostic` : Diagnostic or analysis
  - `topologie` : Topological question
  - `simulation` : Scenario simulation
  - `couverture` : Coverage question
- **`type`** : Question type. Possible values:
  - `attributaire` : Question about attributes
  - `spatial` : Spatial question
  - `géographique` : Geographical question
  - `hydraulique` : Hydraulic question
  - `statistique` : Statistical question
  - `temporel` : Temporal question
  - `patrimonial` : Heritage/asset question
  - `maintenance` : Maintenance question
  - `matériau` : Material question
  - `réseau` : Network question
  - `sécurité_incendie` : Fire safety question
  - `branchement` : Connection/branch question
  - `performance` : Performance question
- **`question`** : The question text in French

## How to Create a New Batch of Questions

### Step 1: Choose the Target File

Determine if you are creating:
- **Main questions** → `questions_fr.json`
- **Dialogues/follow-up questions** → `dialogue_fr.json`

### Step 2: Determine the Difficulty Level

Choose the appropriate level for your questions:
- Start with **N00B** for basic questions
- Use **EASY** for slightly more complex questions
- Use advanced levels for specialized questions

### Step 3: Create the Questions

For each question:

1. **Generate a unique ID**:
   - Format: `LEVEL_NUMBER` (e.g., `N00B_01`, `EASY_15`)
   - Use sequential numbers (01, 02, 03...)
   - Verify it doesn't already exist in the file

2. **Determine the intent**:
   - Analyze what the question asks
   - Choose the appropriate intent from the list above

3. **Determine the type**:
   - Choose the type that best matches the question's domain

4. **Write the question**:
   - Formulate the question in French
   - Be clear and precise
   - Use natural language

5. **Determine which playlist have to be played**:
   - List all playlists level system have to play as an array
   - So you can create questions in advance but prevent them to be played
   - `"playablePlaylist": ["N00B"],` 

### Step 4: Add Questions to the JSON File

1. Open the appropriate JSON file
2. Navigate to the desired level in `levels`
3. Add your question to the level's array
4. Ensure the JSON syntax is correct (commas, braces, etc.)

### Example: Adding a N00B Question

```json
{
  "levels": {
    "N00B": [
      {
        "id": "N00B_01",
        "intent": "lecture",
        "type": "attributaire",
        "question": "Quelle est la longueur totale du réseau ?"
      },
      {
        "id": "N00B_14",
        "intent": "lecture",
        "type": "spatial",
        "question": "Où se trouvent les stations de traitement ?"
      }
    ]
  }
}
```

### Step 5: Update Metadata (if necessary)

If you are creating a new dataset or significantly modifying an existing one:

1. Update `author` with your name
2. Update `date` with the current date (format YYYY-MM-DD)
3. Increment `version` if necessary (e.g., "1.0.0" → "1.1.0")
4. Add/modify `tags` if necessary
5. Update `playablePlaylist` to include the levels you have modified

### Step 6: Validate the JSON

Before saving, verify that:

- The JSON is valid (no syntax errors)
- All IDs are unique
- All required fields are present
- Commas are correctly placed (no comma after the last element of an array)

You can use an online JSON validator or your editor to check the syntax.

## Best Practices

1. **ID Consistency** : Use a consistent format for IDs (e.g., always 2 digits: `01`, `02`, etc.)

2. **Organization** : Group similar questions together in the same level

3. **Progression** : Ensure difficulty increases logically between levels

4. **Clarity** : Questions should be clear and unambiguous

5. **Coverage** : Try to cover different types and intents for each level

6. **Validation** : Test your questions to ensure they are understandable and relevant

## Complete Example: Creating a New EASY Question Batch

```json
{
  "twin": {
    "author": "Your Name",
    "title": "Questions pour le jeu de données Twin",
    "description": "Questions pour le jeu de données Twin",
    "version": "1.0.0",
    "date": "2025-01-20",
    "license": "MIT",
    "tags": ["twin", "questions", "jeu de données"],
    "playablePlaylist": ["N00B", "EASY"],
    "levels": {
      "EASY": [
        {
          "id": "EASY_12",
          "intent": "agrégation",
          "type": "attributaire",
          "question": "Quelle est la longueur moyenne des conduites par commune ?"
        },
        {
          "id": "EASY_13",
          "intent": "statistique",
          "type": "temporel",
          "question": "Quelle proportion du réseau a été posée avant 1980 ?"
        }
      ]
    }
  }
}
```

## Useful Tools

- **JSON Validator** : Use a JSON validator to check syntax
- **Editor with JSON Support** : Use an editor with syntax highlighting and JSON validation
- **Formatting** : Use a JSON formatter to maintain consistent indentation

## Support

For any questions or issues, consult the existing files as reference or contact the project team.

