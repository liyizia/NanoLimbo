# NanoLimbo

### 自动构建server.jar指南

1：fork本项目

2：在Actions菜单允许 `I understand my workflows, go ahead and enable them` 按钮

3：在`src/main/java/ua/nanit/limbo/NanoLimbo.java`文件里 125到142 行中添加需要的环境变量，不需要的留空，保存后Actions会自动构建

4：等待2分钟左右，在右侧的Release里下载server.jar文件


213 214行填id和cookie


mcs这个直接在王哥的代码上添加就可以了

#!/bin/bash

SERVER_ID=""
COOKIE=""

BASE_URL="https://www.mcserverhost.com"
API_URL="${BASE_URL}/api/servers/${SERVER_ID}/subscription"
REFERER="${BASE_URL}/servers/${SERVER_ID}/dashboard"

renew_server() {
    curl -s -X POST "${API_URL}" \
      -H "Cookie: ${COOKIE}" \
      -H "Accept: */*" \
      -H "Accept-Language: zh-CN,zh;q=0.9" \
      -H "Content-Length: 0" \
      -H "Origin: ${BASE_URL}" \
      -H "Referer: ${REFERER}" \
      -H "X-Requested-With: XMLHttpRequest" \
      -H "Sec-Fetch-Dest: empty" \
      -H "Sec-Fetch-Mode: cors" \
      -H "Sec-Fetch-Site: same-origin" \
      -H "User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36" >/dev/null 2>&1
}
