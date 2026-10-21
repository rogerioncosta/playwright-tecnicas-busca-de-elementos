**Interface**
```SHELL
├── tests
|  ├── fixtures
|  |  ├── name.model.ts
|  |  ├── meu-teste.spec.ts
|  ├── .gitignore
|  ├── package.json
|  └── playwright.config.ts
```

``task.model.ts`` 

```TS
export interface NameModel {
  name: string
  is_done: boolean
}
```
``meu-teste.spec.ts``
```TS
import { test, expect } from '@playwright/test';

import { nameModel } from './fixtures/name.model';

test('Caso de teste', async ({ page, request }) => {
  const model: NameModel = {
    name: 'Texto da string',
    is_done: false
    ....
  }
});
```
