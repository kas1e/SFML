# SFML 2.5.1
WIP port of SFML 2.5.1 to AmigaOS4.

Currently only System, Audio and Network modules are working. Window and Graphics in progress.

To build you need:

1. latest cross-compiler (GCC 11.3.0 currently): https://github.com/sba1/adtools
2. latest SDK (53.34 currently): https://hyperion-entertainment.com/index.php/downloads 
3. latest Andrea's clib2 (beta08 currently): https://github.com/afxgroup/clib2 (with rebuilded libstdc++ as well)
4. 3d party libs compiled for clib2 : libopenal, libvorbis/libvorbisfile/libvorbisenc/libogg & libflac


Download repo and:

```
cd repo
mkdir build
cd build

cmake \
-DCMAKE_SYSTEM_NAME=Generic \
-DCMAKE_SYSTEM_VERSION=1 \
-DCMAKE_BUILD_TYPE=Release \
-DBUILD_SHARED_LIBS=NO \
-DSFML_BUILD_AUDIO=YES \
-DSFML_BUILD_NETWORK=YES \
-DSFML_BUILD_GRAPHICS=NO \
-DSFML_BUILD_WINDOW=NO \
-DSFML_MISC_INSTALL_PREFIX="./" \
-DCMAKE_C_FLAGS="-mcrt=clib2" \
-DCMAKE_CXX_FLAGS="-mcrt=clib2" \
-DCMAKE_C_COMPILER="/usr/local/amiga/bin/ppc-amigaos-gcc" \
-DCMAKE_CXX_COMPILER="/usr/local/amiga/bin/ppc-amigaos-g++" \
-DCMAKE_LINKER="/usr/local/amiga/bin/ppc-amigaos-ld" \
-DCMAKE_AR="/usr/local/amiga/bin/ppc-amigaos-ar" \
-DCMAKE_RANLIB="/usr/local/amiga/bin/ppc-amigaos-ranlib" \
-DCMAKE_FIND_ROOT_PATH="/usr/local/amiga/ppc-amigaos/" \
-DOPENAL_INCLUDE_DIR="/usr/local/amiga/ppc-amigaos/SDK/Local/clib2/include/AL" \
-DOPENAL_LIBRARY="/usr/local/amiga/ppc-amigaos/SDK/Local/clib2/lib/libopenal.a" \
-DVORBIS_INCLUDE_DIR="/usr/local/amiga/ppc-amigaos/SDK/Local/common/include/vorbis" \
-DVORBIS_LIBRARY="/usr/local/amiga/ppc-amigaos/SDK/Local/clib2/lib/libvorbis.a" \
-DVORBISFILE_LIBRARY="/usr/local/amiga/ppc-amigaos/SDK/Local/clib2/lib/libvorbisfile.a" \
-DOGG_INCLUDE_DIR="/usr/local/amiga/ppc-amigaos/SDK/Local/common/include/ogg" \
-DOGG_LIBRARY="/usr/local/amiga/ppc-amigaos/SDK/Local/clib2/lib/libogg.a" \
-DVORBISENC_LIBRARY="/usr/local/amiga/ppc-amigaos/SDK/Local/clib2/lib/libvorbisenc.a" \
-DFLAC_INCLUDE_DIR="/usr/local/amiga/ppc-amigaos/SDK/Local/common/include/flac" \
-DFLAC_LIBRARY="/usr/local/amiga/ppc-amigaos/SDK/Local/clib2/lib/flac.a" \
-Wno-dev \
..

make -j4
```
