PyCharm
==

## PyCharmのインストール
1. PyCharmを下記URLからダウンロード
```
https://www.jetbrains.com/pycharm/
```

2. インストールする場所（利用するユーザのrw権限がある場所）にダウンロードしたファイルを移動
```
mv ~/Downloads/pycharm-community-2017.x.x.tar.gz インストール先ディレクトリ
```

3. PyCharmの実行
```
インストール先ディレクトリ/bin/pycharm.sh
```

4. デスクトップアプリケーションに登録
```
emacs ~/.local/share/applications/pycharm.desktop

# 以下を記載
[Desktop Entry]
Version=2017.3.3
Type=Application
Name=PyCharm Community Edition
Icon=path/to/pycharm-installed-location/bin/pycharm.png
Exec="path/to/pycharm-installed-location/bin/pycharm.sh" %f
Comment=Develop with pleasure!
Categories=Development;IDE;
Terminal=false
```


## IDEの設定
### 1行の文字数設定
Hard wrap at 79
```
Settings... > Editor > Code Style > Python > Wrapping and Braces
```

### 空白行のスペース表示
Show whitespaces(Trailingにチェック)
```
Settings... > Editor > General > Appearance
```

###

## プロジェクト作成
1. Create New Project
2. Location（pycharmのワークスペース/プロジェクト名）
3. Interpreter（新規作成）

## TensorFlowの構築
1. Terminalを開く
2. pipをインストール
```
(venv)$ easy_install -U pip
```
3. TensorFlow for Python2.7(CPU only)をインストール
pip install --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-1.4.1-cp27-none-linux_x86_64.whl

4.
