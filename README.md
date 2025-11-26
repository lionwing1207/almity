# almity
flowchart TD

    subgraph GOV["🏛️ 台北市政府內網（Intranet）"]
        KIOSK["🖥️ KIOSK 裝置（你方）<br/>• WebView2<br/>• NFC Reader<br/>• 固定對外連線"]
    end

    FIREWALL["🛡️ 市府防火牆 / 資安設備（UTM / WAF）<br/>• 必須允許 KIOSK → 外部 443<br/>• 過濾未授權流量"]

    subgraph CLOUD["🌐 你方外網環境"]
        APISERVER["💻 API Server（外網）<br/>• https://api.xxx.com<br/>• TCP Port 443<br/>• 後端 KIOSK API"]
    end

    KIOSK -->|"HTTPS (443)<br/>Outbound 流量"| FIREWALL -->|"允許 443<br/>至 API Server"| APISERVER
