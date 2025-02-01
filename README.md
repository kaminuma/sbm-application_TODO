# sbm-application_TODO

Supabase を利用したシンプルな ToDo リストアプリ。

## **🛠 プロジェクト概要**

SBM-TODO は、**SBM-Application シリーズの TODO 管理に特化したアプリケーション** です。  
本プロジェクトでは、これまでの開発とは異なる技術スタックとして **Supabase（BaaS）** を採用し、  
より迅速かつ柔軟な開発を目指します。  
将来的には **SBM-Project（既存の SBM システム）と連携** することを前提としています。

### **主要技術**（現時点のアーキテクチャ）

- **フロントエンド:** Vue.js or Next.js
- **バックエンド:** Supabase（PostgreSQL + Auth + REST API）
- **機能**
  - ToDo の登録・編集・削除
  - ステータス管理（未完了 / 進行中 / 完了）
  - 認証機能（ユーザーごとの ToDo 管理）
  - Supabase の自動生成 API を利用したデータ操作
- **デプロイ:** Vercel / Netlify（無料運用可能）
- **今後の計画:** SBM-API との連携（後日実装）

---

## **📌 なぜ Supabase を採用したのか？**

### **1. 新しい開発形式を取り入れるため**

これまでの **SBM シリーズ** では、主に **フルスクラッチ** でバックエンドを構築してきました。  
しかし、今回は **BaaS（Backend as a Service）** を活用した開発形式を試すことで、  
**より素早く、柔軟にサービスを構築するアプローチ** を取り入れることを目的としています。

Supabase は **PostgreSQL を基盤としたオープンソースの BaaS** であり、  
**データベース管理、認証、ストレージ、リアルタイム通信** などを簡単に実装できるため、  
今後の開発に活かせる技術スタック・経験として触っておくべきと判断して採用しました。

### **2. Firebase より柔軟なデータ管理**

- Supabase は **PostgreSQL ベース** で、RDB のようにスキーマ設計が可能
- NoSQL（Firestore）と異なり、複雑なクエリが扱いやすい

### **3. OSS かつベンダーロックインリスクが低い**

- Supabase は **オープンソース** であり、他の PostgreSQL 環境に移行しやすい
- Firebase とは異なり、**独自のカスタマイズが可能**

### **4. REST / GraphQL API の自動生成**

- Supabase は **データベース操作の API を自動生成**
- フロントエンドと直接連携でき、**バックエンドの構築コストを削減**

### **5. 認証機能が強力**

- Supabase Auth を使うことで、**メール / Google / GitHub 認証が簡単に実装可能**
- Firebase Auth と同様に、**セキュリティポリシー（RLS）を適用可能**

---

## **🚀 セットアップ手順**（現在想定している npm を使用例として）

### **1. 環境構築**

```sh
git clone https://github.com/yourusername/sbm-todo.git
cd sbm-todo
npm install
```
