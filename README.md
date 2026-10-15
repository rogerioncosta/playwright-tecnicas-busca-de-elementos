# playwright-tecnicas-busca-de-elementos
## Técnicas para buscar elementos no playwright (web)

### Pegar a tag: input, button, etc... e olhar suas propriedades:
- placeholder: traz um texto informativo
- type: text
- id
- class

O id é a estratégia mais fácil para identificar o elemento.
- Em qualquer lugar do html
- CTRL + F para buscar se o seletor existe/quantos existem
- #descricaoDoId (se encontrar 1 of 1, ok podemos seguir com ele)
  - Exemplo no código em um input do tipo text
  ```JS
  await page.fill('#descricaoDoId', 'O que deverá ser preenchido no input');
  ```
- 

