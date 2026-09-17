---
cssclasses:
  - cornell-left
  - cornell-border
tags:
  - model-evaluation
  - model-selection
  - bias-variance-tradeoff
  - evaluation-metrics
  - loss-functions
  - regression-metrics
  - classification-metrics
  - confusion-matrix
  - roc-auc
  - triplet-loss
priority: P1
order: 1
topic-group: Model Evaluation
gist: How to calculate loss/cost for regression and classification, and how to select a model using bias-variance and error analysis
aliases:
  - Model Evaluation
  - Model Selection
  - Loss Functions
---
> [!summary] Summary
> - Model evaluation and selection has two halves: **calculating loss/cost** correctly for the task (regression vs. classification, and which of the many error families fits) and **choosing between models** using bias-variance diagnostics, an error-analysis baseline, and computation cost.
> - Regression is scored with scale-dependent, percentage, relative, and scale-free error families (ME, MSE, MAE, MAPE, sMAPE, MRAE, GMRAE, RelMAE, RSE, MASE, RMSSE, PB, RMSLE) and losses (Huber, log loss, RMSE, R², adjusted R², BCE); classification adds zero-one/exponential/KL/BCE/hinge/sparse-CE/label-smoothing/multi-label losses, confusion-matrix metrics, F1, and AUC-ROC, plus embedding losses (triplet, contrastive) and task-specific losses (Wasserstein, Dice).
> - Picking the "best" model is not just lowest loss: it requires diagnosing bias vs. variance against a human-level/Bayes-error baseline and weighing computation efficiency.

## 📌 Original EdrawMind Mindmap & Note

