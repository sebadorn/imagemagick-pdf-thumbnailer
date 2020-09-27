# PDF thumbnailer for GNOME

The normal PDF thumbnailer (evince-thumbnailer) does not work well on my system. Some issues are: not being able to create a thumbnail for PDFs (because of forms?), not being able to create a thumbnail and causing a CPU 100% spike.


## Requirements

* ImageMagick (`convert -thumbnail`) to create a thumbnail from a PDF. Install with: `sudo apt install imagemagick`


## How to install

```bash
# 1. Copy the `imagemagick-pdf-thumbnailer` script to `/usr/bin/`.
sudo cp imagemagick-pdf-thumbnailer /usr/bin/
# 2. Make it executable.
sudo chmod +x /usr/bin/imagemagick-pdf-thumbnailer
# 3. Copy the `imagemagick-pdf.thumbnailer` to `/usr/share/thumbnailers/`.
sudo cp imagemagick-pdf.thumbnailer /usr/share/thumbnailers/
```

You may have to restart Nautilus first.

Then delete `~/.cache/thumbnails/fail/` so that all failed attempts to create a thumbnail are retried the next time the file is visible in the file viewer (probably Nautilus).


## How to uninstall

Delete the files:
* `/usr/share/thumbnailers/imagemagick-pdf.thumbnailer`
* `/usr/bin/imagemagick-pdf-thumbnailer`


## Resources

* https://specifications.freedesktop.org/thumbnail-spec/thumbnail-spec-latest.html
* https://tecnocode.co.uk/2013/10/21/writing-a-gnome-thumbnailer/


## License

MIT License. See LICENSE file for details.
