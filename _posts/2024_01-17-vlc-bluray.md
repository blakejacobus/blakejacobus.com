# Integrating VLC with MakeMKV

## Problem

Unable to read Bluray disc with AACS protection on VLC Media Player

## Windows

1. Open MakeMKV
2. Select "Preferences"
3. Select "Integration"
4. Select "VLC"
5. Open VLC, select "Media" and "Open Disc..."
6. Select the source drive that the disc is running on.

## Linux

### Error

- Cannot add VLC integration to MakeMKV
- Missing `libmmbd`

### Solution

1. Check program installation locations.

``` bash
blake@malibal ~ $ which makemkv
/snap/bin/makemkv
blake@malibal ~ $ which vlc
/usr/bin/vlc
```

1. Try installing programs in the same path.
1. [Compile and install MakeMKV](https://forum.makemkv.com/forum/viewtopic.php?f=3&t=224)

``` bash
blake@malibal ~/Downloads/makemkv-bin-1.17.6 $ which makemkv
/usr/bin/makemkv
blake@malibal ~/Downloads/makemkv-bin-1.17.6 $ which vlc
/usr/bin/vlc
```

### Reference

[Ubuntu Desktop Install and Integration with VLC](https://forum.makemkv.com/forum/viewtopic.php?t=22845)
[Ubuntu configuration](https://www.omgubuntu.co.uk/2022/08/watch-bluray-discs-in-vlc-on-ubuntu-with-makemkv)
[LibMMBD - MakeMKV decryption API](https://www.makemkv.com/libmmbd/)
