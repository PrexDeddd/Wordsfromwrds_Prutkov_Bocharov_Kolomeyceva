# Wordsfromwrds_Prutkov_Bocharov_Kolomeyceva
Выполнили студенты группы ИСП-244: Прутков Иван, Бочаров Илья, Коломейцева Виолетта

# Word-from-Word Level Generator

A lightweight Java utility that generates game levels for "Word-from-Word" (anagram) puzzle games and exports them in JSON format.

## Features

* **Letter Frequency Validation:** Accurately checks if a dictionary word can be constructed using the available letters of a main word without exceeding letter counts.
* **Automatic Filtering:** Removes duplicate dictionary entries, ignores words shorter than the configured threshold, and excludes the main word itself.
* **Dynamic Difficulty Scaling:** Automatically classifies levels as `EASY`, `MEDIUM`, or `HARD` based on the main word's length and caps the maximum number of sub-words accordingly.
* **Zero External Dependencies:** Built using only standard Java libraries (`java.util.*`) with manual JSON serialization.

## Configuration

You can adjust the generation rules directly inside the `main` method of `Main.java`:

| Parameter | Default | Description |
| :--- | :--- | :--- |
| `minSubWordLength` | `3` | Minimum character length required for a valid sub-word. |
| `minWordsToPass` | `4` | Minimum number of valid sub-words required to generate a level (also sets the player's pass threshold). |
| `easyMaxMainWordLength` | `7` | Maximum main word length for the `EASY` difficulty tier. |
| `mediumMaxMainWordLength` | `10` | Maximum main word length for the `MEDIUM` difficulty tier (longer words default to `HARD`). |
| `easyMaxSubWords` | `5` | Maximum number of sub-words included in an `EASY` level. |
| `mediumMaxSubWords` | `10` | Maximum number of sub-words included in a `MEDIUM` level (`HARD` has no limit). |

## Getting Started

### Prerequisites
* Java Development Kit (JDK) 8 or higher.

### Running the Generator
1. Ensure your source file is named `Main.java` (matching the `public class Main` declaration).
2. Compile the code:
   ```bash
   javac Main.java
   ```
3. Run the application:
   ```bash
   java Main
   ```

## Example Output

```text
Пропущено слово: ВЗАИМНОСТЬ (мало подслов)
Пропущено слово: КОРОТКОЕ (мало подслов)
Пропущено слово: СЛОВО (мало подслов)
```

```json
{
  "levels": [
    {
      "id": 1,
      "mainWord": "ДЕМОНСТРАЦИЯ",
      "difficulty": "HARD",
      "minWordsToPass": 4,
      "subWords": [
        { "text": "ДЕСАНТ", "hint": "" },
        { "text": "АДРЕС", "hint": "" },
        { "text": "АРМИЯ", "hint": "" },
        { "text": "МЕСТО", "hint": "" },
        { "text": "МЕТРО", "hint": "" },
        { "text": "ДЕСНА", "hint": "" },
        { "text": "СРЕДА", "hint": "" }
      ]
    }
  ]
}
```
