Lightweight, sandboxed firefox using [xpra](http://xpra.org/) for
remote display. Xpra is "the screen for X". It is an extremely efficient
remote display protocol allowing rooming.

This images smoothly played a fullscreen 1080p Youtube video from 
[Sailabove's](https://labs.runabove.com/docker) cloud over a DSL
connection.

While this is curently more a Proof of Concept than a real application
it shows the potential of both xpra and Docker when it comes to SaaS and
VDI.

Usage
-----

To run this image, pull the repository and run the image:

```bash
docker pull yadutaf/firefox.js
docker run -t --rm -p 8080:8080 yadutaf/firefox
```

Alternatively, you may rebuild the image from sources:

```bash
git clone https://github.com/yadutaf/docker-firefox-xpra.git
cd docker-firefox-xpra
docker build -t firefox .
docker run -t --rm -p 8080:8080 p 10000:10000 firefox
```

Then either visit http://localhost:8080/ or install xpra and use it:

```bash
# Install
echo "deb http://www.xpra.org/dists $(lsb_release -cs) main" | sudo tee -a /etc/apt/sources.list
curl https://www.xpra.org/gpg.asc | sudo apt-key add -
sudo apt-get update && apt-get install xpra

# Run
xpra attach tcp:localhost:10000
```

Enjoy !

License
-------

MIT


