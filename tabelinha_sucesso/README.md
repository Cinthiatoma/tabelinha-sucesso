# Tabelinha do Sucesso

Acompanhamento de tarefas do Junior: consulta em tabela, registro diário (✅ / ❌ / --) e cadastro de tarefas.

Página única e estática (`index.html`), sem dependências nem build.

## Publicar no GitHub Pages

1. Crie um repositório no GitHub e envie estes arquivos:
   ```bash
   git init
   git add index.html README.md
   git commit -m "Tabelinha do Sucesso"
   git branch -M main
   git remote add origin https://github.com/SEU_USUARIO/SEU_REPO.git
   git push -u origin main
   ```
2. No repositório, vá em **Settings → Pages**.
3. Em **Build and deployment**, escolha **Deploy from a branch**, branch `main`, pasta `/ (root)`, e salve.
4. Após alguns minutos, o site fica em `https://SEU_USUARIO.github.io/SEU_REPO/`.

## Observações

- Os dados ficam salvos no `localStorage` do navegador, então são individuais de cada aparelho/navegador.
- Os dados de exemplo ficam na variável `data` dentro do `index.html`. Para começar vazio, troque por `let data={};` e altere a chave `KEY` (ex.: `tarefas-junior-v4`) para descartar o que já estiver salvo.
