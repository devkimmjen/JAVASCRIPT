# What is Deno ?

Deno is simple, modern and sevure runtime for javaScript and TypeScript that uses V8 and is built in Rust

Deno는 Javascript와 Typescript를 실행하기 위한 새로운 Command-line Runtime입니다.

Steps of Explanation for DENO

1. Deno의 기초적인 지식
2. Deno를 설치 한 후 하나하나 체험해보기
3. oak이란 프레임 워크와 함께 간단한 API 서버 만들기

###  디노는 노드js와 80% 비슷하다 


# Deno Basic


### 기반 기술
1. V8 Javascript Runtume
2. Rust(replace C++)
3. Tokio (event loop)
4. TypeScript

# Deno important Features

Deno는 node.js에서 실수한 부분을 개선하기 위한 새로운 특징들을 갖고 있다.

1. 유일하게 ES Modules 시스템 사용
- To connect 3rd party code to our app, Use Http URL
(ex import { serve } from "http://deno.land/std/http/server.ts";)
- By using this URL, download and update the resource on it own, so Deno becomes package manager itself, so good bye npm
- Deno will cache our dependencies to hard drive in first run
=> so it is available offline
2. Enhanced Security
- It requires permission by default when accessing to Disk, Network, or the things that ask for the permission

Options :
        
        --allow-read        Allow file system read access
        --allow-write       Allow file system write access
        --allow-net         Allow network access
        --allow-env         Allow environment access
        --allow-run         Allow running subprocesses
    -A, --allow-all         Allow all permissions
3. Built-in TypeScript
- We don't have to manually configure our environment to work in TypeScript.
- Already built-in so we can just use it

4. Top level await is supported
    
    For Detailed info : https://gituhb.com/tc39/proposal-top-level-await
Running a program with Top level await

:  

    import { serve } from "https://deno.land/std@0.50.0/http/server.ts
    const s = serve({ port : 8000 });
    console.log("http://locathost:8000/");
    for await ( const req of s ) {
        req.respond({ body: "Hello World\n });
    }

W/0 Top level await

    (async () => {
        for await (const req of s) {
            req.respond({ body: "Hello Worln });
        }
    })();

5. Brower compatible
- The subset of Deno programs which are written completely in JavaScript and do not use
the global Deno namespace ( or feature test for it), ought to also be able to be run in a modern web browser without change.

- When using fetch in Node.js, you need to import a library to do that like this.
but in the browser you can just use fetch.

- In deno, you can just fetch resources with fetch() w/o importing the library

- When importing module, no more require('module')!!!
=> use import/export syntax which is browser based way from ES6

예) 