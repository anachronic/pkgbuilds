# Maintainer: Nicolás Salas V. <anachronic@fastmail.com>
pkgname=emacs-29-git
pkgver=29.1
pkgrel=1
pkgdesc="Emacs 29 built from source"
arch=('x86_64')
url="http://git.savannah.gnu.org/cgit/emacs.git"
license=('GPL3')
depends=('alsa-lib' 'cairo' 'gnutls' 'gtk3' 'libxml2' 'libxi' 'libsm' 'xcb-util' 'libxcb' 'libjpeg-turbo' 'libpng' 'giflib' 'libwebp' 'libtiff' 'libxpm' 'jansson' 'harfbuzz' 'gpm' 'libgccjit' 'webkit2gtk' 'tree-sitter')
makedepends=()
optdepends=()
provides=('emacs')
replaces=('emacs' 'emacs-gcc-wayland-devel-bin')
source=("emacs-29::git+https://git.savannah.gnu.org/git/emacs.git#branch=emacs-29")
b2sums=('SKIP')

prepare() {
  cd "$srcdir"/emacs-29

  ./autogen.sh
}

build() {
  cd "$srcdir"/emacs-29

  ./configure \
    --prefix=/usr \
    --sysconfdir=/etc \
    --libexecdir=/usr/lib \
    --localstatedir=/var \
    --mandir=/usr/share/man \
    --with-gameuser=:games \
    --with-sound=alsa \
    --with-modules \
    --with-xinput2 \
    --with-xwidgets \
    --with-native-compilation \
    --with-pgtk \
    --with-json \
    --with-mailutils \
    --with-tree-sitter \
    --without-compress-install \
    --without-gconf \
    --without-libotf \
    --without-m17n-flt \
    --without-xaw3d \
    --enable-autodepend \
    --enable-link-time-optimization \
    "--program-transform-name=s/\([ec]tags\)/\1.emacs/"

  make
}

check() {
  cd "$srcdir"/emacs-29

  make check
}

package() {
  cd "$srcdir"/emacs-29

  make DESTDIR="$pkgdir/" install
}

# vim:set ts=2 sw=2 et:
