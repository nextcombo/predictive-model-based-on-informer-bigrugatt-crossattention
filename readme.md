# Predictive Model Based on Informer-BiGRUGATT-CrossAttention

\tPreface
In response to the challenges of long-term dependency in wind power power prediction and multi-scale spatiotemporal feature modeling, this issue proposes an innovative multi-model fusion architecture—the Informer-BiGRUGATT-CrossAttention model. This model integrates the efficient long-sequence processing capabilities of the Informer with the temporal dependency capturing advantages of the bidirectional Gated Recurrent Unit (BiGRU) and Global Attention mechanism. It employs a cross attention mechanism for deep integration of spatiotemporal features. Additionally, it realizes multi-level modeling of complex time series, providing a new technical path for high-precision prediction tasks.
1. Introduction to the innovative model
\t1.1 Model Evaluation:
1.2 Predictive Visualization:
(1) Task 1: Power Load Forecasting
\t  
(2) Task 2: Wind Power Power Forecasting
\t  
\t1.3 Model Feature Analysis—Visualization:
\t  
\t  
We also provide experiments and comparisons based on multiple datasets in multiple prediction tasks, providing detailed documentation, tutorials, and video explanations. This includes how to replace your own dataset, tutorials on parameter adjustments, and replacement of prediction tasks. The code is commented line by line, with detailed introductions to parameters.
● Dataset: Wind power dataset, power data set, wind speed dataset, etc. of a wind farm
● Environment Framework: Python 3.9, PyTorch 2.1 and above can be run.
● Step-by-step prediction model score: 0.98 on test set
● Usage Object: Paper requirements, graduation design requirements.
● Code Guarantee: The code comments are detailed and ready to run.
2. Introduction to Model Innovation Points
2.1 Overall Architecture Design
The Informer-BiGRUGATT-CrossAttention model proposed in this issue aims to fully leverage the advantages of both the Informer and BiGRU-GlobalAttention models in time series prediction. By employing a parallel structure and cross attention mechanisms, it achieves deep feature fusion, thereby enhancing the accuracy and robustness of wind power forecasting. The overall architecture of the model is illustrated as follows:
Input layer: Normalizes the raw wind power multi-feature time series signals before inputting them into the network.
Informer module: Specially designed for long sequence data, utilizes sparse self-attention mechanisms to quickly capture global temporal dependencies.
BiGRU-GlobalAttention module: Through bidirectional recurrent layers, extracts sequential bidirectional contextual information and combines global attention to focus on key time points in the sequence.
Cross attention fusion layer: Exchanges and fuses the feature representations from both modules to capture complementary information between the two models, enhancing the expressive capability of spatiotemporal features.
Output layer: After fusion, the features are mapped through a fully connected layer to predict values, achieving multi-step load forecasting.
This design balances long-term global modeling with fine-grained capturing of sequential local dynamics, making it particularly suitable for time series data with significant multi-scale changes, complexities, and noise, such as wind power power.
Informer branch:
The Informer module is the core component of the model, optimized based on the Transformer structure, with several key improvements:
Sparse self-attention mechanism: reduces the complexity of self-attention computations in traditional Transformers from \(O(\text{L} \times 2)\) to \(O(\text{L} \log{\text{L}})\), enabling the model to handle time series with thousands of steps or more while maintaining performance.
ProbSparse: Only retains the most important Query, significantly filters out unnecessary computational interference, and utilizes information entropy to select key areas.
Multi-layer encoder structure: stack multiple layers of encoder units, adding residual connections and layer normalization between them to stabilize training and enhance the hierarchy of feature representations.
Multi-head attention and feedforward network: Utilizing multi-head mechanisms in conjunction with position encoding to ensure the capture of temporal position information and different subspace features.
Decoder Structure Design: The decoder is designed based on the prediction step length, supporting multi-step load forecasting, and outputs are flexibly coordinated with the input sequence length.
The normalized wind power sequence input is first mapped to high-dimensional vectors through an embedding layer, then passed into the Informer encoder. After multiple layers of processing, it outputs deep representations that capture global dependencies on long sequences. This module effectively captures the periodicity and long-term changes in wind power data, solving the problem of long sequences that traditional time series models struggle with.
\t2.3 BiGRU-GATT branch
Multi-feature sequence data is processed simultaneously through a BiGRU network optimized with GlobalAttention. GlobalAttention is a mechanism designed to enhance the model's focus on different parts of the input sequence. In the BiGRU model, the global attention mechanism helps the model better concentrate on the most relevant parts of the input sequence, thereby enhancing the model's performance and generalization capabilities. At each time step, the global attention mechanism calculates a weight vector indicating the model's focus on various parts of the input sequence. These weights are then applied to the feature representations output by the BiGRU, allowing for weighted consideration of all features across positions, enabling the model to more specifically focus on important temporal features. This improves the model's ability to perceive temporal features in multi-feature sequences.
2.4 Cross Attention Fusion Mechanism:
Introduction of Cross Attention Mechanism for Informer and BiGRU-GATT Outputs
The cross attention mechanism is introduced to establish connections between the outputs of Informer and BiGRU-GATT. By computing query, key, and value, the cross attention mechanism can effectively integrate long-range dependency features and global multi-scale features. This allows consideration of both temporal and spatial relationships, thereby better capturing features in time series data, enhancing feature representation capabilities, and achieving high-precision predictions.

