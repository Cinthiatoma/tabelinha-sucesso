# 🏆 Tabelinha do Sucesso

Plataforma para acompanhar tarefas de várias pessoas, cada uma com as suas tarefas, dias da semana e período. Os dados ficam no **Firebase (plano gratuito)**, então aparecem iguais em qualquer aparelho.

Arquivos: `index.html` (a página inteira, sem build) e `firestore.rules` (regras de segurança do banco).

## Funcionalidades

- **Consultar**: tabela por período (De / Até), datas como `Ter 13/10`, semanas em cores alternadas, resumo por tarefa (`Total · ✅ · ❌` e % feito) e `--` nos dias sem tarefa planejada. Toque em uma célula para marcar (✅ → ❌ → `--` → vazio) ou na data para atualizar o dia todo.
- **Registrar**: marca as tarefas de um dia, com navegação por setas, calendário e botão Hoje.
- **Cadastro**: usuários e tarefas (com um ou mais dias da semana) e backup/restauração em texto.
- **Login** por e-mail e senha: só quem você cadastrar no Firebase acessa.

## Configurar o Firebase (gratuito, ~10 minutos)

1. Acesse https://console.firebase.google.com e clique em **Adicionar projeto**. Pode desativar o Google Analytics. O plano **Spark** é gratuito e não pede cartão.
2. **Build → Authentication → Vamos começar → E-mail/senha → Ativar**. Na aba **Users**, clique em **Adicionar usuário** e crie o seu e-mail e senha.
3. **Build → Firestore Database → Criar banco de dados**. Escolha o modo de produção e a região `southamerica-east1` (São Paulo).
4. Na aba **Regras** do Firestore, cole o conteúdo de `firestore.rules`, troque `SEU_EMAIL@exemplo.com` pelo e-mail do passo 2 e clique em **Publicar**.
5. Na engrenagem **Configurações do projeto → Seus apps → ícone Web `</>`**, registre um app e copie o `firebaseConfig`.
6. Abra o `index.html`, procure por `const FB=` e preencha com os valores copiados:
   ```js
   const FB={apiKey:"...",authDomain:"...",projectId:"...",appId:"..."};
   ```
7. Em **Authentication → Configurações → Domínios autorizados**, adicione `cinthiatoma.github.io` (ou o seu domínio). Sem isso o login não funciona no GitHub Pages.
8. Suba o `index.html` no GitHub (veja abaixo) e abra o site. Entre com o e-mail e a senha do passo 2.

Na primeira vez que você entrar, o app cria os dados iniciais na nuvem. Se o navegador tinha dados salvos da versão anterior, eles são aproveitados.

## Como os dados ficam guardados

- `config/app`: um documento com os usuários, as tarefas de cada um e o período.
- `marks`: uma linha por usuário e dia, com id `usuario_data` (ex.: `u1_2026-10-13`), contendo o status de cada tarefa (`ok`, `no` ou `na`).

Você vê e edita tudo em **Firestore Database → Dados**. As alterações aparecem em tempo real em todos os aparelhos conectados.

## Limites do plano gratuito (Spark)

Cerca de 1 GiB de armazenamento, 50 mil leituras e 20 mil gravações por dia. Para uso pessoal ou de família, sobra bastante.

## Publicar no GitHub Pages

1. Coloque `index.html` (e, se quiser, `README.md` e `firestore.rules`) no repositório.
2. **Settings → Pages → Deploy from a branch → `main` / `(root)` → Save**.
3. Em 1 a 3 minutos o site abre em `https://SEU_USUARIO.github.io/SEU_REPO/`. Para atualizar, substitua o `index.html` e force o recarregamento (Ctrl+Shift+R ou Cmd+Shift+R).

## Sem Firebase

Se o objeto `FB` ficar vazio, a página funciona em modo local: os dados ficam só no navegador (`localStorage`) e não há login.

## Segurança

A `apiKey` do Firebase pode ficar visível no código, é assim que o Firebase funciona. O que protege os dados são as **regras do Firestore** (passo 4) e o login. Não deixe o banco em modo de teste nem com `allow read, write: if true`.
