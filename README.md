# PKGBUILD_Rapids

a  procedure of building NVIDIA's [RAPIDS](https://rapids.ai/) under Arch Linux with CUDA environment on  '''Single Nvidia's GPU'''.

## Order in build

1. [grpc](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/grpc/PKGBUILD)

```
* Build gRPC 1.27.3 compulsory
* Apache Arrow cannot be build with grpc Ver 1.28 or higher 
```

2.  [protobuf-static](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/protobuf-static/PKGBUILD)
```
* Static library of protobuf is required to build cuDF.
* AUR provides the same package. However,  AUR only contains older ver (3.11.1)., (current ver. is 3.11.4)
```

3.  [arrow](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/arrow/PKGBUILD)
```
* Build Apache Arrow 0.15.1 compulsory
* With Apache Arrow 0.16 or higher, cuDF cannot be build. see [ISSUE](https://github.com/rapidsai/cudf/issues/4605)
```

4.  [python-pyarrow](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/python-arrow/PKGBUILD)
```
* Build  Python Library of Apache Arrow 0.15.1 compulsory
```


5.  [python-cmake-setuptools](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/python-cmake-setuptools/PKGBUILD)
```
* Build  Python Library for enabling to run cmake during "python setup.py build"
```
6.  [cupy](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/cupy/PKGBUILD)
```
* An implementation of NumPy-compatible  array on CUDA presented by Preferred Networks.
* AUR provides the same package. However,  AUR only contains older ver (7.2.0). which does not support CUDA 10.2 , (current ver. is 7.4.0) 
*  See [github](https://github.com/cupy/cupy)
```

7.  [rmm](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/rapids-rmm/PKGBUILD)
```
* RAPIDS Memory Manager provided by  Rapids.
* See [github](https://github.com/rapidsai/rmm)
```

8.  [cuDF](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/rapids-cudf/PKGBUILD)
```
*  a GPU DataFrame taking place of pandas
* See [github](https://github.com/rapidsai/cudf)
```

9.  [cuML](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/rapids-cuml/PKGBUILD)
```
*  A suite of libraries that implement machine learning algorithms presented by Rapids.
* See [github](https://github.com/rapidsai/cuml)
```

Optional.  [cuSignal](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/rapids-cusignal/PKGBUILD)
```
* GPU accelerated signal processing which may replace scipy signal?
* See [github](https://github.com/rapidsai/cusignal)
```





Optional [rapids-cuGraph](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/rapids-cugraph/PKGBUILD)
, [libcypher-parser](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/blob/master/libcypher-parser/PKGBUILD)
```
* a collection of GPU accelerated graph algorithms
* See [github](https://github.com/rapidsai/cugraph)
* libcypher-parser is required before building cuGraph
```

Optional [rapids-cuSpatial](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/rapids-spatial/PKGBUILD)
```
* a library for handling spatial and trajectory data.
* See [github](https://github.com/rapidsai/cuspatial)
```


TBD.  [rapids-dask-cuda](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/rapids-dask-cuda/PKGBUILD)
```
* experimental solution.
* See [github](https://github.com/rapidsai/dask-cuda)
```
## Need for Benchmark

1. [UMAP-Learn](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/blob/master/python-umap-learn/PKGBUILD)

```
* Uniform Manifold Approximation and Projection for Dimension Reduction
* Only running on  Intelx86 (for example it cannot run on Jetson Xavier nx)
```

2. [XGBoost](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/blob/master/xgboost/PKGBUILD)

```
* an optimized distributed gradient boosting library 
* Builds Library and its Python-Wrapper
```
3. [treelite](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/blob/master/treelite/PKGBUILD)

```
* a model compiler for efficient deployment of decision tree ensembles 
* Builds Library and its Python-Wrapper
```

4. [Benchmark](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/blob/master/benchmark/cuml_benchmarks.ipynb)

```
* Benchmark Result 
```
See [URL](https://github.com/rapidsai/cuml/blob/branch-0.14/notebooks/tools/cuml_benchmarks.ipynb)

