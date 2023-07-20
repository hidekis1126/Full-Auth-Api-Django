# Full Auth API

This is the API for the Full Authentication system. It is built with Django and Django Rest Framework.

## Getting Started

First, make sure you have Python and Django installed. You can download Python [here](https://www.python.org/downloads/) and you can install Django using pip:

```bash
pip install django
pip install djangorestframework
pip install djoser
pip install django-cors-headers
pip install djangorestframework-simplejwt
pip install social-auth-app-django
pip install django-storages
pip install boto3
pip install python-decouple
pip install dj-database-url
pip install django-ses

```
or
```bash
pip install -r requirements.txt
```
## Setting Up the Database
This project is set up to use SQLite in development and PostgreSQL in production. To set up the database, run the following command:
```bash
python manage.py makemigrations
python manage.py migrate
```
## Running the Server
To start the server, use the command:
```bash
python manage.py runserver
```
The API will now be running at http://localhost:8000.
## Environment Variables
This project uses the following environment variables:
- **DEVELOPMENT_MODE**: Set to "True" for development mode, "False" for production.
- **DJANGO_SECRET_KEY**: The secret key for Django. This should be kept secret.
- **DEBUG**: Set to "True" to enable Django's debug mode. This should be set to "False" in production.
- **DJANGO_ALLOWED_HOSTS**: A comma-separated list of hosts/domains your site can serve.
- **DATABASE_URL**: The URL of your database. This should be a SQLite URL in development and a PostgreSQL URL in production.
- **CORS_ALLOWED_ORIGINS**: A comma-separated list of origins that are allowed to make cross-origin requests.
- **AWS_SES_ACCESS_KEY_ID**: Your AWS SES access key ID for sending email.
- **AWS_SES_SECRET_ACCESS_KEY**: Your AWS SES secret access key.
- **AWS_SES_REGION_NAME**: The region your AWS SES is located in.
- **AWS_SES_REGION_ENDPOINT**: The endpoint for AWS SES in your region.
- **AWS_S3_ACCESS_KEY_ID**: Your AWS S3 access key ID for storing static files.
- **AWS_S3_SECRET_ACCESS_KEY**: Your AWS S3 secret access key.
- **AWS_STORAGE_BUCKET_NAME**: The name of your AWS S3 bucket.
- **AWS_S3_REGION_NAME**: The region your AWS S3 bucket is located in.
- **SOCIAL_AUTH_GOOGLE_OAUTH2_KEY**: Your Google OAuth2 key for Google sign-in.
- **SOCIAL_AUTH_GOOGLE_OAUTH2_SECRET**: Your Google OAuth2 secret.
- **SOCIAL_AUTH_FACEBOOK_KEY**: Your Facebook key for Facebook sign-in.
- **SOCIAL_AUTH_FACEBOOK_SECRET**: Your Facebook secret.
You should create a .env.local file in the project root and define these variables there. This file should not be checked into version control.

## Testing
You can run the tests with the following command:
```bash
python manage.py test
```
## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.
## License
This project is licensed under the MIT License. See the LICENSE file for details.



# Full Auth API
## ローカルでのプロジェクト設定手順：
- **.env.local** ファイルを開きます。

- **DJANGO_SECRET_KEY** の値を入力します。

- **AWS** にアクセスします。

- AWSアカウントにログインします（アカウントがない場合は作成します）。

- **Simple Email Service (SES)** に移動します。

- 送信者と受信者のメールを2つ検証します。

- **SMTP settings** に移動し、**Create SMTP credentials** をクリックします。

- IAMユーザーを作成した後、**IAM** に移動します。

- **Access management** の下で **users** をクリックします。

- **SES** ユーザーをクリックします。

- **Add permissions** をクリックし、**AmazonSESReadOnlyAccess** 権限を追加します。

- 次に **Security credentials** に移動し、新しいアクセスキーを作成します。

- アクセスキーとシークレットを取得し、それらを **AWS_SES_ACCESS_KEY_ID** と **AWS_SES_SECRET_ACCESS_KEY** 環境変数の値として使用します。

- Simple Email Service を設定したリージョンを **AWS_SES_REGION_NAME** 環境変数に入力します。

- メールを送信するメールアドレスを **AWS_SES_FROM_EMAIL** 環境変数に入力します。

- **Google Cloud** に移動します。

- 設定で **APIs & Services** にマウスを合わせ、**OAuth consent screen** をクリックします。

- OAuth同意画面の詳細を入力します。

- **External** ユーザータイプを作成します。
- **Authorized domains** を追加します。
- **scopes** の下で **ADD OR REMOVE SCOPES** をクリックし、**../auth/userinfo.email, ../auth/userinfo.profile, openid** のスコープを追加します。
- **Test users** の下で、受信用のメールを追加します。
- 次に設定に移動し、**APIS & Services** の上にマウスを合わせ、**Credentials** をクリックします。

- **CREATE CREDENTIALS** をクリックし、**OAuth client ID** をクリックします。

- アクセスキーとシークレットを取得し、それらを **GOOGLE_AUTH_KEY** と **GOOGLE_AUTH_SECRET_KEY** 環境変数の値として使用します。

- **Application type** で **Web application** を選択します。

- **Authorized JavaScript origins** で **http://localhost:3000** を追加します。

- **Authorized redirect URIs** で **http://localhost:3000/auth/google** を追加します。

- 本番環境で動作させるためには、以下の手順を行います。

- **Authorized JavaScript origins** で **https://your-domain.com** を追加します。
- **Authorized redirect URIs** で **https://your-domain.com/auth/google** を追加します。
- **Facebook Developers** に移動します。

- **My Apps** に移動し、**Create App** をクリックし、**Set up Facebook Login** をクリックし、**Next** をクリックします。

- **Website** を選択し、**No, I'm not building a game** を選択し、**Next** をクリックします。

- アプリ名を入力し、**Create app** をクリックします。

- **Use cases** をクリックし、**Authentication and account creation** の下の **Edit** ボタンをクリックします。

- **email** の許可の下で **Add** をクリックします。

- **Settings** の下の **Basic** に移動します。

- **App ID** と **App secret** を取得し、それらを **FACEBOOK_AUTH_KEY** と **FACEBOOK_AUTH_SECRET_KEY** 環境変数の値として使用します。

- **App domains** で **localhost** を追加します。ここで本番環境のドメインも追加できます。

- **App Roles** の下の **Roles** に移動します。

- **Add Testers** をクリックし、フィールドにアプリにログインするためのFacebook IDの値を入力します。

- Facebook IDの値を取得するには、Facebookアカウントにログインし、プロフィールページに移動し、URLからIDを取得します。
- テスターアカウントをアクティベートするために、テスターアカウントで **Facebook Developers** に移動します。

- **My Apps** に移動し、ドロップダウンからアプリのテスターとしてアカウントを受け入れるプロンプトが表示されます。

- 次に **Products** に移動し、**Facebook Login** の下で **Configure** をクリックし、**Settings** をクリックします。

- 開発環境で動作させるためには、この画面で何も入力する必要はありません。

- 本番環境で動作させるためには、**Valid OAuth Redirect URIs** で **https://your-domain.com/auth/facebook** を追加します。

## Digitaloceanへのデプロイ：
- デプロイするには、以下のリンク **HERE** にアクセスします。
- 次に 2:47:14 のタイムスタンプに移動します。ここでDigitaloceanへのデプロイを示しています。

- **環境変数の読み込み**：環境変数は .env.local ファイルから読み込まれています。これにより、プロジェクトの設定に必要な情報（例えば、シークレットキーやデータベースの設定など）を保持します。これにより、コード内に直接機密情報を書くことなく、開発環境や本番環境での設定の違いを管理することができます。

- **データベース設定**：開発モードが有効な場合、SQLiteデータベースが使用されます。開発モードが無効で、collectstatic コマンドが実行されていない場合、dj_database_url パッケージを使用して環境変数からデータベースの設定を読み込みます。

- **メール設定**：AWSの Simple Email Service (SES) を使用してメールを送信するように設定されています。

- **静的ファイルの設定**：開発モードが有効な場合、静的ファイルはローカルの static ディレクトリに保存されます。開発モードが無効な場合、AWS S3を使用して静的ファイルを保存します。

- **認証バックエンドの設定**：Google OAuth2とFacebook OAuth2を使用したソーシャルログインを設定しています。

- **RESTフレームワークの設定**：デフォルトの認証クラスとしてカスタムJWT認証を使用し、デフォルトのパーミッションクラスとして IsAuthenticated を使用しています。

- **CORSの設定**：CORS（Cross-Origin Resource Sharing）の設定を行い、特定のオリジンからのリクエストを許可しています。

- **ユーザーモデルの設定**：デフォルトのユーザーモデルとして UserAccount を指定しています。

<!--Full-Auth-with-Nextjs ファイル名Full-Auth-Main と同じ環境-->