# Adult dataset
In order to have a reliable benchmark where compare our results, we analyzed the performance of our model on the UCI adult dataset: this dataset is an extract of the US census and contains information about working adults, distributed across 14 features. Records are classiﬁed depending on whether the individual earns more or less than 50k dollars each year. This dataset has been used extensively in many other applications that targeted diﬀerential privacy and, therefore, it constitutes a good test for our work. To be able to use accuracy as an evaluation metric, we decided to sample the training and test data in such a way that both classes would be balanced. Although our objective is to guarantee privacy, we also need to verify that the released data still maintain some of their utility. We test our dp-GAN in a classiﬁcation task. In particular, we anonymized the training dataset through our dp-GAN model and then built a random forest classiﬁer on the generated dataset. We compute the accuracy using the test set and compare it with what we measured for the model built using the real (non-anonymized) dataset. If the dp-GAN model behaves correctly, all the correlations between the diﬀerent features should be preserved. So that, the ﬁnal accuracy should be similar to what was achieved by using the real training set. We also tracked the privacy costs to verify that the generated data were correctly anonymized. Every time a grid-search is performed to produce the best random forest model that is then used to compute the accuracy. 
![Alt text](was.png?raw=true "Title")
![Alt text](epss.png?raw=true "Title")
![Alt text](accuracyadult.png?raw=true "Title")
The figures highlights the overall training process of a dp-GAN on the adult dataset. It spots many interesting facts that need to be analysed. Firstly, it is possible to notice that after epoch 110 (where epsilon = 5) the classiﬁcation accuracy reaches a plateu. Regarding model selection, this is a good point where to stop the training because additional epochs will consume more privacy with a limited increase of the accuracy. It is interesting to notice the the wasserstein distance has a similar behaviour compared to the classiﬁcation accuracy. At about the same epoch the graph tend to stabilize although the distance continue to decrease until the end. 

![Alt text](time.png?raw=true "Title")
The overhead introduced by the anonymization process are negligible.

![Alt text](loss.png?raw=true "Title")
The figure represents the losses of the generator and the discriminator during the training. It is interesting to notice that, when the dp-GAN converges the losses tends to stabilize. However, they do not stabilize on a minimum but on an equilibrium. The σ constitutes the best way to manage the utility-privacy trade-oﬀ. A low σ speeds up the training process but at the same time increase the value of epsilon.

![Alt text](original.png?raw=true "Title")
original data distribution
![Alt text](GAN.png?raw=true "Title")
data distribution using GAN
![Alt text](dp-GAN.png?raw=true "Title")
data distribution using dp-GAN with epsilon = 3
For example the fact that a doctorate guarantees higher incomes is preserved. Similarly, the inequality between black women and white men is still visible.
This highlights that GAN and dp-GAN are able to model the joint distribution p(x,y) and use it to generate new data.

![Alt text](params.JPG?raw=true "Title")
