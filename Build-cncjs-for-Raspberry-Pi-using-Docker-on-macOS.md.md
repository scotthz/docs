* Starting point
  [Faster builds on slow machines? #357](https://github.com/cncjs/cncjs/issues/357)
* Build `cncjs` for Raspberry Pi using Docker on macOS

  * [ ] `git clone https://github.com/cncjs/cncjs.git`
  * [ ] Build
    ``` bash
    cd cncjs
    npm run clean
    docker run -v $PWD:/cncjs -w /cncjs arm32v7/node:8.15.1 npm install --unsafe-perm
    ```
  * [ ] Copy to Raspberry Pi
	``` bash
	rsync -av --delete --include='dist/***' --include='node_modules/***' --exclude='*' ./ pi@raspberrypi.local:/home/pi/cncjs/
	```
	
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY3Njk4MTMzMSwtNDA4MzIxMDA5XX0=
-->