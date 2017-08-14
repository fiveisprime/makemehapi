프락시를 사용하면, 서버/서비스 간에 request를 넘겨주는 것이 가능합니다.

서버를 만들어봅시다. 커맨드 라인으로 포트 번호를 받아 설정하고 `/proxy`로 들어오는 request를 전부 `http://localhost:65535/proxy`로 넘겨줍시다.

-----------------------------------------------------------------
## 힌트

이번 과제는 `h2o2` 모듈이 필요합니다. 이 모듈은 프락시를 다룰 수 있는 hapi 플러그인입니다. `proxy` 설정을 사용하려면 이 모듈을 다음과 같이 등록해야 합니다.

```js
var H2o2 = require('h2o2');

server.register(H2o2, function (err) {
    if (err) throw err;
});
```

`proxy` 키를 사용하면 리버스 프락시 handler를 만들 수도 있습니다.

```js
handler: {
    proxy: {
        host: '127.0.0.1',
        port: 65535
    }
}
```

-----------------------------------------------------------------
참고자료: en.wikipedia.org/wiki/Proxy_server