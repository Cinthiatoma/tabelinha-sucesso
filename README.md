# 🏆 Tabelinha do Sucesso

Plataforma simples para acompanhar tarefas de várias pessoas, cada uma com as suas tarefas, dias da semana e período de acompanhamento.

É uma página única e estática (`index.html`), sem dependências, sem build e sem servidor.

## Funcionalidades

### Consultar
- Tabela por período, com as datas no formato `Ter 13/10`.
- Escolha do período em **De / Até** (até 2 anos).
- Semanas (segunda a domingo) separadas por cores alternadas.
- Resumo por tarefa: `Total · ✅ feitas · ❌ não feitas` e a porcentagem feita.
- Dias em que a tarefa não está planejada aparecem automaticamente com `--`.
- O dia de hoje fica destacado em azul. Tocar em uma data abre um painel para atualizar as tarefas daquele dia, sem sair da tela (com setas para o dia anterior e o próximo).

### Registrar
- Escolha o dia (setas, calendário ou botão **Hoje**).
- Marque cada tarefa como ✅ concluída, ❌ não concluída ou `--`. Tocar de novo na opção marcada limpa o campo.

### Cadastro
- **Usuários**: adicionar, renomear e excluir. O seletor no cabeçalho troca de usuário.
- **Tarefas** (de cada usuário): adicionar, renomear e excluir, com um ou mais dias da semana.
  - O total esperado considera só os dias marcados.
  - Sem nenhum dia marcado, a tarefa vale para todos os dias.
- **Backup**: gera um texto com todos os dados e permite restaurá-lo depois (também serve para levar os dados a outro aparelho).

## Como publicar (GitHub Pages)

1. Coloque `index.html` e `README.md` na raiz do repositório:
   ```bash
   git init
   git add index.html README.md
   git commit -m "Tabelinha do Sucesso"
   git branch -M main
   git remote add origin https://github.com/SEU_USUARIO/SEU_REPO.git
   git push -u origin main
   ```
2. No repositório, abra **Settings → Pages**.
3. Em **Build and deployment**, escolha **Deploy from a branch**, branch `main`, pasta `/ (root)`, e clique em **Save**.
4. Em 1 a 3 minutos o site fica em `https://SEU_USUARIO.github.io/SEU_REPO/`.

Para atualizar o site, basta substituir o `index.html` no repositório e fazer o commit. Se a página abrir com a versão antiga, force a atualização com Ctrl+Shift+R (Cmd+Shift+R no Mac).

## Sobre os dados

- Tudo é salvo no `localStorage` do navegador. Cada aparelho e cada navegador tem os seus próprios dados, e limpar os dados do navegador apaga as marcações.
- Faça backup com frequência em **Cadastro → Backup**.
- Para que várias pessoas vejam os mesmos dados em aparelhos diferentes, seria preciso um banco de dados online (por exemplo Supabase ou Firebase). Esta versão não inclui isso.

## Dados iniciais

Na primeira abertura existe o usuário **Junior** com 4 tarefas (Caminhada Seg 14h, Curso Qua, Caminhada Qui 10h, Terapia Qui 17h) e o período 12/10/26 a 09/01/27. Tudo pode ser alterado nas telas.
