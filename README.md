# Face Recognition 人臉辨識匹配


## 什麼是face_recognition
 "face_recognition" 是一個用於人臉識別的模組，它可以幫助你在圖像中偵測和識別人臉，使用深度學習技術來進行人臉特徵提取和匹配。

#

## 資料前處理
- 選定幾位長得相似的人選，分別提供幾張照片，將人名標註在照片檔名上，將這批資料放在known_person資料夾裡。
- 再額外準備這些人選不在known_person裡的照片，隨機打亂且不在照片檔名上做標註，這批資料放在unknown_person資料夾裡。

#

## 如何使用
1. import face_recognition 後創建兩個空list，encodinglist 儲存人臉編碼，labels 儲存人臉的標籤
2. 設定展示圖像排列大小
3. 使用 enumerate 函式迭代處理路徑裡每張圖片
   - 使用 face_recognition.load_image_file(f) 載入圖像。
   - 使用 face_recognition.face_encodings(img)[0] 提取第一個人臉的特徵編碼，存在encodinglist
   - 使用 face_recognition.face_locations(img, model="cnn")[0] 找到第一個人臉的位置坐標（上、右、下、左），並將其用於定位人臉。
   - 從文件路徑中提取出人臉的標籤（文件名），並將其添加到 labels 列表中
   - 使用plt顯示圖片



