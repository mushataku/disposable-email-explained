# 捨てメールの見分けかた

使い捨てメールアドレス（disposable email address / DEA）を、サイト側はどうやって見抜いているのか。
図解中心の1ページ資料です。専門知識なしで読めます。

**📖 https://mushataku.github.io/disposable-email-explained/**

*A Japanese-language visual explainer on how websites detect disposable email addresses.*

## 中身

1. メールアドレスは `@` の左右で役割が違う — 判定に使えるのは右だけ
2. 使い捨てメールとは何か。なぜサイト側が困るのか
3. 検知の正体は「ドメインを切り出してリストと照合する」だけ
4. **実物のブロックリストを開く** — 8,742行のテキストファイルの中身
5. リストに載っていない新しいドメインを、MXレコードで芋づる式に判定する方法
6. 分類したあと、弾くのが正解とは限らない話

## 出典と検証

ブロックリストは [disposable-email-domains](https://github.com/disposable-email-domains/disposable-email-domains)（パブリックドメイン）を使いました。

資料中の**行数・バイト数・行番号・前後の行はすべて実測値**です（2026年9月8日にダウンロードして確認）。
同じものは誰でも確認できます:

```sh
curl -sO https://raw.githubusercontent.com/disposable-email-domains/disposable-email-domains/main/disposable_email_blocklist.conf
wc -l disposable_email_blocklist.conf
grep -n '^kuku\.lu$' disposable_email_blocklist.conf
```

## 注意

このリストは広く使われている定番の1つですが、**どのサイトがどのリストを使っているかは公開されていません**。
「リストに載っている」＝「必ず弾かれる」ではない点にご注意ください。

## ライセンス

MIT（[LICENSE](LICENSE)）。ブロックリスト本体はこのリポジトリに含まれておらず、上記の出典がパブリックドメインで配布しています。
