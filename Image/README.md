# Image

## ``PIL`` vs ``Pillow``

Pillow is the friendly PIL fork by [Alex Clark and Contributors](https://github.com/python-pillow/Pillow/graphs/contributors). PIL is the Python Imaging Library by Fredrik Lundh and Contributors.

## Installation

#####  *External Libraries*

* Many of Pillow’s features require external libraries:

  - **libjpeg** provides JPEG functionality. Pillow has been tested with libjpeg versions **6b**, **8**, **9**, and **9a** and libjpeg-turbo version **8**. Starting with Pillow 3.0.0, libjpeg is required by default, but may be disabled with the`--disable-jpeg` flag.
  - **zlib** provides access to compressed PNGsStarting with Pillow 3.0.0, zlib is required by default, but may be disabled with the`--disable-zlib` flag.
  - **libtiff** provides compressed TIFF functionalityPillow has been tested with libtiff versions **3.x** and **4.0**.
  - **libfreetype** provides type related services.
  - **littlecms** provides color managementPillow version 2.2.1 and below uses liblcms1, Pillow 2.3.0 and above uses liblcms2. Tested with **1.19** and **2.7**.
  - **libwebp** provides the WebP format. Pillow has been tested with version **0.1.3**, which does not read transparent WebP files. Versions **0.3.0** and above support transparency.
  - **tcl/tk** provides support for tkinter bitmap and photo images.
  - **openjpeg** provides JPEG 2000 functionality. Pillow has been tested with openjpeg **2.0.0** and **2.1.0**. Pillow does **not** support the earlier **1.5** series which ships with Ubuntu and Debian.

* Prerequisites are installed on **Ubuntu 12.04 LTS** or **Raspian Wheezy 7.0** with:

  ```shell
  $ sudo apt-get install libtiff4-dev libjpeg8-dev zlib1g-dev libfreetype6-dev liblcms2-dev libwebp-dev tcl8.5-dev tk8.5-dev python-tk
  ```

* Prerequisites are installed on **Ubuntu 14.04 LTS** with:

  ```shell
  $ sudo apt-get install libtiff5-dev libjpeg8-dev zlib1g-dev libfreetype6-dev liblcms2-dev libwebp-dev tcl8.6-dev tk8.6-dev python-tk
  ```

* Prerequisites are installed on **Fedora 23** with:

  ```shell
  $ sudo dnf install libtiff-devel libjpeg-devel libzip-devel freetype-devel lcms2-devel libwebp-devel tcl-devel tk-devel
  ```

* Prerequisites are installed on **Mac OS X** with:

  ```shell
  $ brew install libtiff libjpeg webp littlecms
  ```

#####  *Pillow*

```shell
$ pip install Pillow
```

## References

[1] Pillow@TT4IT, [Pillow — The friendly PIL fork](http://tt4it.com/resources/discuss/924/)