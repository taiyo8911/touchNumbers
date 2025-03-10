# touchNumbers
【iOS】早押しゲームアプリ

## Project Name
**touchNumbers**

## App Name
**タップン**

## App Description
数字を順番にタップして、あなたの集中力を測るシンプルなカジュアルゲーム！

### ゲーム概要
- **スタート**:  
  スタートボタンを押すと、ゲーム画面に遷移し、タイマーがスタートします。
- **ゲーム画面**:  
  5×5のマスに1～25の数字がランダム配置され、次にタップすべき数字が画面に表示されます。  
  正しい数字をタップすると、そのマスの色が変わり、無効化されます。  
  間違った数字をタップすると、ミスとしてカウントされます。
- **クリア**:  
  25まで順番にタップし終えると「クリア」と表示され、結果表示ボタンから結果画面へ移行します。
- **結果画面**:  
  クリアタイム（ミリ秒単位）とミス数を表示し、リトライボタンで再チャレンジが可能です。


## Folder Structure (SwiftUI Project)
```
touchNumbers/
├── touchNumbersApp.swift         // アプリのエントリポイント
├── Models/
│   └── GameModel.swift           // ゲームのロジックとデータモデル
├── Views/
│   ├── StartView.swift           // スタート画面
│   ├── GameView.swift            // ゲーム画面
│   ├── ResultView.swift          // 結果画面
│   ├── BoardView.swift           // 5x5の数字ボード
│   ├── TileView.swift            // 各マスの数字タイル
│   └── TimerView.swift           // タイマー表示用ビュー
├── ViewModels/
│   └── GameViewModel.swift       // ゲーム状態とロジックの管理
├── Utilities/
    ├── TimerManager.swift        // タイマー管理のユーティリティ
    └── Randomizer.swift          // 数字のランダム配置ロジック
```

## アプリシステム
### 1. アプリ起動  
アプリを起動すると **StartView** が表示され、ユーザーは「スタート」ボタンを押すことでゲームを開始できます。  

---

### 2. ゲーム開始  
### **処理の流れ**
1. **GameView** に遷移する  
2. **GameViewModel** によって、以下の処理が実行される：  
   - 1～25の数字をランダムに配置する（`Randomizer.swift`）
   - タイマーを開始する（`TimerManager.swift`）
   - 次にタップすべき数字（現在のターゲット）を1に設定  

---

### 3. 数字タップ時の処理  
#### **正しい数字（ターゲット）をタップした場合**  
✅ **処理内容**  
- タップしたマスを無効化し、色を変える  
- 次のターゲット数字を更新（例：1→2→3…25）  
- 25をタップしたらゲームクリア  

#### **間違った数字をタップした場合**  
❌ **処理内容**  
- ミス数をカウントアップ  
- 画面上に「ミスカウント」を表示  

---

### 4. ゲームクリア  
ユーザーが **1～25の数字をすべて正しくタップ** すると、以下の処理を実行：  
1. **タイマーを停止**（クリアタイムを記録）  
2. **「クリア」と画面に表示**  
3. **「結果を見る」ボタンを表示**  

---

### 5. 結果画面（ResultView）  
ユーザーが「結果を見る」ボタンを押すと、**ResultView** に遷移し、以下を表示：  
- **クリアタイム（ミリ秒単位）**  
- **ミス数**  
- **「リトライ」ボタン**（タップで再挑戦）

リトライボタンを押すと **GameView** に戻り、新しいゲームが開始される。  

---

### まとめ  
1. **StartView** で「スタート」ボタンを押す  
2. **GameView** で1～25を順番にタップ  
3. **間違えるとミスカウント**  
4. **25までタップするとクリア**  
5. **ResultView で結果を表示 & リトライ可能**


## フローチャート
<img width="420" alt="ss" src="https://github.com/user-attachments/assets/fce36b3d-fac9-4a7e-82bc-962f8df8b775" />

