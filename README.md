# moneda-anonima-virtual-beta
Es una moneda virtual.

```bash

yes | pkg install mariadb && yes | pkg install nodejs && yes | pkg install git && npm i mysql2 dotenv

```



```bash
git clone https://github.com/criptogamer/moneda-virtual-anonima.git

```


```bash
cd moneda-virtual-anonima
```




<h2>Crear cuentas</h2>

```nodejs



const network = require('./index.js');

async function main() {
  try {
    console.log('--- 1. Creación de cuentas privadas ---');
    const sender = await network.createAccount();
    const recipient = await network.createAccount();

    console.log('Cuenta del Emisor:', sender);
    console.log('Cuenta del Receptor:', recipient);

    process.exit(0);
  } catch (err) {
    console.log(err);
    process.exit(1);
  }
}

main();





```

```bash
nano create_accounts.js
```

```bash
node create_accounts.js
```

<h2>Crear dirección temporal (Estado Inicial: Activa, Indefinida)</h2>

```nodejs




const network = require('./index.js');

async function main() {
  try {
    const privateAddress = "TU_PRIVATE_ADDRESS";
    const privateKey = "TU_PRIVATE_KEY";

    console.log('\n--- 2. Generación de dirección pública de un solo uso (Estado: active) ---');
    const tempPaymentAddress = await network.generateTemporaryPublicAddress(
      privateAddress,
      privateKey
    );
    console.log('Dirección Pública Temporal Generada:', tempPaymentAddress);

    process.exit(0);
  } catch (err) {
    console.log(err);
    process.exit(1);
  }
}

main();





```

```bash
nano create_temp_address.js
```

```bash
node create_temp_address.js
```

<h2>Desactivar dirección temporal manualmente</h2>

```nodejs




const network = require('./index.js');

async function main() {
  try {
    const privateAddress = "TU_PRIVATE_ADDRESS";
    const privateKey = "TU_PRIVATE_KEY";
    const publicAddressToDeactivate = "DIRECCION_TEMPORAL_A_DESACTIVAR";

    console.log('\n--- Desactivando dirección temporal manualmente ---');
    const result = await network.deactivateTemporaryPublicAddress(
      privateAddress,
      privateKey,
      publicAddressToDeactivate
    );
    console.log('Resultado:', result);

    process.exit(0);
  } catch (err) {
    console.log(err);
    process.exit(1);
  }
}

main();





```

```bash
nano deactivate_temp_address.js
```

```bash
node deactivate_temp_address.js
```

<h2>Transacciones</h2>

```nodejs



const network = require('./index.js');

async function main() {
  try {
    console.log('\n--- 3. Ejecución de Transferencia ---');
    const testnetNetworkId = 7357437;

    const tx = {
      fromAddress: "TU_PRIVATE_ADDRESS",
      fromPrivateKey: "TU_PRIVATE_KEY",
      to: "DIRECCION_TEMPORAL_DESTINO",
      value: 0.00003000,
      networkId: testnetNetworkId
    };

    const txResult = await network.transfer(tx);
    console.log('Resultado de la Transferencia:', txResult);

    process.exit(0);
  } catch (err) {
    console.log(err);
    process.exit(1);
  }
}

main();





```

```bash
nano transaction.js
```

```bash
node transaction.js
```

<h2>Obtener balance</h2>

```nodejs
const network = require('./index.js');

async function get_balance() {
  try {
    const addressPrivate = "TU_PRIVATE_ADDRESS";
    const privateKey = "TU_PRIVATE_KEY";

    const balance = await network.getBalance(addressPrivate, privateKey);
    console.log(balance);

    process.exit(0);
  } catch (err) {
    console.log(err);
    process.exit(1);
  }
}

get_balance();
```

```bash
nano get_balance.js
```

```bash
node get_balance.js
```

<h2>Obtener detalles de transacción por dirección temporal</h2>

```nodejs
const network = require('./index.js');

async function ejecutarBusqueda() {
  try {
    const direccionABuscar = 'DIRECCION_A_CONSULTAR';
    
    const historial = await network.transactionAddress(direccionABuscar);
    console.log('Historial de transacciones obtenido:', historial);
  } catch (error) {
    console.error('Error al obtener las transacciones:', error);
  }
}

ejecutarBusqueda();
```

```bash
nano address_temp_details_transaction.js
```

```bash
node address_temp_details_transaction.js
```

<h2>Obtener detalles por hash</h2>

```nodejs
const network = require('./index.js');

async function main() {
  try {
    console.log('\n--- 4. Consulta de detalles de la transacción ---');
    const txDetails = await network.getTransaction("HASH_DE_TRANSACCION");
    console.log('Información Pública de la Transacción:', txDetails);

    process.exit(0);
  } catch (err) {
    console.log(err);
    process.exit(1);
  }
}

main();
```

```bash
nano details_transaction_hash.js
```

```bash
node details_transaction_hash.js
```

<h2>Obtener detalles por bloque</h2>

```nodejs
const network = require('./index.js');

async function main() {
  try {
    console.log('\n--- 5. Consulta de detalles del bloque ---');
    const blockDetails = await network.getBlock(1); // Reemplazar por ID de bloque real
    console.log('Información Pública del Bloque:', blockDetails);

    process.exit(0);
  } catch (err) {
    console.log(err);
    process.exit(1);
  }
}

main();
```

```bash
nano get_inf_block.js
```

```bash
node get_inf_block.js
```

