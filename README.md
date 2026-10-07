# wsm-video-site

[wsm_tts_youtube](https://github.com/chikashimasaki-lgtm/wsm_tts_youtube)（private）の
**公開用ページ**だけを置くリポジトリ。GitHub Pages で配信する。

## なぜ必要か

Google の OAuth 同意画面を「テスト」から**「本番」へ公開する**には、Branding ページで
次の3つの公開URLが必須になる。これが未入力だと「アプリを公開」ボタンが有効にならない。

| Branding の項目 | このリポジトリのページ |
|---|---|
| アプリのホームページ | `index.html` |
| プライバシーポリシー | `privacy.html` |
| 利用規約 | `terms.html` |

同意画面が「テスト」のままだと、制限スコープのリフレッシュトークンが**約7日で失効**し、
無人で動く Cloud Run Job が `invalid_grant` で落ちる。本番公開はその恒久対策。

## 中身

静的HTML3枚と `style.css` のみ。スクリプト・Cookie・アクセス解析・シークレットは一切含まない。

## 公開URL

- ホーム: https://chikashimasaki-lgtm.github.io/wsm-video-site/
- プライバシーポリシー: https://chikashimasaki-lgtm.github.io/wsm-video-site/privacy.html
- 利用規約: https://chikashimasaki-lgtm.github.io/wsm-video-site/terms.html

## 編集するとき

内容は実装と一致させること。とくにスコープの表（`index.html` と `privacy.html`）は
`wsm_tts_youtube/cloudrun/auth_cloud.py` の `SCOPES` と揃える。
