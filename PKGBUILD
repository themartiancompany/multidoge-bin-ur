# SPDX-License-Identifier: AGPL-3.0

#    ----------------------------------------------------------------------
#    Copyright © 2024, 2025  Pellegrino Prevete
#
#    All rights reserved
#    ----------------------------------------------------------------------
#
#    This program is free software: you can redistribute it and/or modify
#    it under the terms of the GNU Affero General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    This program is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU Affero General Public License for more details.
#
#    You should have received a copy of the GNU Affero General Public License
#    along with this program.  If not, see <https://www.gnu.org/licenses/>.

# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Truocolo <truocolo@0x6E5163fC4BFc1511Dbe06bB605cc14a3e462332b>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: Pellegrino Prevete (dvorak) <dvorak@0x87003Bd6C074C713783df04f36517451fF34CBEf>
# Original maintainer Alex Talker < Alextalker at openmailbox dot com >
# Support Maintainer Filip Brcic < brcha at gna dot org >
# Contributor bitwave < aur [at] oomlu [d0t] de >
# Alex say thanks to Filip about support this package while he was away from Arch.
# Contributor: Pellegrino Prevete (dvorak) <pellegrinoprevete@gmail.com>
# Contributor: Truocolo (truocolo@aol.com) 

_pkg="multidoge"
pkgname="${_pkg}-bin"
pkgver=0.1.7
pkgrel=1
pkgdesc="Java-based DogeCoin client"
arch=(
  'i686'
  'x86_64'
  'arm'
)
url="http://${_pkg}.org"
license=(
  'GPL'
)
install=${_pkg}.install
depends=(
  'bash'
  'java-runtime'
  'jre8-openjdk'
)
provides=(
  "${_pkg}=${pkgver}"
)
conflicts=(
  "${_pkg}"
)
_gh="github.com"
_ns="langerhans"
_url="https://${_gh}/${_ns}/${_pkg}"
source=(
  "${_url}/releases/download/v${pkgver}/${_pkg}-${pkgver}-linux.jar"
  "${_pkg}"
  install.properties
  "${_pkg}.desktop"
  dogecoin.png
)
md5sums=(
  'e69a81b1e86c7aa72d3b36d0d5fb4218'
  '937bebe7bdda35b2089415fbe0c79926'
  'ecb77c4f6857760ac0bb278b2771ee1c'
  'd66bfe1d4f5856dccc93e7e63d3f9f4d'
  'de465c84e7b5169b6b2aa77d4948adb6'
)
noextract=(
  "${_pkg}-${pkgver}-linux.jar"
)
package() {
  msg \
    "Install package..."
  cd \
    "${srcdir}"
  # bugfix causing the izpack
  # installer to return an error
  java \
    -jar \
    "${_pkg}-${pkgver}-linux.jar" \
    -options \
      install.properties || \
    true
  
  install \
    -Dm 644 \
    "tmp-install/${_pkg}-exe.jar" \
    "${pkgdir}/usr/share/java/${_pkg}/${_pkg}.jar"
  install \
    -Dm 755 \
    "${_pkg}" \
    "${pkgdir}/usr/bin/${_pkg}"
  install \
    -Dm 644 \
    "${_pkg}.desktop" \
    "${pkgdir}/usr/share/applications/${_pkg}.desktop"
  install \
    -Dm 644 \
    "dogecoin.png" \
    "${pkgdir}/usr/share/pixmaps/${_pkg}.png"
  msg \
    "Done!"
}
