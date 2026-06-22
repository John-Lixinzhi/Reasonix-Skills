---
name: skillopt-wrapper
description: [system] SkillOpt skill optimizer - USE when need to auto-improve skills. DO trajectory-driven edits, validation-gated updates. NOT for writing new skills. Triggers: optimize skill/improve quality/skill training
---

# SkillOpt 鎶€鑳戒紭鍖?
寰蒋鐮旂┒闄㈠嚭鍝侊紙8.6k猸愶級锛屽儚璁粌绁炵粡缃戠粶涓€鏍疯嚜鍔ㄤ紭鍖?skill 鏂囨湰銆?
## 鏍稿績鑳藉姏
- 鎶?skill 鏂囨。褰撲綔"鍙缁冨弬鏁?
- optimizer 妯″瀷鑷姩鍔?鍒?鏀?skill 鍐呭
- 楠岃瘉闂ㄦ帶锛氬彧鏈変弗鏍兼彁鍗囨墠閲囩撼
- 浜у嚭 compact best_skill.md锛?00-2000 tokens锛?
## 浣跨敤鏂瑰紡
```bash
skillopt-train --config configs/my_config.yaml
skillopt-eval --skill best_skill.md --benchmark my_benchmark
```

## 鏁堟灉
- 6涓熀鍑嗘祴璇?2涓疄楠屽叏閮ㄦ渶浼?- GPT-5.5鍑嗙‘鐜囨彁鍗?+23.5鍒?- 璺ㄦā鍨?璺ㄥ钩鍙拌縼绉绘湁鏁?
## 瀹夎鐘舵€?宸查€氳繃 pip install skillopt 瀹夎
闇€瑕侀厤缃?LLM API 瀵嗛挜鎵嶈兘浣跨敤璁粌鍔熻兘
