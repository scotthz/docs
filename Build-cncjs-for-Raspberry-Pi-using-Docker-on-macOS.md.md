* Build `cncjs` for Raspberry Pi using Docker on macOS

  * [ ] `git clone https://github.com/cncjs/cncjs.git`
  * [ ] Build

    ``` bash
    cd cncjs
    npm run clean
    docker run -v $PWD:/cncjs -w /cncjs arm32v7/node:8.15.1 npm install --unsafe-perm
    ```

  * [ ] Copy to Raspberry Pi


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA1NDM5ODQzN119
-->