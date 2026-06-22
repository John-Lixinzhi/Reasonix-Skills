---
name: math-modeling
description: [绔炶禌] 鏁板寤烘ā绔炶禌 鈥?USE when 鍙傚姞鏁版ā姣旇禌/闇€瑕佸缓妯?棰勬祴/鍒嗙被/浼樺寲/璇勪环銆侱O 妯″瀷閫夋嫨鈫掍唬鐮佹ā鏉库啋璁烘枃鍐欎綔銆侼OT for 鏃ュ父鏁版嵁鍒嗘瀽锛堢敤scrapling/excel锛夈€俆riggers: 鏁板寤烘ā/鍥借禌/缇庤禌/寤烘ā姣旇禌/妯″瀷姹傝В
---

# 鏁板寤烘ā绔炶禌

瑕嗙洊鍥借禌/缇庤禌/鍗庝负鏉?鐢靛伐鏉?Mathorcup绛変富娴佽禌浜嬨€?
## 涓€銆佹ā鍨嬪垎绫婚€熸煡

### 棰勬祴妯″瀷
- **鍥炲綊鍒嗘瀽**锛氱嚎鎬?澶氬厓/Logistic鍥炲綊
- **XGBoost**锛氭瀬绔搴︽彁鍗囨爲锛屽垎绫?+ 鍥炲綊 + 鐗瑰緛閲嶈鎬у垎鏋?- **鐏拌壊棰勬祴 GM(1,1)**锛氬皬鏍锋湰鏁版嵁棰勬祴
- **鏃堕棿搴忓垪**锛欰R/MA/ARIMA/LSTM
- **寰垎鏂圭▼**锛歄DE/SDE/PDE 鍔ㄦ€佸缓妯?- **椹皵鍙か棰勬祴**锛氱姸鎬佽浆绉婚娴?- **鏀寔鍚戦噺鏈哄洖褰掞紙SVR锛?*锛氬皬鏍锋湰闈炵嚎鎬ч娴?
### 璇勪环妯″瀷
- **灞傛鍒嗘瀽娉?AHP**锛氫富瑙傝祴鏉?- **鐔垫潈娉?*锛氬瑙傝祴鏉?- **TOPSIS**锛氶€艰繎鐞嗘兂瑙ｆ帓搴?- **妯＄硦缁煎悎璇勪环**锛氬鍥犵礌妯＄硦璇勫垽
- **涓绘垚鍒嗗垎鏋?PCA**锛氶檷缁?缁煎悎璇勪环
- **鏁版嵁鍖呯粶鍒嗘瀽 DEA**锛氭晥鐜囪瘎浠?- **绉╁拰姣旀硶 RSR**锛氱粺璁¤瘎浠?
### 浼樺寲妯″瀷
- **绾挎€?鏁存暟/闈炵嚎鎬ц鍒?*锛氬熀纭€浼樺寲
- **閬椾紶绠楁硶**锛氬叏灞€鎼滅储浼樺寲
- **绮掑瓙缇ょ畻娉?PSO**锛氱兢浣撴櫤鑳戒紭鍖?- **妯℃嫙閫€鐏?*锛歍SP/鑳屽寘闂
- **澶氱洰鏍囪鍒?*锛氬垎灞傚簭鍒楁硶/Pareto鏈€浼?- **鍔ㄦ€佽鍒?*锛氬闃舵鍐崇瓥
- **鍥捐妯″瀷**锛氭渶鐭矾寰?Dijkstra/Floyd)/鏈€灏忕敓鎴愭爲/鏈€澶ф祦

### 鍒嗙被妯″瀷
- **SVM**锛氭渶浼樿秴骞抽潰鍒嗙被
- **闅忔満妫灄**锛氶泦鎴愬涔犲垎绫?- **XGBoost/LightGBM**锛氭搴︽彁鍗囧垎绫?- **KNN**锛氭渶杩戦偦鍒嗙被
- **鏈寸礌璐濆彾鏂?*锛氭鐜囧垎绫?- **绁炵粡缃戠粶**锛氭繁搴﹀涔犲垎绫?
## 浜屻€丳ython 閫氱敤浠ｇ爜妯℃澘

### XGBoost 鍒嗙被
```python
import pandas as pd
from sklearn.model_selection import train_test_split
from xgboost import XGBClassifier
from sklearn.metrics import accuracy_score, classification_report, confusion_matrix

data = pd.read_excel("data.xlsx")
X = data.drop(columns=["label"])
y = data["label"]
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42, stratify=y)
model = XGBClassifier(n_estimators=100, max_depth=3, learning_rate=0.1, subsample=0.8, colsample_bytree=0.8, eval_metric="logloss")
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
print(accuracy_score(y_test, y_pred))
```

### XGBoost 鍥炲綊
```python
from xgboost import XGBRegressor
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score
model = XGBRegressor(n_estimators=200, max_depth=3, learning_rate=0.05)
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
```

## 涓夈€佽鏂囧啓浣滆鐐?- 缁撴瀯锛氭憳瑕佲啋闂閲嶈堪鈫掓ā鍨嬪亣璁锯啋绗﹀彿璇存槑鈫掓ā鍨嬪缓绔嬧啋姹傝В鈫掔粨鏋滃垎鏋愨啋浼樼己鐐?- 鎽樿鏈€閲嶈锛佽瘎瀹″厛鐪嬫憳瑕?- LaTeX 妯℃澘锛氬浗璧?缇庤禌鍚勬湁涓撶敤妯℃澘
- 鍥捐〃娓呮櫚锛屽叕寮忚鑼?
## 鍥涖€佸父鐢ㄨ蒋浠?- MATLAB / Python + Jupyter
- SPSS / Stata 缁熻
- Lingo / Gurobi 浼樺寲姹傝В
- LaTeX / Word 鎺掔増
- Visio / Origin / AxGlyph 缁樺浘

## 浜斻€佸弬鑰冭祫鏂?- GitHub 瀹濊棌搴擄細personqianduixue/Math_Model (4.6k猸?
  - 鍖呭惈鍥借禌/缇庤禌/鐮旇禌璁烘枃銆佺畻娉曚唬鐮併€丩aTeX妯℃澘銆佷功绫?00+鏈?