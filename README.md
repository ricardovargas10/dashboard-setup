# Dashboard Temeron

Dashboard estático para visualização de métricas de Instagram a partir de exportações do Meta Business Suite.

---

## Estrutura de arquivos

```
dashboard-setup/
├── index.html              ← dashboard principal (não editar)
├── logo.png                ← logotipo do cliente (barra lateral)
├── favicon.png             ← ícone da aba e rodapé
├── temeron-logo.png        ← logotipo Temeron (rodapé)
├── data/
│   ├── 2026-03.csv         ← exportação mensal do Meta Business Suite
│   ├── 2026-04.csv         ← um arquivo por mês, no padrão YYYY-MM.csv
│   └── dados_gerais.xlsx   ← planilha de dados de conta (seguidores, etc.)
└── posts/
    └── DVtS7Q6E6W1.jpg     ← imagens dos posts (shortcode.jpg)
```

---

## Fluxo mensal

### 1. Publicações (Meta Business Suite)

1. Acesse **Meta Business Suite → Insights → Publicações**
2. Selecione o período do mês desejado
3. Clique em **Exportar → CSV**
4. Renomeie o arquivo para `YYYY-MM.csv` (ex: `2026-04.csv`)
5. Suba na pasta `data/` do repositório

### 2. Dados da conta (planilha)

1. Baixe o `dados_gerais.xlsx` do repositório
2. Na aba do ano correspondente, adicione uma linha com os dados do mês:

| Coluna | Onde encontrar no Meta |
|---|---|
| Ano / Mês | Preencha manualmente |
| Total seguidores | Público → Tendências → Seguidores (Total) |
| Seguidores ganhos | Público → Tendências → Seguidores (novos) |
| Deixaram de seguir | Público → Tendências → Deixaram de seguir |
| Conversas | Desempenho → Conversas iniciadas |
| Novos contatos | Desempenho → Novos contatos |
| Taxa de resposta | Desempenho → Taxa de resposta (só o número, sem %) |

3. Salve e suba o arquivo no repositório (substitui o anterior)

### 3. Imagens dos posts

1. Abra o post no Instagram e copie o shortcode da URL:
   - `https://www.instagram.com/p/DVtS7Q6E6W1/` → shortcode: `DVtS7Q6E6W1`
   - `https://www.instagram.com/reel/DWPJ0vxOeg9/` → shortcode: `DWPJ0vxOeg9`
2. Salve a imagem como `[shortcode].jpg`
3. Suba na pasta `posts/` do repositório

---

## Adaptar para outro cliente

No `index.html`, localize e edite as linhas:

```javascript
const CLIENT_NAME = 'SetUp English School';
const ACCOUNT     = 'setup.english';
```

Substitua também `logo.png` pelo logotipo do novo cliente.

---

## Observações técnicas

- **Fuso horário:** o Meta Business Suite exporta os horários em UTC-8 (Pacífico). O dashboard aplica automaticamente +5h para exibir no horário de Brasília (BRT/UTC-3).
- **Imagens:** o dashboard tenta `.jpg` primeiro, depois `.png`. Se nenhum arquivo for encontrado, exibe um placeholder.
- **Dados de conta opcionais:** se a planilha `dados_gerais.xlsx` não tiver dados de um mês, o dashboard exibe um aviso no lugar da seção.
- A Vercel republica automaticamente sempre que um arquivo for alterado no repositório.