> [!quote] Mindmap Source Content
> ```text
> MODEL EVALUATION AND SELECTION
> 	Evaluation metrics (loss/ lost)
> 		Probability calibration
> 			Calibration curves
> 			Calibrating a classifier
> 	Calculating loss/cost
> 		Regression metric
> 			Metric for evaluation
> 				Scale-dependent error
> 					Mean error (ME)
> 						How to calculate
> 						Example
> 						Pros and cons
> 					Mean squared error (MSE)
> 						How to calculate
> 							Square loss/ square error
> 								And formula for squared error
> 						Example
> 							We use this function to calculate the difference and 1/2 is to cancel when we derivate this function error
> 						Pros and cons
> 					Mean absolute error (MAE)
> 						How to calculate
> 						Example
> 						Pros and cons
> 				Percentage error
> 					Mean absolute percentage (MAPE)
> 						How to calculate
> 						Example
> 						Pros and cons
> 					Symmetric mean absolute percentage error (sMAPE)
> 						How to calculate
> 						Example
> 						Pros and cons
> 				Relative errors
> 					Mean relative absolute error (MRAE)
> 						How to calculate
> 						Example
> 						Pros and cons
> 					Geometric mean relative absolute error (GMRMAE)
> 						How to calculate
> 						Example
> 						Pros and cons
> 				Relative measures
> 					Relative mean absolute error (RelMAE)
> 						How to calculate
> 						Example
> 						Pros and cons
> 					Relative squared error (RSE)
> 						How to calculate
> 						Example
> 						Pros and cons
> 				Scale error
> 					Mean absolute scaled error (MASE)
> 						How to calculate
> 							Normalize for deniminator
> 						Example
> 						Pros and cons
> 					Root mean squared scaled error (RMSSE)
> 						How to calculate
> 				Other
> 					Percentage better (PB)
> 						How to calculate
> 						Example
> 					Root mean squared logarithmic error (RMSLE)
> 						How to calculate
> 						Example
> 			Loss
> 				Huber loss
> 					Combining MAE and MSE
> 				Log loss
> 					We will take -log(probability function)
> *Note: we will have negative cause log between 0 and 1 has negative result => -log we will find minimize (if f(x max) we will receive x max in log f(x) because log is cresent function [hàm lưỡi liềm])
> *One of advantages using log is that with very tiny number (0.000000000000001) in log this number will change into very large negative number 
> 					For example: we toss a coin 10 times => we wanna find 7 heads and 3 tails. And we solve it with normal
> 						We release it is too difficult to solve (normal solution, we must use product rule and chain rule, while log we make it use sum rule being easier) and another way to solve it easier is that log
> 				Root mean squared error (RMSE)
> 				R-squared
> 				Adjusted R-squared
> 				Binary Cross Entropy
> 					This is
> 		Classification metrics
> 			Loss
> 				Basic classfication loss
> 					Zero-one
> 						How to calculate
> 						Example
> 					Exponential loss function
> 						How to calculate
> 				Kullback-Leibler Divergence (KL Divergence)
> 					This method for calculating distance between two distributions (P and Q)
> 					In this fomular, log was used to scale value and reduce effect of large number
> 					And statistic of x is to make weight instead of using 1/n (mean)
> 					Summary
> 				Binary Cross Entropy (BCE)
> 					This is
> 					This method with two ways
> 						The mean of entropy
> => when data is too diversity (high entropy) -> difficult to decide (it is difficilt to take stable one type )
> => when data is less diversity (low entropy) -> easy to decide (because we use hand to take samples more easy with one type classification because it is dominant)
> 						We can use with KL divergence to prove this
> 							Here is way to prove KL divergence and entropy
> 				Hingle loss
> 					How to calculate
> 					This loss was used in SVM
> 						This function is more linear and less focus on outlier compare to exponential loss
> 				Sparse Categorical Cross-Entropy
> 					This method does not like one-hot encoding + CE
> It will direct to comparison between softmax and classification
> 				Label smoothing
> 					This method is to reduce bias of module in classification
> We can image that banana is yellow but another place it can have other color
> => we change distribution
> 					How to works
> 						alpha is hyperparameter
> 						C is the number of class
> 				Multi-label
> 					We cannot use softmax because it just makes one class being more higher
> => Reduce other classes
> 					=> WE NEED TO USE SIGMOID
> 						With CE:
> We can see inner summation to caluclate class in a sample
> The outer summation to go throught each sample
> 						With pairwise ranking loss:
> It will create a loss to classification between active label and weak label
> 				Summary
> 			Focal Loss
> 			Threshold (often using with sigmoid)
> 				This value makes our model understand how to classify model's output into positive or negative
> 				I.e. for using threshold with changing evaluation metrics (sensitivity and specificity)
> 			Metric
> 				Confusion matrix
> 					Define
> 						It will use to make our result more sotisphicated
> 						Here is confusion matrix and its value is to example for calculate precision and recall
> (Có thể hiểu false, true là để hiểu là model dự đoán đúng hay sai, positive và negative là để hiểu là model dự đoán ra giá trị gì) 
> 						I.e. false positive nghĩa là model dự đoán sai cho ra prediction là positive (mà thực tế là negative)
> 					Basic metric
> 						Accuracy
> 						Sensitivity
> 						Specificity
> 						Summary
> 							I.e.
> 						Positive predictive value (PPV)
> 						Negative predictive value (NPV)
> 						Summary
> 					This matrix helps calcualte basic metrics above more effectively
> 				F1 score
> 					Define
> 						To solve the problem balancing precision and recall in order to have the best result 
> 						Precision
> 							=> high precision -> if we diagnose patients having the rare disease, probably patient have it and it's an accurate diagnosis
> 						Recall
> 							=> high recall -> if patient with rare disease, our model will correctly identify they have that disease
> 						In reality, it depends on what we want our model to do by chaning thresthold of our model to match with our desire 
> 						Motivation:
> Why we dont use average of precision and recall?
> i.e. with example below, we can see that algorithm 3 having high average but it is the same as print  y_hat = 1 because recall value is too perfect/ too high 
> 					=> we will have the formula for F1-score by reversing average of 1/p and 1/r (in math was called Harmonic mean) 
> => we will choose algorithm 1, it has a balance between p and rmore
> 				Area under the ROC curve (AUC-ROC)
> 					Receiver Operating Characteristic (ROC) Curve
> 					Area Under the Curve (AUC)
> 						Plots true positive rate against false positive rate at various threshold settings.
> 		Other loss function
> 			Triplet Loss
> 				Concept: Minimizes the distance between an anchor image and a positive image (same person) while maximizing the distance to a negative image (different person).
> 				Benefit: Encourages the model to create embeddings where images of the same person are close together, and images of different people are far apart.
> 				=> we must repair a lot of data
> 					Multiple Images per Identity: Necessary to form meaningful anchor-positive pairs.
> 					Variety in Data: Include images with different poses, lighting, and expressions.
> 				Uses triplets consisting of an anchor image, a positive image, and a negative image.
> 					Anchor (A): The reference image we're comparing others to.
> 					Positive (P): An image of the same person as the anchor.
> 					Negative (N): An image of a different person.
> 					Triplet Formation
> 						The network learns from triplets of images: (A, P, N).
> 						Anchor-Positive Pair: Should have small distance between embeddings.
> 						Anchor-Negative Pair: Should have large distance between embeddings.
> 					How to choose triplet?
> 						Importance of Triplet Selection
> 							Hard Triplets: Triplets where the negative is close to the anchor, making the task challenging.
> 							Easy Triplets: Triplets that already satisfy the loss condition, contributing little to learning.
> 						Strategy
> 							Focus on hard triplets to effectively train the network.
> 							Avoid Random Selection: Random negatives may not help the network learn meaningful distinctions.
> 				Objective is to make the distance between the anchor and positive less than the distance between the anchor and negative by a margin.
> 					Explain formation
> 					Alpha is to help
> 			Contrastive Loss
> 				Encourages the model to output low distances for positive pairs and high distances for negative pairs.
> 			Wasserstein Loss (for GANs)
> 			Dice Loss (for segmentation tasks)
> 	Model selection criteria
> 		Bias-Variance trade-off
> 			High bias and high variance
> Underfitting and Overfitting
> 				High bias is not doing well in training dataset
> 					=> When we feed a lot of data into situation, this is not necessary
> 					Check algorithm (avoidable bias)
> 						Try adding polynomial features
> 							Bigger network
> 							Try tailored/ train better optimization algorithm
> 							Change other neural network architecture
> 							Try changing hyperparameter
> 						Try getting additional features
> 						Try decreasing the regularization parameter
> 					Underfit
> 						Sometimes was called high bias
> 						Does not fit the training set well
> 				High variance is the worse in cross validation dataset than training dataset
> 					Increasing size of training dataset  (more data)
> 					Try increasing the regularization parameter
> 					Try smaller sets of features
> 					Try other neural network architecture
> 					Try changing hyperparameter
> 					Overfit
> 						Sometimes was called high variance
> 						Fits training set absolutely -> lack of generalization, new data will be predicted wrong
> 						Fix:
> 							select features, which is importaint/ useful in real life, is to train
> 							Collect more training examples
> 							Regularization
> 				We try to find case "just right" (more generalization)
> 			Error analysis
> 				How do we know base line for comapring to conclude high bias or high variance
> -> we have 3 ways to do
> 					Human level performance
> 						Optimal (bayesian) error (by expecting machine surpassing human ability in specific task)
> 							When we choose human-level performance, we need to choose the lowest value
> 						If ML is worse than humans, we can:
> 							Get labeled data from humans
> 							Gain insight from manual error analysis:
> Why did a person get this right?
> 							Better analysis of bias/ variance
> 					Completing algorithms performance
> 					Guess based on experience
> 				If we split into training, training-dev, dev and test set
> 					=> we will have final summary about how to diagnosis
> 					How to fix?
> 						Analyze difference between training and dev/ test sets
> 						Make/ collect training data more similar with dev/ test set
> 			Bias-variance trade-off
> 				Bias means the ability of our model capture true relationship between points 
> => high bias will be high error -> high bias and vice versa.
> 				Variance means that applying your model to another data (testing data,...) will give you various result (different/ similar value error)  
> -> with similarity will low variance and with difference will high variance
> 		Computation efficiency
> 	Evaluation multiple ideas in parallel
> Summary
> 	I.e.
> Summary
> In reality, it depends on what we want our model to do by chaning thresthold of our model to match with our desire 
> Summary
> Summary
> ```

