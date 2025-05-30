	Your	approach	


    Question 1

Ran a Series of Exploratory Data Analysis to give some insite on the data using random forest, and other tehniques.

Output was validated using ROC, Cross Validation, Confision Matrix and F1 Score



Question 2

csv File Handling: Extracts content from .csv

Semantic Search: Uses Gemini's embeddings to convert content into dense vector representations.
Vector Database Integration: Stores embeddings in a ChromaDB collection and allows semantic querying.
Conversational Answer Generation: Uses Gemini to return friendly and informative answers based on the retrieved content.


    Steps:

Step 1: Unzipping and Extracting Documents All files inside X_Files.zip are extracted and processed by type. Their text contents are stored in a Python dictionary.

Step 2: Embedding with Gemini Each document is passed through GeminiEmbeddingFunction, generating embeddings via text-embedding-004. These are stored in ChromaDB with unique IDs.

Step 3: Querying with Natural Language A query like "why do patients get readmitted withing 30 days?" is vectorized and used to search ChromaDB. Top-matching documents are retrieved.

Step 4: Answer Generation The retrieved documents are appended to a contextual prompt, and Gemini generates a complete, user-friendly answer.

Example Query query = "why do patients get readmitted withing 30 days?" Expected Output: A detailed answer using relevant documents retrieved from your dataset.


    -	Key	results	
        - ROC AUC : 
        The ROC curve evaluates the model as follows:

        The model never makes a false positive or false negative in your the  set.
        While this is ideal, it’s also unrealistic in real-world data.

        This may be as a result of Overfitting (the model may have memorized training data).
        Data leakage (information from the target variable unintentionally included in training) is also a concern

    - Confusion Matrix :
        Orange line (Train accuracy): Accuracy of the model on the training data.

        Blue line (Mean cross-validation accuracy): Average performance on unseen data across folds during cross-validation.

        Blue shaded area: Likely represents the standard deviation or confidence interval around the mean cross-validation accuracy.

        After a tree depth of ~5 or 6, the training accuracy keeps improving, but the validation accuracy stagnates or worsens. This indicates overfitting 

    - F1 Score :

        Class 0 :
        Very strong performance with 93% recall (almost all true class 0s are correctly identified).

        High F1-score (0.80) indicates a well-balanced performance between precision and recall for class 0.

        Class 1 :
        Very weak performance:

        Precision: 33% → When it predicts class 1, it's correct only 1 out of 3 times.

        Recall: 8% → The model is missing 92% of actual class 1 examples.

        F1-score: Extremely low (0.13), suggesting the model fails to capture class 1 instances.


    -	Practical	implications
        The model does a good job in predicting patioents who are not likely to be readmitted and does not predict customers who are likely to be re admitted after 30 days correctly.

        Thia has a negative impact on the usefulness of the model as the class 1 predictore was of more concern

    -	What	you’d	do	with	more	time	or	more	data	

        Add More Data
        
            More training data helps the model learn general patterns and reduces the risk of memorizing noise.

            Data augmentation is also helpful in image/text domains.