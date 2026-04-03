# Dashboard Temeron

Dashboard estático para visualização de métricas de redes sociais a partir de exportações do Meta Business Suite.

## Estrutura de Arquivos

- `index.html`: Arquivo principal contendo a interface, formatação de dados e lógicas de visualização.
- `data/`: Diretório destinado aos arquivos CSV exportados.
- `posts/`: Diretório destinado às imagens de capa das publicações.
- `logo.png`: Logotipo da empresa exibido na barra lateral.
- `favicon.png`: Ícone da aba do navegador e logotipo base para o selo da marca no rodapé.

## Preparação de Dados

1. Exporte os dados em formato CSV por meio da plataforma Meta Business Suite.
2. Renomeie o arquivo mensal utilizando o padrão `YYYY-MM.csv` (exemplo: `2026-03.csv`).
3. Para dados gerais da conta (seguidores, saldo, conversões), crie o arquivo `YYYY-MM-conta.csv`.
4. Transfira os arquivos para o diretório `data/`.

*Nota sobre fuso horário:* O Meta Business Suite exporta os horários das publicações com base no Horário do Pacífico (PT). O código aplica uma compensação de +5 horas para ajustar os registros de tempo para o Horário de Brasília (BRT).

## Gerenciamento de Imagens

1. Extraia o shortcode da URL da publicação no Instagram. (exemplo: na URL `https://www.instagram.com/p/DVbPpeqiFvM/`, o shortcode é `DVbPpeqiFvM`).
2. Salve o arquivo visual no diretório `posts/` nos formatos `.jpg`, `.jpeg` ou `.png`.
3. Nomeie o arquivo obrigatoriamente como `[shortcode].jpg` (exemplo: `DVbPpeqiFvM.jpg`).

## Configurações do Cliente

A identificação do projeto está localizada na linha 25 do arquivo `index.html`. Proceda com a substituição conforme necessário:

```javascript
const CLIENT_NAME = 'SetUp English School';
const ACCOUNT     = 'setup.english';
