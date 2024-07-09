# Simple Introduction to Contrastive Learning (Preparaing)
Contrastive learning is a self-supervised learning technique that has gained significant traction in the machine learning community. Its primary goal is to learn effective representations of data without the need for labeled samples. In contrastive learning, the model is typically trained using a loss function that encourages the representation of similar sample to be close in the feature space while pushing the representations of dissimilar sample farther apart. This approach leverages data augmentation techniques to create positive pairs from the same data instance and negative pairs from different instances.

Various frameworks and algorithms have been proposed for Contrastive learning. Among these methods, SimCLR (A Simple Framework for Contrastive Learning of Visual Representations) <sup>[1]</sup> stands out as a remarkable work. SimCLR learns representations by maximizing agreement between differently augmented views of the same data example using a contrastive loss in the latent space. It not only simplifies the process of contrastive learning but also significantly improves the performance of visual representation learning. 

## Data Augmentation
As previously mentioned, contrastive learning falls under the umbrella of self-supervised learning. Since we do not have readily available labeled data, we need to construct similar data (positive examples) and dissimilar data (negative examples) ourselves. So, how does SimCLR go about building these two types of data? In SimCLR, positive and negative examples are constructed as follows:

- Positive examples: For each input image, SimCLR creates augmented versions through random transformations (e.g., rotation, cropping, color distortion). The original image and one of its transformed versions form a positive pair, as these transformations preserve the image's intrinsic content, making them close in the feature space.

* Negative examples: Negative examples are the transformed versions of other images in the same batch. Since each image is different, their transformed versions should be far apart in the feature space. Thus, each image in the batch forms negative pairs with all other transformed images in the batch.

This approach allows SimCLR to learn effective visual representations through contrastive learning in a self-supervised manner, leveraging large amounts of unlabeled data without manual labeling. 

![Data augmentation operators used in SimCLR](./images/SimCLR_Data_Augmentation.pdf)

## Framrwork
SimCLR proposes a method for constructing negative samples based on the idea that an input image is randomly transformed through data augmentation to produce two images, $x_i$ and $x_j$. These images are then passed through an encoder to obtain their respective representations, $h_i$ and $h_j$. A nonlinear fully connected layer is then used to derive the final representations, $z_i$ and $z_j$. The learning task is to maximize the similarity between these two representations, $z_i$ and $z_j$, for the same image. Once the network has been trained, $h_i$ and $h_j$ can be used as feature representations of the image for downstream tasks.

![The proposed framework of SimCLR](./images/SimCLR_Framework.pdf)

## Contrastive Loss
SimCLR employs a contrastive loss function known as the _NT-Xent_ (Normalized Temperature-scaled Cross Entropy Loss). This loss function ensures that the feature representations of positive pairs are close while those of negative pairs are far apart. The NT-Xent loss is defined as:

![](https://latex.codecogs.com/png.image?\large&space;\dpi{120}\bg{white}\ell_{i,j}=-\log\frac{\exp(\mathrm{sim}(z_i,z_j)/\tau)}{\sum_{k=1}^{2N}\mathrm{1}_{[k\neq&space;i]}\exp(\mathrm{sim}(z_i,z_k)/\tau)})

where 𝜏 is a temperature parameter, _2N_ is the number of samples in a batch, and sim(u,v) denotes the cosine similarity between two vectors 𝑢 and 𝑣 defined as following:

![](./images/SimEqn.png)


## References
[1] Chen, T., Kornblith, S., Norouzi, M. &amp; Hinton, G.. (2020). A Simple Framework for Contrastive Learning of Visual Representations. <i>Proceedings of the 37th International Conference on Machine Learning</i>, in <i>Proceedings of Machine Learning Research</i> 119:1597-1607.

