# Artificial Intelligence

### Foundations
- Artificial Intelligence (AI)
- Machine Learning (ML)
- Deep Learning (DL)
- Artificial Neural Networks (ANN)

### Common AI Tasks
- `Binary Classification`
- `Multi-Class Classification`
- `Multi-Label Classification`
- `Regression` Predicts a numerical value (e.g., House price).
- `Clustering`
- `Anomaly Detection` Detects rare or abnormal patterns in data (e.g., Fraud detection).
- `Recommendation`
- `Ranking` Orders items by relevance or importance.
- `Time Series Forecasting`
- `Object Detection`
- `Image Segmentation`
- `Text Generation`
- `Question Answering (QA)`
- `Machine Translation`
- `Speech Recognition (ASR)`
- `Image Generation`

### Linear Algebra Fundamentals
- `Scalar` A single value (0D Tensor), e.g., `5`.
- `Vector` A one-dimensional array of values (1D Tensor), e.g., `[2, 4, 6]`.
- `Matrix` A two-dimensional array of values (2D Tensor), e.g., `[[1,2],[3,4]]`.
- `Tensor` A multidimensional array (N-D).
- `Dot Product` Vector * Vector = Scalar
- `Matrix Multiplication` Matrix * Matrix = Matrix
- `Transpose` Swaps the dimensions of a matrix or tensor.

### Learning Paradigms
-  `Supervised Learning` Predicts labels from labeled data (Classification, Regression)
    - Classification Algorithms ( Logistic Regression, SVM, Naive Bayes, KNN, Decision Tree, Random Forest )
    - Regression Algorithms ( Linear Regression, Decision Tree, Random Forest )
-  `Unsupervised Learning` Finds hidden patterns in unlabeled data (Clustering, Dimensionality Reduction)
    - Clustering Algorithms ( K-Means, Hierarchical Clustering )
    - Dimensionality Reduction Algorithms ( PCA, t-SNE )

-  `Semi-Supervised Learning` Combines a small amount of labeled data with a large amount of unlabeled data to enhance accuracy

-  `Self-Supervised Learning`  the model creates `its own training labels` from the data itself, without requiring manual labeling.

-  `Reinforcement Learning (RL)` Learns through `rewards` and `penalties` to perform tasks better 
    - Reinforcement Learning from Human Feedback (RLHF)

### Neural Network Fundamentals
- `Perceptrons, Neuron, Node` A unit in a neural network that takes inputs and generates an output
- `Bias` A value that helps the neuron make better decisions
- `Weights`  Values that determine how important each input is
- `Activation Functions` Help the network learn complex patterns.
    - `ReLU (Rectified Linear Unit)` Keeps positive values and turns negative values into zero.
    - `GELU (Gaussian Error Linear Unit)` A smoother version of ReLU that used in Transformer models
    - `Sigmoid`  Converts values into a range between 0 and 1.
    - `Tanh (Hyperbolic Tangent)` Converts values into a range between -1 and 1.
    - `Softmax` Converts outputs into probabilities 0% to 100% used for classification.
  
- `Loss Functions`  Functions that measure how far the model's predictions are from the correct answers.
- `Forward Propagation` Passes data through the network to generate an output.
- `Backpropagation` Updates the network using prediction errors to improve learning.

### Deep Learning Architectures
- `MLP ( Multilayer Perceptron )` A neural network where data moves in one direction only, from input to output through multiple layers, with no memory or loops
- `CNN ( Convolutional Neural Networks )` designed for images that uses filters to detect patterns like edges, shapes, and textures.
    - `Input layers`: The image or input data that enters the network.
    - `Convolution (filters, kernels) layers`: Slides over the input to extract important features (like edges, textures, shapes)
    - `Padding layers`: Adds extra pixels (usually zeros) around the image to preserve its size after convolution
    - `Activation Functions layers`
    - `Pooling layers`: Reduces the size of the data while keeping important features( Max Pooling, Average Pooling )
    - `Flatten`: Converts the 2D feature maps into a 1D vector before feeding it to fully-connected layers
    - `Output`: Prediction is made
