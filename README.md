# Go Minify Docker Image

Docker image for executing the go library [tdewolff/minify](https://github.com/tdewolff/minify)

[![ImageLayers](https://imagelayers.io/badge/mysocialobservations/docker-tdewolff-minify:latest.svg)](https://imagelayers.io/?images=mysocialobservations/docker-tdewolff-minify:latest 'Get your own badge on imagelayers.io')

For documentation on the go command line tools visit
[cmd](https://github.com/tdewolff/minify/tree/master/cmd/minify) 

## Example Commands

The following are examples to minify specific file types.

The first example will look in the `public` directory for any files ending in
`.js` of type `text/javascript` and places the minified files in the same
directory, overwriting the original files. 

```bash
$ minify --recursive --verbose --match=\.*.js$ --type=js --output public/ public/

INFO: use mimetype text/javascript
INFO: expanding directory public/ recursively
INFO: minify 4 input files
INFO: minify to output directory public/
INFO: (  978.8µs, 2.6 kB,  96.7%, 2.8 MB/s) - public/js/ie/html5shiv.min.js
INFO: (1.391021ms, 4.6 kB,  99.8%, 3.3 MB/s) - public/js/ie/respond.min.js
INFO: (10.964597ms,  87 kB, 100.0%, 7.9 MB/s) - public/js/jquery.min.js
INFO: (2.168347ms, 9.0 kB,  99.4%, 4.2 MB/s) - public/js/skel.min.js
INFO: 15.501965ms total
```

The second example is similar to the first example but looking for files ending
in `.css` of type `text/css`

```bash
$ minify --recursive --verbose --match=\.*.css$ --type=css --output public/ public

INFO: use mimetype text/css
INFO: expanding directory public/ recursively
INFO: minify 4 input files
INFO: minify to output directory public/
INFO: (6.467248ms,  31 kB,  99.9%, 4.8 MB/s) - public/css/font-awesome.min.css
INFO: (1.581092ms, 3.0 kB,  66.4%, 2.8 MB/s) - public/css/google-font.css
INFO: (1.51752ms,  569 B,  58.1%, 645 kB/s) - public/css/ie8.css
INFO: (1.441086ms, 1.0 kB,  63.5%, 1.1 MB/s) - public/css/ie9.css
INFO: 11.006946ms total
```

## Example Docker Runs

To run the container and minification at once execute similar to the following:
```bash
docker run -v $(pwd):/src mysocialobservations/tdewolff-minify /bin/sh -c 'cd /src; minify --recursive --verbose --match=\.*.js$ --type=js --output public/ public/'
```

```bash
docker run -v $(pwd):/src mysocialobservations/tdewolff-minify /bin/sh -c 'cd /src; minify --recursive --verbose --match=\.*.css$ --type=css --output public/ public/'
```

This will move to the mounted directory from the host, execute the minification
on the files and exit the container.

# Licence

MIT.
