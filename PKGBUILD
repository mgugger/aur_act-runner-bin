# Maintainer: Manuel Gugger <mdgdot[at]tutanota[dot]com>

pkgname=act-runner-bin
pkgver=0.2.10
pkgrel=1
pkgdesc="A runner for Gitea Actions based on GitHub's Act"
arch=('x86_64' 'aarch64')
url="https://gitea.com/gitea/act_runner"
license=('MIT')
optdepends=('docker: for running containers')
provides=('act_runner')
conflicts=('act_runner')

source_x86_64=("https://gitea.com/gitea/act_runner/releases/download/v${pkgver}/act_runner-${pkgver}-linux-amd64.xz")
source_aarch64=("https://gitea.com/gitea/act_runner/releases/download/v${pkgver}/act_runner-${pkgver}-linux-arm64.xz")

sha256sums_x86_64=('8dc95565f5d1c8d8b3cf717ce8fde72a2fae7de3c284447962e6d35850c0eeea')
sha256sums_aarch64=('8c79b533b52d78c8bd241f239442ef271553e2b263f9e457aee662f57fec7017')

source=('act_runner.service'
        'act_runner.yaml'
        'act_runner.sysusers'
        'act_runner.tmpfiles')
sha256sums=('245f610f82bcb5140d9040f997332186c03a575b98cce603e39f1f0300773e3e'
            'ff4cc6b9b604da75254bbdcb550103d08b749a6986671c8fd69e1dbda2f230a6'
            '5ba0c3203cf42cb1e2b58840726b53e481fe980b8cfc24d14fba057d31d676ca'
            '5f8944df92d0e5278e3a29795dfcd8bcd340bea37075627d4f9d3303cdb58607')

package() {
    if [[ $CARCH == "x86_64" ]]; then
        mv act_runner-${pkgver}-linux-amd64 act_runner
    elif [[ $CARCH == "aarch64" ]]; then
        mv act_runner-${pkgver}-linux-arm64 act_runner
    fi
    install -Dm755 act_runner -t "$pkgdir/usr/bin"
    install -Dm644 "$srcdir/act_runner.service" "$pkgdir/usr/lib/systemd/system/act_runner.service"
    install -Dm644 "$srcdir/act_runner.yaml" "$pkgdir/etc/act_runner/act_runner.yaml"
    install -Dm644 "$srcdir/act_runner.sysusers" "$pkgdir/usr/lib/sysusers.d/act_runner.conf"
    install -Dm644 "$srcdir/act_runner.tmpfiles" "$pkgdir/usr/lib/tmpfiles.d/act_runner.conf"
}
