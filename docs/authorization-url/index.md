# Oauth認可画面URLの作り方

## 概要

認可コード取得にはユーザーの許可が必要です。
認可画面は https://alis.to/oauth というURLに以下のクエリパラメータを加えてください。

* client_id
* redirect_uri
* scope
* code_challenge

## 各パラメータ説明

### client_id

OAuthアプリケーションを登録した際に発行されたclient_idを指定して下さい

### redirect_uri

OAuthアプリケーションを登録した際に指定したredirect_uriの内一つを指定して下さい。

### scope

OAuthアプリケーションのscopeを指定します。
`read` もしくは `write` のみ指定できます。

### code_challenge

[PKCE](https://tools.ietf.org/html/rfc7636#appendix-B)で使用するパラメータです。
ALIS APIを使用するアプリケーション側でcode_verifierを生成し、code_challengeを計算して下さい。

例) 

    code_verifier = "dBjftJeZ4CVP-mB92K27uhbUJU1p1r_wW1gFWFOEjXk"
    code_challenge = "E9Melhoa2OwvFrEMTJguCHaoeK1t8URWbuGJSstw-cM"

## URL例


* client_id = `12345678901234`
* redirect_uri = `https://example.com`
* scope = `openid read`
* code_challenge = `hcCb3gToI1GPZeS_SIYWvaNT_5u0GB1oqOGQJqRKMSE`

上記パラメーターの場合,URLは以下の通りです。

    
    https://alis.to/oauth?client_id=12345678901234&redirect_uri=https%3A%2F%2Fexample.com&scope=openid+read&code_challenge=hcCb3gToI1GPZeS_SIYWvaNT_5u0GB1oqOGQJqRKMSE
