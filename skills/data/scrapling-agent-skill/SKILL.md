---
name: scrapling-agent-skill
description: [Scrapling][鏁版嵁] 缃戦〉鏁版嵁閲囬泦 鈥?瑙﹀彂鏉′欢锛氶渶瑕佹姄鍙栫綉椤垫暟鎹?web_fetch澶辫触/鏈塁loudflare鍙嶇埇/闇€瑕佸ぇ瑙勬ā鐖櫕銆傛敮鎸丮CP鐩存帴璋冪敤(get/fetch/stealthy_fetch)锛屼篃鏀寔Python缂栫爜
---

# Scrapling 瀹樻柟 Agent Skill

Scrapling 鏄竴涓嚜閫傚簲 Web Scraping 妗嗘灦锛屽鐞嗕粠鍗曟璇锋眰鍒板叏閲忕埇鍙栫殑涓€鍒囬渶姹傘€?
**瑕佹眰锛歅ython 3.10+ | pip install "scrapling[all]>=0.4.9"**

## 蹇€熷垽鏂敤鍝釜宸ュ叿

| 鍦烘櫙 | 鐢ㄥ暐 |
|------|------|
| 闈欐€侀〉闈紝鏃犲弽鐖?| `get` 鈥?鏈€蹇紝HTTP 璇锋眰 |
| 澶氫釜闈欐€侀〉闈?| `bulk_get` 鈥?骞跺彂 |
| JS 娓叉煋/SPA 椤甸潰 | `fetch` 鈥?Playwright 娴忚鍣?|
| Cloudflare/寮哄弽鐖?| `stealthy_fetch` 鈥?闅愯韩 + 鎸囩汗浼 |
| 鎵归噺甯﹀弽鐖〉闈?| `bulk_stealthy_fetch` |
| 鍚屼竴绔欑偣澶氫釜椤甸潰 | `open_session` + session_id 澶嶇敤 |
| 鎴浘 | `open_session` + `screenshot` |

**鍘熷垯锛?* 浠?`get` 寮€濮嬶紝琚嫤鎴簡鍗囧埌 `fetch`锛屽啀鏈?Cloudflare 灏变笂 `stealthy_fetch`

## CLI 鐢ㄦ硶

`scrapling extract` 鍛戒护缁勶細

```
scrapling extract get/put/post/delete/fetch/stealthy-fetch <url> <output>
```

杈撳嚭鏍煎紡鐢辨墿灞曞悕鍐冲畾锛歚.md`=Markdown銆乣.html`=HTML銆乣.txt`=绾枃鏈?
鍏抽敭鍙傛暟锛歚--css-selector` 缂╁皬鍐呭鐪?tokens銆乣--solve-cloudflare` 杩?CF銆乣--ai-targeted` 闃叉敞鍏ャ€乣--proxy` 浠ｇ悊

## MCP 宸ュ叿锛圧easonix 鐩存帴鐢級

鎴戝凡瀵规帴濂?Scrapling MCP 鏈嶅姟鍣紝10 涓伐鍏峰彲鐢細

- `get` / `bulk_get` 鈥?HTTP 璇锋眰锛堟敮鎸?TLS 鎸囩汗妯℃嫙銆丠TTP/3锛?- `fetch` / `bulk_fetch` 鈥?娴忚鍣ㄦ覆鏌擄紙Playwright锛?- `stealthy_fetch` / `bulk_stealthy_fetch` 鈥?闅愯韩妯″紡锛堣繃 Cloudflare Turnstile锛?- `open_session` / `close_session` / `list_sessions` 鈥?浼氳瘽绠＄悊
- `screenshot` 鈥?椤甸潰鎴浘

鐪?tokens 鎶€宸э細`css_selector` 鍙傛暟鎻愬墠绛涢€夈€乣extraction_type="markdown"` 榛樿鏈€鐪併€乣main_content_only=true` 鍘诲鑸爮

## 瀹夊叏瑙勮寖
- 鍙埇鏈夋潈闄愯闂殑鍐呭
- 閬靛畧 robots.txt锛堢埇铏敤 `robots_txt_obey=True`锛?- 澶х埇铏姞 `download_delay`
- 涓嶇埇鏁忔劅鏁版嵁銆佷笉缁曡繃浠樿垂澧?