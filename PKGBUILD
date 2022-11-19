#!/bin/bash

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# @ToDo:
# @ToDo: Add files: User documentation
# @ToDo: Add files: Tooling
# @FixMe: Namcap warnings and errors

# @Maintainer: Ross Clark <https://github.com/Archiv8/prettier/discussions>
# @Contributor: Ross Clark <https://github.com/Archiv8/prettier/discussions>

pkgname="prettier"
pkgver=2.7.0
pkgrel=1
pkgdesc="An opinionated code formatter for JS, JSON, CSS, YAML and much more"
arch=("any")
url="https://prettier.io/"
license=("MIT")
depends=("nodejs")
makedepends=("yarn")
source=("https://github.com/$pkgname/$pkgname/archive/$pkgver/$pkgname-$pkgver.tar.gz")
sha512sums=('86c6af269a5d6e15924d8d718ceb534542549ab94d66deade740d1465fa89d79')

prepare() {
    cd "$pkgname-$pkgver"
    yarn --frozen-lockfile
}

build() {
    cd "$pkgname-$pkgver"
    yarn build
}

package() {
    cd "$pkgname-$pkgver"
    install -d "$pkgdir/usr/"{bin,"lib/$pkgname","share/licenses/$pkgname"}
    cp -a dist/* "$pkgdir/usr/lib/$pkgname"
    ln -s "/usr/lib/$pkgname/bin-$pkgname.js" "$pkgdir/usr/bin/$pkgname"
    ln -s "/usr/lib/$pkgname/LICENSE" "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
