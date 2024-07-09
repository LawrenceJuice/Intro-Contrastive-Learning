# Intro-Contrastive-Learning
Contrastive learning is a self-supervised learning technique that has gained significant traction in the machine learning community. Its primary goal is to learn effective representations of data without the need for labeled samples. In contrastive learning, the model is typically trained using a loss function that encourages the representation of similar sample to be close in the feature space while pushing the representations of dissimilar sample farther apart. This approach leverages data augmentation techniques to create positive pairs from the same data instance and negative pairs from different instances.

Various frameworks and algorithms have been proposed for Contrastive learning. Among these methods, SimCLR (A Simple Framework for Contrastive Learning of Visual Representations) <sup>[1]</sup> stands out as a remarkable work. It not only simplifies the process of contrastive learning but also significantly improves the performance of visual representation learning. 

SimCLR learns representations by maximizing agreement between differently augmented views of the same data example using a contrastive loss in the latent space. SIMCLR proposes a method for constructing negative samples based on the idea that an input image is randomly transformed through data augmentation to produce two images, $x_i$ and $x_j$. These images are then passed through an encoder to obtain their respective representations, $h_i$ and $h_j$. A nonlinear fully connected layer is then used to derive the final representations, $z_i$ and $z_j$. The learning task is to maximize the similarity between these two representations, $z_i$ and $z_j$, for the same image. Once the network has been trained, $h_i$ and $h_j$ can be used as feature representations of the image for downstream tasks.



[1] Chen, T., Kornblith, S., Norouzi, M. &amp; Hinton, G.. (2020). A Simple Framework for Contrastive Learning of Visual Representations. <i>Proceedings of the 37th International Conference on Machine Learning</i>, in <i>Proceedings of Machine Learning Research</i> 119:1597-1607.

