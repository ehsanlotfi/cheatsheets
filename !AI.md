# Artificial Intelligence & Machine Learning

## Types of Machine Learning

### 1. Supervised Learning
- Predicts labels from labeled data (Classification, Regression)
    - Classification Algorithms
        - Logistic Regression
        - SVM
        - Naive Bayes
        - KNN
        - Decision Tree
        - Random Forest
    - Regression Algorithms
        - Linear Regression
        - Decision Tree
        - Random Forest

### 2. Unsupervised Learning
- Finds hidden patterns in unlabeled data (Clustering, Dimensionality Reduction)
    - Clustering Algorithms
        - K-Means
        - Hierarchical Clustering
    - Dimensionality Reduction Algorithms
        - PCA
        - t-SNE

### 3. Semi-Supervised Learning
- Combines a small amount of labeled data with a large amount of unlabeled data to enhance accuracy
    - Techniques
        - Self Training
        - Low Density Separation
        - Graph-based Algorithms

### 4. Reinforcement Learning (RL)
- Learns through `rewards` and `penalties` to perform tasks better
    - Reinforcement Learning from Human Feedback (RLHF)
    - Algorithms
        - Q-Learning
        - Deep Q-Networks (DQN)
        - RL from Human Feedback (RLHF)

## Artificial Neural Networks (ANNs)

