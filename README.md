# Suno v6 活用ガイド

**v6 / v6-wild / v6-mini — 2026年10月版**

Suno v6系モデルの使い分け、プロンプト、設定、編集機能、トラブル対処を日本語でまとめた調査ノートです。公式発表・ヘルプとコミュニティの報告を分けて読みやすく整理しています。

> [!IMPORTANT]
> 本資料は2026年10月21日作成の調査文書を整理したものです。掲載内容には公式発表の要約と第三者の体験談・推奨値が含まれます。仕様や法的事項を独立に検証・保証するものではありません。

## まず結論

| モデル | 主な役割 | 使いどころ |
|---|---|---|
| **v6-mini** | 下書き | メロディ・歌詞・構成を素早く試す |
| **v6-wild** | 発想の探索 | 予想外のリフ、音色、ジャンル混合 |
| **v6** | 仕上げ | 構成・歌声・スタイルを狙って整える |

**基本的な制作フロー：** miniで下書き → wildでアイデアを探す → v6で仕上げる。

## 最初に試したい設定

- **Variety 0：** スタイル指定をできるだけ保持したいときの出発点（原資料で紹介された公式FAQの説明に基づく）。
- **Style Influence：** 指定スタイルへの忠実度を調整。70〜80%などは**コミュニティ等の経験則**で、公式最適値ではありません。
- **Weirdness：** 安定性と意外性を調整。50%が標準とされています。
- **Max Mode：** 原資料では長めの曲、カバー、声・スタイルの一貫性が必要な制作向けとして紹介。クレジット増に注意。

## 目次

1. [公式発表と主な変更点](docs/SUNO_V6_GUIDE_JA.md#主な調査結果)
2. [モデル別の使い方](docs/SUNO_V6_GUIDE_JA.md#a-モデル別の使い方)
3. [Reddit等の実践的なコツ](docs/SUNO_V6_GUIDE_JA.md#b-redditで共有されている実践的なコツ)
4. [プロンプトと歌詞タグ](docs/SUNO_V6_GUIDE_JA.md#c-プロンプトと歌詞タグの書き方)
5. [Cover・Remasterなどの関連機能](docs/SUNO_V6_GUIDE_JA.md#d-関連機能との組み合わせ)
6. [よくある失敗と対策](docs/SUNO_V6_GUIDE_JA.md#e-よくある失敗と対策)
7. [注意事項と出典](docs/SUNO_V6_GUIDE_JA.md#注意事項未検証情報)

### 📖 [詳しいガイド全文を読む](docs/SUNO_V6_GUIDE_JA.md)

## 主要な公式リンク

- [Introducing v6](https://suno.com/blog/introducing-v6)
- [Suno リリースノート](https://suno.com/release-notes/introducing-v6)
- [What's new in v6?](https://help.suno.com/en/articles/13924801)
- [v6 FAQ](https://help.suno.com/en/articles/13924481)

---

**原資料：** [Googleドキュメント](https://docs.google.com/document/d/1zbmTP5u-6xAdceDD5ZejNhnpkyElablYXuHyyzVFj-s/edit?usp=drivesdk)  
**言語：** 日本語  
**注記：** Suno公式とは無関係の非公式ガイドです。
