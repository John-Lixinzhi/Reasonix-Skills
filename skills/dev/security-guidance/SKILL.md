---
name: security-guidance
description: [鐮斿彂] 瀹夊叏瀹℃煡 鈥?USE when 瀹℃牳浠ｇ爜瀹夊叏鎬?鎵炬紡娲?瀹夊叏鍚堣妫€鏌ャ€侱O 3灞傞槻鎶わ細妯″紡璀﹀憡鈫扡LM瀹℃煡鈫掕法鏂囦欢杩借釜銆侼OT for 甯歌浠ｇ爜瀹℃煡锛堢敤superpowers-review锛夈€俆riggers: 瀹夊叏妫€鏌?婕忔礊/娓楅€?瀹夊叏瀹℃煡/鎵鹃闄?---

# Security Guidance 鈥?瀹夊叏瀹℃煡

3 灞傚畨鍏ㄩ槻鎶や綋绯伙紝鐢ㄤ簬瀹℃煡 AI 鐢熸垚鐨勪唬鐮併€?
## 涓夊眰闃叉姢
1. **妯″紡璀﹀憡** 鈥?鍗虫椂姝ｅ垯妫€鏌?25+ 鍗遍櫓妯″紡锛坹aml.load銆乸ickle.load銆乮nnerHTML銆佺‖缂栫爜瀵嗛挜绛夛級
2. **LLM diff 瀹℃煡** 鈥?姣忔淇敼鍚庡彂閫?diff 缁欏ぇ妯″瀷鍋氬畨鍏ㄥ鏌ワ紝楂樹弗閲嶅害闂鑷姩淇
3. **Agentic 鎻愪氦瀹℃煡** 鈥?git commit 鏃惰法鏂囦欢杩借釜鏁版嵁娴侊紝鎹曡幏澶氭枃浠舵紡娲烇紙IDOR銆佽璇佺粫杩囥€佽法鏂囦欢 SSRF锛?
## 瑕嗙洊鑼冨洿
- SQL/鍛戒护娉ㄥ叆
- XSS/CSRF
- SSRF
- 纭紪鐮佸瘑閽?鍑嵁
- IDOR/鏉冮檺缁曡繃
- 涓嶅畨鍏ㄥ弽搴忓垪鍖?- 璺緞閬嶅巻
- 鏁忔劅鏁版嵁娉勯湶

## 宸ヤ綔娴?1. 鍏堣窇 `/superpowers-review` 鍋氬父瑙勪唬鐮佸鏌?2. 鍐嶈窇鏈?skill 鍋氬畨鍏ㄤ笓椤瑰鏌?3. 鎸変弗閲嶅害鍒嗙骇锛欳ritical / High / Medium / Low
4. Critical 鍜?High 蹇呴』淇鎵嶈兘缁х画