### Components
- [Perceptrons, Neuron, Node](https://www.youtube.com/watch?v=zd-Ku1GbtKU)
- Bias

### Architectures
- MLP
- Feedforward
- Radial Basis Functions
- Hopfield

### Learning Techniques
- Forward/Backward Propagation
- Gradient Descent

## Deep Learning

### Convolutional Neural Networks (CNN)
- [Demo](https://poloclub.github.io/cnn-explainer/?utm_source=chatgpt.com)
- Layers
    - `Input`: The image or input data that enters the network
    - `Convolution (filters, kernels)`: Slides over the input to extract important features (like `edges`, `textures`, `shapes`)
    - `Padding`: Adds extra pixels (usually zeros) around the image to preserve its size after convolution
    - `Activation Functions`: Add non-linearity to the model, helping it learn complex patterns
        - `ReLU (Rectified Linear Unit)`: Keeps only positive values; turns negative values into zero
        - `Softmax`: Converts the output into probabilities (used in the final layer for classification)
    - `Pooling`: Reduces the size of the data while keeping important features
        - `Max Pooling`: Selects the maximum value from each region (most common)
        - `Average Pooling`: Calculates the average value from each region
    - `Flatten`: Converts the 2D feature maps into a 1D vector before feeding it to fully-connected layers
    - `Output`: Prediction is made

- Techniques
    - Data Augmentation
    - Super-Pixel
    - Inception Module
    - Feature Extractor

### Recurrent Neural Networks (RNN)
- Challenges
    - Vanishing Gradient
    - Exploding Gradient

### Advanced Architectures
- AlexNet
- VGGNet
- GoogleNet
- ResNet
- YOLO
- SqueezeNet
- SegNet
- GANs: (e.g., U-Net, DeepLab)

## Web3 & Blockchain

### Smart Contract Platforms
- Blockchains like `Ethereum` that allow developers to create self-executing contracts without intermediaries (e.g., for `finance` or `games`)
- solority
- remix IDE
- hardHat
- NFT
- DAPP

### Pine Script
- Is a lightweight programming language created by `TradingView` for writing custom indicators, strategies, and alerts on financial charts
- Easy to learn and allows traders to automate technical analysis directly within the TradingView platform

### Decentralized Finance (DeFi)
- A financial system built on blockchain where users lend, borrow, trade, or earn without relying on banks or central authorities

## Keywords and Concepts

### Generative AI / LLMs
- Creates new content (text, images, music) using models like Large Language Models (`LLMs`)
- Learn patterns from data to generate human-like output

### AI Ethics and Governance
- Focuses on responsible AI use, including fairness, transparency, bias reduction, and regulation to ensure AI benefits society safely

### Digital Twin
- A digital replica of a physical object, system, or structure (such as a factory, data center, the Earth, or a shrine)
- Allows us to observe and analyze it in real time

### Unconditional Image Generation
- Models that generate new images without requiring specific input
- Example: GAN (Generative Adversarial Network)

### Depth Estimation
- Models that estimate depth (3D information) from 2D images
- Example: Estimating depth of objects like cars and trees in a road image

### Zero-Shot Image Classification
- Models that can classify images without being directly trained on those specific categories
- Example: Classifying an "elephant" without training data for elephants

### Zero-Shot Object Detection
- Models that can recognize objects without having seen specific examples before
- Example: Recognizing a "bus" without direct training on buses

### Token Classification
- Models that assign each word or token in a sentence to a specific category
- Example: Classifying "Ali" as a name and "school" as a location in "Ali went to school"

### Table Question Answering
- Models that answer questions about data in tables
- Example: Answering "Which product had the highest sales?" from a sales table

### Fill-Mask
- Models that fill in missing words in a sentence
- Example: Completing "The weather is [MASK]" to "The weather is sunny"

### Voice Activity Detection
- Models that detect which parts of an audio file contain speech
- Example: Identifying segments with human speech in a long audio recording

### Tabular Classification
- Models that classify tabular data based on different categories
- Example: Classifying customers into "loyal buyer" and "regular buyer" categories

### Tabular Regression
- Models that predict continuous values based on tabular data
- Example: Predicting house prices based on features like size and location

### Time Series Forecasting
- Models that predict future trends based on time series data
- Example: Forecasting stock price changes for the next month

### Model Distillation
- Technique where a big model (teacher) teaches a smaller model (student)
- The big model is smart but slow; the small model learns to be fast while maintaining quality
- Uses soft outputs (like 0.7 cat, 0.2 dog, 0.1 rabbit) instead of just hard labels

### Model Collapse
- Problem where a model starts giving very limited or repetitive outputs
- Example: A generative model producing almost the same image or sentence every time

### Mixture of Experts (MoE)
- Machine learning approach using multiple specialized models (experts)
- A gating model decides which expert to use for each input
- Combines strengths of different models for better efficiency and power

### Bias
- Generally: An `unfair preference` for or against something
- In AI: Refers to unfairness toward certain outcomes, people, or ideas
- Example: Gender bias in AI trained mostly on male data

## Steps in the Machine Learning Process

### 1. Define the Problem
- Determine the problem you are trying to solve (e.g., classification, regression)

### 2. Collect Data
- Gather relevant data from various sources (e.g., CSV files, databases, APIs)

### 3. Data Preprocessing
- Clean the data (e.g., handle missing values, correct errors)
- Scale/normalize the data if necessary
- Encode categorical features
- Feature engineering (select/create useful features)

### 4. Select the Model
- Choose the appropriate algorithm for your problem (e.g., Logistic Regression, SVM, Random Forest)

### 5. Split the Data
- Divide the data into training and testing sets (e.g., 70%-30%, 80%-20%)
- `Training Data`: Data used for model learning
- `Test Data`: Data used to evaluate model performance (like an exam)

### 6. Train the Model
- Train the model using the training data
```python
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.datasets import make_regression
from sklearn.metrics import mean_squared_error

# Generate some synthetic data (features and labels)
X, y = make_regression(n_samples=100, n_features=1, noise=10, random_state=42)

# Step 1: Split the Data (80% training, 20% testing)
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Step 2: Train the Model
model = LinearRegression()
model.fit(X_train, y_train)

# Step 3: Test the Model
y_pred = model.predict(X_test)

# Step 4: Evaluate the Model
mse = mean_squared_error(y_test, y_pred)
print(f"Mean Squared Error: {mse:.2f}")
```

### 7. Evaluate the Model
- Evaluate the model's performance using the test data
- Use metrics like accuracy, precision, recall, or MSE (Mean Squared Error)
    - `Accuracy`: Out of all predictions, how many were correct?
    - `Precision`: Out of positive predictions, how many were actually positive?
    - `Recall`: Out of actual positives, how many were correctly identified?

### 8. Tune Hyperparameters
- `Hyperparameters`: Settings chosen before training (e.g., Learning rate, Number of layers)
- `Fine-tune`: Finding the best combination of hyperparameters for optimal performance

### 9. Test and Optimize the Model
- Test with new data and adjust as needed
- Use techniques like cross-validation to prevent overfitting/underfitting
    - `Overfitting`: Model learned too much, including noise
    - `Underfitting`: Model didn't learn enough, too simple

### 10. Deploy the Model
- Deploy the model into production for real-time predictions

### 11. Model Maintenance and Updates
- Regularly update and retrain the model with new data to maintain accuracy

## 𝐓𝐨𝐩 𝐌𝐚𝐜𝐡𝐢𝐧𝐞 𝐋𝐞𝐚𝐫𝐧𝐢𝐧𝐠 𝐀𝐥𝐠𝐨𝐫𝐢𝐭𝐡𝐦𝐬

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
    - These are models that generate new images without requiring specific input. a model like GAN.

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

0. Model Distillation 
    - Is a technique where a big model (teacher) teaches a smaller model (student).
    - The big model is smart but slow. The small model learns from it to be fast and still good.
    - It uses the soft outputs (like 0.7 cat, 0.2 dog, 0.1 rabbit) instead of just hard labels.

0. Model Collapse
    - is a problem where a model starts giving very limited or repetitive outputs.
    - a generative model might start producing almost the same image or sentence every time.

0. Mixture of Experts (MoE)
    - is a machine learning approach where multiple specialized models (called "experts") are trained to handle different tasks. A gating model decides which expert to use for a given input.
    - The idea is to combine the strengths of different models, making the system more efficient and powerful by using the right expert for each task.

0. GNN (Graph Neural Network)
    - A neural network designed for graph-structured data (e.g., social networks), learning from relationships between nodes and edges.

0. GCN (Graph Convolutional Network)
    - A special type of GNN that applies convolution to graphs, enabling deep learning on non-grid structures (e.g., molecules, networks).

## Recommendation Systems (RS)
0. Recommendation Systems
    -  A system that suggests items (like movies, products, or songs) to users based on their preferences and behavior.

## Tools
    - ML and Data Analysis
        - Numpy
        - Pandas
        - Matplotlib
        - Scikit-learn
        - TensorFlow
        - Keras
        - PyTorch

    - Data Visualization
        - Seaborn
        - Plotly

    - Deep Learning Frameworks
        - Jupyter
        - PySpark
        - Polar

    - Image Processing
        - YOLO
        - Detectron2
        - MediaPipe

    - Vector Databases
        - Pinecone
        - Weaviate

    - Text Processing
        - NLP tools and models

    - Data Analyst
        - Power BI
        - Tableau