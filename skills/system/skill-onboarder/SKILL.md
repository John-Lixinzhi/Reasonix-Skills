---
name: skill-onboarder
description: [system] Skill onboarder - USE when installing new skill/importing skill. DO fetch, analyze, install_skill, update catalog. NOT for modifying existing. Triggers: install/new skill/onboard/import/add skill
---

# Skill Onboarder 鈥?鏂版妧鑳芥帴鍏ヤ笓鍛?
鎴戞槸鎶€鑳?HR閮ㄩ棬"锛岃礋璐ｆ妸姣忎釜鏂?skill 鎸夋爣鍑嗘祦绋嬭瀺鍏ョ敓鎬併€?
## 瑙﹀彂鏉′欢

- 鐢ㄦ埛璇?瑁呬釜鏂皊kill" / "瀹夎XX鎶€鑳? / "瀵煎叆杩欎釜skill"
- 鐢ㄦ埛缁欎簡 GitHub 鍦板潃鎴?skill 鍐呭锛岃姹傝鍒?Reasonix
- 鐢ㄦ埛璇?鎶婅繖涓姞鍒扮敓鎬侀噷"
- 鏂?skill 闇€瑕侀厤缃Е鍙戝満鏅€佸垎绫汇€佷緷璧栧叧绯?
## 鎺ュ叆鏍囧噯娴佺▼

### Step 1 路 鑾峰彇婧愮爜
- 濡傛灉鏄?GitHub 浠撳簱 鈫?鐢?GitHub MCP 鑾峰彇鍐呭锛屾垨涓嬭浇 ZIP 鍒?D:\
- 濡傛灉鏄洿鎺ョ粰鐨勬枃鏈?鈫?璇诲彇鍐呭
- 纭畾 skill 鐨勬牳蹇冩枃浠讹紙SKILL.md / README / 涓绘枃浠讹級

### Step 2 路 鍒嗘瀽鍒嗙被
- 瀹冨睘浜庡摢涓鍩燂紵鐮斿彂/鏁版嵁/鍔炲叕/璁捐/宸ュ叿/绯荤粺/...
- 瀹冪殑瑙﹀彂鍦烘櫙鏄粈涔堬紵浠€涔堟儏鍐靛簲璇ヨ嚜鍔ㄨ皟鐢紵
- 瀹冨拰鐜版湁 skill 鏈夋病鏈夐噸鍙?鍐茬獊锛?- 瀹冧緷璧栧叾浠?skill 鍚楋紵
- 鏈夋病鏈夋槑纭笉璇ョ敤瀹冪殑鍦烘櫙锛堣礋鏍锋湰锛夛紵

### Step 3 路 瀹夎鍒?Reasonix
- 鐢?`install_skill` 鍒涘缓 Reasonix skill
- description 鎸夋爣鍑嗘牸寮忥細`[鍒嗙被] 鍚嶇О 鈥?瑙﹀彂鏉′欢锛歺xx銆備綔鐢細xxx`
- 濡傛灉鏄ぇ鍨嬮」鐩紙鏈夋ā鏉?鍙傝€冩枃浠讹級锛屽悓鏃跺厠闅嗗埌 D:\

### Step 4 路 鏇存柊鐩綍
- 鎵撳紑 `SKILLS_CATALOG.json`
- 娣诲姞鏂版潯鐩細name / description / category / tags / triggers / negative_samples / dependencies / priority
- 纭娌℃湁鍒嗙被鍐茬獊

### Step 5 路 姹囨姤
- 鍛婅瘔鐢ㄦ埛瑁呭ソ浜?- 缁欏嚭锛氭妧鑳藉悕绉?/ 鍒嗙被 / 瑙﹀彂鏉′欢 / 鍜岀幇鏈夌敓鎬佺殑鍏崇郴 / 璋冪敤鏂瑰紡
