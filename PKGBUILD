#Maintainer: Juanma Hernandez <juanmah@gmail.com>

pkgname=gnome-shell-extension-gnome2-notifications-git
pkgver=20120507
pkgrel=1
pkgdesc="gnome-shell-gnome2-notifications is YAGSE (Yet Another GNOME Shell extension) that tries to provide an "old-skool" gnome2 way of showing application's tray icons."
arch=('any')
url="https://github.com/rcmorano/gnome-shell-gnome2-notifications"
license=('GPL2')
depends=('gnome-shell')
optdepends=('gnome-tweak-tool: A tool to customize advanced GNOME 3 options.')
makedepends=('git' 'gnome-common' 'intltool')
install='gschemas.install'

_gitroot="https://github.com/rcmorano/gnome-shell-gnome2-notifications"
_gitname="gnome-shell-gnome2-notifications"

build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone $_gitroot $_gitname
  fi

  msg "GIT checkout done or server timeout"
}

_extpath="$pkgdir/usr/share/gnome-shell/extensions"
_extname="gnome-shell-classic-systray@emergya.com"

package() {
  mkdir -p "$_extpath/$_extname"
  cd "$srcdir/$_gitname/$_extname"
  cp extension.js metadata.json "$_extpath/$_extname"
}
