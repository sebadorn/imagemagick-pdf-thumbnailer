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

It is very likely you already have a PDF thumbnailer in `/usr/share/thumbnailers/`, e.g. `evince.thumbnailer`. Edit its file and remove `application/pdf;` from its list of handled mime types.

You may have to restart Nautilus first.

Then delete `~/.cache/thumbnails/fail/` so that all failed attempts to create a thumbnail are retried the next time the file is visible in the file viewer (probably Nautilus).


## How to uninstall

Delete the files:
* `/usr/share/thumbnailers/imagemagick-pdf.thumbnailer`
* `/usr/bin/imagemagick-pdf-thumbnailer`

Restore the evince thumbnailer by doing the opposite from the step above – add back `application/pdf` to the mime type list.

Probably restart Nautilus.


## Resources

* https://specifications.freedesktop.org/thumbnail-spec/thumbnail-spec-latest.html
* https://tecnocode.co.uk/2013/10/21/writing-a-gnome-thumbnailer/


## License

MIT License. See LICENSE file for details.
