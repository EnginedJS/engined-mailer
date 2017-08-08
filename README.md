# engined-mailer

Mailer service for engined, used to send email in backend.


## Installation

Install via NPM:

```shell
npm install engined-mailer
```

## Usage

Start engined-mailer service in engined, see example below:

```javascript
const { Manager } = require('engined');
const MailerService = require('engined-mailer');

const mailer = MailerService();

const main = async () => {

	// Create manager
	let serviceManager = new Manager({ verbose: true });

	// Adding service to manager
	serviceManager.add('Mailer', mailer);

	// Start all services
	await serviceManager.startAll();
};

main();
```

## Using specific mailer backend

Here is example to get agent for specific backend to save file:

```javascript

// Using local mailer backend
let localAgent = this.getContext().get('Mailer').getAgent('default');

// Send Email
localAgent.sendMailWithTokens({
	from: config.get('mailer').sender.name + ' <' + config.get('mailer').sender.address + '>',
	to: 'example@email.com',
	subject: 'test',
	html: '<p>1234</p>'
})

```

## Register mailer backend

```javascript

// Register mailer backend
this.getContext('Mailer').registerAgent('local', agent);
```

## License
Licensed under the MIT License

## Authors
Copyright(c) 2017 Leon Lin（林為志） <leonlin14@gmail.com>