---

> [!cue] What is it?

### Probability calibration

Calibration asks whether a model's predicted *probabilities* are trustworthy, not just whether its final class label is right — e.g. among all the times the model says "70% chance of X", X should actually happen about 70% of the time.

- **Calibration curves**: a reliability diagram — predicted probability (binned) on one axis vs. observed frequency of the positive class on the other; a perfectly calibrated model sits on the diagonal.
- **Calibrating a classifier**: post-hoc techniques (e.g. Platt scaling, isotonic regression) that rescale a model's raw scores so they behave like real probabilities.

*(Outline-only in the mindmap — no worked example yet.)*

### Calculating loss/cost — Regression

#### Regression metric families

The mindmap groups regression error metrics by *what they normalize against*. Most entries below are still empty headers ("How to calculate / Example / Pros and cons") in the original notes, so they are indexed here rather than derived in full:

| Family | Metrics | What the family normalizes against |
|---|---|---|
| Scale-dependent error | Mean Error (ME), Mean Squared Error (MSE), Mean Absolute Error (MAE) | Nothing — stays in the original unit, so it can't compare across series with different scales |
| Percentage error | MAPE, sMAPE | The actual value, as a percentage — scale-free but breaks near zero actuals |
| Relative errors | MRAE, GMRAE | Error of a naive/benchmark forecast |
| Relative measures | RelMAE, RSE | A reference model's error |
| Scale error | MASE, RMSSE | The in-sample naive-forecast error (a fixed denominator, so it stays defined even at zero) |
| Other | Percentage Better (PB), RMSLE | Pairwise win-rate against a baseline (PB) / log-scale error, which favors under- over over-prediction (RMSLE) |

