# Maintainer:   Maximilian Weiss <$(echo "bWF4QG1heHdlaXNzLmlv" | base64 -d)>
# Contributor:  D. Bohdan <http://dbohdan.com/contact/>

pkgname=s2png-git
pkgver=v0.11.1.r135
pkgrel=3

pkgdesc='stuff to PNG'
arch=('any')
url='https://github.com/dbohdan/s2png'
license=('GPLv2')
depends=('gd')
makedepends=('cargo' 'rust' 'rustfmt' 'coreutils' 'gcc' 'binutils' 'just')
provides=('s2png' 's2png-git')
conflicts=('s2png' 's2png-git')
source=('git+https://github.com/dbohdan/s2png')
sha256sums=('SKIP')

pkgver() {
    cd "$srcdir/s2png/"
    git reset --hard HEAD > /dev/null 2>&1
    echo $(git describe --tags | sed 's/-/./g' | cut -d"." -f1-3)".r"$(git rev-list --all --count)
}

build() {
    cd "$srcdir/s2png/"
    git reset --hard HEAD > /dev/null 2>&1
    cargo build --release --all-features
    mv "$srcdir/s2png/target/release/s2png" ./s2png_release_bin
    strip s2png_release_bin
}

package() {
    install -Dm755 "$srcdir/s2png/s2png_release_bin" "$pkgdir/usr/bin/s2png"
}

