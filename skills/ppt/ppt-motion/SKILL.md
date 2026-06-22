---
name: ppt-motion
description: [ppt] Motion & animation - USE when need smooth transitions/slide animations. DO control transitions, entry animations, background micro-motion. NOT for static PPTs. Triggers: animation/transition/motion/smooth
---

# PPT 杞満涓庡姩鏁堟寚鍗?
閰嶅悎 guizang-ppt-skill 浣跨敤锛岃鐢熸垚鐨?HTML PPT 鍏锋湁涓濇粦杞満鍜屽姩鎬佹晥鏋溿€?
## 涓€銆佺炕椤佃浆鍦猴紙Slide Transition锛?
### 鍦?template 涓疄鐜?guizang 妯℃澘宸插唴缃?`#deck` 瀹瑰櫒鐨?transition锛?```css
#deck{transition:transform .9s cubic-bezier(.77,0,.175,1)}
```
杩欎釜缂撳姩鏇茬嚎鏄?鎱?蹇?鎱?鐨勪笣婊戞晥鏋滐紝0.9s 鏄渶鑸掓湇鐨勬椂闀裤€?
### 鍙彔鍔犵殑杩囨浮澧炲己
鍦?`#deck` 瀹瑰櫒涓婂姞涓€涓?overlay 閬僵锛岀炕椤垫椂娣″叆娣″嚭锛?```css
/* 鍦?deck 鍜?slide 涔嬮棿鍔犱竴灞?*/
#deck::after {
  content:''; position:fixed; inset:0; z-index:5;
  background:var(--paper);
  pointer-events:none;
  opacity:0;
  transition:opacity .4s ease;
}
body.transitioning #deck::after { opacity:.3 }
```

### 缂撳姩鏇茬嚎鎺ㄨ崘
| 鏁堟灉 | cubic-bezier | 閫傜敤 |
|------|-------------|------|
| 涓濇粦鏍囧噯 | `.77,0,.175,1` | 榛樿缈婚〉 |
| 鏇磋蒋 | `.83,0,.17,1` | 鍙欎簨鍨婸PT |
| 寮规€?| `.34,1.56,.64,1` | 鍒涙剰鍨嬶紙鎱庣敤锛?|
| 骞茶剢 | `.25,.46,.45,.94` | 鏁版嵁鍨?|

## 浜屻€佸叆鍦哄姩鐢伙紙Entry Animation锛?
guizang 妯℃澘宸查泦鎴?Motion One锛屾瘡椤靛彲鍔犵嫭绔?`data-anim`锛?
### 涓昏鍔ㄧ敾绫诲瀷
- `fade-up` 鈥?浠庝笅寰€涓婃贰鍏ワ紙鏈€甯哥敤锛?- `fade-left` / `fade-right` 鈥?浠庝晶杈规粦鍏?- `scale-in` 鈥?缂╂斁寮瑰叆锛堥€傚悎鏁板瓧/澶у瓧鎶ワ級
- `stagger` 鈥?鍒楄〃椤归€愪釜浜ら敊鍑虹幇
- `reveal` 鈥?閬僵灞曞紑

### 姣忛〉涓€涓涔夊寲鍔ㄦ晥
- 灏侀潰 鈫?澶ф爣棰?`scale-in` + 鍓爣棰?`fade-up`锛堝欢杩燂級
- 鏁版嵁椤?鈫?鏁板瓧 `scale-in` + 鍥捐〃 `stagger`
- 鍥炬枃椤?鈫?鍥剧墖 `fade-left` + 鏂囧瓧 `fade-right`
- 绔犺妭椤?鈫?澶у瓧 `reveal`

**涓嶈兘鎵€鏈夐〉鐢ㄥ悓涓€涓?animation recipe銆?*

## 涓夈€佽儗鏅井鍔紙Background Motion锛?
妯℃澘鏈?WebGL 鑳屾櫙宸茬粡甯︿簡娴佷綋/缃戞牸鍔ㄧ敾銆?棰濆鍙互鍔犵殑锛?- **瑙嗗樊** 鈥?鑳屾櫙 `transform:translateY()` 閫熷害鏄墠鏅殑涓€鍗?- **鍛煎惛鍏夋檿** 鈥?寮鸿皟鑹?radial-gradient 缂撴參鍙樺寲 opacity
- **寰绮?* 鈥?CSS 绮掑瓙灞傜紦鎱㈢Щ鍔?
## 鍥涖€佸姩鏁?QA 娓呭崟
- [ ] 缈婚〉杩囨浮鏄惁涓濇粦锛堜笉鏄崱椤胯烦鍙橈級
- [ ] 姣忛〉鏈夌嫭绔嬬殑鍏ュ満鍔ㄦ晥
- [ ] 鍔ㄦ晥涓嶈繃搴︼紙涓嶇偒鎶€锛屼笉骞叉壈闃呰锛?- [ ] 鍔ㄧ敾鏃堕暱鍚堢悊锛堝叆鍦?0.3-0.6s锛岃繃娓?0.7-0.9s锛?- [ ] 浣庢€ц兘妯″紡鏈夐檷绾ф柟妗堬紙B閿垏鎹級
- [ ] 鎵€鏈夊唴瀹规渶缁堥兘鑳介潤鎬佸睍绀猴紙鍔ㄧ敾涓嶄緷璧?JS锛?