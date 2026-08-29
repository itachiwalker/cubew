# 🎲 Cube Puzzle Simulator

ブラウザで動作する3x3キューブパズル（ルービックキューブやGANなど）のシミュレーターです。  
[GitHub Pages](https://itachiwalker.github.io/cubew) にデプロイしています。

**現在のバージョン: v3.48.x**

<!-- TODO: 下記のscreenshot.pngを実際のスクリーンショット画像に差し替えてください（cubewリポジトリ直下に配置） -->
![cubewのスクリーンショット](screenshot.png)

---

## 🚀 起動方法

GitHub Pages [https://itachiwalker.github.io/cubew](https://itachiwalker.github.io/cubew) を開くだけで動作します。  
動作確認済み：Windows (Firefox / Chrome) · Android (Chrome) · iPhone (Safari)

---

## ✨ 主な機能

| 機能 | 説明 |
|------|------|
| スワイプ回転 | 面をスワイプして直感的に回転。高速連続スワイプはバッファリングで取りこぼしなく処理 |
| <img src="icons/icon-wide.svg" width="14" align="absmiddle">ワイド / <img src="icons/icon-double.svg" width="14" align="absmiddle">ダブルトグル | 次の1回のスワイプ（キーボード操作含む）だけ、ワイド回転（Rw等）・2倍回転（U2等）を適用する一回限りのトグル |
| ダブルタップコマンド | 各面のマスをダブルタップで登録済みコマンドを自動実行。Undo（背景ダブルタップ）は1回でコマンド全手数分を一括で戻る |
| コマンド設定（<img src="icons/icon-cmd.svg" width="14" align="absmiddle">） | 長押しで記録モードに入り、キューブ操作をコマンドとして登録。他面・左右対称・U面への自動コピー対応 |
| スクランブル（<img src="icons/icon-shuffle.svg" width="14" align="absmiddle">） | 100手ランダム（前手と同じ面を除いた5面からランダム選択）・速度演出付き |
| 履歴ナビゲーション | <img src="icons/icon-rev.svg" width="14" align="absmiddle"><img src="icons/icon-first.svg" width="14" align="absmiddle"><img src="icons/icon-back.svg" width="14" align="absmiddle"><img src="icons/icon-go.svg" width="14" align="absmiddle"><img src="icons/icon-last.svg" width="14" align="absmiddle"><img src="icons/icon-play.svg" width="14" align="absmiddle"> で自動再生・逆再生含む全履歴を操作。ナビゲーション中は次の手を矢印でキューブ上に表示。末尾/先頭で順再生/逆再生を押すと、反対側から全履歴を再生する形でラップアラウンドする |
| 視点ピン留め（<img src="icons/icon-campin.svg" width="14" align="absmiddle">） | 自由/試験ブラウジング中、またはスタンドアロンのステップ実行（SbS）中に、下の「コマンド再現」ボタンとペアで表示（履歴に`CAM()`が無い場合はDisabled）。ON時、<img src="icons/icon-first.svg" width="14" align="absmiddle"><img src="icons/icon-back.svg" width="14" align="absmiddle"><img src="icons/icon-go.svg" width="14" align="absmiddle"><img src="icons/icon-last.svg" width="14" align="absmiddle"><img src="icons/icon-rev.svg" width="14" align="absmiddle"><img src="icons/icon-play.svg" width="14" align="absmiddle">操作でその手を実際に操作した瞬間の視点を再現（SbSの場合は宣言された`CAM()`視点）。オートプレイ中は背景ドラッグとカメラ系3ボタン（<img src="icons/icon-home.svg" width="14" align="absmiddle"><img src="icons/icon-rock.svg" width="14" align="absmiddle"><img src="icons/icon-spin.svg" width="14" align="absmiddle">）を自動的に無効化 |
| コマンド再現（<img src="icons/icon-cmd.svg" width="14" align="absmiddle">） | 視点ピン留めボタンと同じ場面で、ペアで表示（履歴にダブルタップコマンド`C_Xn`が無い場合はDisabled）。チェック時（既定）は<img src="icons/icon-first.svg" width="14" align="absmiddle"><img src="icons/icon-back.svg" width="14" align="absmiddle"><img src="icons/icon-go.svg" width="14" align="absmiddle"><img src="icons/icon-last.svg" width="14" align="absmiddle"><img src="icons/icon-play.svg" width="14" align="absmiddle">操作でコマンドを1つの塊としてまとめて再現し、⏵自動再生中はその開始位置に⌖が一瞬光る。アンチェック時は、コマンドも他の手と同様に1手ずつバラして扱う |
| 回転ボタンパッド（<img src="icons/icon-kbd.svg" width="14" align="absmiddle">） | U/D/E, R/L/M, F/B/S, x/y/z に加えワイド回転（Uw/Dw/Rw/Lw/Fw/Bw）も含む全6行のボタン群 |
| ステップ実行（SbS） | SETダイアログで手順文字列を「Step by Step」モードで実行。矢印ガイドに従ってスワイプで1手ずつ進める |
| 照準オーバーレイ（C_XX） | SbS手順中に指定マスに照準（<img src="icons/icon-cmd.svg" width="14" align="absmiddle"> = 円＋貫通十字線）を表示。ダブルタップまたは<img src="icons/icon-go.svg" width="14" align="absmiddle">でコマンドを自動実行 |
| ガイド矢印 | ナビゲーション・ステップ実行中にキューブ上に次の手をカラーフェードイン矢印で表示。180°は「×2」付き |
| 視点指定（CAM） | SbS手順中に`CAM(θ,φ)`でカメラ視点を指定。直前に宣言された最も近いCAMがforward/reverse共通で使われ、同じCAMグループ内ではユーザーの手動視点調整が保持される |
| FACE補正（<img src="icons/icon-face.svg" width="14" align="absmiddle">） | どの向きからでも正面=緑・上面=白に自動補正 |
| キューブ状態設定（<img src="icons/icon-set.svg" width="14" align="absmiddle">） | タブ構成（設定／試験／履歴）。設定タブはkociemba形式54文字での状態読み書き・コマンド実行（ワイルドカード W/w/面色小文字 対応）。履歴タブは初期状態文字列と、回転コマンド文字列3種類（通常版、視点が変化した箇所に`CAM(θ,φ)`を挿入した版、さらにダブルタップコマンドを`C_key(seq)`として復元した版）を、それぞれ手数付きで省略表示しつつコピーボタン付きで表示（コピーは省略前の全文）。非チュートリアルのステップ実行（SbS）中・試験中も開くことができ、その場合は履歴タブのみ表示（進行中の状態把握用、閲覧専用。設定／試験タブは非表示）。SET→自動実行や外部ソルバーによる解法実行中は、ストップウォッチ欄に「自動実行」と表示され、ナビバーには実際の進捗（完了手数/総手数）が表示され、完了するまで他のほとんどの操作が無効化される |
| 外部ソルバー（<img src="icons/icon-solve.svg" width="14" align="absmiddle">） | 状態検証・確認ダイアログを経て6面を自動で揃える。解法をカウントダウン後に自動実行。サーバーの起動待ち（Render無料枠のスリープ復帰）のため、アプリ起動から約1分間、および使用後1分間（クールダウン）は利用不可。この間、ボタン直下に細いプログレスバーが表示され、待ち時間ぶん減っていく（ボタンも無効化）。実際に解法を実行中は、他のほとんどの操作が無効化される（RESETのみ有効で、押すと中断できる） |
| 試験モード（SET画面「試験」タブ） | 初期状態・ゴール状態を指定して自由に操作。初期状態欄はSET画面を開いた時点のキューブ状態で自動初期化。ゴール状態と一致すると自動でお祝い演出。専用の「最初からやり直す」ボタンで確認なしに初期状態へ即リセット可能。RESET（⊞）はモード終了（確認ダイアログ経由）として機能 |
| ストップウォッチ | スクランブル後の最初の手動操作で自動開始・6面揃いで自動停止。停止時に順位表示（圏外含む）。白点滅中タップでハイスコア表示 |
| ハイスコア | スクランブル後に6面揃えたタイムと手数を上位10件保存。クリア後にハイスコア画面を自動表示・今回のタイムを強調。500手以内で揃えた場合、該当行に<img src="icons/icon-play.svg" width="14" align="absmiddle">ボタンが表示され、押すとその解法をステップ実行（視点移動・ダブルタップコマンド含む、最後はホーム視点で終了）として再生できる。再生中は、ベストタイムの表示位置にその解法のタイトル（日付・手数・タイム）が表示される |
| お祝い演出 | 6面揃えると花火・視点回転（まずホームポジションへ移動してから水平に1周、着地はスムーズに減速）・メッセージ表示（9言語対応、長文は横スクロール） |
| 展開図（<img src="icons/icon-net.svg" width="14" align="absmiddle">） | 常時表示、操作に連動してリアルタイム更新。3パターンのレイアウトを循環切替 |
| チュートリアル | LBL法の段階的レッスン・試験（初期状態→完成系を目指す自由操作）・用語解説の3種類のコンテンツで構成。矢印ガイド・照準・視点移動でステップごとに誘導。9言語対応。画面右下の📚ボタンから起動。「<img src="icons/icon-rev.svg" width="14" align="absmiddle">前へ」は進捗があれば現在のレッスン/試験をリセット、無ければ前の項目へ移動 |
| コマンド一括登録 | チュートリアル一覧の各レベル見出しに「<img src="icons/icon-cmd.svg" width="14" align="absmiddle"> まとめて登録」ボタン。レベル内全レッスンのコマンドを一度に登録・矛盾検出（レッスン間で同じマスに異なる内容がある場合の作者向け警告） |
| チュートリアル記法 | `C_F3(seq)`=照準コマンド / `R(F)`=矢印面限定 / `CAM(θ,φ)`=視点移動（2引数） / `X2'`=方向付き180° |
| シェア機能 | Web Share APIでアプリのURLを共有（<img src="icons/icon-menu.svg" width="14" align="absmiddle">メニュー） |
| QRコード表示 | 現在のURLをQRコードで表示（<img src="icons/icon-menu.svg" width="14" align="absmiddle">メニュー） |
| <img src="icons/icon-menu.svg" width="14" align="absmiddle"> メニュー | 設定・シェア・QRコード・ヘルプ・ハイスコア・ライセンス |
| 設定画面 | 言語設定（9言語）・速度設定（4段階）・座標軸表示設定 |
| ライセンス表示 | 使用OSSのライセンス全文を表示（<img src="icons/icon-menu.svg" width="14" align="absmiddle"> → ライセンス） |
| ツールチップ（<img src="icons/icon-help.svg" width="14" align="absmiddle">） | 4段階トグル: 簡易ヘルプページ → 左パネル → 右パネル → 消去。ページロード時は自動で案内表示 |
| 多言語対応 | 日本語・中文・Français・English・한국어・Español・Português・Deutsch・Русский（9言語） |
| localStorage 保存 | 速度・言語・座標軸・コマンド設定・ピン留め設定・ハイスコアをブラウザ再起動後も保持 |

---

## 🎮 操作方法

### タッチ・マウス

| 操作 | 動作 |
|------|------|
| キューブ面をスワイプ | その層を90度回転 |
| キューブ面をダブルタップ | 登録済みコマンドを実行 |
| キューブ面を長押し | コマンドを記録・登録 |
| 背景をダブルタップ | Undo（自由操作中）/ <img src="icons/icon-back.svg" width="14" align="absmiddle">1手前（ナビゲーション中） |
| 背景をドラッグ | 視点を移動（アニメーション中も操作可。オートプレイ中かつピン留めONの場合は無効） |
| 2本指ピンチ | ズームイン/アウト |
| タイマー（白点滅中）をタップ | ハイスコア画面を表示 |

### キーボードショートカット

| キー | 動作 |
|------|------|
| u/U d/D f/F b/B l/L r/R | 各面を時計/反時計回り |
| m/M e/E s/S | M/E/S層を時計/反時計回り |
| x/X y/Y z/Z | キューブ全体をX/Y/Z軸で回転 |
| w | <img src="icons/icon-wide.svg" width="14" align="absmiddle">（ワイド）トグルON/OFF |
| 2 | <img src="icons/icon-double.svg" width="14" align="absmiddle">（ダブル）トグルON/OFF |
| Back Space | Undo |
| h | 視点をホームに戻す |
| ← / → | ブラウジング/SbS中に<img src="icons/icon-back.svg" width="14" align="absmiddle">/<img src="icons/icon-go.svg" width="14" align="absmiddle"> |

---

## 🔘 ボタン一覧

### 上部（ナビゲーション）

| ボタン | 機能 |
|--------|------|
| <img src="icons/icon-rev.svg" width="18" align="absmiddle"> <img src="icons/icon-play.svg" width="18" align="absmiddle"> | 逆再生 / 順再生（履歴の自動移動） |
| <img src="icons/icon-first.svg" width="18" align="absmiddle"> <img src="icons/icon-back.svg" width="18" align="absmiddle"> <img src="icons/icon-go.svg" width="18" align="absmiddle"> <img src="icons/icon-last.svg" width="18" align="absmiddle"> | 履歴の先頭/前/次/末尾へ移動 |

### 右パネル

| ボタン | 機能 |
|--------|------|
| <img src="icons/icon-reset.svg" width="18" align="absmiddle"> | リセット（チュートリアル中は常にDisabled。「<img src="icons/icon-rev.svg" width="14" align="absmiddle">前へ」に統合） |
| <img src="icons/icon-shuffle.svg" width="18" align="absmiddle"> | スクランブル |
| <img src="icons/icon-face.svg" width="18" align="absmiddle"> | FACE補正 |
| <img src="icons/icon-set.svg" width="18" align="absmiddle"> | キューブ状態設定（設定／試験／履歴タブ） |
| <img src="icons/icon-solve.svg" width="18" align="absmiddle"> | 外部ソルバー（状態検証→確認ダイアログ→自動実行） |
| <img src="icons/icon-cmd.svg" width="18" align="absmiddle"> | コマンド設定ダイアログ |

### 左パネル

| ボタン | 機能 |
|--------|------|
| <img src="icons/icon-net.svg" width="18" align="absmiddle"> | 展開図の表示/非表示（3パターン循環） |
| <img src="icons/icon-kbd.svg" width="18" align="absmiddle"> | 回転ボタンパッドの表示/非表示 |
| <img src="icons/icon-wide.svg" width="18" align="absmiddle"> | 次の1回のスワイプをワイド回転にする（中央層のスワイプはx/y/z等キューブ全体の回転、端のスライスはUw/Rw等2層分の回転になる） |
| <img src="icons/icon-double.svg" width="18" align="absmiddle"> | 次の1回のスワイプを2倍回転にする（⬱との同時ONも可） |

### 下部パネル

| ボタン | 機能 |
|--------|------|
| <img src="icons/icon-menu.svg" width="18" align="absmiddle"> | メニュー（このアプリについて・シェア・QRコード・設定・ヘルプ・ハイスコア・ライセンス） |
| <img src="icons/icon-help.svg" width="18" align="absmiddle"> | ツールチップ表示（4段階トグル）。ロード時は自動で案内表示。チュートリアル中はDisabled |
| <img src="icons/icon-rock.svg" width="18" align="absmiddle"> | 視点を縦方向に往復 |
| <img src="icons/icon-home.svg" width="18" align="absmiddle"> | 視点を定位置に戻す |
| <img src="icons/icon-spin.svg" width="18" align="absmiddle"> | 視点を横方向に1周 |
| <img src="icons/icon-campin.svg" width="18" align="absmiddle"> | ピン留め（下のボタンとペアで、自由/試験ブラウジング中またはスタンドアロンSbS中に表示。履歴に`CAM()`が無ければDisabled）。ONで<img src="icons/icon-first.svg" width="14" align="absmiddle"><img src="icons/icon-back.svg" width="14" align="absmiddle"><img src="icons/icon-go.svg" width="14" align="absmiddle"><img src="icons/icon-last.svg" width="14" align="absmiddle"><img src="icons/icon-rev.svg" width="14" align="absmiddle"><img src="icons/icon-play.svg" width="14" align="absmiddle">操作時に実操作時の視点を再現 |
| <img src="icons/icon-cmd.svg" width="18" align="absmiddle"> | コマンド再現（上のピン留めボタンと同じ場面でペアで表示。履歴にダブルタップコマンドが無ければDisabled） |
| 📚 / 🚪 | チュートリアル一覧を開く / 終了（同じスロットで排他表示）。モードに応じてEnabled/Disabled/非表示が切り替わる（③④記録中は非表示、②自由ブラウジング・⑤SbSガイド中・⑧試験ブラウジング中はDisabled） |

---

## ⚙️ 設定項目

| 項目 | 内容 |
|------|------|
| 言語 | 9言語から選択（日本語・中文・Français・English・한국어・Español・Português・Deutsch・Русский） |
| 速度設定 | キューブの回転アニメーション速度を4段階から選択（超高速・高速・中速（標準）・低速） |
| 座標軸表示設定 | 表示する軸（y軸のみ／x,y,z軸）と表示タイミング（表示しない／視点移動時のみ／常に表示）を設定。x軸=赤・y軸=白・z軸=緑 |

---

## 🔀 自動実行とSbs（ステップ実行）の違い

本質的な性質はこうです。

- **Sbs（ステップ実行）**は、**決まった記録を再生・閲覧する**モードです。全ての手・視点はあらかじめ決まっていて、開始後は行き来（1手ずつ進める、最初/最後へジャンプ、好きな速さでオートプレイ）はできても、自分の手を割り込ませたり内容を書き換えたりはできません。向いている用途：チュートリアル、記録した解法の再現（例：ハイスコアの<img src="icons/icon-play.svg" width="14" align="absmiddle">ボタン）、アルゴリズムを1手ずつ確認しながら練習する。
- **自動実行**は、**今の状態に対して一連の操作を実行する**モードです。実行後はその手順も普通の操作履歴の一部になるので、Undoできますし、続けて自分の手で操作を続けられます。向いている用途：どこかで見つけたスクランブルやアルゴリズムを試しに流し込む、SET→履歴でコピーした文字列を素早く再現する、特定の局面を作ってからそこで自分で解き始める。

SET画面（<img src="icons/icon-set.svg" width="14" align="absmiddle">）の「実行モード」で、回転コマンドをどちらの方式で実行するか選べます。**状態文字列の仕様はどちらも共通**（`U R F D L B u r f d l b W w`）ですが、**回転コマンドの記法には違い**があります。

| | 自動実行 | Sbs（ステップ実行） |
|---|---|---|
| 基本手（`U` `R'` `F2` `Uw2'`等） | ✅ | ✅ |
| `CAM(θ,φ)`（視点移動） | ✅（遭遇するとアニメーション付きで視点移動） | ✅ |
| `C_Xn` / `C_Xn(seq)`（照準コマンド） | ❌（構文エラー） | ✅ |
| `U(F)`等（ガイド矢印の表示面限定） | ❌（構文エラー） | ✅ |
| 実行方法 | ボタン操作で即座に全手数を実行 | 矢印ガイドに従いスワイプで1手ずつ進める |

Sbs実行中、回転コマンドに`CAM()`が1つでも含まれていれば、視点はその指定に自動追従します（オートプレイ中は背景ドラッグ・カメラ3ボタンが無効化）。`CAM()`が無ければ視点は自動追従せず、オートプレイ中でも自由に操作できます。SET画面から開始した非チュートリアルのSbSでは<img src="icons/icon-campin.svg" width="14" align="absmiddle">ピン留めボタンが表示され、この自動追従のON/OFFを選べます（チュートリアルのレッスンは常に`CAM()`に追従し、ピン留めボタンは表示されません）。

同様に、履歴にダブルタップコマンド（`C_Xn`/`C_Xn(seq)`）が1つでも含まれていれば、<img src="icons/icon-cmd.svg" width="14" align="absmiddle">「コマンド再現」ボタンが表示されます。ピン留めボタンとペアで、自由/試験ブラウジング中・スタンドアロンSbS実行中に表示され、視点・コマンドいずれも該当データが無い場合は非表示ではなくDisabled表示になります。チェック時（既定）はコマンドを1つの塊としてまとめて再現し、⏵自動再生中はその開始位置に⌖が一瞬光ります。アンチェック時は、コマンドも他の手と同様に1手ずつバラして扱います。チュートリアルのレッスンでは両ボタンとも非表示ですが、その効果（視点は常に追従・コマンドは常にコマンドとして再現）自体は有効なままです。

SET→履歴タブの「CAM付き」回転コマンド文字列（上記キューブ状態設定を参照）は、どちらのモードの回転コマンド欄にも貼り付け可能です。自動実行モードでも、記録された視点移動をSbSと同じようにアニメーション付きで再現します。

---

## 🛠 技術スタック

| 項目 | 内容 |
|------|------|
| 言語 | HTML / CSS / JavaScript（バニラ）+ WebAssembly（Rust） |
| 3Dライブラリ | Three.js r128（MIT） |
| 花火ライブラリ | canvas-confetti 1.9.4（ISC） |
| ツールチップ | Tippy.js 6.3.7 + Popper.js 2.11.8（MIT、アプリ独自のダークテーマに変更済み） |
| QRコード | qrcode.js 1.4.4（soldair、MIT） |
| アイコン | プラットフォーム間の描画差異を避けるため主要ボタンはSVG化済み。色は`currentColor`指定にしており、ボタンの状態（通常/ホバー/無効化等）に応じてCSS側から自動追従。残るはチュートリアルの2ボタン（入/出）のみ保留中 |
| フォント | Noto Sans Symbols 2（Google Fonts / OFL 1.1） |
| ファイル構成 | HTMLファイル単体 |

---

## 📁 リポジトリ構成

開発・公開のリポジトリを分けています。

```
cubew/              (public, ライセンスなし＝全著作権留保) ← アプリ公開用（GitHub Pages）
cubew_tutorial/     (public, MITライセンス) ← チュートリアルデータ公開用
cube_solver_api/    (public, GPL-2.0ライセンス) ← 外部ソルバー（Renderでホスティング）
```

### cubew（public）

`index.html`・`favicon.svg`・`about.*.html`（「このアプリについて」9言語）・`tutorial/`一式。GitHub Pagesで公開。

### cubew_tutorial（public、MIT）

`default.json`・`LBL/*.png`・`terms/*.png`・`README.md`/`README.ja.md`・`schema.md`/`schema.ja.md`。チュートリアルデータのみを独立して公開し、フォーク・改変を歓迎する想定。

### cube_solver_api（public、GPL-2.0）

外部ソルバー（Flask + kociemba）。Renderにデプロイ済み。kociembaがGPL-2.0ライセンスのため、ソース公開時はGPL-2.0が必須。

---

## 📋 バージョン管理

`v X.Y.Z` 形式。

- **X**: メジャー（大きな設計変更）
- **Y**: マイナー（機能追加）
- **Z**: パッチ（バグ修正・微修正）

---

## 🗺 今後の予定

- 3rdチュートリアルデータの読み込み機能（URL指定での外部JSON読み込み）
- ブックマーク/エクスポート機能（初期状態+履歴の保存・呼び出し）

要望は[Issues](https://github.com/itachiwalker/cubew/issues)に記載をお願いします。

---

## 📄 ライセンス

本リポジトリのソースコードにライセンスは付与しておらず、著作権はすべて作者に留保されます（No License）。

### できること

- 本サービス（GitHub Pages）上で、本アプリを自由にご利用いただくこと

### 禁止事項

以下の行為はご遠慮ください。

- 本アプリのファイルをダウンロードして、本サービス以外の場所で実行すること
- 個人利用であっても、ソースコードを改変すること
- 逆コンパイル・逆アセンブル・難読化解除など、内部構造を解析する行為
- 本アプリの複製・再配布

※ チュートリアルデータ（[cubew_tutorial](https://github.com/itachiwalker/cubew_tutorial)）はMITライセンスで別途公開しており、この制限の対象外です。
