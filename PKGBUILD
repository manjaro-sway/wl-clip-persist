# Maintainer: maple
pkgname=wl-clip-persist
pkgver=0.4.0
pkgrel=1
pkgdesc="Keep Wayland clipboard even after programs close"
arch=('any')
url="https://github.com/Linus789/wl-clip-persist"
license=('MIT')
provides=('wl-clip-persist')
conflicts=('wl-clip-persist')
depends=('wayland')
makedepends=('git' 'cargo' 'wayland-protocols')
source=("$pkgname::git+https://github.com/Linus789/wl-clip-persist.git#commit=6ba11a2aa295d780f0b2e8f005cf176601d153b0")
sha256sums=('SKIP')

prepare() {
  cd "$pkgname"
  export RUSTUP_TOOLCHAIN=stable
  cargo fetch --locked --target "$CARCH-unknown-linux-gnu"
}

build() {
  cd "$pkgname"
  export RUSTUP_TOOLCHAIN=stable
  export CARGO_TARGET_DIR=target
  export RUSTFLAGS="--remap-path-prefix=$HOME=/home --remap-path-prefix=$PWD=/src"
  cargo build --frozen --release --all-features
}

package() {
  cd "$pkgname"
  install -Dm755 "target/release/wl-clip-persist" -t "$pkgdir/usr/bin"
  install -Dm644 LICENSE -t "$pkgdir/usr/share/licenses/wl-clip-persist"
}
