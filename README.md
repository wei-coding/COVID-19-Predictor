# COVID-19-Predictor

利用sklearn分析疫情資料，預測隔日及長期確診數趨勢

## 使用方法

直接使用API取得資料

### **GET** /v1/

回傳伺服器健康狀態

```json
{"message": "ok"}
```

### **GET** /v1/update/

手動更新資料，重新預測

```json
// success
{"message": "ok"}
// update process is going on
{"message": "bad"}
```

### **GET** /v1/update/check/

確認更新資料進度

```json
// finished
{"message": "ok"}
// faild
{"message": "bad"}
// not yet
{"message": "not yet"}
```

### **GET** /v1/predict/

回傳隔日預估確診數(int)

```json
{"message": "ok", "data": 46853}
```

### **GET** /v1/predict/\<days-from-1-1\>/

傳入參數，格式為距離1月1日幾天(1月2日為1天，傳入1)，回傳該日預估確診數(int)

```json
{"message": "ok", "data": 46853}
```

### **GET** /v1/predict/decrease/

回傳預估幾日後確診數會降低(int)

```json
{"message": "ok", "data": 29}
```

### **GET** /v1/algorithm/

檢視目前使用的演算法，預設為擬合5次多項式

```json
{
    "message": "ok",
    "data": {
        "algorithm": "polynomial",
        "power": 5
    }
}
```