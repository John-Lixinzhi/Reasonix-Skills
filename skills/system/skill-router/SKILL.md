---
name: skill-router
description: [system] Skill router - USE when multiple skills match/unsure which to use. DO analyze request, query catalog, recall, rerank, execute. NOT for known single skill. Triggers: which skill/router/not sure/help choose
---

# Skill Router 鈥?鎶€鑳借矾鐢辩鐞嗗櫒

## 瀹氫綅
鎴戞槸鎵€鏈夋妧鑳界殑"缁忕悊浜?銆傚綋浣犻潰瀵瑰ぇ閲忔妧鑳戒笉纭畾鐢ㄥ摢涓椂锛岀敱鎴戞潵鍋氳矾鐢卞喅绛栥€?
## 瑙﹀彂鏉′欢
- 鐢ㄦ埛璇锋眰鍙兘鍛戒腑澶氫釜鎶€鑳?- 浣犱笉澶‘瀹氱敤鍝釜鎶€鑳芥渶鍚堥€?- 鎶€鑳芥暟閲忚秴杩?5 涓紝闇€瑕佺缉灏忛€夋嫨鑼冨洿
- 鐢ㄦ埛鏄庣‘璇?鐢ㄥ悎閫傜殑鎶€鑳藉鐞?

## 宸ヤ綔娴佺▼

### 1. 璇荤洰褰?璇诲彇 `SKILLS_CATALOG.json` 浜嗚В鎵€鏈夋妧鑳界殑鍒嗙被銆佹爣绛俱€佽Е鍙戝満鏅拰璐熸牱鏈?
### 2. 鍒嗘瀽璇锋眰
浠庣敤鎴疯姹備腑鎻愬彇锛?- 鏍稿績鎰忓浘锛堣鍋氫粈涔堬級
- 棰嗗煙锛堝紑鍙?鏁版嵁/璁捐/宸ュ叿/瀛︿範锛?- 鎶€鏈爤锛圥ython/JS/Go...锛?- 鎺掗櫎淇″彿锛堟槑鏄句笉鐩稿叧鐨勯鍩燂級

### 3. 鍙洖鍊欓€?鐢ㄨ涔夊尮閰嶄粠鐩綍涓彫鍥?top-3 鍒?top-5 鍊欓€夋妧鑳?
### 4. 閲嶆帓閫夋嫨
浠庡€欓€変腑閫夊嚭鏈€鍖归厤鐨?1 涓妧鑳斤紝缁欏嚭鐞嗙敱

### 5. 鎵ц鎴栭摼寮忚皟鐢?- 濡傛灉 1 涓妧鑳藉鐢?鈫?璋冪敤瀹?- 濡傛灉闇€瑕佸涓妧鑳藉崗浣?鈫?鎸?SKILLS_CATALOG 涓殑 dependencies 閾惧紡璋冪敤