#### Mean Squared Error (MSE) — the one branch with real notes

MSE is the **square loss / square error** applied to the mean:
$$ \text{MSE} = \frac{1}{m}\sum_{i=1}^{m}\left(y^{(i)} - \hat{y}^{(i)}\right)^2 $$

The mindmap's own note on this: the squaring is what turns a signed difference into a loss you can minimize, and the conventional $\frac{1}{2}$ factor (as in $\frac{1}{2}(y-\hat{y})^2$) exists purely so it **cancels out when you take the derivative** during backpropagation/gradient descent — it does not change which point minimizes the loss.

Mean Error (ME) and Mean Absolute Error (MAE) are the same family (signed vs. absolute difference) but have no worked example in the original notes yet.

#### Regression losses

- **Huber loss**: combines MAE and MSE — quadratic (like MSE) for small errors, linear (like MAE) for large ones, so it is less sensitive to outliers than pure MSE.
- **Log loss**: see the dedicated section below — it is really a classification-style loss (probability-based) that shows up again in the regression list because it is derived from the same $-\log$ mechanics as BCE.
- **RMSE**: $\sqrt{\text{MSE}}$, back in the original unit of $y$.
- **R-squared / Adjusted R-squared**: proportion of variance in $y$ explained by the model; adjusted R² penalizes adding features that don't actually help.
- **Binary Cross Entropy**: listed here too since a regression target that is itself a probability (e.g. calibration) can be scored with BCE — full mechanics under Classification below.

#### Log loss, in detail

Log loss takes $-\log(\text{predicted probability of the true class})$. The mindmap's reasoning for the two "notes" it leaves here:

