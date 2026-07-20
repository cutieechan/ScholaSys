# ScholaSys – 大学院データ管理システム
# ScholaSys – Graduate Data Management System


ScholaSysは、PHP（フレームワーク不使用のネイティブ実装）とMySQLで構築され、XAMPP環境で動作する、包括的なWebベースの**卒業生データ管理システム**です。本システムは、教育機関による卒業生の追跡、就職状況の管理、追跡調査（トレーサー・サーベイ）の実施、同窓会イベントの運営などを支援します。

また、ユーザー権限管理、二要素認証（2FA）、メールリマインダー、PDFレポート出力、ドキュメントのアップロード、公開型同窓生名簿といった高度な機能も備えています。

ScholaSys is a complete web‑based **Graduate Data Management System** built with PHP (vanilla) and MySQL, running on XAMPP. It helps educational institutions track graduates, manage employment data, conduct tracer surveys, organize alumni events, and more.

The system includes advanced features like user roles, 2FA, email reminders, PDF reports, document uploads, and a public alumni directory.

---

## 📋 要件
## 📋 Requirements

* **XAMPP/Laragon:** Apache、MySQL、PHP 7.4以上（PHP 8.5.5の最新版で動作確認済み）
* **Composer:** 依存関係の管理に必要
* **ブラウザ:** Chrome、Firefox、またはEdge
---
* **XAMPP/Laragon:** Apache, MySQL, PHP 7.4 or higher (Tested on PHP 8.5.5 latest version)
* **Composer:** Required for dependency management
* **Browser:** Chrome, Firefox, or Edge

---
## 🚀 インストール
## 🚀 Installation

1. **リポジトリをクローンまたはダウンロード**し、XAMPPの `htdocs` フォルダに配置します：

    ```bash
    C:\xampp\htdocs\scholasys\
    ```

2. **XAMPPを起動**し、**Apache** と **MySQL** の両方を有効にします。

3. phpMyAdminで `scholasys` という名前の**データベースを作成**します。

4. **データベーススキーマをインポート**します：
    phpMyAdminを開き、`scholasys` データベースを選択して、ルートフォルダにある `scholasys.sql` ファイルをインポートします。

5. **PHPの依存関係をインストール**します：
    プロジェクトフォルダでターミナルを開き、以下のコマンドを実行します：

    ```bash
    composer install
    ```

    *注: これにより、PHPMailer、Dompdf、TwoFactorAuthがインストールされます。手動でインストールしたい場合は、以下を使用してください：*

    ```bash
    composer require phpmailer/phpmailer dompdf/dompdf robthree/twofactorauth
    ```

6. **ファイル権限を設定**します：`assets/uploads/` フォルダが書き込み可能であることを確認してください。

7. **SMTP設定を更新**します：`send_survey_reminders.php`、`send_anniversary_reminders.php`、および `pages/newsletter.php` を編集し、ご自身のメール認証情報を設定してください。

8. ブラウザで**システムにアクセス**します：

    ```text
    http://localhost/scholasys/public/
    ```

9. デフォルトの管理者アカウントで**ログイン**します：
    * **ユーザー名:** `admin`
    * **パスワード:** `admin123`

    > **⚠️ 重要:** 初回ログイン後、すぐにパスワードを変更してください。

    **⚠️ 注意**: SMTP認証情報はご自身のGmailアカウントのものに更新する必要があります。セキュリティ上の理由（GitGuardianによる公開制限など）から、デフォルト設定のままにしていますので、ご自身で変更してください。

---

1. **Clone or download** this repository into your XAMPP `htdocs` folder:

    ```bash
    C:\xampp\htdocs\scholasys\
    ```

2. **Start XAMPP** and enable both **Apache** and **MySQL**.

3. **Create a database** named `scholasys` in phpMyAdmin.

4. **Import the database schema:**
    Open phpMyAdmin, select the `scholasys` database, and import the file `scholasys.sql` located in the root folder.

5. **Install PHP dependencies:**
    Open a terminal in the project folder and run:

    ```bash
    composer install
    ```

    *Note: This installs PHPMailer, Dompdf, and TwoFactorAuth. If you prefer manual installation, use:*

    ```bash
    composer require phpmailer/phpmailer dompdf/dompdf robthree/twofactorauth
    ```

6. **Set file permissions:** Ensure the `assets/uploads/` folder is writable.

7. **Update SMTP settings:** Edit `send_survey_reminders.php`, `send_anniversary_reminders.php`, and `pages/newsletter.php` with your email credentials.

