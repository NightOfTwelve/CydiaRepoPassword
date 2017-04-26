# Cydia Repo Password

Password protected repo script

# Setup

* Make a regular APT repo.
* Edit your nginx config (usually in `/etc/nginx/nginx.conf`) add this to the main server block:
```
# Repo password
autoindex off;
rewrite ^/secretrepo/.+\.deb$ /secretrepo/main.php?request=$request_filename;
```

where `secretrepo` is the directory under the website directory (e.g. if your repo is at `https://goeo.pink/wowsupersecretrepo` make it `/wowsupersecretrepo/`).

* Edit `config.php`, what you should do are commented.
* Edit your `Packages` file, add `Depiction: https://link-to-your-re.po/depiction.php` to every package. If your package already has a depiction, make it `https://link-to-your-re.po/depiction.php?iframe=<olddepiction>`.
* Move all the files to the repo directory.
* Create an `auth` directory at the root of your repo.
* Make whoever runs php able to write to auth, you can usually 
`chown $(whoami):webserver; chmod u+rwx,g+rwx,o+rx-w`.

# License
```
This is free and unencumbered software released into the public domain.

Anyone is free to copy, modify, publish, use, compile, sell, or
distribute this software, either in source code form or as a compiled
binary, for any purpose, commercial or non-commercial, and by any
means.

In jurisdictions that recognize copyright laws, the author or authors
of this software dedicate any and all copyright interest in the
software to the public domain. We make this dedication for the benefit
of the public at large and to the detriment of our heirs and
successors. We intend this dedication to be an overt act of
relinquishment in perpetuity of all present and future rights to this
software under copyright law.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND,
EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF
MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT.
IN NO EVENT SHALL THE AUTHORS BE LIABLE FOR ANY CLAIM, DAMAGES OR
OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE,
ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR
OTHER DEALINGS IN THE SOFTWARE.

For more information, please refer to <http://unlicense.org>
```
