# Face Recognition with LBPs
### Local Binary Patterns (LBPs)

> We apply the LBPs algorithm to identify each of the subjects in the CALTECH Faces dataset. LBP histograms (right) for the white cells (such as the eyes) are weighed 4x more than the other cells:

<div align="center">
<img src=mylib/misc/weigh.png?raw=true "weighing scheme" width=570 >
</div>

---

## Simple Theory

- First up, we divide a face image into 7x7 equally sized cells.
- Then, for each of these cells, we compute a LBP histogram. That implies spatial encoding a level of spatial information such as the eyes, nose, mouth, etc.
- This allows us to weigh the resulting histograms from each of the cells differently, giving more discriminative power to more distinguishing features of the face (refer above image).
- For every image in the training data, LBPs are extracted, weighted, and concatenated as a single feature vector.
- Finally, k-NN (with k=1) is implemented with x2 (x square) distance to find the closest match from the training data.

## Inference

- Download and extract CALTECH Faces dataset from [**here**](http://www.vision.caltech.edu/html-files/archive.html).
- To train and test the recognizer:

``` python run.py --dataset caltech_faces
```
- Results:

<div align="center">
<img src=mylib/misc/result1.png?raw=true "sklearn" width=520 >
</div>

> NOTE: Pretty good accuracy. Feel free to change the cell size, usually 8x8 (64 histograms) or higher results in higher accuracy. However, the computations to extract features, memory storage and training time also increases.

- Actual Vs. Predicted:

<div align="center">
<img src=mylib/misc/result2.png?raw=true "sample" width=580 >
</div>


## References
- CALTECH Faces dataset: http://www.vision.caltech.edu/html-files/archive.html
- LBPs paper: https://link.springer.com/content/pdf/10.1007%2F978-3-540-24670-1_36.pdf
- OpenCV implementation: https://docs.opencv.org/master/df/d25/classcv_1_1face_1_1LBPHFaceRecognizer.html
- For In-depth Theory: https://www.pyimagesearch.com/pyimagesearch-gurus/

---

saimj7/ 07-03-2021 © <a href="http://saimj7.github.io" target="_blank">Sai_Mj</a>.
