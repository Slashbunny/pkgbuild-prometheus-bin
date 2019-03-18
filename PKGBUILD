# Maintainer: Slashbunny <demodevil5[at]yahoo>

pkgname=prometheus-bin
pkgver=2.8.0
pkgrel=1
pkgdesc="An open-source service monitoring system and time series database (binary, not built from source)"
arch=('x86_64' 'arm' 'armv6h' 'armv7h')
url="http://prometheus.io"
license=('Apache')
depends=()
makedepends=()
provides=('prometheus')
conflicts=('prometheus' 'prometheus-git')
install='prometheus.install'
backup=('etc/prometheus/prometheus.yml')
source=('prometheus.service')
source_x86_64=("https://github.com/prometheus/prometheus/releases/download/v${pkgver}/prometheus-${pkgver}.linux-amd64.tar.gz" )
source_arm=("https://github.com/prometheus/prometheus/releases/download/v${pkgver}/prometheus-${pkgver}.linux-armv5.tar.gz" )
source_armv6h=("https://github.com/prometheus/prometheus/releases/download/v${pkgver}/prometheus-${pkgver}.linux-armv6.tar.gz" )
source_armv7h=("https://github.com/prometheus/prometheus/releases/download/v${pkgver}/prometheus-${pkgver}.linux-armv7.tar.gz" )
sha256sums=('0c99b68b282d72feb9fd2bc0b190554659a59dada74ec92ca2b2f48016a9b805')
sha256sums_x86_64=('b8649bc6317af31fd3c998648ef0aa8bc0099fece24952fd1aca1bff665e9216')
sha256sums_arm=('e8851146541bd78edf3dfdd3d4c352fa2c05b7a3dfbce58b84ef970b4e6c904d')
sha256sums_armv6h=('a04f36612368b6fe2dfe0f96c50e8f7bf2cc231e6d724d053911e050bab4901a')
sha256sums_armv7h=('a5655688286eb72244489bad2b27eb399158cf35dec556e7e1eeb96c66dec311')

package() {
    case "$CARCH" in
        'x86_64') ARCH='amd64';;
        'arm') ARCH='armv5';;
        'armv6h') ARCH='armv6';;
        'armv7h') ARCH='armv7';;
        'aarch64') ARCH='arm64';;
    esac
    cd "${srcdir}/prometheus-${pkgver}.linux-${ARCH}"

    # Install Binaries
    install -D -m0755 prometheus \
        "${pkgdir}/usr/bin/prometheus"

    install -D -m0755 promtool \
        "${pkgdir}/usr/bin/promtool"

    # Install Config File
    install -D -m0755 prometheus.yml \
        "${pkgdir}/etc/prometheus/prometheus.yml"

    # Install SystemD Service File
    install -D -m0644 "${srcdir}/prometheus.service" \
        "${pkgdir}/usr/lib/systemd/system/prometheus.service"

    # Install Console files
    cp -R consoles/ \
        "${pkgdir}/etc/prometheus/consoles"

    cp -R console_libraries/ \
        "${pkgdir}/etc/prometheus/console_libraries"
}
