# UI/UXモックアップレポート
## インクルーシブ防災情報センター 統合ダッシュボード設計書

作成日：2025年6月20日  
作成者：JPT Deep Research インターンシップ

---

## 1. プロジェクト概要

### 1.1 背景
IBARAKI NEXT戦略のGROWTH施策「インクルーシブ防災情報センター」において、視覚・聴覚障害者が防災情報の収集・分析・発信を担当する革新的な職場環境を実現するため、最先端のアクセシビリティ技術を活用した統合ダッシュボードを設計しました。

### 1.2 設計理念
- **Universal Design First**：障害の有無に関わらず、全ての職員が効率的に業務遂行可能
- **Multi-Modal Interface**：視覚、聴覚、触覚の複数チャンネルで情報伝達
- **Adaptive Personalization**：個々の障害特性に応じた最適なUI自動調整

---

## 2. ユーザーペルソナ

### ペルソナ1：田中さん（視覚障害・全盲）
- **年齢**：32歳
- **スキル**：音声認識技術に精通、聴覚による状況把握能力が高い
- **ニーズ**：音声とキーボードショートカットによる完全操作

### ペルソナ2：佐藤さん（聴覚障害・重度難聴）
- **年齢**：28歳
- **スキル**：視覚情報処理能力が高い、手話・筆談でコミュニケーション
- **ニーズ**：視覚的アラート、振動通知、リアルタイム字幕

### ペルソナ3：鈴木さん（精神障害・発達障害）
- **年齢**：25歳
- **スキル**：パターン認識能力が高い、ルーティンワークに強い
- **ニーズ**：明確な作業フロー、視覚的な進捗管理

---

## 3. ダッシュボード機能設計

### 3.1 メインダッシュボード構成

```
┌─────────────────────────────────────────────────────────────┐
│  茨城県インクルーシブ防災情報センター 統合ダッシュボード     │
├─────────────────────────────────────────────────────────────┤
│ ┌─────────────┐ ┌─────────────────────┐ ┌─────────────┐ │
│ │ 緊急度表示  │ │   リアルタイム     │ │ 音声/触覚  │ │
│ │ (色/音/振動)│ │   災害情報マップ   │ │ フィード   │ │
│ └─────────────┘ └─────────────────────┘ └─────────────┘ │
│ ┌─────────────────────────┐ ┌─────────────────────────┐ │
│ │   情報ソース統合       │ │   コミュニケーション   │ │
│ │   モニタリング         │ │   ハブ                 │ │
│ └─────────────────────────┘ └─────────────────────────┘ │
│ ┌───────────────────────────────────────────────────────┐ │
│ │              タスク管理・進捗トラッカー              │ │
│ └───────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────┘
```

### 3.2 主要機能詳細

#### 【機能1】マルチモーダル緊急度表示システム
- **視覚モード**：
  - 色分け（緑→黄→橙→赤）
  - アイコンサイズの動的変化
  - 点滅パターンの調整
  
- **聴覚モード**：
  - 緊急度別の警報音
  - 音声読み上げ（速度調整可能）
  - 3Dサウンドによる方向指示
  
- **触覚モード**：
  - 振動パターンの差別化
  - 点字ディスプレイ連動
  - ウェアラブルデバイス通知

#### 【機能2】リアルタイム災害情報マップ
- **アクセシブルマップ**：
  - 高コントラストモード
  - 音声による地域説明
  - キーボードナビゲーション完全対応
  
- **情報レイヤー**：
  - 気象情報オーバーレイ
  - 避難所位置表示
  - 交通情報統合
  
- **インタラクション**：
  - ジェスチャー操作対応
  - 音声コマンド対応
  - スクリーンリーダー最適化

#### 【機能3】統合コミュニケーションハブ
- **チャンネル統合**：
  - 行政無線のテキスト化
  - SNS情報の自動収集・分類
  - 市民通報の一元管理
  
- **アクセシビリティ機能**：
  - リアルタイム字幕生成
  - 手話動画自動生成（AI活用）
  - 多言語対応（やさしい日本語含む）

---

## 4. アクセシビリティ設計詳細

### 4.1 視覚障害者向け最適化

