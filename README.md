**imgopt** is a JPG & PNG image optimization tool 

**Dependencies:**

- [oxipng](https://github.com/shssoichiro/oxipng) - multithreaded lossless PNG compression
- [jpegtran](https://linux.die.net/man/1/jpegtran) - lossless transformation of JPEG files (single thread)

**Features:** 

- Can be run as cronjob each time optimizing only newely added images
- Shows progress bar

**Install:**

    composer global require orange35/imgopt:dev-master
    
**Usage:**

**Example #1:** Magento 1. Run from console:
 
    $ cd ~/public_html
    $ imgopt -s cache -l var/log/imgopt.log media
    Progress: 17% [344/1943] Elapsed: 00:00:06 Left: 00:00:27 Total: 00:00:33

where:

- **media** - is a root images directory
- **-l var/log/imgopt.log** - write logs (there might be some errors from oxipng & jpegrtan)
- **-s cache** - means find images in subfolders named "cache" instead of the whole "media" folder

**Example #2:** Magento 1. Cron Job:

    0 7 * * * $HOME/.composer/vendor/bin/imgopt -s cache -l $HOME/public_html/var/log/imgopt.log $HOME/public_html/media