1. **Why the negative sign**: $\log$ of a probability (always between 0 and 1) is always $\le 0$. Since $\log$ is a strictly increasing (monotonic) function, $-\log$ flips it into something you can *minimize* — minimizing $-\log(p)$ is the same optimization problem as maximizing $p$, just phrased as a loss.
2. **Why $\log$ helps with tiny numbers**: a probability like $10^{-15}$ is awkward to do arithmetic with directly, but $\log$ turns it into a large-magnitude (very negative) number that is numerically stable and easy to compare.

The worked example in the notes: computing the probability of getting exactly 7 heads out of 10 coin tosses directly (via the binomial's product/chain-rule form) is awkward algebra; taking the $\log$ first turns the product into a **sum** (log-likelihood), which is why maximum-likelihood estimation almost always works in log-space.

### Calculating loss/cost — Classification

#### Basic classification losses

- **Zero-one loss**: $1$ if the prediction is wrong, $0$ if right — the "true" classification error, but non-differentiable, so it is not used directly for gradient-based training.
- **Exponential loss**: penalizes misclassified points exponentially in their margin; this is the loss AdaBoost minimizes, and (per the note below) it is *more* sensitive to outliers than hinge loss.

#### Kullback–Leibler Divergence (KL Divergence)

KL divergence measures the **distance between two probability distributions** $P$ (true) and $Q$ (model). Two things the mindmap flags as the mechanism:
- $\log$ is used the same way as in log loss: to scale values and reduce the effect of very large or very small numbers.
- The weighting inside the sum uses $P(x)$ itself (how likely each outcome actually is) instead of a flat $\frac{1}{m}$ average — rare outcomes under $P$ contribute little, common ones dominate.

#### Binary Cross-Entropy (BCE)

BCE can be read as **the mean of entropy** across examples, and the mindmap connects this directly to intuition about class diversity:
- **High entropy (very mixed classes)** → the distribution is hard to predict confidently → harder decision.
- **Low entropy (one class dominates)** → easy to predict, since picking the dominant class is usually right.

KL divergence and entropy are directly related (cross-entropy = entropy of $P$ + KL divergence between $P$ and $Q$), which is the "proof" the note points at without writing out the derivation.

#### Hinge loss

Used to train **SVMs**. Compared to exponential loss, hinge loss is **more linear and less sensitive to outliers** — it only penalizes points that are on the wrong side of the margin, and does so linearly rather than exponentially.

#### Sparse Categorical Cross-Entropy

The same cross-entropy idea as BCE/categorical CE, but the target is given as an **integer class index** rather than a one-hot vector — it compares the softmax output directly against "which index is correct" instead of doing a full one-hot dot product.

#### Label smoothing

Reduces a model's tendency to be **overconfident** (the note's example: a model that has only ever seen yellow bananas shouldn't assign probability ~1.0 to "yellow" for every banana, since bananas can be green or brown too). Instead of a hard one-hot target, the true-class probability is softened and a little mass ($\alpha$, the smoothing hyperparameter) is spread across the other $C$ classes (number of classes), changing the target distribution the model is trained against.

#### Multi-label classification

When an example can belong to **more than one class at once** (the mindmap's examples: a patient with diabetes *and* hypertension; an image containing a car *and* a bus), softmax is the wrong tool — softmax forces probabilities to compete and sum to 1, which suppresses every class but one. Instead:
- Use an **independent sigmoid per class** (not one softmax over all classes).
- **With cross-entropy**: the loss has an inner summation over the classes within one example, and an outer summation over all examples (each class gets its own binary loss, summed).
- **With pairwise ranking loss**: creates a margin between the score of an active (true) label and a weak (non-active) label, rather than scoring each class in isolation.

#### Focal loss

Down-weights the loss contribution of examples the model already classifies confidently and correctly, so training focuses on hard or minority-class examples — the standard fix for severe class imbalance (e.g. dense object detection). *(Header-only in the mindmap; no worked example yet.)*

#### Threshold

The threshold (typically applied on top of a sigmoid output) is the cutoff that turns a predicted probability into a **positive/negative** class decision. Moving it trades off sensitivity against specificity — the same threshold that maximizes accuracy is rarely the one that matches the real-world cost of a false positive vs. a false negative.

### Metrics for classification

#### Confusion matrix

The confusion matrix separates two independent questions:
- **True/False** — did the model predict *correctly*?
- **Positive/Negative** — what did the model actually *predict*?

So, per the original note: a **false positive** means the model predicted positive but the ground truth is negative (the prediction was wrong, and what it predicted was "positive"). From the four cells (TP, FP, FN, TN) come:

| Metric | Definition | Answers |
|---|---|---|
| Accuracy | (TP+TN) / total | Overall, how often is the model right? |
| Sensitivity (Recall) | TP / (TP+FN) | Of all actual positives, how many did we catch? |
| Specificity | TN / (TN+FP) | Of all actual negatives, how many did we correctly reject? |
| PPV (Precision) | TP / (TP+FP) | Of everything predicted positive, how many really are? |
| NPV | TN / (TN+FN) | Of everything predicted negative, how many really are? |

#### F1 score

F1 exists to balance **precision** and **recall** when neither alone tells the full story:
- **High precision** matters when a positive prediction must be trustworthy (e.g. diagnosing a rare disease — you want most "positive" diagnoses to be real).
- **High recall** matters when missing a positive is costly (e.g. you want to catch every patient who actually has the rare disease, even at the cost of some false alarms).

The note's own motivating question — *why not just average precision and recall?* — is answered with a counterexample: a degenerate model that always predicts $\hat{y}=1$ gets perfect recall (catches every positive) and a mediocre precision, and a plain average can make that model look deceptively competitive against a genuinely balanced one. F1 fixes this by using the **harmonic mean** of precision and recall instead of the arithmetic mean:
$$ F_1 = \frac{2}{\frac{1}{P} + \frac{1}{R}} = 2\cdot\frac{P \cdot R}{P+R} $$
The harmonic mean punishes imbalance between $P$ and $R$ much more than an arithmetic average would, which is exactly why the notes conclude "we will choose [the balanced algorithm], it has a balance between p and r" over a lopsided one.

#### Area under the ROC curve (AUC-ROC)

- **ROC curve**: plots the true positive rate (sensitivity) against the false positive rate (1 − specificity) as the decision threshold is swept.
- **AUC**: the area under that curve — a single number summarizing performance across *all* thresholds at once, rather than one threshold at a time.

### Other loss functions

#### Triplet loss

Trains embeddings so that, given three inputs — an **Anchor (A)**, a **Positive (P)**, same identity as the anchor, and a **Negative (N)**, a different identity — the distance $d(A,P)$ is pushed smaller than $d(A,N)$ by at least a margin $\alpha$:
$$ d(A,P) + \alpha < d(A,N) $$
This directly produces embeddings where same-identity images cluster together and different-identity images sit apart, which is exactly what face-verification / re-identification systems need.

Two things the notes flag as essential to make this work in practice:
- **Data requirements**: multiple images per identity (to form real anchor-positive pairs) and enough pose/lighting/expression variety to generalize.
- **Triplet selection matters more than triplet quantity**: "easy" triplets (already satisfying the margin) contribute almost nothing to learning; training should focus on **hard triplets** (negative close to the anchor) rather than random sampling.

#### Contrastive loss

The pairwise version of the same idea: instead of anchor/positive/negative triplets, it trains on **pairs**, pushing the embedding distance down for positive (same-class) pairs and up for negative (different-class) pairs.

#### Wasserstein loss (for GANs) / Dice loss (for segmentation)

Named but not elaborated in the mindmap yet — Wasserstein loss is the Earth-Mover's-distance-based objective used to stabilize GAN training; Dice loss directly optimizes overlap between predicted and ground-truth masks, which is the standard choice for segmentation with class imbalance.

### Model selection criteria

#### Bias-variance tradeoff

The full theory table (underfit/overfit symptoms and fixes, L2 regularization, data augmentation) already lives in [[03_Diagnostics-and-Error-Analysis]] — this note does not repeat it. What *this* mindmap adds on top is the piece that note doesn't cover yet: **how do you know, in the first place, whether an error gap is high bias or high variance?**

The notes give three ways to establish the baseline you compare training/dev error against:
1. **Human-level performance**, treated as a proxy for the **Bayes (optimal) error** — the theoretical floor no model can beat. When several human benchmarks exist, use the *lowest* one (the most skilled human), since that is the closest available estimate of the Bayes error.
2. The trend of **prior algorithms' own performance** over time.
3. A domain **guess based on experience** when neither of the above is available.

If the model is worse than the human-level baseline (**avoidable bias**), the notes point at: getting more human-labeled data, doing manual error analysis ("why did a person get this one right?"), and a more careful bias/variance breakdown — rather than immediately reaching for "more data," which mainly helps *variance*, not bias.

Once training/**training-dev**/dev/test splits are in place (see [[01_Project-Scoping-and-Dataset]] for why the training-dev set exists), comparing the gaps between them gives a full diagnosis: a training-vs-training-dev gap is variance, a training-dev-vs-dev gap is data mismatch, and dev-vs-test overfitting means the model has started fitting the dev set itself. The fix in every case is the same shape: analyze *where* the gap is, then either collect more training data that better matches that distribution, or make the dev/test data more representative.

Definitions, restated from the notes:
- **Bias** = how well the model can capture the true relationship in the data → high bias shows up as high error almost everywhere, including on training data.
- **Variance** = how much the model's error swings when applied to *different* data samples → high variance means training error is low but it doesn't hold up on unseen data.

#### Computation efficiency

Flagged as a model-selection criterion alongside accuracy — a more accurate model that is too slow or expensive to run in production is not automatically the right choice. *(Header-only in the mindmap; no detail captured yet.)*

#### Evaluating multiple ideas in parallel

Running several candidate models/ideas side-by-side against the same dev set, so they can be compared directly instead of sequentially re-testing one idea at a time. *(Header-only in the mindmap; no detail captured yet.)*

> [!cue] Why is it important?

Every piece above answers the same underlying question: *how do you know your model is actually good, and which lever do you pull next if it isn't?* Picking the wrong loss silently changes what "good" means to gradient descent — an MSE-trained regressor chases outliers, a plain-softmax classifier can't express "this image has three objects," and an uncalibrated classifier's probabilities can't be trusted for a downstream decision even if its accuracy looks fine. Picking the wrong *metric* disconnects model improvement from the actual business goal, which is exactly the failure mode [[01_Project-Scoping-and-Dataset]] guards against with optimizing/satisficing metrics. And skipping the diagnostic step — establishing a human-level/Bayes-error baseline before deciding "more data" or "bigger model" — wastes engineering effort chasing the wrong fix, the same "diagnose before you fix" discipline behind [[03_Diagnostics-and-Error-Analysis]]'s error analysis. Model evaluation and selection is what turns "the loss went down" into "the model is actually ready."

> [!cue] How is it related to ...?

- [[01_Project-Scoping-and-Dataset]]: the single-number, optimizing/satisficing metrics chosen during project scoping are exactly what the loss/metric toolbox in this note implements; the training/training-dev/dev/test split machinery used for diagnosing distribution mismatch is the same split structure the bias-variance baseline here relies on.
- [[03_Diagnostics-and-Error-Analysis]]: owns the core bias-variance tradeoff table (underfit/overfit symptoms, regularization, data augmentation) — this note extends it with the missing baselining step (human-level performance, Bayes/optimal error, avoidable bias) rather than duplicating the tradeoff theory.
- [[01_ML-Fundamentals-and-Terminology]]: defines the loss-vs-cost distinction (loss = per single example, cost = averaged over the dataset) that every metric and loss family in this note is built on top of.
