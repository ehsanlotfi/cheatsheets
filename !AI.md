# Artificial Intelligence

### Foundations
- Artificial Intelligence (AI)
- Machine Learning (ML)
- Deep Learning (DL)
- Artificial Neural Networks (ANN)

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
- `RNN ( Recurrent Neural Networks )` A neural network designed for sequential data that **remembers previous information** to help process current inputs.

### Transformers
- Encoder
- Decoder
- Attention
- Self-Attention

### Generative AI
- `LLMs ( Large Language Models )`
- `Generative Models` 
  - GAN (Generative Adversarial Network)
  - VAE
  - Diffusion Models

### Computer Vision
- `Image Classification`
- `Object Detection` YOLO, Faster R-CNN
- `Image Segmentation` U-Net, SegNet, DeepLab
- `Depth Estimation`
- `Image Generation`

### NLP ( Natural Language Processing )
- `Text Classification`
- `Token Classification`
- `Question Answering`
- `Text Generation`
- `Summarization`
- `Translation`

### Speech & Audio
- `Speech Recognition`
- `Text To Speech (TTS)`
- `Voice Activity Detection`

### Modern LLM Concepts
- `RAG`
- `Fine-Tuning`
- `LoRA`
- `RLHF`
- `Distillation`
- `Quantization`
- `Mixture of Experts (MoE)`


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

### Web3 & Blockchain
- `Smart Contract Platforms` Blockchains like Ethereum that allow developers to create self-executing contracts without intermediaries (e.g., for finance or games )solority, remix IDE, hardHat, NFT, DAPP

- `Pine Script` Is a lightweight programming language created by TradingView for writing custom indicators, strategies.

- `Decentralized Finance (DeFi)` A financial system built on blockchain where users lend, borrow, trade, or earn without relying on banks or central authorities

### Keywords
- `Digital Twin` A digital replica of a physical object, system, or structure (such as a factory, data center, the Earth, or a shrine) Allows us to observe and analyze it in real time.
  
- `Fill-Mask` models that fill in missing words in a sentence e.g. "The weather is [MASK]" to "The weather is sunny".

- `KD ( Knowledge Distillation )` Technique where a big model (teacher) teaches a smaller model (student), The big model is smart but slow; the small model learns to be fast while maintaining quality, Uses soft outputs (like 0.7 cat, 0.2 dog, 0.1 rabbit) instead of just hard labels.

- `Model Collapse` Problem where a model starts giving very limited or repetitive outputs. e.g. A generative model producing almost the same image or sentence every time.

- `MoE ( Mixture of Experts )` uses multiple specialized models and selects the most suitable one for each input.
- `Recommendation Systems (RS)` A system that suggests items users may like based on their preferences.
- `Overfitting` Model learned too much, including noise.
- `Underfitting` Model didn't learn enough, too simple.


### Reasoning Strategies in LLMs
- `CoT ( Chain of Thought )` step-by-step reasoning before giving an answer.
- `ToT ( Tree of Thoughts )` exploring multiple reasoning paths and choosing the best one.
- `Self-Consistency` generating multiple answers and selecting the most consistent one.
- `CoT + Voting / Reflection` comparing multiple reasoning paths and correcting mistakes.
- `Program-Aided CoT` using code execution to help solve and verify problems.
- `ReAct (Reason + Act)` combining reasoning with external actions like search or tools.
- `Tool-Use / Toolformer` use external tools during reasoning.
- `Tree Search / MCTS` exploring many possible solutions and selecting the most promising one.