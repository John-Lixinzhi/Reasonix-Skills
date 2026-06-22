---
name: cua-skill
description: [tools] CUA computer control - USE when need AI to control desktop/mouse/keyboard. DO open-source Computer-Use Agent infra for macOS/Windows/Linux. NOT for web scraping. Triggers: desktop/click/type/control PC/automate
---

# CUA 鈥?璁＄畻鏈轰娇鐢?Agent

鏉ユ簮锛歵rycua/cua (18.6k猸?

璁?AI 鑳芥搷鎺х數鑴戞闈㈢殑鍩虹璁炬柦鈥斺€旂偣榧犳爣銆佹暡閿洏銆佹埅鍥俱€佽繍琛屽懡浠ゃ€?
## 鏍稿績缁勪欢
- **cua-driver**锛氬悗鍙版闈㈤┍鍔紙macOS/Windows/Linux锛夛紝涓嶆姠鍏夋爣涓嶆姠鐒︾偣
- **cua-sandbox**锛氭矙绠辩幆澧?SDK锛屽垱寤洪殧绂荤殑铏氭嫙鏈?瀹瑰櫒
- **cua-bench**锛氬熀鍑嗘祴璇曞拰寮哄寲瀛︿範鐜
- **Lume**锛歮acOS 铏氭嫙鏈虹鐞嗭紙Apple Silicon锛?
## 鎺ュ叆鏂瑰紡
```bash
# Windows 瀹夎
irm https://raw.githubusercontent.com/trycua/cua/main/libs/cua-driver/scripts/install.ps1 | iex

# 鎺ュ叆 Claude Code 浣滀负 MCP
claude mcp add --transport stdio cua-driver -- cua-driver mcp
```

## 瀵规垜鐢熸€佺殑浠峰€?- 濡傛灉鎺ュ叆锛屾垜鍙互鐩存帴鎿嶄綔浣犵殑鐢佃剳妗岄潰
- 鎵撳紑杞欢銆佺偣鍑绘寜閽€佹埅鍥鹃獙璇併€佽法搴旂敤鎿嶄綔
- 閰嶅悎 Scrapling 鐨勬埅鍥惧姛鑳藉彲浠ュ疄鐜板畬鏁寸殑瑙嗚闂幆
