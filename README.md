# Face Recognition 人臉辨識匹配


## What is face_recognition?
 `face_recognition` 是一個用於人臉識別的模組，它可以幫助你在圖像中偵測和識別人臉，使用深度學習技術來進行人臉特徵提取和匹配。

`face_recognition` is a module for facial recognition that assists in detecting and identifying faces in images. It utilizes deep learning techniques to extract and match facial features.

#

## Data preprocessing
- 選定幾位長得相似的人選，分別提供幾張照片，將人名標註在照片檔名上，將這批資料放在known_person資料夾裡。
- 再額外準備這些人選不在known_person裡的照片，隨機打亂且不在照片檔名上做標註，這批資料放在unknown_person資料夾裡。

- Select a few individuals who resemble each other, provide several photos for each person, and label their names in the file names. Place this batch of data in the "known_person" folder.
- Additionally, prepare photos of these individuals who are not included in the "known_person" folder. Randomly shuffle the photos and do not label the file names. Put this batch of data in the "unknown_person" folder.

#

## How to use
1. import face_recognition 後創建兩個空list，encodinglist 儲存人臉編碼，labels 儲存人臉的標籤
2. 設定展示圖像排列大小
3. 使用 enumerate 函式迭代處理路徑裡每張圖片
   - 使用 `face_recognition.load_image_file(f)` 載入圖像。
   - 使用 `face_recognition.face_encodings(img)[0]` 提取第一個人臉的特徵編碼，存在encodinglist
   - 使用 `face_recognition.face_locations(img, model="cnn")[0]` 找到第一個人臉的位置坐標（上、右、下、左），並將其用於定位人臉。
   - 從文件路徑中提取出人臉的標籤（文件名），並將其添加到 labels 列表中
   - 使用matplotlib(plt)顯示圖片
4. 讀取unknown_flist的照片進行人臉辨識，並獲取人臉位置的座標(上下左右)
5. 使用 OpenCV 的 rectangle 函數在圖像上繪製一個矩形框，將檢測到的人臉圈起來，並指定矩形的顏色和粗細。
6. 計算未知人臉特徵向量與已知人臉特徵向量的距離，找到最接近的已知人臉特徵向量的名稱，作為預測結果。
7. 將處理後的圖像以網格的形式顯示在 Matplotlib 圖表中。

#

1. After importing "face_recognition," create two empty lists: "encodinglist" for storing face encodings and "labels" for storing face labels.
2. Set the arrangement size for displaying images.
3. Use the "enumerate" function to iterate through each image path:
   - Load the image using `face_recognition.load_image_file(f).`
   - Extract the feature encoding of the first face using `face_recognition.face_encodings(img)[0]` and store it in "encodinglist."
   - Locate the coordinates (top, right, bottom, left) of the first face using `face_recognition.face_locations(img, model="cnn")[0]` and use them for positioning the face.
   - Extract the face label (filename) from the file path and add it to the "labels" list.
   - Display the image using matplotlib (plt).
4. Read the photos from "unknown_flist" for face recognition and obtain the coordinates (top, right, bottom, left) of the face.
5. Use the OpenCV "rectangle" function to draw a rectangular box around the detected face on the image, specifying the color and thickness of the rectangle.
6. Calculate the distance between the feature vectors of unknown faces and known faces. Find the name of the closest known face feature vector as the prediction.
7. Display the processed images in a grid format on a Matplotlib chart.

