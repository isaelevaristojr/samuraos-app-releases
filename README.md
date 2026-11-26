# Samuraos — APK para instalação direta

Este repositório guarda o **instalador Android (APK)** do Samuraos, o sistema
de gestão de academias de artes marciais em **https://samuraos.com.br**.

## Baixar

O link oficial (sempre a última versão publicada) é

    https://github.com/isaelevaristojr/samuraos-app-releases/releases/latest/download/Samuraos.apk

Esse é exatamente o link que o botão **“Baixar APK”** da tela de login e a
tela de **“Atualize o app para continuar”** usam. A versão e o mínimo exigido
ficam no manifesto público:

    https://samuraos.web.app/releases.json

## Como instalar

1. Toque no link e baixe o arquivo.
2. Abra o arquivo baixado e toque em **Instalar**.
3. Se o celular avisar sobre “origem desconhecida”, permita a instalação uma
   única vez (é normal para app distribuído fora da Play Store).

## Por que o APK não fica no Firebase Hosting?

O plano gratuito do Firebase Hosting (Spark) **recusa arquivo executável** —
o upload do `.apk` é rejeitado pelo próprio serviço
(`Executable files are forbidden on the Spark billing plan`). O hosting
continua no Firebase (`samuraos.web.app`), só o binário fica aqui.

## Versionamento

- **tag** = `v<versão>` (ex.: `v1.0.0`), que é a versão que o app mostra em
  *Perfil → Sobre* e a que o portão de versão compara.
- **asset** = `Samuraos.apk` (nome fixo, para o link de “latest” nunca mudar).
- Cada publicação é feita por `backend/tool/deploy_apk.dart`, que sobe o
  release aqui, grava o `releases.json` no Hosting e lembra de espelhar
  `MIN_ANDROID_VERSION` no servidor.

Assinatura: por enquanto o release é assinado com a chave de desenvolvimento
(gere `android/key.properties` + keystore próprio antes de publicar na Play
Store; trocar de chave depois exige desinstalar).
