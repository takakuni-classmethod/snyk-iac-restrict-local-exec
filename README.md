## フォルダー構成

```
├── README.md
├── lib
│   ├── main.rego
│   └── testing
│       ├── main.rego
│       └── tfplan.rego
└── rules
    └── RULE_ID
        ├── fixtures
        │   ├── allowed.tf
        │   └── denied.tf
        ├── main.rego
        └── main_test.rego
```

次のファイルを各フォルダーで用意する。

- テストに合格するファイル
- テストに不合格するファイル
- カスタムルールを定義したmain.regoファイル
- テスト用のmain_test.regoファイル

## 手順

### スケルトンファイルの作成

```bash
snyk-iac-rules template --rule RULE_ID --format {hcl2,json,yaml,tf-plan}
```

#### 参考
```bash
Usage:
  snyk-iac-rules template [path] [flags]

Flags:
  -f, --format {hcl2,json,yaml,tf-plan}       provide rule format
  -h, --help                                  help for template
  -r, --rule string                           provide rule id
  -s, --severity {low,medium,high,critical}   provide rule severity (default low)
  -t, --title string                          provide rule title (default "Default title")
```

### テスト実行

```bash
snyk-iac-rules test
```

#### 参考

```bash
Usage:
  snyk-iac-rules test [path...] [flags]

Flags:
      --explain {fails,full,notes}   enable query explanations (default fails)
  -h, --help                         help for test
      --ignore strings               set file and directory names to ignore during loading (default [.*,fixtures])
  -r, --run string                   run only test cases matching the regular expression
      --timeout duration             set test timeout (default 5s)
  -v, --verbose                      set verbose logging mode
```