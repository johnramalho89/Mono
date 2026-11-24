# Como publicar o site do mono. (GitHub Pages, grátis)

O Google exige que a página inicial e a política de privacidade fiquem num domínio que **você comprova ser seu**. O jeito gratuito é o GitHub Pages com o seu "site de usuário" (`SEUUSUARIO.github.io`), porque nele dá para colocar o arquivo de verificação do Google na raiz.

## 0. Antes de tudo: troque o e-mail
Nos três arquivos `.html`, troque `SEU_EMAIL_AQUI` pelo e-mail de contato (o mesmo do "e-mail de suporte" da tela de consentimento). No VS Code: Ctrl+Shift+H, substituir em todos os arquivos.

## 1. Criar o site
1. Entre em github.com (crie a conta se não tiver).
2. **New repository** com o nome exato `SEUUSUARIO.github.io` (troque SEUUSUARIO pelo seu nome de usuário do GitHub), **Public**.
3. **Add file › Upload files**: arraste `index.html`, `privacidade.html`, `termos.html`, `estilo.css` e a pasta `fonts`. **Commit changes**.
4. Em **Settings › Pages**, confira: *Source: Deploy from a branch*, *Branch: main / (root)*.
5. Em 1 a 2 minutos o site abre em `https://SEUUSUARIO.github.io/`.

## 2. Comprovar no Google que o site é seu (Search Console)
1. Abra search.google.com/search-console com **a mesma conta Google** do projeto no Google Cloud.
2. **Adicionar propriedade › Prefixo do URL** › `https://SEUUSUARIO.github.io/`.
3. Escolha **Arquivo HTML**, baixe o arquivo (`googleXXXX.html`) e envie para o mesmo repositório (Upload files), na raiz.
4. Espere o site atualizar (1 a 2 min) e clique em **Verificar**.

## 3. Preencher no Google Cloud (Google Auth Platform › Branding)
| Campo | Valor |
|---|---|
| Nome do app | `mono.` (ou "mono diário de idiomas"; use o mesmo nome da página inicial) |
| E-mail de suporte | o seu e-mail |
| Página inicial do aplicativo | `https://SEUUSUARIO.github.io/` |
| Política de Privacidade | `https://SEUUSUARIO.github.io/privacidade.html` |
| Termos de Serviço | `https://SEUUSUARIO.github.io/termos.html` |
| Domínios autorizados | `SEUUSUARIO.github.io` |
| Logotipo | deixe em branco (logotipo dispara revisão extra) |

Em **Acesso a dados**, o único escopo deve ser `.../auth/drive.appdata`.

## 4. Publicar
**Público-alvo › Publicar app**. Como o escopo é não sensível, não há revisão de escopo. O Google pode pedir a **verificação da marca** (nome + página + política), que costuma levar de 2 a 3 dias úteis; enquanto isso o login funciona, e a tela de consentimento pode mostrar o aviso de app não verificado.

## Observações
- A política descreve o login com Google como recurso **opcional** do app, que guarda só uma cópia criptografada na pasta oculta do app no Drive. Ela precisa continuar verdadeira: se o app mudar o que faz com os dados do Google, atualize a página.
- Se já tiver um domínio próprio, pode hospedar os mesmos arquivos nele; o processo de verificação é o mesmo.
