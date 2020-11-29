# nuxt-shopsys

### Build Setup

```bash
# install dependencies
$ yarn install

# serve with hot reload at localhost:3000
$ yarn dev

# build for production and launch server
$ yarn build
$ yarn start

# generate static project
$ yarn generate
```


### test
+ 测试数据
    
    [db.json](https://github.com/quan930/nuxt-shopsys/blob/main/test/db.json)
    
    运行
    ```bash
    # run json-server
    $ json-server -W -p 4000 db.json 
    ```
  
+ SSR(服务端渲染)

    [Dockerfile](https://github.com/quan930/nuxt-shopsys/blob/main/test/ssr/Dockerfile)
    ```shell script
    # build
    $ docker build -t nuxtshop .
    # run
    $ docker run -d -p 3000:3000 nuxtshop
    ```

+ SSG(静态网站渲染)
    
    [Dockerfile](https://github.com/quan930/nuxt-shopsys/blob/main/test/ssg/Dockerfile)
    ```shell script
    # build
    $ docker build -t nuxtshopssg .
    # run
    $ docker run -d -p 80:80 nuxtshopssg
    ```
