# Face Recognition from Scratch

## Simple Explanation

- First up, we leverage Base64, which allows multiple images to be serialized to a single plaintext file.
- Haar cascade frontal face detector is used to detect the presence of faces (i.e., extracting ROIs).
- Then the ROIs are passed on to our recognizer (LBPs) for face identification.

## Inference

- To gather your own data, run the following command and press 'C' to get into the capture mode:

```
python gather_data.py --face-cascade cascades/haarcascade_frontalface_default.xml --output output/faces/desiredname.txt
```
> Make sure to enter your desired name instead of 'desiredname.txt' and the result would be saved in 'output/faces' folder.

- To train the recognizer:

```
python train.py --data output/faces --classifier output/classifier --sample-size 100
```
> The trained model would be saved in 'output/classifier' folder.

- To test the recognizer:

```
python test.py --face-cascade cascades/haarcascade_frontalface_default.xml --classifier output/classifier
```

## References
- Local Binary Patterns (LBPs): https://github.com/saimj7/Face-Recognition-Algorithms/tree/main/Face%20Recognition%20with%20LBPs

---

saimj7/ 11-03-2021 © <a href="http://saimj7.github.io" target="_blank">Sai_Mj</a>.
