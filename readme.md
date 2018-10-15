## Data Dimensionality Reduction

## Content
* Principal Component Analysis - * pca *
* Finding sample dimensions by nonlinear methods - * nonlinear *
* MNIST sample selection - * mnist visualization *

## Conclusions on laboratory work

### Principal Component Method
A linear method for reducing the dimension of PCA data was considered. To demonstrate the capabilities of the method, several data sets were used:
* Sample from two-dimensional normal distribution
* Airfoils
* Digits
* Faces

The possibility of data compression with the loss of "invisible to the eye" could not fail to impress. For example, 4096 numbers are required to store one source image from the Olivetti face set. With the principal component method, this number can be stirred up to 150 with a loss, loosely speaking, of only 5%. It is practical imperceptible to man. Thus, for one image 30 times less memory is required. But you need to keep in mind that to restore the object you need to perform a linear transformation matrix of size 4096 * 150. And, accordingly, it must also be stored. But if this method squeezed a lot of objects, for example, 100000, then the benefit from memory is obvious.

_______________________________
### Finding sample dimensions by nonlinear methods
Three non-linear methods for finding data dimensions were considered:
* Levina-Bickel method (1 method)
* Isomap method (2 method)
* Granata-Carnevale method (3 method)

To test their performance, both model data, for which the true dimension is known, and real, were used.
From the results on the model data, one can find the distinctive features of the methods that must be kept in mind in order to draw conclusions about the real data.
##### Results on model data
Let us consider more closely the results of experiments on multidimensional spheres.
* On the data of a small dimension to 10, the 1st method accurately coped. For larger dimensions, more and more, his answer does not reach the true dimension.

* 2nd method failed. According to the results of his work, one cannot conclude that the data lie in a variety of dimensions of a smaller number of features. He always ranked on top.

* The 3rd method up to dimension 21 gives the number of signs as an answer. Next - lower bound

All three methods managed the noisy data of Swiss_roll, Moons and S_curve. However, only the 2nd method turned out to be resistant to noise, while the 1st and 3rd methods overestimated their estimate.
##### Results on real data
On real data, most likely, it is impossible to say in a variety of what dimension they lie, but we can conclude the following conclusions:
* The first method did well on low-dimensional data, so the dimension of airfoils is about 4, and the second method also gives an estimate from above.
* MNIST data of about 12 dimensions. The first two methods talk about this. The 3rd method overestimates this estimate, but judging by the model data, it should be trusted on data of a higher dimension.
* Iris of dimension about 3. All three methods gave a close to this estimate.
* Trusting the first method in small dimensions - Diabetes dimension 6.
* Boston - about 3.
* Olivetti from 7 to 10. The first method was decided to be trusted on small dimensions, and the second method gave an estimate from above.
* California - 3.
* Lfw - about 30.
##### About Resources and Efficiency
It is worth noting that the first method worked much faster than the first two. And at the same time it gives good results, and even better on the data of dimension to 10.
The second and third methods consumed much more memory and could not perform calculations on some data.
_________________
### MNIST fetch visualization
For acquaintance with non-linear methods of reducing the dimension was used sample MNIST size 5000.
There is a hypothesis (true for many data sets): objects of the same class or similar objects are at a small distance from each other, and different objects are at a large one. Metric data analysis methods are based on this hypothesis.

The methods considered found two-dimensional representations of the MNIST sample. Some methods did worse: there are significant intersections of different classes. Best of all, the t-SNE method handled the task. He managed to find a two-dimensional representation of MNIST, in which different classes practically do not overlap.
