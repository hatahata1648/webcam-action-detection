# webcam-action-detection
ウェブカメラ アクション検出アプリ
ウェブカメラの映像にMP4動画をオーバーレイで重ね、人物のアクションを検出して特定の動画エフェクトを再生するWebアプリケーションです。
機能

ウェブカメラライブ映像: リアルタイムでウェブカメラの映像を全画面表示
オーバーレイ動画: 背景に透明度付きでMP4動画をループ再生
AI アクション検出: TensorFlow.js と BlazePose を使用した人物動作認識
動的エフェクト: 検出したアクションに応じて動画エフェクトを人物の近くで再生
全画面表示: 自動的に全画面モードで動作

検出可能なアクション

両手を上げる: 両手を肩より上に上げると祝福エフェクトが再生
手を振る: 右手を高く上げて横に振ると手振りエフェクトが再生

必要なファイル
以下のMP4ファイルを同じディレクトリに配置してください：

video.mp4: 背景オーバーレイ動画（常時ループ再生）
celebration.mp4: 両手を上げた時の祝福エフェクト動画
wave_effect.mp4: 手を振った時のエフェクト動画

セットアップ

このリポジトリをクローンまたはダウンロード
必要なMP4ファイルを配置
index.html をWebブラウザで開く
カメラの許可を与える
画面をクリックして全画面表示にする

使用方法

ブラウザで index.html を開く
ウェブカメラのアクセス許可を与える
画面をクリックして全画面表示にする
カメラの前で以下のアクションを試してみてください：

両手を上に上げる
右手を高く上げて横に振る



技術仕様

AI モデル: TensorFlow.js + BlazePose
ブラウザ要件: WebRTC対応の現代的なブラウザ
解像度: 1920x1080 (フルHD)
フレームレート: リアルタイム (ブラウザ性能に依存)

カスタマイズ
新しいアクションの追加
index.html の checkForActions 関数を編集してアクションを追加できます：
javascript// 例: 拍手アクション
if (leftWrist && rightWrist) {
    const handsClose = Math.abs(leftWrist.x - rightWrist.x) < 50;
    const handsUp = leftWrist.y < leftShoulder.y && rightWrist.y < rightShoulder.y;
    
    if (handsClose && handsUp) {
        triggerActionVideo(centerX, centerY, 'clap');
    }
}
動画ファイル名の変更
triggerActionVideo 関数内で動画ファイル名を変更できます：
javascriptif (actionType === 'hands_up') {
    actionVideo.src = 'your_celebration_video.mp4';
} else if (actionType === 'wave') {
    actionVideo.src = 'your_wave_video.mp4';
}
エフェクト表示時間の調整
エフェクト動画の表示時間を変更するには、タイムアウト値を調整します：
javascript// 5秒後に削除 → 10秒後に削除
setTimeout(() => {
    // ...
}, 10000); // 5000 → 10000
ブラウザ互換性

Chrome 88+
Firefox 90+
Safari 14+
Edge 88+

トラブルシューティング
カメラが起動しない

ブラウザがカメラアクセスを許可しているか確認
HTTPS環境で実行（ローカルの場合はlocalhostでOK）
他のアプリケーションがカメラを使用していないか確認

AI モデルが読み込めない

インターネット接続を確認
ブラウザが JavaScript を有効にしているか確認
TensorFlow.js がサポートされているブラウザか確認

動画が再生されない

MP4ファイルが正しい場所に配置されているか確認
動画ファイルが破損していないか確認
ブラウザが自動再生を許可しているか確認

ライセンス
このプロジェクトは MIT ライセンスのもとで公開されています。詳細は LICENSE ファイルを参照してください。
貢献
プルリクエストやイシューの報告を歓迎します。
作者

開発者: [Your Name]
連絡先: [Your Email]

謝辞

TensorFlow.js - 機械学習フレームワーク
BlazePose - 人物ポーズ検出モデル
