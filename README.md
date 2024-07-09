# Intro-Contrastive-Learning
Contrastive learning is a self-supervised learning technique that has gained significant traction in the machine learning community. Its primary goal is to learn effective representations of data without the need for labeled samples. The core idea is to train a model to distinguish between similar (positive) and dissimilar (negative) pairs of data points.

In contrastive learning, the model is typically trained using a loss function that encourages the representation of similar sample to be close in the feature space while pushing the representations of dissimilar sample farther apart. This approach leverages data augmentation techniques to create positive pairs from the same data instance and negative pairs from different instances.

Various frameworks and algorithms have been proposed. Among these methods, SimCLR (A Simple Framework for Contrastive Learning of Visual Representations)[^1] stands out as a remarkable work. It not only simplifies the process of contrastive learning but also significantly improves the performance of visual representation learning. Next, we will delve into the details of SimCLR and explore how it has become an important milestone in the field of contrastive learning.



[^1] Chen, T., Kornblith, S., Norouzi, M. &amp; Hinton, G.. (2020). A Simple Framework for Contrastive Learning of Visual Representations. <i>Proceedings of the 37th International Conference on Machine Learning</i>, in <i>Proceedings of Machine Learning Research</i> 119:1597-1607 Available from https://proceedings.mlr.press/v119/chen20j.html.

