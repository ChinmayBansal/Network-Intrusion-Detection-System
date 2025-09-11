# AI-Powered Network Intrusion Detection System (AI-NIDS)

🛡️ **Machine Learning vs Signature-Based Network Intrusion Detection**

## 🎯 Project Overview

This project builds and evaluates machine learning models for network intrusion detection, comparing their performance against traditional signature-based detection systems. The goal is to demonstrate whether ML approaches can outperform conventional rule-based IDS like Snort and Suricata in detecting both known and unknown network attacks.

## 📊 Datasets

### Primary Dataset: UNSW-NB15
- **Size**: ~2.5M network flow records
- **Features**: 49 features including protocols, packet sizes, flags, flow statistics
- **Labels**: Normal traffic + 9 attack categories
  - Fuzzers, Analysis, Backdoors, DoS, Exploits
  - Generic, Reconnaissance, Shellcode, Worms

## 🧠 Machine Learning Approaches

### Baseline Models
- **Logistic Regression**: Simple linear classifier
- **Random Forest**: Ensemble method for feature importance analysis

### Advanced Models
- **LightGBM/XGBoost**: Gradient boosting for high performance
- **Autoencoders**: Unsupervised anomaly detection

### Classification Strategies
1. **Binary Classification**: Normal vs Attack (higher accuracy)
2. **Multi-class Classification**: Specific attack categories (more realistic)

## 📑 Case Study: ML vs Signature-Based Detection

### Problem Statement
Traditional signature-based IDS systems like Snort and Suricata rely on predefined rules and patterns, making them ineffective against:
- Zero-day attacks
- Polymorphic malware  
- Advanced persistent threats (APTs)
- Encrypted malicious traffic

### Hypothesis
Machine learning models can achieve better detection rates by:
- Learning complex patterns from network flow statistics
- Adapting to new attack variants
- Reducing false positive rates
- Detecting anomalous behavior without explicit rules

### Evaluation Methodology
1. **Performance Metrics**: Accuracy, Precision, Recall, F1-Score, ROC-AUC
2. **Model Comparison**: ML models vs simulated signature-based detection
3. **Analysis**: Feature importance, confusion matrices, error analysis
4. **Real-world Applicability**: Deployment considerations and limitations

## 📈 Results

### Baseline Model: Logistic Regression
**Binary Classification Performance (Normal vs Attack)**

| Metric | Score | Assessment |
|--------|-------|------------|
| Accuracy | 83.65% | Strong generalization |
| Precision | 80.29% | Good false alarm control |
| Recall | 93.18% | Excellent attack detection |
| F1-Score | 86.26% | Well-balanced performance |
| ROC-AUC | 95.64% | Outstanding discriminative ability |

**Key Findings:**
- ✅ **93.2% attack detection rate** - Catches vast majority of network threats
- ✅ **95.6% AUC score** - Near-perfect separation between normal and malicious traffic  
- ⚠️ **28% false alarm rate** - Acceptable for security applications (better safe than sorry)
- ✅ **Strong baseline** - Establishes excellent foundation for advanced models

The logistic regression baseline demonstrates that machine learning can effectively detect network intrusions with high accuracy.

### Multi-Class Classification Performance (Attack Type Identification)

**Enhanced Logistic Regression with Feature Engineering**

| Metric | Achieved | What does it mean |
|--------|----------|-------------------|
| **Test Accuracy** | 65.45% | Correctly classifies 65% of network flows into specific attack types |
| **Weighted Precision** | 83% | When model predicts a specific attack type, it's correct 83% of the time |
| **Weighted Recall** | 65% | Model successfully identifies 65% of all actual attacks by their correct type |
| **Weighted F1-Score** | 71% | Balanced performance measure across all 10 attack categories |
| **Feature Engineering Impact** | +2.5% | Domain-specific features improved accuracy by 2.5 percentage points |
| **Classes Handled** | 10 categories | Successfully distinguishes Normal + 9 attack types despite severe imbalance |

**Key Findings:**
- ✅ **Attack Type Specificity** - Model successfully identifies specific attack categories for targeted response
- ✅ **Feature Engineering Success** - 13 domain-specific features significantly improved reconnaissance detection (+56%)
- ⚠️ **Class Imbalance Challenge** - 430:1 ratio between most/least common classes creates detection variability
- ✅ **Operational Value** - Provides actionable intelligence for security teams with attack-specific classifications

**Attack Category Performance:**
- **Best Detection**: Generic (96% recall), Worms (82% recall), Reconnaissance (74% recall)
- **Challenging Classes**: Backdoor (8% recall), Analysis (63% recall but high false positives)
- **High Precision**: Normal (98%), Generic (99%), Exploits (78%)

The multi-class model trades some overall accuracy for attack type granularity, providing security teams with specific threat intelligence for incident response and threat hunting.
