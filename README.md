# Heart Disease Identification with K-Nearest Neighbors

A JavaFX desktop application that connects an interactive health-attribute form to a nearest-neighbor classifier. The project demonstrates an end-to-end machine-learning application: dataset parsing, numeric scaling, feature-based comparison, evaluation, and presentation of a binary classification result.

## Classification pipeline

```text
Cleveland records → DataParser → Scaled training points
                                      |
User-entered attributes → Scaled point → Five-neighbor vote → UI result
```

The supplied `processed.cleveland.data` contains the training records. `DataParser` reads comma-separated attributes and manages feature scaling. `Distance` computes Euclidean distance over the selected attributes: age, chest-pain type, resting electrocardiographic results, exercise-induced angina, slope, major-vessel count, and thalassemia indicator.

`Knn` ranks training observations and uses a **five-neighbor majority vote**. A target value of zero represents absence of disease; nonzero labels are grouped into the presence class.

## Application structure

| Path | Responsibility |
| --- | --- |
| `src/app/Main.java` | JavaFX application entry point |
| `src/ui/UserInterface.java` | Input controls and result presentation |
| `src/parsing/DataParser.java` | Dataset loading and scaling |
| `src/ml/` | Data model, distance ranking, classifier, and evaluation |
| `src/files/` | Dataset, correlation information, and UI image |

The evaluation component calculates confusion-matrix counts, accuracy, recall, precision, and F-score. [The proposal](HeartDiseaseProposal.pdf) provides the accompanying project context.

## Launch

Import the repository into a Java IDE with a JDK and JavaFX controls configured. Mark `src/` as the source root and run `app.Main` from the repository root so `src/files/processed.cleveland.data` resolves correctly. Enter the requested attributes in the form and submit them to follow the classification workflow.

**Technical focus:** supervised classification, feature selection, preprocessing, evaluation metrics, and integration of a custom model with a desktop interface.
