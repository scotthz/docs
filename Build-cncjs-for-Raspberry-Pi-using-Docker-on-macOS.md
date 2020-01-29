## [Faster builds on slow machines? #357](https://github.com/cncjs/cncjs/issues/357)

* Build `cncjs` for Raspberry Pi using Docker on macOS
  These are the fundamental steps. Not optimized, e.g. to build everything but `serialport` natively on macOS, and build just `serialport` in an `arm32v7` container (or on the RPi).

  * [ ] Clone the repo
	``` bash
	git clone https://github.com/cncjs/cncjs.git
	```
  * [ ] Build everything using Docker
    ``` bash
    cd cncjs
    npm run clean
    docker run -v $PWD:/cncjs -w /cncjs arm32v7/node:8.15.1 npm install --unsafe-perm
    ```
  * [ ] Copy to Raspberry Pi
	``` bash
	rsync -av --delete --include='dist/***' --include='node_modules/***' --exclude='*' ./ pi@raspberrypi.local:/home/pi/cncjs/
	```

## [Comment cited in #357 regarding build optimization](https://github.com/cncjs/cncjs/issues/437#issuecomment-479995117)
* On Pi:
 * [ ] npm run clean npm run prebuild-prod npm run build-prod-server
  * [ ] create symlinks named "cncjs", and "cncjs-server" in
       /usr/local/bin, referring to /bin/cncjs.
* On PC or Mac:
  * [ ] npm install
  * [ ] copy dist/cnc/web/* to the Pi (at /dist/cnc/web)

The procedure above avoids running eslint, stylint, and test on the Pi, which are time-consuming and redundant.
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc0NTQ2MjY3OCwyMTI4OTUzMzM3LC01MD
UyNzE4NDAsMTMwMjg3NzY0NiwtNjc2OTgxMzMxXX0=
-->