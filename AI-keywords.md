
## Supervised Learning vs Unsupervised Learning
1. Supervised Learning
    - In this type of learning, the data is labeled, and the goal is to predict new labels (such as classification and regression)
    - Logistic and Linear Regression, SVM, Naive Bayes, KNN, Random Forest

2. Unsupervised Learning
    - In this type of learning, the data is unlabeled, and the goal is to identify patterns and hidden structures within the data (such as clustering and dimensionality reduction).
    - K-Means, PCA, t-SNE, Hierarchical Clustering

## Steps in the Machine Learning Process
1. Define the Problem
    - Determine the problem you are trying to solve (e.g., classification, regression).

2. Collect Data
    - Gather relevant data from various sources (e.g., CSV files, databases, APIs).

3. Data Preprocessing
    - Clean the data (e.g., handle missing values, correct errors).
    - Scale/normalize the data if necessary.
    - Encode categorical features.
    - Feature engineering (select/create useful features).

4. Select the Model
    - Choose the appropriate algorithm for your problem (e.g., Logistic Regression, SVM, Random Forest).

5. Split the Data
    - Divide the data into training and testing sets (e.g., 70%-30%, 80%-20%).

6. Train the Model
    - Train the model using the training data.

7. Evaluate the Model
    - Evaluate the model's performance using the test data.
    - Use metrics like accuracy, precision, recall, or MSE.
        - ###### Imagine you are trying to catch thieves.
        - `Accuracy`: Out of all the people you saw (thieves and good people), how many did you guess correctly?
        - `Precision`: Out of all the people you said are thieves, how many were actually thieves?
        - `Recall`: Out of all the real thieves, how many did you catch and not miss?

8. Tune Hyperparameters
    - Fine-tune the hyperparameters to improve model performance (e.g., Grid Search, Random Search).

9. Test and Optimize the Model
    - Test the model with new data and adjust as needed to improve performance.
    - Use techniques like cross-validation to prevent overfitting/underfitting.

10. Deploy the Model
    - Deploy the model into production to make real-time predictions.

11. Model Maintenance and Updates
    - Update and retrain the model regularly with new data to maintain its accuracy.

## 𝐓𝐨𝐩 𝐌𝐚𝐜𝐡𝐢𝐧𝐞 𝐋𝐞𝐚𝐫𝐧𝐢𝐧𝐠 𝐀𝐥𝐠𝐨𝐫𝐢𝐭𝐡𝐦𝐬:

0. K-Means

    - First, we specify the number of clusters (K).
    - Then, we select K points as the initial centers and assign each data point to the nearest center.
    - After that, we calculate the mean of the points in each group and update the cluster center.
    - We repeat these steps until no further changes occur in the cluster centers.
    - Finally, the data is categorized into K similar groups.

0. Linear Regression vs Logistic Regression
    - Regression itself means predicting the changes in one variable based on the changes in another variable.
    - The `sigmoid` function is a mathematical function that takes any input and keeps its output between 0 and 1.

    - Linear Regression
        - It is used for predicting a numerical (continuous) value.
        - For example: predicting house prices, temperature, employee salary.
        - The output is a real number (e.g., 73.5).
    - Logistic Regression
        - It is used for predicting a category (class).
        - For example: Is the email spam or not? Is the person sick or healthy?
        - The output is a probability between 0 and 1.


0. Decision Tree
    - A decision tree is a machine learning model that classifies or predicts data by using a series of yes/no questions or comparisons.

0. Random Forest
    - It creates a set of decision trees (each making a prediction). By taking a vote from all the trees, it makes the final decision.

0. Naive Bayes
    - We calculate the probability of a data point belonging to each class and select the one with the highest probability.

0. KNN
    - It looks at the K nearest neighbors and makes a decision based on their votes regarding similarity.

0. SVM (Support Vector Machine)
    - SVM is a classification algorithm that finds the best line or hyperplane that separates data from different classes and tries to maximize the distance between the data points and the separating boundary.

0. Dimensionality Reduction
    - When the data has many features, these algorithms help keep only the most important ones. This makes the model faster, simpler, and more accurate.

## Kaywords
0. Digital twin
    - A digital twin is a digital replica of a physical object, system, or structure (such as a factory, data center, the Earth, or a shrine), which allows us to observe and analyze it in real time.  


0. Unconditional Image Generation
    - These are models that generate new images without requiring specific input. A model like GAN.

0. Depth Estimation
    - These are models that estimate depth (3D information) from 2D images.  
    - Example: Imagine you have an image of a road—the model estimates the depth of different objects like cars and trees.

0. Zero-Shot Image Classification
    - These are models that can classify images without being directly trained on those specific categories.
    - Example: If a model has been trained on categories like "dog" and "cat," but is able to classify an image of an "elephant" without having seen any training data for "elephant."

0. Zero-Shot Object Detection
    - These are models that can recognize an object in images without having seen specific examples of that object before.
    - Example: The model has been trained to identify "cars" and "bicycles," but is now able to recognize a "bus" without direct training on it.

0. Token Classification
    - These are models that assign each word or token in a sentence to a specific category.
    - Example: In a sentence like "Ali went to school," the model can classify "Ali" as a name and "school" as a location.


0. Table Question Answering
    - These are models that answer questions about data in tables.
    - Example: You have a table of product sales and ask, "Which product had the highest sales?"—the model provides the answer.

0. Fill-Mask
    - These are models that fill in missing words in a sentence.
    - Example: You give the model a sentence like "The weather is [MASK]," and the model completes it as "The weather is sunny."

0. Voice Activity Detection
    - These are models that detect which parts of an audio file contain speech.
    - Example: A model that identifies segments with human speech in a long audio recording.

0. Tabular Classification
    - These are models that classify tabular data based on different categories.
    - Example: A model that classifies customer data into categories like "loyal buyer" and "regular buyer."

0. Tabular Regression
    - These are models that predict continuous values based on tabular data.
    - Example: A model that predicts the price of a house based on features like size and location.

0. Time Series Forecasting
    - These are models that predict future trends based on time series data.
    - Example: A model that forecasts how stock prices will change in the next month.

0. Reinforcement Learning
- These are models that learn how to perform tasks better through rewards and penalties.
- A model that learns to play a video game by trying different moves. When it wins or scores points, it gets a reward, and when it loses, it gets a penalty. Over time, it learns which actions lead to better results and plays the game more skillfully.

0. Model Distillation 
    - is a technique where a small, simple model learns to copy the behavior of a larger, more complex model.
    The goal is to keep the accuracy but make the model faster and lighter.

0. Model Collapse
    - is a problem where a model starts giving very limited or repetitive outputs.
    - a generative model might start producing almost the same image or sentence every time, no matter the input.

0. Mixture of Experts (MoE)
    - is a machine learning approach where multiple specialized models (called "experts") are trained to handle different tasks. A gating model decides which expert to use for a given input.
    - The idea is to combine the strengths of different models, making the system more efficient and powerful by using the right expert for each task.

0. Fine-Tune
 is the process of taking a pre-trained model and making small adjustments to it using a new, often smaller, dataset. The goal is to adapt the model to a specific task or improve its performance on a related task without training it from scratch.
