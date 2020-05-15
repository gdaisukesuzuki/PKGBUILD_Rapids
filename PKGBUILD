# Maintainer: Sven-Hendrik Haase <svenstaro@gmail.com>
# Contributor: bartus <arch-user-repoᘓbartus.33mail.com>
# Contributor: pingplug <pingplug@foxmail.com>
# Contributor: cornholio <vigo.the.unholy.carpathian@gmail.com>

pkgname=(rapids-cudf)
_pkgname=cudf
pkgver=0.14.0a.r4705.gb9853810d
pkgrel=1
pkgdesc="RAPIDS Memory Manager"
arch=('x86_64')
url="https://rapids.ai/"
license=('custom')
depends=('arrow-cudf<0.16.0' 'gcc8' 'cuda' 'cmake' 'rapids-rmm' 'dlpack' 'boost-libs' 'python-dask'  'python-distributed' 'protobuf')
makedepends=('python-cmake_setuptools' 'protobuf-static')
# depends=('arrow-cudf<0.16.0' 'gcc8' 'cuda' 'cmake' 'rapids-rmm' 'dlpack' 'boost-libs')
source=("${_pkgname}::git+https://github.com/rapidsai/cudf.git"
  "cudf_setup.py.patch" "nvst_CMakeLists.txt.patch")

sha256sums=('SKIP' 'SKIP' 'SKIP')

pkgver() {
    cd cudf

    local _version
    local _revision
    local _shorthash

    _version="$(git tag | sort -Vr | head -n1 | sed 's/^v//')"
    _revision="$(git rev-list v"${_version}"..HEAD --count)"
    _shorthash="$(git rev-parse --short HEAD)"

    printf '%s.r%s.g%s' "$_version" "$_revision" "$_shorthash"
}

prepare() {
  cd "${srcdir}"
  patch -p0 < nvst_CMakeLists.txt.patch
  patch -p0 < cudf_setup.py.patch
}

build() {
  cd "${srcdir}/cudf"
#   git submodule update --init --remote --recursive
  git submodule sync --recursive && git submodule update --init --recursive

  cd cpp
  mkdir -p build
  cd build
  export CC=/usr/bin/gcc-8
  export CXX=/usr/bin/g++-8
  export CUDAHOSTCXX=/usr/bin/g++-8

  #  -DCMAKE_CXX_FLAGS="-march=skylake -O3" \
  cmake .. \
    -DCMAKE_CXX_FLAGS="-march=skylake -O3" \
    -DCMAKE_BUILD_TYPE=Release \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DBUILD_SHARED_LIBS=ON \
    -DBUILD_BENCHMARKS=OFF \
    -DBUILD_LEGACY_TESTS=OFF \
    -DGPU_ARCHS=75 \
    -DUSE_NVTX=OFF \
    -DCMAKE_CXX11_ABI=ON 


  cd "${srcdir}"/cudf/cpp/build

  make -j6 nvstrings cudf VERBOSE=1

  export LD_LIBRARY_PATH=/usr/lib:/opt/cuda/lib64:/opt/cuda/extras/CUPTI/lib64:/opt/magma/lib
  export CUDA_PATH=/opt/cuda
  export CUDA_HOME=/opt/cuda

  export PATH=/opt/cuda:$PATH
  export CFLAGS='-march=skylake -mtune=native -O3 -pipe -fstack-protector -I/opt/cuda/include'
  export NVCC='/opt/cuda/bin/nvcc'
  export CUB_PATH=/usr

  # cd "${srcdir}"
  # patch -p0 < nvst_CMakeLists.txt
  # patch -p0 < cudf_setup.py.patch

  cd "${srcdir}"/cudf/python/nvstrings
  python setup.py build_ext  --build-lib=${PWD}  --library-dir="${srcdir}"/cudf/cpp/build --verbose
  cd "${srcdir}"/cudf/python/cudf
  PARALLEL_LEVEL=6 python setup.py build_ext  --inplace  --library-dir="${srcdir}"/cudf/cpp/build --verbose

  cd "${srcdir}"/cudf/python/dask_cudf
  python setup.py build_ext --inplace


}

package_rapids-cudf() {
  cd "${srcdir}"/cudf/cpp/build

  make DESTDIR="${pkgdir}" install_nvstrings
  make DESTDIR="${pkgdir}" install_cudf

  rm ${pkgdir}/usr/include/arrow/gpu/cuda_api.h
  rm ${pkgdir}/usr/include/arrow/gpu/cuda_arrow_ipc.h
  rm ${pkgdir}/usr/include/arrow/gpu/cuda_common.h
  rm ${pkgdir}/usr/include/arrow/gpu/cuda_context.h
  rm ${pkgdir}/usr/include/arrow/gpu/cuda_memory.h
  rm ${pkgdir}/usr/include/arrow/gpu/cuda_version.h

  cd "${srcdir}"/cudf/python/nvstrings
  python setup.py install --single-version-externally-managed --prefix=/usr --root="${pkgdir}" --optimize=1

  cd "${srcdir}"/cudf/python/cudf
  python setup.py install --single-version-externally-managed --prefix=/usr --root="${pkgdir}" --optimize=1

  cd "${srcdir}"/cudf/python/dask_cudf
  python setup.py install --single-version-externally-managed --prefix=/usr --root="${pkgdir}" --optimize=1

  install -Dm644 ${srcdir}/cudf/cpp/src/utilities/legacy/*.hpp ${pkgdir}/usr/include/cudf/utilities/legacy/
  install -Dm644 ${srcdir}/cudf/LICENSE ${pkgdir}/usr/share/licenses/rapids-cudf/LICENSE

}

# vim:set ts=2 sw=2 et:
