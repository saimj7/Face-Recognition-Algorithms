# Face Recognition with the Eigenfaces algorithm
### Applying PCA and SVM

> We apply the algorithm to identify each of the subjects in the CALTECH Faces dataset. The image on the left is simply the average of all faces in the dataset, while the figures on the right show the most prominent deviations (Eigenfaces) from the mean in dataset:

<div align="center">
<img src=mylib/misc/one.png?raw=true "Eigenfaces" width=570 >
</div>

---

## Simple Theory

- First up, we divide a face image into KxK grayscale pixels.
- Then, we flatten each image in the dataset into a k2-dim feature vector. Nothing but concatenating all of the rows together, forming a single, long K2 (k square) list of grayscale pixel intensities.
- Next, we form a matrix M with Z rows (no. of images) and k2 columns (flattened images).
- The previous step is required to apply PCA.

## Principal Component Analysis (PCA)

- General steps include computing the mean of every column in the matrix M (gives us the avg. pixel intensities), computing covariance matrix, performing eigenvalue decomposition of such matrix to get eigenvalues and eigenvectors.
- Sorting eigenvectors w.r.t eigenvalues, largest to smallest.
- Taking the top N eigenvectors with the largest corresponding eigenvalue magnitude.
- Finally transforming the input data by projecting (i.e., taking the dot product) it onto the space created by the top N eigenvectors — these eigenvectors are called our eigenfaces. Refer above image.

## Face Identification

- Given the eigenface vectors, we can represent a new face by taking the dot product between the (flattened) input face image and the N eigenfaces. This allows us to represent each face as a linear combination of principal components:
```
Test Face = 36% of Eigenface #1 + -8% of Eigenface #2 … + 21% of Eigenface N
```
- To perform the actual face identification, originally we project the test image onto the eigenface space (as discussed in PCA) and take the Euclidean distance between the eigenface representations (k-NN classifier). However, we ended up using SVM to further improve the accuracy.

---

## Inference

- Download and extract CALTECH Faces dataset from [**here**](http://www.vision.caltech.edu/html-files/archive.html) (already included).
- To train and test the algorithm:

```
python run.py --dataset caltech_faces
```
- Results:

<div align="center">
<img src=mylib/misc/two.png?raw=true "sklearn" width=520 >
</div>

> NOTE: Pretty good accuracy. Feel free to change the number of principal components and check the performance.

- Actual Vs. Predicted:

<div align="center">
<img src=mylib/misc/three.png?raw=true "sample" width=580 >
</div>


## References
- CALTECH Faces dataset: http://www.vision.caltech.edu/html-files/archive.html
- Eigenfaces paper: https://www.researchgate.net/publication/19588504_Low-Dimensional_Procedure_for_the_Characterization_of_Human_Faces
- PCA: https://en.wikipedia.org/wiki/Principal_component_analysis
- PCA implementation: https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html
- More on PCA: https://www.coursera.org/learn/machine-learning
- SVMs: https://scikit-learn.org/stable/modules/svm.html
- For in-depth theory: https://www.pyimagesearch.com/pyimagesearch-gurus/

---

saimj7/ 09-03-2021 © <a href="http://saimj7.github.io" target="_blank">Sai_Mj</a>.
