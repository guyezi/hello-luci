### 路由器端API：
0. 获取csrfToken（用于POST请求）
   ```
    GET /cgi-bin/luci/admin/store/token


    {"token":"xxx"}
   ```
1. 已安装软件列表
   ```
    GET /cgi-bin/luci/admin/store/installed


    [
       {
        "description": "DDNS.TO内网穿透",
        "tags": [
          "net",
          "tool"
        ],
        "entry": "/cgi-bin/luci/admin/services/ddnsto",
        "author": "xiaobao",
        "depends": [
          "ddnsto",
          "luci-app-ddnsto",
          "luci-i18n-ddnsto-zh-cn"
        ],
        "title": "DDNS.TO",
        "time": 1629356347,
        "release": 1,
        "website": "https://www.ddnsto.com/",
        "name": "ddnsto",
        "version": "1.0.0"
      }
    ]
   ```
2. 安装软件
   ```
   POST /cgi-bin/luci/admin/store/install
   token=xxx&package=upnp


   {"code":0, "stdout":"", "stderr":""}
   ```
3. 更新软件
   ```
   POST /cgi-bin/luci/admin/store/upgrade
   token=xxx&package=upnp


   {"code":0, "stdout":"", "stderr":""}
   ```
4. 卸载软件
   ```
   POST /cgi-bin/luci/admin/store/remove
   token=xxx&package=upnp


   {"code":0, "stdout":"", "stderr":""}
   ```
5. 刷新可用软件列表
   ```
   POST /cgi-bin/luci/admin/store/update
   token=xxx


   {"code":0, "stdout":"", "stderr":""}
   ```
6. 查询特定软件状态
   ```
   GET /cgi-bin/luci/admin/store/status?package=ddnsto


    {
        "description": "DDNS.TO内网穿透",
        "tags": [
        "net",
        "tool"
        ],
        "entry": "/cgi-bin/luci/admin/services/ddnsto",
        "author": "xiaobao",
        "depends": [
        "ddnsto",
        "luci-app-ddnsto",
        "luci-i18n-ddnsto-zh-cn"
        ],
        "installed": true,
        "title": "DDNS.TO",
        "time": "1629356347",
        "release": 1,
        "website": "https://www.ddnsto.com/",
        "name": "ddnsto",
        "version": "1.0.0"
    }


    {"installed":false}
   ```
7. 任务状态（日志）
   ```
   GET /cgi-bin/luci/admin/store/log


   {
      "stdout": "Installing app-meta-ddnsto (1.0.0) to root...\nDownloading http://192.168.9.168:9999/packages/aarch64_cortex-a53/meta/app-meta-ddnsto_1.0.0_all.ipk\nConfiguring app-meta-ddnsto.\n",
      "stderr": "",
      "code": 206
   }

   {"stdout":"","stderr":"","code":0}
   ```
8. 上传安装
   ```
   POST /cgi-bin/luci/admin/store/upload


   (文件上传表单，支持文件扩展名".ipk,.run")


   {"code":0, "stdout":"", "stderr":""}
   ```
