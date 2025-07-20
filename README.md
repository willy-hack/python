# <div align="center">python 指令說明 && 終端機指令</div>

終端指令`Terminal基本指令`
```bash
clear # 清除輸出
cd <地址> # 進入目錄
ls # 掃描當前資料夾
echo <環境變數> # 輸出指令
```

終端指令`系統控制指令`
```bash
sudo poweroff # 關機指令(基本Linux都可使用)
sudo reboot # 重新起動
ip a # 查看主機擁有的ip地址及mac地址
hostname # 查看主機名稱
```

終端指令 `apt`
```bash
sudo apt update # 下載最新的程式庫清單
sudo apt upgrade # 進行系統更新
sudo apt full-upgrade # 進行全局更新
sudo apt install <程式庫名稱> # 下載程式庫或者程序套件
```

終端指令`systemctl`
```bash
sudo systemctl daemon-reload # 重新加載服務清單
sudo systemctl start <服務名稱> # 啟動服務
sudo systemctl restart <服務名稱> # 重新啟動服務
sudo systemctl stop <服務名稱> # 關閉服務
sudo systemctl status <服務名稱> # 查看服務狀態
sudo systemctl enable <服務名稱> # 設置服務為自啟動模式
```

未來工程代碼重點解析 - 自訂義程式庫介紹
```python
# 生成二值化畫面以及黑點統計數值
gray, black_pixels = process_roi()
```

未來工程代碼重點解析 - 需要匯入的程式庫
```python
import cv2
import numpy as np
import serial as AC
import struct
import time
import Adafruit_BNO055.BNO055 as BNO055
from function import process_roi, detect_color_final, pd_control, draw_multiple_curves, detect_color_final
import Jetson.GPIO as GPIO
```

未來工程代碼重點解析 - 變數定義[資格賽]
```python
rois = [ (370, 150, 640, 200), (0, 150, 270, 200) ] # 左右ROI偵測框座標
target_heading = [0] * 4 # 儲存繞圈模式
left_heading = [-90, -180, 90, 0] # 左轉彎模式
right_heading = [90, 180, -90, 0] # 右轉彎模式
turn_side = 0 # 目前狀態代碼
# 邊牆位置校正係數
kp_roi = 0.03
kd_roi = 0.05
combined_control_signal = 0 # servo 轉向角度
count = 0 # 線條計數器
PWM = 100 # 馬達運轉速度
round_number = 0 # 圈數
data_to_send = 0 # 要傳輸的資料
output_pin = 40 # LED 燈腳位
```

未來工程代碼重點解析 - GPIO設置[資格賽]
```python
GPIO.setmod(GPIO.BOARD) # 設置GPIO模式, 目前設置為引腳編號模式
GPIO.setup(output_pin, GPIO.OUT) # 設置引腳為輸出, GPIO.IN 為輸入模式
GPIO.output(output_pin, GPIO.HIGH) # 設置目標引腳為高電為, GPIO.LOW 為低電位
```

未來工程代碼重點解析 - 通訊窗口設置[資格賽]
```python
try :
    # (通道, 通訊頻率, 連線超時時間)
    ser = AC.Serial('/dev/ttyTHS1', 115200, timeout=1) # 設置通訊窗口
except AC.SerialException as e:
    print(f"無法開啟通訊窗口, 錯誤資訊:{e}")
    exit()
```

未來工程代碼重點解析 - 設置imx477通道[資格賽]
```python
cap = cv2.VideoCapture(
    'nvarguscamerasrc ! video/x-raw(memory:NVMM), width=640, height=480, format=(string)NV12,framerate=12/1 ! nvvidconv ! video/x-raw, format=BGRx ! videoconvert ! video/x-raw, format=BGR ! appsink drop=true sync=false',
    cv2.CAP_GSTREAMER)
```

未來工程代碼重點解析 - 設置BNO055感測器[資格賽]
```python
bno = BNO055.BNO055(busnum=1)
```

未來工程代碼重點解析 - 讀取BNO055感測器數值[資格賽]
```python
heading, roll, pitch = bno.read_euler() # 獲取航向角
accel_x, accel_y, accel_z  = bno.read_linear_acceleration() # 目前未使用到
if heading > 180: # 大於180度轉換角度
    heading -= 360
```

未來工程代碼重點解析 - imx477畫面校正[資格賽]
```python
h, w = frame.shape[:2]
new_camera_matrix, roi = cv2.getOptimalNewCameraMatrix(camera_matrix, distortion_coefficents, (w, h), 0.12, (w, h))
undistorted_frame = cv2.undistort(frame, camera_matrix, distortion_coefficents, None, new_camera_matrix)
```