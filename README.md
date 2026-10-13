# site-vendas

Apresentação navegável da **AUVP Escola**. É um arquivo único, `index.htm`,
com as imagens, vídeos e logos ao lado. Não tem build nem dependência: basta
abrir o `index.htm` no navegador.

Navegação: setas `←` `→` entre seções, `H` ou `Esc` para a Home. O menu lateral
abre pelo ícone ☰ no canto superior esquerdo (basta passar o mouse); as teclas
de 1 a 9 levam direto a cada seção, na ordem do menu. A apresentação em PDF (`AUVP Escola - 2026.pdf`)
pode ser baixada pelo menu lateral e pelo botão no fim da apresentação.

## PDF de download

O `AUVP Escola - 2026.pdf` é um guia em A4 que reúne as informações da
apresentação e do material de apoio. A fonte dele é `pdf/guia-auvp-escola.htm`
(com as fotos já otimizadas em `pdf/img/`). Para mudar o texto, edite esse
arquivo e gere o PDF de novo com o Chrome, rodando no PowerShell a partir da
pasta do repositório (o Chrome precisa dos caminhos completos):

```powershell
& "C:\Program Files\Google\Chrome\Application\chrome.exe" --headless --no-pdf-header-footer --virtual-time-budget=15000 "--print-to-pdf=$PWD\AUVP Escola - 2026.pdf" "$PWD\pdf\guia-auvp-escola.htm"
```

Ou abra o `pdf/guia-auvp-escola.htm` no Chrome, `Ctrl+P` → Salvar como PDF,
com margens "Nenhuma" e "Gráficos de plano de fundo" marcado.

- **Botão do WhatsApp (última página):** ainda sem link. Quando houver o número
  do Closer, troque no fim do `guia-auvp-escola.htm` o `<span class="cta">` por
  `<a class="cta" href="https://wa.me/55DDDNUMERO">` (e o `</span>` por `</a>`)
  e gere o PDF de novo.
- **Capa e fechamento** usam `pdf/img/capa-fundo.jpg` e `pdf/img/fecho-fundo.jpg`,
  fotos com o escurecimento já aplicado. Não volte a pôr degradê transparente
  por cima de foto: isso deixa o PDF lento para rolar.

## Versões

| Versão | Onde está | Commit |
| --- | --- | --- |
| **V1** — snapshot de 16/09/2026 | branch `v1` | `8faf9a8` |
| Em desenvolvimento | branch `main` | segue adiante |

A branch **`v1`** é um ponto de retorno congelado, guardado antes da rodada de
mudanças seguinte. Ela não recebe commits: todo trabalho novo vai para a `main`.

### O que a V1 contém

- **11 seções**: Home, Quem somos nós?, O Ecossistema AUVP, A Escola, Dinâmica
  das aulas, Módulos do treinamento, Materiais de apoio, Ferramentas, Lives
  comunidade e app, Calculadoras e Boas-vindas.
- **Ecossistema** com os 7 produtos em anel, o card da Escola em destaque e os
  cards abrindo como painel, com a logo do produto.
- **Calculadoras** com as quatro em destaque em cards dourados de cor cheia,
  cada uma com link próprio.
- **Cronograma** com 12 módulos.
- **Logos dos produtos vetorizadas**, sem depender de fonte instalada na
  máquina de quem abre.

### Como voltar à V1

Para só olhar, sem mexer em nada:

- No GitHub, trocar a branch para `v1` e abrir o `index.htm`.
- Ou baixar tudo pronto:
  <https://github.com/ProdutosAUVP/site-vendas/archive/refs/heads/v1.zip>

Com o repositório na máquina:

```bash
git fetch origin
git checkout v1        # olhar a V1
git checkout main      # voltar para a versão em desenvolvimento
```

Para trazer a V1 inteira de volta como versão corrente, criando um commit que
desfaz tudo que veio depois — sem apagar o histórico:

```bash
git checkout main
git rm -rq --ignore-unmatch .   # tira o que existe hoje
git checkout origin/v1 -- .     # traz tudo que a V1 tinha
git commit -m "Volta a apresentação para a V1"
```
