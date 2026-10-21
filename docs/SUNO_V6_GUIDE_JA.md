# Suno v6 / v6-wild / v6-mini 活用ガイド

**2026年10月版** · [概要に戻る](../README.md)

原文：[Googleドキュメント](https://docs.google.com/document/d/1zbmTP5u-6xAdceDD5ZejNhnpkyElablYXuHyyzVFj-s/edit?usp=drivesdk)

> 本文は原資料を整理して掲載したものです。公式仕様、二次情報、個人の検証・推奨設定が混在します。現在の仕様や数値を独立に再検証したものではありません。

結論から言うと、いちばん安定するのは「V6-MINIで下書き → V6-WILDでアイデア出し（短く区切る）→ V6で仕上げ（Variety 0・Style Influence高め・長尺ならMax Mode）」という分業です。3モデルは品質の上下ではなく、役割の違いとして使い分けるのが正解です。

## 要点（TL;DR）

- 使い分け：V6＝狙いが決まっている曲の仕上げ用（Pro/Premier）。V6-WILD＝予想外の展開・質感を掘る探索用（Pro/Premier、当たり外れが大きい）。V6-MINI＝高速な下書き用（全プラン）。3モデルとも1回の生成で最大8分です。
- 最重要設定：スタイル指定を守らせたいときは Variety=0（公式FAQによると、Varietyはスタイルプロンプトそのものを書き換える機能です）。長尺、原曲に忠実なカバー、ボーカルの一貫性が必要な場面では Max Mode を使います（公式推奨。クレジット消費は増えます）。プロンプトは短いタグの羅列ではなく、楽器ごとの役割を書いた文章形式が有効です。
- 注意点：V5.5以前のモデルはすべて廃止され、元には戻せません。Redditでは「こもる・ボーカルが埋もれる・没個性」という不満が多く出ています。対策は、MINIの下書きをV6でカバー/リマスターして音を安定させること、プロンプトを「プロデューサーへの指示書」のように書くこと、後半の崩れを毎回確認することです。

## 主な調査結果

#### 1. 公式が発表している事実（2026年9月9日リリース）

- Sunoは2026年9月9日、CEOのMikey Shulman名義のブログ「Introducing v6」でV6ファミリーを発表しました。Warner Music Group、BMG、Believeと共同で開発した「新世代」モデルとされています。
- 公式による各モデルの位置づけは次のとおりです。
- v6：「reliable, precise and consistently delivers polished music across every genre and style. When you know what you want, v6 helps you get there.」（Pro/Premier向け）
- v6-wild：「less predictable and more varied, producing unexpected, textured and ambitious results. It gives you new ideas to riff on, build from or bring back into v6 for further refinement.」（Pro/Premier向け）
- v6-mini：「a faster, more efficient version available to everyone」（全プラン）
- ヘルプセンターの「What's new in v6?」には、3モデルとも1回の生成で最大8分まで作れること、Remix & Edit（Extend、Cover、Replace Section など）、Custom Models、Suno SoundsがすべてV6で動いていることが書かれています。
- v6 FAQ によると、V6以前のモデルはすべて廃止されました。過去の曲はライブラリに残り、再生・共有・リマスター・カバーはできますが、新しく作るものはすべてV6系で生成されます。既存のCustom Modelも自動的にV6ベースへ更新されます。
- クレジット消費は従来と同じで、1回の生成で2曲、合計10クレジットです。ただし画像や動画を多く入力した場合とMax Modeを使った場合は消費が増えます。

#### 2. V6で新しくできるようになったこと（公式）

- 自然な言葉での部分編集（例：「Change the chorus so it's sung by a gospel choir」）
- 一語単位の歌詞差し替え（例：「Change the lyric from 'love' to 'light'」）
- 複数の曲を組み合わせたマッシュアップ（例：「Take the vocals from x, drums from y…」）
- サンプリングとビート構築の一括指示（例：「Sample the riff at 0:45, isolate the guitar, build a beat around it」）
- テキスト・音声・画像・動画を組み合わせた入力（Simple modeでは、Cover/Remix/Extendのどれを使うかをモデルが自分で判断する）

#### 3. 2つの重要な設定項目（公式FAQの定義）

- Variety：「adjusting and updating your style prompts. If you'd like to retain full control of your style tags, reduce the Variety slider to 0.」つまり、ランダム性の幅を広げる機能ではなく、ユーザーが書いたスタイル指定をAIが書き換える機能です。ytyng.comの検証では、10〜12語のタグ指定が30〜50語の文章に膨らみ、指定していない楽器（handclaps、brass glissandoなど）や性別（female/male）が勝手に追加されていました。
- Max Mode：「best for: songs longer than two minutes, covers where you want the result to stay close to the original, transferring the style of one song onto another, and keeping vocals and style consistent through the whole track.」音質を上げる機能ではなく、狙いを外さないための機能と考えてください。ytyng.comはクレジット消費が倍になると報告しており、Roo's Newsletterも「Double the spend per generation and your Pro draft ceiling halves from 500 songs to 250.」（1回あたりの消費が倍になり、Proプランで作れる下書きの上限が500曲から250曲に半減する）と試算しています。
- Weirdness／Style Influence（ヘルプセンター「Creative Sliders」より）：Weirdnessは「Safe to Chaos」の範囲で、50%が標準。Style Influenceは「Loose to Strong」の範囲で、スタイル指定への忠実さを調整します。

## 詳細

### A. モデル別の使い方

| モデル | 向いている用途 | 推奨設定（出発点） | 主なリスク |
|---|---|---|---|
| V6 ／ 構成・歌詞・ボーカル像が決まった曲の仕上げ、カバーの安定化 ／ Variety 0／Style Influence 70〜80%／Weirdness 15〜25%／2分を超える曲はMax Mode ON ／ 整っているが平板、ボーカルのグルーヴが弱い |
| V6-WILD ／ リフ探し、イントロ違い、質感の探索、ジャンル混合 ／ Weirdnessは低めから始めて1つずつ上げる／Max Mode ON推奨（ytyng.comの主観評価） ／ Roo's Newsletterによると、初期の実機テストで「roughly half of v6-wild generations coming back unusable」（生成の約半分が使えない）との報告あり（同誌は「one tester's sample rather than a benchmark」＝一人の検証例であり、ベンチマークではないと注記）。後半の崩れ、ボーカルのにじみ |
| V6-MINI ／ メロディや全体構成の高速な下書き、歌詞の試し打ち、無料での探索 ／ プロンプトは短く単純に ／ デモ品質で、仕上げには向かない |
デモ品質で、仕上げには向かない
- 公式の推奨フローも「WILDで出したアイデアをV6に持ち帰って仕上げる」形です。
- Grammy投票権を持つエンジニアのSamori Colesは、V5.5と3つのV6モデルを同じ条件で比較しました。評価は次のとおりです（aimusicpreneur経由）。
- V6は音（暖かさ・広がり・低域）でV5.5に勝つが、ボーカルのグルーヴでは負ける
- WILDは曲によって当たり外れが大きい
- MINIは下書き用
- Max Modeはカバーを原曲に近づける効果があり、2分を超える曲なら倍のクレジットを払う価値がある
- 一語差し替え機能が最も実用的

### B. Redditで共有されている実践的なコツ

> ※ Redditのページを直接開くことはできなかったため、引用はAIReiterとUndetectrによる二次引用です（スレッドURLは確認済み）。
**1. MINIで作った曲をV6でカバー/リマスターして安定させる**
- u/New_Lettuce_8778：「You can also take the v6 mini versions and cover them in v6 Pro or Wild, and it really does a good job of stabilizing the sound」
- u/Ok-Acanthaceae-5243：V6のボーカルが「child's karaoke toy」のように聞こえる問題はMINIでは起きず、V6でリマスターすると改善したと報告しています。

#### 2. MINIは下書き、Proは艶出し、WILDは楽器の質感づけ

- u/Ok-Acanthaceae-5243：「Mini is best for complete draft, hitting all the parts I need with some rough edges.」

#### 3. WILDは使いどころを限定する

- u/candeloro1：「riff mining…It's bat shit crazy but that's what I'm after」
- u/Objective_Mousse7216：Weirdnessを0にしないと「random garbage」になると報告しています。
- u/ShitFartDoodoo：「we're all getting wildly different experiences」
- 体験談が人によって大きく違うので、自分のジャンルで試してから判断するのが前提です。

#### 4. スタイル欄は決まった順番で書く

- u/Auree_Gil：「Genre -> Vocals -> Drums -> Guitars -> Bass -> Other Instruments -> Arrangement/Energy -> Production Quality -> Ending Instruction -> Sliders」の順に書いたらサビが良くなったと報告しています。

#### 5. プロデューサーに話しかけるように書く

- スレッド「I owe suno v6 an apology」で、u/frescomafiaが「You have to actually talk to it like you're talking to a producer.」と書いています。

#### 6. 禁止事項を足すのではなく、余計な言葉を削る

- 叫び声が止まらない問題では、「叫ぶな」と指示を追加しても直らず、プロンプトから単語を減らすほうが効いたと報告されています。

#### 7. 後半の崩れに注意する

- 「start crisp, but around the 90-second mark, the mix completely falls apart」という報告があります。
- 対策は、Max Modeを使う、生成する長さを短くする、良い部分だけ残してExtendまたはReplace Sectionで直す、の3つです。

#### 8. Suno公式チュートリアルの補足

- 不完全さや生っぽさが欲しいときは、そのことをはっきり書き、楽器構成・録音の質感・演奏の様子を描写するよう勧めています（Undetectr経由）。

### C. プロンプトと歌詞タグの書き方

- スタイル欄は文章で書く：Roo's Newsletterは、V6ではタグの羅列よりも「ジャンル→BPM→グルーヴ→各楽器が何をしているか→ボーカルの声質と歌い方→曲の流れ（感情の起伏）→ミックスの質感」を2〜3文で書くほうが良いとしています。V5.5の頃の「タグは5〜8個がベスト」という助言は撤回されています。
- 入れたくない要素はExclude Styles欄へ：スタイル欄に「no autotune」と書いても効きません。Exclude欄に短い語句で入れます。
- アーティスト名は使えない：年代、楽器、声質に分解して書きます。日本語のnote記事でも「1998 Shibuya, MD Walkman…」のような情景描写が効くと紹介されています。
- スタイル欄は英語、歌詞は日本語が現時点の最適解とされています（note系の日本語ガイド複数）。韓国のDCinsideでは、日本語の歌詞を入れるとVarietyが日本語のスタイル指定を生成して品質が落ちる場合がある、という未検証の報告もあります。日本語の曲ではVariety 0がより重要です。
- 歌詞タグ：［Verse］［Pre-Chorus］［Chorus］［Bridge］［Outro］などは行頭に単独で置き、タグ自体は英語にします。サビとそれ以外が同じように聞こえる場合は、[Chorus | full band, doubled vocals] のようにセクションの演出を書き添えます。
- 読み間違い対策：漢字の誤読が気になる箇所はひらがなに直す。助詞の「は」「へ」は「わ」「え」と表記する。V6では会話調の歌詞が語り（spoken）になりやすいので、スタイル欄で「not as actual dialogue, but through a passionate vocal performance」のように歌わせる意図を書く（note「[Suno v6] Definitive Guide! How to Create Duets」より）。
- 曲の長さ：V6は長めに生成する傾向があります（HookGeniusの検証では約3:10）。尺を決めたいときはDurationをCustomにします。

### D. 関連機能との組み合わせ

- Cover：曲調・歌い手・テンポを大きく変える用途です。原曲に近づけたい場合はMax Mode ONにします。MINIで作った曲をV6でカバーする方法は、音の安定化策としても有効です。
- Remaster（公式ヘルプ）：「happy with the structure, lyrics, and performance」の状態で、音質・ミックスバランス・発音の明瞭さを改善するための機能です。「not intended for changing lyrics or drastically altering the musical style」とされています。構成に問題がある曲はRemasterでは直りません。
- Extend／Replace Section／一語差し替え：崩れた区間だけを修正するのに使います。曲全体を作り直すより、クレジットの節約にもなります。
- Persona／Voices：2025年12月以降、Create画面のPersonasボタンはVoicesに置き換えられ、Style PersonasはVoicesメニューの中に残っています（公式Voices FAQ）。ただし公式Voices FAQは2026年3月版のままで、まだ「v5.5を選択」と書かれています。V6でのVoices/Personaの挙動を説明した公式記事は確認できませんでした。Jack Righteousは、V6でExtendするとPersonaが次のセクションににじむ（声が切り替わらない）という報告を紹介しています。対策は、ボーカルの切れ目（楽器だけの区間）で区切ってから延長することです。
- Custom Models：自動的にV6ベースへ更新されます。声や音色の一貫性を保ちたい場合の有力な選択肢です。

### E. よくある失敗と対策

| 症状 | 主な原因 | 対策 |
|---|---|---|
| 指定したタグが無視される、勝手に楽器が追加される | Varietyがスタイル指定を書き換えている | Variety 0にする。そのうえでStyle Influenceを上げる |
| 同じプロンプトで2曲がまるで別の曲になる | Varietyが高い／2曲の差がもともと大きい | 検証中はVariety 0にし、1回分の結果だけで判断しない |
| こもる、ボーカルが埋もれる | V6の音作りの傾向（MusicRadar〔2026年9月17日〕が報じたRedditユーザーの声：「muffled, dull and strangely lifeless… the vocals are often buried, the high end feels almost completely gone」。ytyng.comの測定ではV6以前と比べ「8-12kHz is down by 2.3dB or more」） | 楽器の指示を減らす、MINIの下書きをV6でリマスター、ボーカルの扱いを明記、WILD（Weirdness約20／Style Influence約80）で試す |
| 90秒あたりから崩れる、声が変わる | 長尺生成での一貫性の低下 | Max Mode ON、生成を短く区切る、Replace Sectionで直す |
| WILDが雑音っぽい | Weirdness・Varietyと実験的なモデル特性が重なっている | Weirdnessから先に下げる。用途を短いインストやリフ探しに限定する |
| 叫び声や過剰な表現が止まらない | 指示が多すぎる | 禁止事項を足さず、プロンプトの単語を減らす |
| 昔のプロンプトが平板に聞こえる | V5向けの「タグの羅列」形式 | 楽器の役割を書いた文章形式に書き直す |
楽器の役割を書いた文章形式に書き直す

## 注意事項・未検証情報

- Redditの一次情報：Redditのページを直接開くことはできなかったため、u/〜の引用はすべてAIReiterとUndetectrによる二次引用です。Undetectrは、AI生成音楽の検出を回避するツールを販売している業者である点に注意してください。
- 数値設定：Weirdness 20%、Style Influence 75%などの数値は業者やユーザーの経験則であり、Sunoの公式値ではありません。
- 評価が割れている：V6の評価ははっきり分かれています。MusicRadar（2026年9月17日）は、Reddit上の「muffled, generic, soulless garbage」や解約宣言を報じました。一方で、aimusicpreneurによるとGrammy投票権を持つエンジニアのSamori Colesは「v6 the better sounding record and the weaker vocal performance」（同じプロンプトで比べると、音としてはV6が上だがボーカルの表現は弱い）と評価しており、逆にGearnewsのMarcus Schmahl（2026年9月22日）は自身の検証でV6のボーカルが「sound flatter now… less depth, less body, less overall dynamics」になったと述べています。訓練データの縮小が原因だという説はユーザーの推測にとどまり、Suno自身はMusic Business Worldwide（2026年9月22日、Variety経由）に対し、V6は「content licensed from our partners, interactions including creations and preference signals from our community, and the accumulated learnings from our team」で訓練したと説明しています。
- 訴訟リスク：SonyとUMGは2026年9月18日、マサチューセッツ連邦地裁に45ページの訴状を提出しました（Variety報道）。V6を「fruit of the same poisoned tree」と呼び、「training a 'new' model on the outputs of an infringing model does not eliminate the infringement; it launders it」と主張しています。LawCommentaryによると、訴状は特定済みの60,202件の録音がコピーされたとも主張しています。商用リリースの前に、規約やライセンスの最新状況を確認してください。
- 未確認事項：V6でのVoices/Personaの公式仕様、日本語の発音改善の程度は、今回の調査では確認できませんでした。

## 参考資料・出典

- Suno「Introducing v6」 <https://suno.com/blog/introducing-v6>
- Suno リリースノート <https://suno.com/release-notes/introducing-v6>
- Suno ヘルプ（What's new in v6?） <https://help.suno.com/en/articles/13924801>
- Suno ヘルプ（v6 FAQ） <https://help.suno.com/en/articles/13924481>
- Suno ヘルプ（Voices FAQ） <https://help.suno.com/en/articles/11362433>
- ytyng.com <https://www.ytyng.com/en/blog/suno-v6-review-variety-max-mode-spectrum>
- Roo's Newsletter <https://roo.beehiiv.com/p/suno-v6-features> ／ <https://roo.beehiiv.com/p/best-suno-prompts-v6>
- AIReiter <https://aireiter.com/blog/suno-v6-vs-v6-wild-vs-v6-mini>
- Undetectr <https://undetectr.com/blog/suno-v6-pro-production-prompts>
- aimusicpreneur <https://www.aimusicpreneur.com/ai-tools-news/suno-v6-user-backlash-cancellations-licensed-training-data/>
- MusicRadar <https://www.musicradar.com/music-tech/im-cancelling-my-subscription-suno-users-slam-its-v6-update-as-muffled-generic-soulless-garbage>
- Jack Righteous <https://jackrighteous.com/en-us/blogs/guides-using-suno-ai-music-creation/suno-v6-voice-persona-drift-extend-bleeding-sections-fix>
- HookGenius <https://hookgenius.app/learn/suno-song-structure-tips/>
