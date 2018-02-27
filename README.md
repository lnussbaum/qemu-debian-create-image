# qemu-debian-create-image

Simple script to create a [QEMU](https://www.qemu.org/)
[Debian](https://www.debian.org/) or [Ubuntu](https://www.ubuntu.com/)
Linux `.qcow2` disk image using `debootstrap` and `nbd`.

## Usage

    sudo apt-get install debootstrap qemu-utils util-linux debian-archive-keyring
    export FLAVOUR={debian|ubuntu}   # default: debian
    export ARCH={amd64|...}          # default: amd64
    export MIRROR=...                # default: http://deb.debian.org/debian
    export IMGSIZE=...               # default: 8G
    qemu-debian-create-image debian-test.qcow2 debian-test.hostname stretch

Any additional arguments will be passed through to `debootstrap`.

See [blog post by Kamil Trzcinski](https://ayufan.eu/projects/debootstrap-kvm/)
for more detail.  Note that this version of the script will also create
the initial disk image for you (of `IMGSIZE` size) so it is nearly fully
automated.

`apt-cacher-ng` can be used to reduce the download requirements by
specifying a `MIRROR` value like:

    http://localhost:3142/us.archive.ubuntu.com/ubuntu/

and with that style of `MIRROR` value [should allow running offline
providing all packages are
cached](https://askubuntu.com/questions/958795/how-do-i-use-debootstrap-with-apt-cacher-ng).

## History

*  Manual procedure designed and documented by
   [Diogo Gomes](http://diogogomes.com/about/) in a
   [blog post](http://diogogomes.com/2012/07/13/debootstrap-kvm-image/)

*  [Automated version](https://ayufan.eu/projects/debootstrap-kvm/qemu-debian-create-image)
   created by [Kamil Trzcinski](https://ayufan.eu/) and [released in a
   blog post](https://ayufan.eu/projects/debootstrap-kvm/)
   under the GPL (GPL version unstated -- assumed to be GPL 2 or later).

*  Several later modifications posted in GitHub gists by:

   *   [Pablo Lorenzzoni -- @spectra](https://github.com/spectra)
       in [gist](https://gist.github.com/spectra/10301941)

   *   [Tamás JALSOVSZKY -- @jalsot](https://github.com/jalsot) in
       [gist](https://gist.github.com/jalsot/a24aa543021889ad0c70)

   *   [Lưu Danh, Hiếu -- @ldhieu](https://github.com/ldhieu) in
       [gist](https://gist.github.com/ldhieu/716db2f79ce49b95aa18e29885c16259)

   *   [Lucas Nussbaum -- @lnussbaum](https://github.com/lnussbaum) in
       [gist](https://gist.github.com/lnussbaum/34e97071827361e344acd8529b9564d8)

   also assumed to be released under GPL 2 or later.

*  Turned into a [git
   repo](https://github.com/lnussbaum/qemu-debian-create-image)
   by [Lucas Nussbaum -- @lnussbaum](https://github.com/lnussbaum), with
   additional changes (also assumed to be released under GPL 2 or later).

*  Other modified versions of [original
   gist](https://gist.github.com/spectra/10301941) (not included in
   `git` repo, but may have useful ideas):

   *   [SS Salehi -- @salehi](https://github.com/salehi) in
       [gist](https://gist.github.com/salehi/081d61d3f80f3f681c63)

   *   [@mplx](https://github.com/mplx) in
       [gist](https://gist.github.com/mplx/dfecd55db8328a5e07842d75005333a2)

   *   [@cyrhenry](https://github.com/cyrhenry) in
       [gist](https://gist.github.com/cyrhenry/02353b9bc498d2bdb9d3dac0877e058c)

   *   [@janpekar](https://github.com/janpekar) in
       [gist](https://gist.github.com/janpekar/2e16d2a8792c52dde493dcff633eb484)
