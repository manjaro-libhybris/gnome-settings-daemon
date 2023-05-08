# Maintainer: Bardia Moshiri <fakeshell@bardia.tech>
# Contributor: Jan Alexander Steffens (heftig) <heftig@archlinux.org>

pkgname=gnome-settings-daemon-hybris
pkgver=43.0
pkgrel=3
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
  git checkout -b bookworm
  git checkout 9bf12fdc630aa68eddf9d38e3a1dd78c628bae87
}

build() {
  arch-meson $pkgbase build
  meson compile -C build
}

package() {
  DESTDIR="$pkgdir" meson install -C build
}
