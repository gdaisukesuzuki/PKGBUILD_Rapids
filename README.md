# PKGBUILD_Rapids

a  procedure of building NVIDIA's [RAPIDS](https://rapids.ai/) under Arch Linux with CUDA environment on  '''Single Nvidia's GPU'''.

## Order in build


1.  [protobuf-static](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/protobuf-static/PKGBUILD)
```
* Static library of protobuf is required to build cuDF.
* AUR provides the same package. However,  AUR only contains older ver (3.11.1)., (current ver. is 3.12.2)
```

2.  [arrow](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/arrow/PKGBUILD) / [python-pyarrow](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/python-arrow/PKGBUILD)
```
* Build Apache Arrow 0.15.1 and and its associated Python-Wrapper compulsory
* With Apache Arrow 0.16 or higher, cuDF cannot be build. see [ISSUE](https://github.com/rapidsai/cudf/issues/4605)
* Apache Orc is required located in AUR.
* During compilation in Apache Flight, there is a patch so that gRPC-c++-plugin cab be easily integrated in Higher Version.
```

3.  [python-cmake-setuptools](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/python-cmake-setuptools/PKGBUILD)
```
* Build  Python Library for enabling to run cmake during "python setup.py build"
```
4.  [cupy](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/cupy/PKGBUILD)
```
* An implementation of NumPy-compatible  array on CUDA presented by Preferred Networks.
* AUR provides the same package. However,  AUR only contains older ver (7.2.0). which does not support CUDA 10.2 , (current ver. is 7.4.0) 
*  See [github](https://github.com/cupy/cupy)
```

5.  [python-llvm](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/blob/master/python-llvmlite/PKGBUILD) / [python-numba](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/blob/master/python-numba/PKGBUILD)
```
* An open source JIT compiler that translates a subset of Python and NumPy code into fast machine code.
* These PKGBUILDs provide llvmlite 0.33.0rc1 and Numba 0.50.0rc1, respectively.
*  See githubs. [llvmlite](https://github.com/numba/llvmlite) and [numba](https://github.com/numba/numba)
```


6.  [RMM](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/rapids-rmm/PKGBUILD)
```
* RAPIDS Memory Manager provided by  Rapids.
* See [github](https://github.com/rapidsai/rmm)
```

7.  [cuDF](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/rapids-cudf/PKGBUILD)
```
*  a GPU DataFrame taking place of pandas
* See [github](https://github.com/rapidsai/cudf)
```

8.  [cuML](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/rapids-cuml/PKGBUILD)
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
* its building depends on Python-Numba (See No.5).
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

