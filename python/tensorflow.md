TensorFlow
==

## インストール with virtualenv
TensorFlow用にpython仮想環境を構築し、そこにTensorFlowをインストールします。

1. pipとvirtualenvをインストール
```
sudo apt-get install python-pip python-dev python-virtualenv
```

2. virtualenvの仮想環境を構築
※ターゲットディレクトリはpython仮想環境のルートディレクトリになる
```
virtualenv --system-site-packages ターゲットディレクトリ
```

3. 仮想環境のアクティベート（仮想環境を使用する際に実行）
```
source ターゲットディレクトリ/bin/activate
```

4. 仮想環境にpipをインストール
```
(tensorflow)$ easy_install -U pip
```

5. TensorFlow for Python 2.7(CPU only)をインストール
```
(tensorflow)$ pip install --upgrade tensorflow
```
※失敗した場合は環境に合わせてtfBinaryURLを指定
```
(tensorflow)$ pip install --upgrade https://storage.googleapis.com/tensorflow/linux/cpu/tensorflow-1.4.1-cp27-none-linux_x86_64.whl
```

6. virtualenvの仮想環境実行を停止（仮想環境の使用を終了する際に実行）
```
(tensorflow)$ deactivate
```
