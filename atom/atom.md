Atom
==

## Keymaps Customization
### キーマップ設定の開き方
1. ``ctrl-comma``で設定を開く
2. [Keybindings]を選択
3. キーバインドの説明文内の[your keymap file]のリンクを開く

### 特定のキーマップの無効化
```
'SELECTOR':
  'KEY_STROKE': 'unset!'
```

### セレクター``atom-text-editor:not([mini])``の意味
コードを書く部分以外


## markdown-preview
### mdファイルからhtmlファイルを生成
1. mdファイルを編集中に``ctrl-shift-M``でプレビューを開く
2. プレビュー上で右クリック
3. [Save as HTML...]でhtmlで保存

### プレビューのCSS変更
1. ``ctrl-comma``で設定を開く
2. [Themes]を選択
3. テーマの説明文内の[your stylesheet]のリンクを開く
4. ``.markdown-preview``クラス内に記述 
