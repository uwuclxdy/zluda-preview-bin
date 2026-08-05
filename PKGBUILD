# Maintainer: uwuclxdy <uwuclxdy@pm.me>

pkgname=zluda-preview-bin
pkgver=7.preview.5
pkgrel=1
pkgdesc='CUDA on AMD GPUs (pre-release ZLUDA binary).'
arch=('x86_64')
url='https://github.com/vosen/ZLUDA'
license=('Apache-2.0 OR MIT')
depends=('gcc-libs' 'glibc' 'hip-runtime-amd' 'hipblaslt' 'miopen-hip' 'rocblas' 'rocm-smi-lib')
provides=('zluda')
conflicts=('zluda' 'zluda-git' 'nvidia-utils')
options=(!strip !debug)

_tag=v7-preview.5
_commit=9238e8e3

source=(
    "zluda-linux-${_commit}.tar.gz::https://github.com/vosen/ZLUDA/releases/download/${_tag}/zluda-linux-${_commit}.tar.gz"
    "LICENSE-MIT::https://raw.githubusercontent.com/vosen/ZLUDA/${_tag}/LICENSE-MIT"
)
sha256sums=('00257f3f7236c0074d085ab201c65b66cd614ab469a6c29071f8410c4ebfc84f'
            '23f18e03dc49df91622fe2a76176497404e46ced8a715d9d2b67a7446571cca3')

package() {
    install -d -m755 "${pkgdir}/usr/lib"
    cp -dr --no-preserve=ownership zluda/lib*.so* zluda/zluda_ld "${pkgdir}/usr/lib/"

    install -dm755 "${pkgdir}/usr/lib/zluda"
    cp -dr --no-preserve=ownership zluda/trace zluda/trace_nvidia "${pkgdir}/usr/lib/zluda/"

    install -Dm755 zluda/zluda_ld         "${pkgdir}/usr/bin/zluda_ld"
    install -Dm755 zluda/ptxas            "${pkgdir}/usr/bin/ptxas"
    install -Dm755 zluda/zluda_precompile "${pkgdir}/usr/bin/zluda_precompile"

    install -Dm644 LICENSE-MIT -t "${pkgdir}/usr/share/licenses/${pkgname}/"
}
