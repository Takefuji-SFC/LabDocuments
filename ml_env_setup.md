# 機械学習用環境構築ドキュメント

## これなんのドキュメント？
タイトル通り

## 環境構築ステップ
- Python入れる
- ライブラリ入れる
- 試してみる

環境はMacを前提としているのでそうでない人は適宜自分で読み替えてくだしあ。

## Python入れよう
### Pythonって？
オブジェクト指向のスクリプト言語。
オブジェクト指向とスクリプト言語の意味がわからないやつはググれ。

文法的に楽に書けて、書き方の幅が狭いため、誰が書いても同じ感じに書ける。というか同じ感じに書くように設計されている。

同僚であるRubyは自由だが、人によって書き方が大きく異る。

科学計算系のライブラリが豊富で、昨今の機械学習や統計系のライブラリが豊富。
機械学習やる人はまずこの言語からやると良いと言われてる。(自分もそう思う)

### Pythonのインストール
実はMacやLinuxにはOSでデフォルトでPythonが入っているのだが、OSのデフォルトのPythonはなるべく使わないほうがいい。

今回の環境構築では、仮想環境を作り上げるpyenvを入れて環境構築を行う。

### pyenvって？
ざっくり言うとPythonのバージョンをディレクトリごとに切り替えてくれる便利なやつ。
普段はこのPythonを使うようにして、OSのPythonにはなるべく触れないようにする。

### pyenvのインストール
以下の手順を踏む

- 1.homebrewが入っているか確認(入ってなかったら2で入れる)
- 2.homebrewをインストール
- 3.homebrewのアップデート
- 4.pyenvのインストール
- 5.Pythonのインストール
- (6.pyenv-virtualenvで環境をわかりやすくする)

### 1.homebrewが入っているか確認
`brew --version`
で確認。

出力を見て2か3へ。

### 2.homebrewをインストール
`/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
`

### 3.homebrewのアップデート
`brew update && brew upgrade`

### 4.pyenvのインストール
`brew install pyenv`

`echo 'export PYENV_ROOT="${HOME}/.pyenv"' >> ~/.bash_profile`

`echo 'export PATH="${PYENV_ROOT}/bin:$PATH"' >> ~/.bash_profile`

`echo 'eval "$(pyenv init -)"' >> ~/.bash_profile`

`exec $SHELL -l`

### 5.Pythonのインストール
`pyenv install 2.7.9`

`pyenv global 2.7.9`

これでpyenvにより、現在のPythonのバージョンは2.7.9に切り替わったはずです。
コマンドで`python`と打ってみましょう。
`Python 2.7.9`と出れば成功です。

さて、ここまではグローバルのPythonを設定しましたが、ディレクトリによってPythonのバージョンを切り変えたいと思いませんか？思いますよね？思います。

というわけで、研究会用のディレクトリを作り、それのバージョンを指定してみましょう。

作成したディレクトリまで移動し、インストールしたいPythonバージョンをインストールします。

例えば

`pyenv install 3.5.2`

とし、この3.5.2をこのディレクトリのPythonのバージョンとして設定します。

`pyenv local 3.5.2`

こうすることで、そのディレクトリだけPythonのバージョンを変わります。試しに`python`と打ってバージョンを確認してみてください。3.5.2に切り替わっているはずです。

### 機械学習用ライブラリのインストール
上の手順ではPythonを入れただけなので、これでは機械学習のプログラムは走りません。
最後に機械学習用のライブラリを入れて終わりにしましょう。
以下のコマンドを打ってください。

`pip install pandas`

`pip install sklearn`

この２つは機械学習をPythonで扱うのに必要な最低限のライブラリです。必ず入れましょう。

pipはPythonのライブラリを管理するパッケージ管理ツールです。詳しい使い方はご自身でググりやがれ。
