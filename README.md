# みちくさ (michikusa)

**🎮 公開URL: https://tt-prog-commits.github.io/HuckThon/**

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
5. `index.html` はリポジトリ直下にあるため、公開URLは `https://tt-prog-commits.github.io/HuckThon/` になります(サブフォルダは付きません)

## グループ対戦モードの設定 (Firebase Realtime Database)

タイトル画面の「グループで対戦」（ルームコードで複数人が参加し、最後にスコアをランキング表示する対戦モード）を使うには、無料のFirebaseプロジェクトを1つ作成し、その設定値を `index.html` 内の `FIREBASE_CONFIG` に貼り付ける必要があります。Firebaseの設定が済んでいない間は、グループ対戦ボタンを押すと「サーバー設定が完了していません」と表示され、ソロモードはこれまで通り遊べます。

1. https://console.firebase.google.com/ を開き、Googleアカウントでログイン
2. 「プロジェクトを追加」から新しいプロジェクトを作成(名前は任意、例: `michikusa-kyoto`。Googleアナリティクスは不要ならオフでOK)
3. 作成したプロジェクトの画面で、左メニューの **構築 → Realtime Database** を開き、「データベースを作成」
   - ロケーションは任意(例: `asia-southeast1` など)
   - セキュリティルールは、ハッカソン用の一時的な検証としてテストモード(`.read: true, .write: true`)のままで問題ありません。本番運用する場合はルームコード単位で書き込みを制限するルールに変更してください
4. 左メニューの **プロジェクトの設定**(歯車アイコン) → 「全般」タブを開き、下の方の「マイアプリ」で「</> (ウェブ)」アイコンをクリックしてウェブアプリを追加(ニックネームは任意、Firebase Hostingは不要)
5. 表示される `firebaseConfig` オブジェクト(`apiKey`, `authDomain`, `databaseURL`, `projectId` など)をコピー
6. `index.html` 内で検索した `FIREBASE_CONFIG` の値(`YOUR_API_KEY` などのプレースホルダー)を、コピーした値にそのまま置き換えて保存
7. `git add` → `git commit` → `git push` して公開すれば、グループ対戦が使えるようになります

`firebaseConfig` の値はクライアント側に埋め込まれる前提の識別情報で、一般的なFirebaseアプリでも公開コードに含まれるものです(APIキーそのものに秘匿性はなく、実際のアクセス制御はRealtime Databaseのセキュリティルール側で行います)。

## 企画書

`message.txt` に企画の詳細(コンセプト、ゲームの流れ、スコア設計、MVP範囲など)をまとめています。

## 備考

- Google Street View の API キーを入力すると実写のストリートビュー画像を取得しますが、未入力でも同梱の京都写真16枚でそのまま遊べます。
- 結果画面の地図には Leaflet + OpenStreetMap を使用しています(同梱・APIキー不要)。
