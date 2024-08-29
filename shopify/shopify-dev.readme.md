1. cli解决墙内firewall问题（原因： node fetch不走全局代理）： @shopify/cli下 全局安装 https-proxy-agent ，修改C:\Users\esr-administrator\AppData\Roaming\nvm\v20.9.0\node_modules\@shopify\cli\dist\chunk-xxx.js中
	const proxy_url = "http://127.0.0.1:10809";
  const agent = new HttpsProxyAgent(proxy_url);
  return runWithTimer("cmd_all_timing_network_ms")(
    () => debugLogResponseInfo({ url: url2.toString(), request: fetch(url2, {...init, agent}) })
    // () => debugLogResponseInfo({ url: url2.toString(), request: fetch(url2, init) })
  );

  还有一处graphql-client代理：
  E:\www\node-dev\p-options\node_modules\@shopify\admin-api-client\dist\graphql-client\dist\graphql-client\http-fetch.js
  var { HttpsProxyAgent } = require("https-proxy-agent");

  const proxy_url = "http://127.0.0.1:10809";
  const agent = new HttpsProxyAgent(proxy_url);
  requestParams[1].agent = agent;
  response = await customFetchApi(...requestParams);

 2. cli解决墙内firewall问题(ruby): 
 	设置系统终端代理或者全局代理（需要终端走代理）

 3. 自定义数据可以存到metafields 和 metaobject中，这样可以做到服务器端渲染

 4. 
