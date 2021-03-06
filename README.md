# fonk-nif-validator

[![CircleCI](https://badgen.net/github/status/Lemoncode/fonk-nif-validator/master?icon=circleci&label=circleci)](https://circleci.com/gh/Lemoncode/fonk-nif-validator/tree/master)
[![NPM Version](https://badgen.net/npm/v/@lemoncode/fonk-nif-validator?icon=npm&label=npm)](https://www.npmjs.com/package/@lemoncode/fonk-nif-validator)
[![bundle-size](https://badgen.net/bundlephobia/min/@lemoncode/fonk-nif-validator)](https://bundlephobia.com/result?p=@lemoncode/fonk-nif-validator)

This is a [fonk](https://github.com/Lemoncode/fonk) microlibrary that brings validation capabilities to:

- Validate if a field of a form is a valid NIF (DNI, NIE and/or CIF)

How to install it:

```bash
npm install @lemoncode/fonk-nif-validator --save
```

How to add it to an existing form validation schema:

We have the following form model:

```
const myFormValues = {
  providerCIF: 'P9316179B',
  clientDNI: '31016922L'
}
```

We can add a nif validation to the myFormValues

```javascript
import { nif } from '@lemoncode/fonk-nif-validator';

const validationSchema = {
  field: {
    providerCIF: [
      {
        validator: nif.validator,
        customArgs: { validTypes: [nif.types.CIF] },
      },
    ],
    clientDNI: [
      {
        validator: nif.validator,
        customArgs: { validTypes: [nif.types.DNI, nif.types.NIE] },
      },
    ],
  },
};
```

You can customize the error message displayed in two ways:

- Globally, replace the default error message in all validationSchemas (e.g. porting to spanish):

```javascript
import { nif } from '@lemoncode/fonk-nif-validator';

nif.setErrorMessage('El campo debe de ser un DNI válido');
```

- Locally just override the error message for this validationSchema:

```javascript
import { nif } from '@lemoncode/fonk-nif-validator';

const validationSchema = {
  field: {
    providerCIF: [
      {
        validator: nif.validator,
        customArgs: { validTypes: [nif.types.CIF] },
        message: 'Error message only updated for the validation schema',
      },
    ],
    clientDNI: [
      {
        validator: nif.validator,
        customArgs: { validTypes: [nif.types.DNI, nif.types.NIE] },
        message: 'Error message only updated for the validation schema',
      },
    ],
  },
};
```

Please, refer to [fonk](https://github.com/Lemoncode/fonk) to know more.

## License

[MIT](./LICENSE)

# About Basefactor + Lemoncode

We are an innovating team of Javascript experts, passionate about turning your ideas into robust products.

[Basefactor, consultancy by Lemoncode](http://www.basefactor.com) provides consultancy and coaching services.

[Lemoncode](http://lemoncode.net/services/en/#en-home) provides training services.

For the LATAM/Spanish audience we are running an Online Front End Master degree, more info: http://lemoncode.net/master-frontend
