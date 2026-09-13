# Lesson JSON Format

This folder contains JSON lesson files for pre-scripted dialogue lessons.

## File Naming Convention
- Filename: `{lessonId}.json`
- Example: `cafe_basics_001.json`

## JSON Structure

```json
{
  "LessonId": "unique_lesson_id",
  "ScenarioId": "scenario_001",
  "Title": "Lesson Title",
  "Description": "Brief description of the lesson",
  "AvatarPositions": {
    "avatar_id_1": "AvatarPos_1",
    "avatar_id_2": "AvatarPos_2"
  },
  "Turns": [
    {
      "TurnId": "turn_001",
      "TurnNumber": 1,
      "AvatarId": "avatar_id_1",
      "DialogueText": "What the avatar says",
      "AudioPath": "Audio/Lessons/folder/audio.mp3",
      "CameraName": "Camera_Name",
      "Duration": 3.5,
      "QuestionData": {
        "QuestionId": "q_001",
        "QuestionText": "Question to ask after this turn?",
        "QuestionType": "MultipleChoice",
        "Options": [
          "Option A",
          "Option B",
          "Option C",
          "Option D"
        ],
        "CorrectAnswer": 1,
        "Explanation": "Why this is correct",
        "Points": 10
      }
    }
  ]
}
```

## Field Descriptions

### Root Level
- **LessonId**: Unique identifier for the lesson (must match filename without .json)
- **ScenarioId**: Associated scenario ID
- **Title**: Display title of the lesson
- **Description**: Brief description shown to users
- **AvatarPositions**: Dictionary mapping avatar IDs to spawn point names

### Turn Object
- **TurnId**: Unique identifier for this turn
- **TurnNumber**: Sequential number (1-based)
- **AvatarId**: Which avatar speaks (must match a key in AvatarPositions)
- **DialogueText**: The dialogue text to display and speak
- **AudioPath**: Path to audio file in StreamingAssets (relative to StreamingAssets folder)
- **CameraName**: Name of Cinemachine camera to activate
- **Duration**: Expected duration in seconds (optional, used for timing)
- **QuestionData**: Optional comprehension question (see below)

### QuestionData Object (Optional)
- **QuestionId**: Unique identifier for the question
- **QuestionText**: The question to ask
- **QuestionType**: "MultipleChoice" (more types in Phase 4)
- **Options**: Array of answer choices (strings)
- **CorrectAnswer**: Index of correct option (0-based)
- **Explanation**: Explanation of the correct answer
- **Points**: Points awarded for correct answer

## Camera Names
Available cameras in AvatarScene:
- `Camera_Barista_Closeup`
- `Camera_Customer_Closeup`
- `Camera_Wide_Shot`

Add more cameras in AvatarScene and reference them by GameObject name.

## Avatar IDs
Must match the AvatarId field in the scenario's avatar list:
- `barista` (for scenario_001)
- `customer` (for scenario_001)

## Audio Files
Audio files should be placed in:
`StreamingAssets/Audio/Lessons/{folder_name}/{filename}.mp3`

Supported formats: MP3, WAV, OGG

## Example Lessons
- `test_lesson_001.json` - Simple 6-turn coffee shop conversation
- `cafe_basics_001.json` - 7-turn conversation with a comprehension question
