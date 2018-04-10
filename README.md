[Mac の開発環境構築を自動化する（2017年晩夏編）](https://scrapbox.io/uknmr/Mac_%E3%81%AE%E9%96%8B%E7%99%BA%E7%92%B0%E5%A2%83%E6%A7%8B%E7%AF%89%E3%82%92%E8%87%AA%E5%8B%95%E5%8C%96%E3%81%99%E3%82%8B%EF%BC%882017%E5%B9%B4%E6%99%A9%E5%A4%8F%E7%B7%A8%EF%BC%89) で書いた playbook。

## つかいかた

### 準備編

とりあえず Xcode いれよう。

```bash
$ sudo xcodebuild -license
```

あと Homebrew をいれないと始まらない。

```bash
$ /usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)
$ brew doctor # 念のため
$ brew doctor # brew doctor でなんか言われたらね
```

Ansible も構築に必要なのでいれておく。

```bash
$ brew install ansible
```

GitHub からこの repository を落としてくる。
[これ](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/)をやっておく。

### Ansible の流しかた

```bash
$ ansible-playbook site.yml -vK
```

一部だけ流したい場合は、

```bash
$ ansible-playbook site.yml -vK --tags=homebrew,fish-shell
```

fisherman のスクリプト壊れてるんだけど、とりあえず…

```
$ curl -Lo ~/.config/fish/functions/fisher.fish --create-dirs https://git.io/fisher
```

### 構成

[Best Practices](http://docs.ansible.com/ansible/latest/playbooks_best_practices.html) を参考にした。


```bash
.
├── roles
│   ├── atom
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── vars
│   │       └── main.yml
│   ├── fish-shell
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── vars
│   │       └── main.yml
│   ├── homebrew
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── vars
│   │       └── main.yml
│   ├── homebrew-cask
│   │   ├── tasks
│   │   │   └── main.yml
│   │   └── vars
│   │       └── main.yml
│   └── mac-app-store
│       ├── tasks
│       │   └── main.yml
│       └── vars
│           └── main.yml
├── README.md
├── ansible.cfg
├── hosts
├── localhost.yml
└── site.yml
```

### その他

全然自動化できていない。それらをここに記しておく。

- Terminal のフォント設定を　Ricty for Powerline の 14px に変更する
- Spectacle を設定
  - アクセシビリティ権限を許可
  - background 機動
  - フルスクリーンを ⎇ + ⌘ + F による検索がつかえなくなるので ⎇ + ⌘ + M に変更する
- f.lux を設定
  - Daytime で 3,800K
- Google 日本語入力
  - 半角スペース
  - バックスラッシュ
- 入力ソース
  - Google 日本語 ひらがな
  - Google 日本語 英数半角
  - デフォルトを削除
- Chrome の検索設定を追加
- Gitify
  - ログイン
  - On Click, Mark as Read
  - Tray Icon only
- 一般
  - メニューバーと Dock を暗くする
  - メニューバーを自動的に表示 / 非表示
  - スクロールバーのクリック時: クリックされた場所にジャンプ