8. **Access the system** in your browser:

    ```text
    http://localhost/scholasys/public/
    ```

9. **Log in** with the default administrator account:
    * **Username:** `admin`
    * **Password:** `admin123`

    > **⚠️ Important:** Change the password immediately after your first login.

    **⚠️ Reminder**: You have to update an smtp credential your own gmail account because they are not allowed to public from gitguardian my gmail so I decided to use a default smtp to modified yourself

---

## ✨ 特徴
## ✨ Features

### 基本管理機能

* **卒業生データ管理:** データの追加・編集・検索・絞り込み、およびCSV形式でのエクスポート。
* **就職状況の追跡:** 現在の勤務先情報および詳細な職歴の管理。
* **追跡調査（アンケート）:** 回答を自動記録できる、固有トークン付きリンクを用いた公開フォーム。
* **レポート機能:** プログラム別の就職率、主要な就職先企業の集計、PDF形式でのレポート出力。
* **ダッシュボード:** リアルタイム統計、就職動向グラフ、業界別分布の表示。

### 卒業生との連携・交流

* **イベント管理:** 公開登録フォームおよび参加状況の管理。
* **お知らせ:** 全ユーザーが閲覧可能なニュースや情報の投稿。
* **公開名簿:** 詳細検索・絞り込み機能を備えた、登録制（オプトイン方式）の卒業生名簿。

### ユーザー管理・セキュリティ

* **役割別アクセス権限:** 管理者（全権限）およびスタッフ（管理業務のみ）の役割設定。
* **セキュリティ:** Google Authenticatorを利用した二要素認証（2FA）の導入（任意設定）。
* **アクティビティログ:** システムの変更履歴やユーザーの操作履歴の記録・追跡。

---

### Core Management

* **Graduate Records:** Add, edit, search, filter, and export data to CSV.
* **Employment Tracking:** Manage current job details and complete employment history.
* **Tracer Surveys:** Public forms with unique token links for automated response recording.
* **Reporting:** Employment rates by program, top employers, and PDF downloads.
* **Dashboard:** Real-time statistics, employment trend charts, and industry distribution.

### Alumni Engagement

* **Events Management:** Public registration and attendance tracking.
* **Announcements:** Post news updates visible to all users.
* **Public Directory:** Opt-in directory with advanced search and filtering.

### User & Security

* **Multi-role Access:** Admin (full control) and Staff (management only) roles.
* **Security:** Optional Two-Factor Authentication (2FA) via Google Authenticator.
* **Activity Logs:** Track system changes and user actions.

---

## 📁 ファイル構成
## 📁 File Structure

```text
scholasys/
├── assets/           # CSS、JS、およびアップロードされたファイル
├── includes/         # 設定、ヘッダー、フッターなどのファイル
├── pages/            # 認証が必要なアプリケーションページ
├── public/           # 公開ページ（ログイン、アンケート、2FAなど）
├── vendor/           # Composerの依存関係ファイル
├── send_*.php        # 自動化・Cron用スクリプト
├── scholasys.sql     # データベーススキーマのダンプファイル
└── README.md         # ドキュメント
```

```text
scholasys/
├── assets/           # CSS, JS, and uploaded files
├── includes/         # Config, header, and footer files
├── pages/            # Protected application pages
├── public/           # Publicly accessible pages (Login, Survey, 2FA)
├── vendor/           # Composer dependencies
├── send_*.php        # Automation/Cron scripts
├── scholasys.sql     # Database schema dump
└── README.md         # Documentation
```

---

## 🔧 Cron Jobs (Windows)

To automate emails, create two scheduled tasks in **Windows Task Scheduler** to run daily:

* **Survey Reminders:**
    `php C:\xampp\htdocs\scholasys\send_survey_reminders.php`
* **Anniversary Reminders:**
    `php C:\xampp\htdocs\scholasys\send_anniversary_reminders.php`

---

## 🛠️ Troubleshooting

| Issue | Solution |
| :--- | :--- |
| **Login Fails** | Ensure the password hash in the DB is correct or use a reset script. |
| **PDF Errors** | Verify `dompdf` is in the `vendor/` folder and `autoload.php` is included. |
| **404 Errors** | Check directory mapping (e.g., `/public/` vs `/pages/`). |
| **Composer Errors** | Ensure PHP 8.2+. Try `composer install --ignore-platform-reqs` for compatibility. |

---

## 📝 License

This project is open‑source and free for educational use. No warranty is provided.

**Enjoy using ScholaSys!** 🎓