#### スクリーンリーダー対応
```html
<!-- セマンティックHTML構造例 -->
<main role="main" aria-label="防災情報ダッシュボード">
  <section aria-labelledby="emergency-heading">
    <h2 id="emergency-heading">緊急情報</h2>
    <div role="alert" aria-live="assertive">
      <p>大雨警報発令：県北地域</p>
    </div>
  </section>
</main>
```

#### キーボードショートカット体系
| ショートカット | 機能 |
|--------------|------|
| Alt + 1 | 緊急情報へジャンプ |
| Alt + 2 | 地図情報へジャンプ |
| Alt + 3 | タスク一覧へジャンプ |
| Ctrl + Space | 音声コマンド起動 |
| F1 | ヘルプ読み上げ |

### 4.2 聴覚障害者向け最適化

#### ビジュアルアラートシステム
- 画面全体のフラッシュ通知
- デスクトップ通知API活用
- アイコンアニメーション強化

#### リアルタイム字幕システム
```javascript
// 音声認識による自動字幕生成
const recognition = new webkitSpeechRecognition();
recognition.continuous = true;
recognition.interimResults = true;
recognition.onresult = (event) => {
  const transcript = event.results[event.results.length-1][0].transcript;
  displaySubtitle(transcript);
};
```

### 4.3 認知・精神障害者向け最適化

#### 情報構造の簡素化
- プログレッシブディスクロージャー
- 重要度による情報の階層化
- ビジュアルヒエラルキーの明確化

#### ストレス軽減デザイン
- カスタマイズ可能な配色
- アニメーション速度調整
- 情報密度の個別調整

---

## 5. 技術仕様

### 5.1 フロントエンド技術スタック
- **フレームワーク**：React 18 + TypeScript
- **状態管理**：Redux Toolkit
- **UIライブラリ**：Material-UI (アクセシビリティ対応)
- **地図**：Mapbox GL JS (アクセシブルカスタマイズ)

### 5.2 アクセシビリティツール統合
- **スクリーンリーダー**：NVDA, JAWS, VoiceOver対応
- **音声認識**：Web Speech API
- **点字ディスプレイ**：BrailleBack API
- **手話生成**：SignLanguage.js (カスタム開発)

### 5.3 バックエンド連携
```javascript
// WebSocket によるリアルタイムデータ配信
const socket = new WebSocket('wss://ibaraki-emergency.jp/stream');
socket.onmessage = (event) => {
  const data = JSON.parse(event.data);
  updateDashboard(data);
  triggerMultiModalAlert(data.severity);
};
```

---

## 6. ユーザビリティテスト計画

### 6.1 テスト参加者
- 視覚障害者：10名
- 聴覚障害者：10名
- 認知・精神障害者：10名
- 健常者（比較対象）：10名

### 6.2 評価指標
- タスク完了時間
- エラー率
- 主観的満足度（SUS: System Usability Scale）
- 認知負荷（NASA-TLX）

### 6.3 改善サイクル
1. プロトタイプ開発（1ヶ月）
2. ユーザビリティテスト（2週間）
3. 改善実装（2週間）
4. 再テスト・検証（1週間）

---

## 7. 期待される成果

### 7.1 業務効率の向上
- 情報処理速度：従来比 **150%向上**
- エラー率：**70%削減**
- 職員満足度：**85%以上**

### 7.2 社会的インパクト
- 障害者の専門職としての地位確立
- 防災情報の質的向上
- インクルーシブデザインのモデルケース

### 7.3 波及効果
- 他自治体への展開可能性
- 民間企業への技術移転
- 国際的な注目・評価

---

## 8. 実装ロードマップ

### Phase 1（月1-3）：基本機能開発
- コアダッシュボード実装
- 基本的なアクセシビリティ機能

### Phase 2（月4-6）：高度機能追加
- AI音声認識・手話生成
- マルチモーダルアラート

### Phase 3（月7-9）：最適化・展開
- パフォーマンス最適化
- 全県展開準備

---

## 9. 結論

本UI/UXデザインは、単なる「バリアフリー対応」を超えて、障害者の特性を強みとして活かす「インクルーシブ・アドバンテージ」を実現します。

このダッシュボードにより、インクルーシブ防災情報センターは、日本初の「障害者が主体となって地域を守る」モデルケースとなり、茨城県の防災力向上と障害者雇用促進の両立を実現します。

**「守られる存在」から「守る存在」へ。**

この paradigm shift こそが、IBARAKI NEXT戦略の真髄です。