# みちくさ (michikusa)

**🎮 公開URL: https://tt-prog-commits.github.io/HuckThon/matimiru/**

移動中の暇な時間を「京都の道中で出会うお題スポットを探すゲーム」に変える、位置情報×ストリートビュー体験のプロトタイプです。

- 現在地と目的地、移動時間の目安を設定
- 道中に出現するお題(京都の名所の写真)を見て、似た景色を実際に探して撮影
- お題地点と撮影地点の距離をもとにスコアを算出(近いほど高得点)
- GPSが使えない場合は「体験モード」でも遊べます

## 遊び方 (ローカルで確認する場合)

`index.html` をブラウザで開くだけで動作します(外部ライブラリはすべて同梱済み)。

## GitHub Pages の設定 (設定済み)

このリポジトリはすでに GitHub Pages で公開されています。設定は以下の通りです(参考・再設定用)。

1. GitHub のリポジトリページで **Settings** タブを開く
2. 左メニューの **Pages** を選択
3. **Build and deployment** の **Source** で `Deploy from a branch` を選択
4. **Branch** を `main` / フォルダを `/ (root)` にして **Save**
5. `index.html` が `matimiru/` フォルダの中にあるため、公開URLは `https://tt-prog-commits.github.io/HuckThon/matimiru/` になります(リポジトリ直下ではなく `matimiru/` が付く点に注意)

## 企画書

`message.txt` に企画の詳細(コンセプト、ゲームの流れ、スコア設計、MVP範囲など)をまとめています。

## 備考

- Google Street View の API キーを入力すると実写のストリートビュー画像を取得しますが、未入力でも同梱の京都写真16枚でそのまま遊べます。
- 結果画面の地図には Leaflet + OpenStreetMap を使用しています(同梱・APIキー不要)。
