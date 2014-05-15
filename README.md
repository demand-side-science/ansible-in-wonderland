このリポジトリは Demand Side Science 会社ブログ内、『不思議の国のAnsible』のチュートリアルで使用する環境を再現するためのものです。



## 連載へのリンク

- [第1章 インフラの落とし穴にはまって](http://demand-side-science.jp/blog/2014/ansible-in-wonderland-01/)





## 動作要件

- OS (いずれも最新のリビジョンを推奨)
  - Mac OS (推奨)
  - Linux
  - Windows
- 空きメモリ容量 512MB以上
- 空きディスク容量 80GB以上(推奨)
- インターネット接続が可能であること
- 192.168.100.0/24 セグメントのIPアドレスが未使用であること


## セットアップ手順

### 1. VirtualBox のインストール

  こちらの公式サイトから、お使いのOSに適した最新版パッケージをダウンロードし、インストールしてください。
  https://www.virtualbox.org/wiki/Downloads

### 2. Vagrant のインストール

  こちらの公式サイトから、お使いのOSに適した最新版パッケージをダウンロードし、インストールしてください。
  http://www.vagrantup.com/downloads.html

### 3. 本リポジトリのダウンロード

  - [こちら](https://github.com/demand-side-science/ansible-in-wonderland/archive/master.zip)から Zip ファイルをダウンロードして適当な場所に解凍するか、

  - もしくは[こちらのページ](http://git-scm.com/book/ja/%E4%BD%BF%E3%81%84%E5%A7%8B%E3%82%81%E3%82%8B-Git%E3%81%AE%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB)を参考に ```git``` をインストールし、以下のコマンドを実行してください。

```
git clone https://github.com/demand-side-science/ansible-in-wonderland.git
```


## 使用方法

### 1. 仮想マシンの作成

本リポジトリをダウンロードした場所(Vagrantfileが存在する階層)で、以下のコマンドを実行します。
初回はイメージのダウンロード・セットアップが行われるため、数分程度の時間がかかります。

```
vagrant plugin install vagrant-vbguest
vagrant up
```

### 2. 仮想マシンへのログイン

```
vagrant ssh an11
```

```vagrant``` ユーザでのログインが行われます。
同様に、an12 へのログインも可能です。

- ネットワーク構成

![image](https://raw.githubusercontent.com/demand-side-science/ansible-in-wonderland/master/images/network.png)


### 3. alice ユーザになる

```
sudo -s -u alice
cd
```

これで、チュートリアルと同じ状態を再現できます。


## 仮想マシンの起動と終了

- 起動

```
vagrant up
```

- 停止

```
vagrant halt
```

- 仮想マシンの破棄

```
vagrant destroy
```

確認に対して ```y``` を入力すると仮想マシンの破棄がなされ、データが削除されます。

