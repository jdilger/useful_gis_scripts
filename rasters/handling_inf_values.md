At times a raster may have been processed in such a way that positive or negative infinity values are present in one or more of you bands.

One method to deal with inf/-inf values is to set them to 0. 

https://stackoverflow.com/questions/52458409/how-to-remove-nan-and-inf-values-from-a-numpy-matrix

```python
arr = np.array([[np.inf, -np.inf, 1.0, np.nan],
             [np.inf, 40, 1.0, 20],
             [2, -np.inf, 1.0, 10]])
infmask = np.isfinite(arr)
arr[~infmask] = 0
```
The tilde (~) is a bitwise not which inverts the boolean mask.


output
```
array([[ 0.,  0.,  1.,  0.],
       [ 0., 40.,  1., 20.],
       [ 2.,  0.,  1., 10.]])
```