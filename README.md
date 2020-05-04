# PKGBUILD_Rapids

a  procedure of building [Rapids](https://rapids.ai/) on Arch Linux with CUDA environment.

## Order in build

1. [grpc](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/grpc/PKGBUILD)

```
* Build gRPC 1.27.3 compulsory
*Apache Arrow cannot be build with grpc Ver 1.28 or higher 
```

2.  [arrow](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/arrow/PKGBUILD)
```
* Build Apache Arrow 0.15.1 compulsory
* With Apache Arrow 0.16 or higher, cuDF cannot be build. see [ISSUE](https://github.com/rapidsai/cudf/issues/4605)
```

3.  [python-pyarrow](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/python-arrow/PKGBUILD)
```
* Build  Python Library of Apache Arrow 0.15.1 compulsory
```

4.  [protobuf-static](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/protobuf-static/PKGBUILD)
```
* Static library of protobuf is required to build cuDF.
* AUR provides the same package. However,  AUR only contains older ver (3.11.1)., (current ver. is 3.11.4)
```

5.  [cupy](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/cupy/PKGBUILD)
```
* An implementation of NumPy-compatible  array on CUDA presented by Preferred Networks.
* AUR provides the same package. However,  AUR only contains older ver (7.2.0). which does not support CUDA 10.2 , (current ver. is 7.4.0) 
*  See [github](https://github.com/cupy/cupy)
```

6.  [rmm](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/rapids-rmm/PKGBUILD)
```
* RAPIDS Memory Manager provided by  Rapids.
* See [github](https://github.com/rapidsai/rmm)
```

Optional.  [rapids-dask-cuda](https://github.com/gdaisukesuzuki/PKGBUILD_Rapids/tree/master/rapids-dask-cuda/PKGBUILD)
```
* experimental solution.
* See [github](https://github.com/rapidsai/dask-cuda)
```

