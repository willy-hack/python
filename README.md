# <div align="center">python 指令說明 && 終端機指令</div>

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

終端指令`文件管理指令` - `ls`
```bash
ls # 掃描當前目錄所有文件及資料夾
ls -l # 詳細列表
ls -a # 輸出詳細列表
ls -lh # 輸出可讀文件
```

終端指令`文件管理指令` - `cd`
```bash
cd # 切換資料夾
cd ~ # 回到主目錄
cd .. # 上一資料夾
```

終端指令`文件管理指令` - `mkdir`
```bash
mkdir <資料夾名稱> # 新增資料夾
mkdir -p <資料夾一名稱>/<資料夾二名稱> # 一次新增多層資料夾
rmdir # 刪除空目錄
```

終端指令`文件管理指令` - `rm`
```bash
rm -r <資料夾名稱> # 刪除資料夾
rm -f <文件名稱> # 刪除文件
```

終端指令`文件管理指令` - `cp`
```bash
cp <檔案名稱> <檔案名稱2> # 複製文件
cp -r <資料夾名稱> <資料夾名稱2> # 複製資料夾
```

終端指令`文件管理指令` - `mv`
```bash
mv <原檔案名稱> <要更改的名稱> # 修改文件名稱
mv <檔案名稱> <目標資料夾> # 移動文件位置
```

終端指令`文件管理指令` - `其他`
```bash
pwd # 顯示當前目錄
touch <文件名稱> # 新增文件
```