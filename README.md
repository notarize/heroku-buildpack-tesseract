# heroku-buildpack-tesseract

- `libarchive13` and its dependecy `liblzo2-2` are required by tesseract but aren't installed due to them being present at build time, but not runtime (https://devcenter.heroku.com/articles/stack-packages)
- these packages are manually added to Aptfile so heroku-buildpack-apt will install them, however `liblzo2-2` is installed in location not in `LD_LIBRARY_PATH`
- this buildpack adds `.apt/lib/x86_64-linux-gnu` to `LD_LIBRARY_PATH` so `liblzo2-2` will be found