- `RNN ( Recurrent Neural Networks )` A neural network designed for sequential data that **remembers previous information** to help process current inputs. Two improved architectures of this method are given below.
    - `LSTM` (Long Short-Term Memory) 
    -  `GRU` (Gated Recurrent Unit)`

- `Transformers` The main idea of this architecture is that instead of reading words one by one in order, it looks at all elements at the same time and uses an `Self-Attention` mechanism to figure out how each part is related to the other parts.

### Generative AI
- `LLMs ( Large Language Models )`
- `Generative Models` 
  - GAN (Generative Adversarial Network)
  - VAE
  - Diffusion Models

### Modern LLM Concepts
- `Prompt Engineering`
    - zero-shot
    - one-shot
    - few-shot
- `Embeddings` vector representation of text
- `RAG (Retrieval-Augmented Generation)`
- `Fine-Tuning`
  - `SFT (Supervised Fine-Tuning)` Training a model on labeled input–output examples so it learns to produce correct answers.
- `LoRA`
- `RLHF`
  - `DPO (Direct Preference Optimization)` Training a model using preference data so it learns to choose better responses over worse ones.
- `Vector Database (Vector DB)`
- `Similarity Methods`
  - Cosine
  - Dot Product
  - Euclidean distance

### Reasoning Strategies in LLMs
- `CoT ( Chain of Thought )` step-by-step reasoning before giving an answer.
- `ToT ( Tree of Thoughts )` exploring multiple reasoning paths and choosing the best one.
- `Self-Consistency` generating multiple answers and selecting the most consistent one.
- `CoT + Voting / Reflection` comparing multiple reasoning paths and correcting mistakes.
- `Program-Aided CoT` using code execution to help solve and verify problems.
- `ReAct (Reason + Act)` combining reasoning with external actions like search or tools.
- `Tool-Use / Toolformer` use external tools during reasoning.
- `Tree Search / MCTS` exploring many possible solutions and selecting the most promising one.

### Model Compression Techniques
- `Quantization` Reduce weight (e.g., FP32 → INT8/INT4).
- `KD (Knowledge Distillation)` Technique where a large model (teacher) transfers its knowledge to a smaller model (student). The goal is to keep most of the teacher's performance while reducing model size and inference cost. The student learns from the teacher's soft predictions rather than only the correct labels.
  - Type
    - `response-based` Student learns from the teacher's output probabilities.
    - `feature-based` Student learns from intermediate features or hidden layers.
    - `relation-based` Student learns relationships between samples, features, or layers.
  - Method
    - `offline` A pre-trained teacher trains a separate student model.
    - `online` Teacher and student are trained together at the same time.
    - `self-distillation` A model learns from its own deeper layers or earlier versions.
- `Pruning` Remove less important weights or neurons from the model.
- `Low-Rank Factorization` Replace large matrix with smaller matrix.

### Evaluation
- `Accuracy`
- `Precision`
- `Recall`
- `F1 Score`
- `Confusion Matrix`

### Library & Frameworks
- `Scikit-learn`
- `TensorFlow`
- `PyTorch`
- `NumPy`
- `Pandas`
- `Matplotlib`
- `Seaborn`
- `Plotly`


### Keywords
- `Digital Twin` A digital replica of a physical object, system, or structure (such as a factory, data center, the Earth, or a shrine) Allows us to observe and analyze it in real time.
  
- `Fill-Mask` models that fill in missing words in a sentence e.g. "The weather is [MASK]" to "The weather is sunny".

- `Model Collapse` Problem where a model starts giving very limited or repetitive outputs. e.g. A generative model producing almost the same image or sentence every time.

- `MoE ( Mixture of Experts )` uses multiple specialized models and selects the most suitable one for each input.
- `Recommendation Systems (RS)` A system that suggests items users may like based on their preferences.
- `Overfitting` Model learned too much, including noise.
- `Underfitting` Model didn't learn enough, too simple.
- `Hard Target vs Soft Target (Dark Knowledge)` Hard targets contain only the correct label, while soft targets include confidence scores and class relationships (e.g., Hard: Cat=1, Dog=0 | Soft: Cat=0.7, Dog=0.2, Rabbit=0.1).
- `Logit` The raw output of a neural network before applying activation like softmax or sigmoid (e.g., [2.3, -1.1, 0.7] before converting to probabilities).
- `Dropout` A method where random neurons are turned off during training to prevent overfitting.

