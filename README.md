# Meu Livro Caixa — PWA

App de controle financeiro pessoal. Funciona no navegador, instala na tela inicial
do celular, roda offline e guarda os dados no próprio aparelho.

## Publicar no GitHub Pages

1. Crie um repositório novo no GitHub — pode se chamar `livro-caixa`. Deixe **público**
   (o Pages gratuito exige repositório público).
2. Envie estes arquivos para a raiz do repositório. Pelo site: **Add file → Upload files**,
   arraste tudo (inclusive a pasta `lib/`) e confirme o commit.
3. No repositório, vá em **Settings → Pages**.
4. Em *Source*, escolha **Deploy from a branch**; em *Branch*, escolha `main` e a pasta `/ (root)`. Salve.
5. Espere 1–2 minutos. O endereço aparece na mesma tela:
   `https://SEU-USUARIO.github.io/livro-caixa/`

Pelo terminal, se preferir:

```bash
git init
git add .
git commit -m "Livro Caixa"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/livro-caixa.git
git push -u origin main
```

## Instalar no celular

- **Android (Chrome):** abra o endereço → menu ⋮ → *Instalar app* / *Adicionar à tela inicial*.
- **iPhone (Safari):** abra o endereço → botão Compartilhar → *Adicionar à Tela de Início*.
  Precisa ser pelo Safari; outros navegadores no iOS não instalam.

Depois de instalado, ele abre com ícone próprio, em tela cheia, e funciona sem internet.

## Avisos de vencimento

O botão **Ativar avisos** pede permissão de notificação. O app avisa sobre contas
vencidas ou vencendo quando você o abre — uma vez por dia.

Notificação que chega com o app fechado (push de verdade) exige um servidor enviando
as mensagens; não dá para fazer só com arquivos estáticos. No iPhone, notificação de PWA
só funciona depois de instalar na tela inicial.

## Onde ficam os dados

Tudo é salvo no `localStorage` do navegador — no seu aparelho, não na nuvem. Cada
dispositivo tem sua própria base. Para levar os dados de um para outro, use
**Exportar Excel** num e **Importar Excel** no outro.

Limpar os dados de navegação do site apaga os lançamentos. Exporte de vez em quando.

## Arquivos

| Arquivo | O que é |
|---|---|
| `index.html` | O app inteiro — interface, lógica, gráficos |
| `manifest.json` | Nome, ícone e cores da instalação |
| `sw.js` | Service worker: guarda o app em cache para uso offline |
| `icon-*.png` | Ícones da tela inicial |
| `lib/xlsx.full.min.js` | Biblioteca SheetJS (Apache 2.0), para importar e exportar Excel |

## Testar antes de publicar

Service worker só funciona em `https://` ou em `localhost`. Para testar na sua máquina:

```bash
python3 -m http.server 8000
```

Depois abra `http://localhost:8000`. Abrir o `index.html` por duplo clique não ativa
o modo offline nem a instalação.
