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