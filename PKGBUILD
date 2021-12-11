# Maintainer: Jan Alexander Steffens (heftig) <heftig@archlinux.org>

pkgname=gnome-settings-daemon-hybris
pkgver=3.38.1
pkgrel=1
pkgdesc="GNOME Settings Daemon"
url="https://github.com/droidian/gnome-settings-daemon"
arch=(x86_64 aarch64)
license=(GPL)
depends=(dconf gnome-desktop gsettings-desktop-schemas libcanberra-pulse libnotify systemd-libs
         libwacom pulseaudio pulseaudio-alsa upower librsvg libgweather geocode-glib geoclue nss
         libgudev gtk3 libnm gcr)
makedepends=(xf86-input-wacom libxslt docbook-xsl python git meson usbguard)
checkdepends=(python-gobject python-dbusmock)
optdepends=('usbguard: USB protection support')
conflicts=('gnome-settings-daemon')
provides=('gnome-settings-daemon')
source=("gnome-settings-daemon-hybris::git+https://github.com/droidian/gnome-settings-daemon.git"
        "git+https://github.com/droidian/libgnome-volume-control.git")
sha256sums=('SKIP'
            'SKIP')

prepare() {
  cd $pkgbase

  git submodule init
  git submodule set-url subprojects/gvc "$srcdir/libgnome-volume-control"
  git submodule update
}

build() {
  arch-meson $pkgbase build
  meson compile -C build
}

#check() {
#  meson test -C build --print-errorlogs
#}

package() {
  DESTDIR="$pkgdir" meson install -C build
}

