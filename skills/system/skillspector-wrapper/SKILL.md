---
name: skillspector-wrapper
description: [system] SkillSpector security scanner - USE before installing new skill. DO scan 64 vulnerability patterns. NOT for regular use. Triggers: scan skill/security check/is it safe
---

# SkillSpector 瀹夊叏鎵弿

NVIDIA 鍑哄搧鐨?AI Agent Skill 瀹夊叏鎵弿鍣紙9k猸愶級銆?
## 鍔熻兘
- 鎵弿 SKILL.md 鎴栨暣涓?skill 鐩綍
- 妫€娴?64 绉嶆紡娲炴ā寮忥紝16 涓被鍒?- 鎵撳垎 0-100锛岀粰鍑哄畨鍏ㄥ缓璁?- 鏀寔缁堢/JSON/Markdown/SARIF 杈撳嚭

## 浣跨敤鏂瑰紡
```bash
skillspector scan ./my-skill/
skillspector scan ./SKILL.md --no-llm
skillspector scan ./my-skill/ --format json --output report.json
```

## 鍦?onboarder 涓殑浣嶇疆
姣忔瑁呮柊 skill 鍓嶅厛璺戯細
1. skillspector scan 鈫?瀹夊叏妫€鏌?2. 纭瀹夊叏 鈫?缁х画瀹夎
3. 鍙戠幇楂橀闄?鈫?鎷掔粷瀹夎骞舵姤鍛?
## 瀹夎鐘舵€?宸查€氳繃 pip 瀹夎锛岃矾寰勶細Python312\Scripts\skillspector.exe