3 Data Sets Introduction: Wind Power Power Dataset
3.1 Importing Data
The wind power dataset consists of 35,040 samples with 15 features, and we visualize the first 6,000 samples for visualization purposes.

3.2 Data Set Production and Preprocessing
Detailed instructions are provided in the document provided!
Prediction Model Based on Informer-BiGRUGATT-CrossAttention
4.1 Definition of the Informer-BiGRUGATT-CrossAttention prediction network model
4.2 Setting parameters and training the model
Training for 50 epochs, MSE is 0.00156, indicating that the Informer-BiGRUGATT-CrossAttention prediction is significantly effective. The model can fully utilize the long-term dependency modeling capability of Informer and the short-term dependency capture capability of BiGRUGATT, with fast convergence speed, superior performance, high prediction accuracy, and further improvement in model prediction performance by appropriately adjusting model parameters.
5 Results Visualization and Model Evaluation
5.1 Prediction result visualization
5.2 Model evaluation
Click to download: Complete original data, Python code
Previously interesting content:
Time Series Forecasting: Analysis and comparison of LSTM, ARIMA, Holt-Winters, SARIMA models
Wind Speed Forecast (Part I): Introduction and preprocessing of the dataset
Wind Speed Prediction (II) EMD-LSTM Model Based on Pytorch
Wind Speed Prediction (III) EMD-LSTM-Attention Model
Wind Speed Prediction (IV) EMD-Transformer Model Based on Pytorch
Wind Speed Prediction (5) EMD-CNN-LSTM Model Based on Pytorch
Wind Speed Prediction (VI) - EMD-CNN-GRU Parallel Model Based on Pytorch
CEEMDAN + Combination Forecasting Model (BiLSTM-Attention + ARIMA)
CEEMDAN + Combination Forecasting Model (CNN-LSTM + ARIMA)
CEEMDAN + Combination Forecasting Model (Transformer - BiLSTM + ARIMA)
CEEMDAN + Combination Forecasting Model (CNN-Transformer + ARIMA)
Multi-feature Variable Sequence Prediction (I) - CNN-LSTM Wind Speed Prediction Model
Multi-feature Variable Sequence Prediction (II) - CNN-LSTM-Attention Wind Speed Prediction Model
Multi-feature Variable Sequence Prediction (III) - CNN-Transformer Wind Speed Prediction Model
Multi-feature Variable Sequence Prediction (IV) - Transformer-BiLSTM Wind Speed Prediction Model
Multi-feature Variable Sequence Prediction (V) CEEMDAN+CNN-LSTM Wind Speed Prediction Model
Multi-feature Variable Sequence Prediction (VI) CEEMDAN+CNN-Transformer Wind Speed Prediction Model
Predictive Model Based on the Optimized Algorithm of Sparrows SSA-CEEMDAN-BiLSTM-Attention
CEEMDAN-Transformer-BiGRU Prediction Model Based on Optimized Algorithm SSA for Sparrows
Super Predictive Model: Secondary Decomposition-Combination Prediction
Multi-feature Variable Sequence Prediction (7) CEEMDAN+Transformer-BiLSTM Prediction Model
Multi-feature Variable Sequence Prediction (8) CEEMDAN-SSA-BiLSTM Prediction Model Based on Plumage Optimization Algorithm
Multi-feature Variable Sequence Prediction (11) TCN-GRU Prediction Model Based on Pytorch
VMD + CEEMDAN Secondary Decomposition, CNN-LSTM Prediction Model
VMD + CEEMDAN Secondary Decomposition, CNN-Transformer Prediction Model
VMD + CEEMDAN Secondary Decomposition, Transformer-BiGRU Prediction Model
Prediction Model Based on Plumage Optimization Algorithm SSA - Complete Code Kit
Superior Combination Prediction Model!
High Innovation | CEEMDAN + SSA-TCN-BiLSTM-Attention Prediction Model
Superior Combination Prediction Model!
Lowest Price Online | Continuous Updates for the Complete Kit!
Based on TCN-SENet + BiGRU-GlobalAttention Parallel Prediction Model
Secondary Decomposition - Innovative Model Prediction Complete Kit
BiTCN-BiGRU-CrossAttention Fusion of Spatiotemporal Features High Innovation Prediction Model
Combination Prediction Update | Superior Combination Prediction Model!
Spatiotemporal Feature Fusion BiTCN-Transformer Parallel Prediction Model
Based on Multi-level Attention Mechanism Parallel Prediction Model
CEEMDAN-CNN-GRU-GlobalAttention + XGBoost Combination Prediction
Multi-step Prediction Series | LSTM, CNN, Transformer, TCN, Serial, Parallel Model Collection
End

## Images

<!-- PAYMENT_BLOCK -->

## Get this dataset

- Payment link (Stripe): [Buy now](https://buy.stripe.com/3cs8yP7sY87d0vu9AB)
- Payment QR code: ![Payment QR code](pay.png)

<!-- /PAYMENT_BLOCK -->
