[Mac の開発環境構築を自動化する（2017年晩夏編）](https://scrapbox.io/uknmr/Mac_%E3%81%AE%E9%96%8B%E7%99%BA%E7%92%B0%E5%A2%83%E6%A7%8B%E7%AF%89%E3%82%92%E8%87%AA%E5%8B%95%E5%8C%96%E3%81%99%E3%82%8B%EF%BC%882017%E5%B9%B4%E6%99%A9%E5%A4%8F%E7%B7%A8%EF%BC%89) で書いた playbook。

## つかいかた

```bash
$ ansible-playbook site.yml -vK
```

一部だけ流したい場合は、

```bash
$ ansible-playbook site.yml -vK --tags=homebrew,fish-shell
```

## 構成

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
