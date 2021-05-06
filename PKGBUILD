pkgname=ntfs3-dkms
pkgver=26.0.0
pkgrel=3
pkgdesc="NTFS read-write driver GPL implementation by Paragon Software. Current version works with NTFS (including v3.1), normal/compressed/sparse files and supports journal replaying."
arch=('any')
url='https://www.paragon-software.com/home/ntfs3-driver-faq/'
license=('GPL2')
depends=('dkms')
options=('!strip')
source=(Makefile.patch
        dkms.conf
        "v${pkgver}~1.patch::https://lore.kernel.org/lkml/20210402155347.64594-2-almaz.alexandrovich@paragon-software.com/raw"
        "v${pkgver}~2.patch::https://lore.kernel.org/lkml/20210402155347.64594-3-almaz.alexandrovich@paragon-software.com/raw"
        "v${pkgver}~3.patch::https://lore.kernel.org/lkml/20210402155347.64594-4-almaz.alexandrovich@paragon-software.com/raw"
        "v${pkgver}~4.patch::https://lore.kernel.org/lkml/20210402155347.64594-5-almaz.alexandrovich@paragon-software.com/raw"
        "v${pkgver}~5.patch::https://lore.kernel.org/lkml/20210402155347.64594-6-almaz.alexandrovich@paragon-software.com/raw"
        "v${pkgver}~6.patch::https://lore.kernel.org/lkml/20210402155347.64594-7-almaz.alexandrovich@paragon-software.com/raw"
        "v${pkgver}~7.patch::https://lore.kernel.org/lkml/20210402155347.64594-8-almaz.alexandrovich@paragon-software.com/raw"
        "v${pkgver}~8.patch::https://lore.kernel.org/lkml/20210402155347.64594-9-almaz.alexandrovich@paragon-software.com/raw"
        legacy_kernel.patch)
sha512sums=('5b5b487eb66d2f74699cbd10c0c669c0dbbd87c0c8ed1d96685aa5f3eb992fdfe859f0eb7aa3a31ade9e267cf6a9a9df228a760f305ff4a2874f01cd7844bf98'
            '67147d0dc534a9bec5f1761f24ff182add0a8e79aab9c094f78263fb00c8f508e6bdd69b389a2b0d8ae3673007eaad5dc6986cff77ba9e77559d9580b40abac3'
            'b5492e4398c0155bb8f9c23a70435983579d142b8e4e8f90c6b03a67ccefd20c56a26e9cb62f74b1a8c172be300b81582e01a788b2c730f49d39cad70641d0a8'
            'a5085e27cba9e813ca4f28f77560bbec6a8a74fee813abf85cd0016af127aefd3f977c347633ea4b82efa5ea6155487a99a2bf321da0aa75fc308d5f9f56c556'
            '7cbee87a82fdac6f3258c19ec9a3045f504e53193c0bde53ee66a6032893f6d62ba2f17d03255fafb21773d4b80cd15ed7bc8d426cfdcf76ac543d8baaeaa546'
            '23b812379685bd0a6ccad609a81c674dc539a369889d28d063c063797697c55a16a1a12c9d4e597a46fd097813c262d705c6df84c1d946bd538e2f784a59ea88'
            '08874361f27bfb7f221c29ebcffb5ddb95437fbf29534d063d7a51a5b1edce0aca6a66c2f7ca5130560d044e373adf92e878cde75cb61d4612f37bc49ecc60d7'
            '480fac64807eecd2bfce5b2fd534f85b9afe09a0cecdc49f84a492de6624af83189ba8ae65a4731eb459b4de3e220e0483e878608a737fa921ff6499df4aa8fe'
            '03a286070e940f8578538d6281acf473f8e7fb2861db1bf282559008cb4228feb3f7c99a7bc3ae3b24a99af8317cca355996df3f2f046a61945de1f9140d35d8'
            'c94ca55ae72980de9515815257f22a28865cc05b6db95093caf1055c3c2e57523c21af41368896b0997933f271a8f47377993b0752560990a395eb449c35c62d'
            '374c6fa524defb5dcac093493bc7526e43ca9fe07602357fb51df4a26b02280ba4f2d764d3ba2ba2b32d5318ef466f3e0b6cbfdad1cdac0b04c31e8543114e33')


prepare() {
  mkdir -p "${pkgver}"
  cd "${pkgver}"

  for patch in "${srcdir}/v${pkgver}~"* ; do
    patch -p3 -N -i "${patch}"
  done

  patch -p0 -N -i "${srcdir}/Makefile.patch"
}

package() {
  local dest="${pkgdir}/usr/src/ntfs3-${pkgver}"
  mkdir -p "${dest}"
  cd "${dest}"
  cp -r "${srcdir}/${pkgver}/"* ./
  cp "${srcdir}/dkms.conf" ./
  mkdir -p "./patches"
  cp "${srcdir}/legacy_kernel.patch" "./patches/"
}
