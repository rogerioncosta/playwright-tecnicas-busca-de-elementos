# playwright-tecnicas-busca-de-elementos
## Técnicas para buscar elementos no playwright (web)
**Seletores CSS**
- Rodar em modo debug para acompanhar cada passo (por padrão é headless, onde não vemos o navegador abrindo):
  - npx playwright test test/nome-do-teste.spec.ts --debug
- Rodar em modo onde o navegador abre como um usuário normal acessando
  - npx playwright test test/nome-do-teste.spec.ts --headed

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
  ```TS
  await page.fill('#descricaoDoId', 'O que deverá ser preenchido no input');
  ```
**Quando temos o ID**
- Buscando pelo placeholder
  - input[placeholder="Descricao do placeholder"]
  ```TS
  await page.fill('input[placeholder="Descricao do placeholder"]', 'O que deverá ser preenchido no input');
  ```
**Sem placeholder**
- buscando pelo type
```TS
await page.fill('input[type=text]', 'O que deverá ser preenchido no input');
```
**Buscando pelo classe**
- ._nomeDaClasse no buscador de elementos
```TS
await page.fill('._nomeDaClasse', 'O que deverá ser preenchido no input');
```
**Caso o nome da classe possa ter atualização após nova versão ou mudança no código**
- input[class*=nomeDaClasse] (o * contém partes do nome e ``funciona para qualquer propriedade``)
```TS
await page.fill('input[class*=nomeDaClasse]', 'O que deverá ser preenchido no input');
```
**Submetendo forms HTML**
- Utilizando a função de localizador:
```TS
await page.locator('input[class*=nomeDaClasse]').fill('O que deverá ser preenchido no input');
```
ou guardando o localizador em uma constante
``Utilizar constantes é bom para controlar o comportamento de alguns elementos para criar padrões de projeto conforme a automação cresce`` 
```TS
const inputName = page.locator('input[class*=nomeDaClasse]');
await inputName.fill('O que deverá ser preenchido no input'); // só passa o que será preenchido no input
```

