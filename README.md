
## Etapa 2.4 - Teste de responsividade

* **Quantas colunas aparecem com a janela em ~800px de largura:** Em média 4 colunas.
* **Quantas colunas aparecem com a janela em ~400px de largura:** 2 colunas.
* **O que acontece quando não há largura suficiente nem para uma coluna de 160px:** O card para de encolher (já que 160px é o limite mínimo definido no `minmax`) e acaba causando um transbordamento (overflow), forçando a criação de uma barra de rolagem horizontal na tela.

---

## Etapa 3.4 - Questão reflexiva

* **`justify-items` (no container) vs `justify-self` (no item):** O `justify-items` é definido no elemento pai (container) e alinha horizontalmente todos os itens da grade de uma só vez. O `justify-self` é aplicado diretamente em um item específico, servindo para sobrescrever a regra do container e alinhar apenas aquele item.
* **`align-items` vs `align-content`:** O `align-items` alinha os itens verticalmente dentro de suas respectivas linhas ou células na grade. O `align-content` alinha o bloco inteiro de linhas em relação ao container (só tem efeito visual se o container for mais alto que o conteúdo total das linhas).

---

## Etapa 4.4 - Questão de consolidação

* **Por que redefinimos grid-template-areas na media query em vez de apenas grid-template-columns?** Porque redefinir o layout para apenas 1 coluna não garante a ordem visual correta das seções. Ao redefinir o `grid-template-areas` na media query, nós forçamos explicitamente a ordem vertical exata que o wireframe mobile exige (topo, destaque, novidades, categorias e rodapé), garantindo que as áreas fiquem empilhadas perfeitamente.

---

## Revisão final - conectando os pontos

### Questão 1
**Qual é a função do -1 na notação grid-column: 1/-1? Por que é mais robusto do que escrever o número exato da última linha?** **Resposta:** O valor `-1` aponta dinamicamente para a última linha explícita da grade. Ele é mais robusto porque, se no futuro o layout for alterado (adicionando ou removendo colunas), o elemento continuará se esticando até o limite final da grade automaticamente, sem que o desenvolvedor precise lembrar de atualizar o número da linha no CSS.

### Questão 2
**Diferencie auto-fill de auto-fit dentro de repeat(). Em qual situação um se comporta de forma diferente do outro?** **Resposta:** Ambos criam a quantidade máxima de colunas que couberem no container, mas a diferença ocorre quando sobra espaço na tela. O `auto-fill` mantém colunas vazias (fantasmas) ocupando o espaço restante. Já o `auto-fit` colapsa (zera a largura) dessas colunas vazias, forçando os cards existentes a se esticarem para preencher 100% da largura disponível.

### Questão 3
**O que acontece se você criar uma grid-template-areas não-retangular - por exemplo, nomear uma área em forma de L? O navegador gera erro, ignora silenciosamente ou algo diferente?** **Resposta:** O navegador considera a declaração inválida e a ignora silenciosamente (a grade quebra). O CSS Grid tem uma regra estrita de que todas as áreas nomeadas no `grid-template-areas` precisam formar áreas perfeitamente retangulares; formatos irregulares como "L" não são suportados.

### Questão 4 - Identifique o erro
**O CSS abaixo não produz o layout esperado. Identifique e corrija o problema:** * **Qual é o problema:** Existem três problemas de sintaxe no CSS: 1) As propriedades `grid-area` estão recebendo valores entre aspas (ex: `"header"`), o que é incorreto. 2) Os nomes mapeados no `header` e `footer` não correspondem aos nomes definidos no `grid-template-areas` (onde estão como "cabecalho" e "rodape"). 3) Está faltando um ponto e vírgula no final da declaração do footer.
* **Como corrigir o header:** `header { grid-area: cabecalho; }`
* **Como corrigir o footer:** `footer { grid-area: rodape; }`