bitcoin_edd_plugin
==================

EasyDigitalDownloads bitcoin gateway (100% compatible with Campaignify)


Workflow
----
Once a bitcoin request has been done, an email will be send to purchaser with @BTC information. The purchase will be marked as pending until admin confirms complete status through Campaigns - Payment History. 

Agents
-----
- PHP @btc generator.
- Bitcoin blockchain monitor: Daemon to monitor a list of btc addresses against an obelisk server and notify some web service.
- Deterministic wallet: A deterministic wallet is a wallet where private and public keys are all derived from a starting seed value. Take hash(seed + n) where n starts from 1 and increment as additional keys are needed. Use this value to generate the nth private key.

Configuration
--------------
1) Set gateway default values on *Campaings - Settings - Gateways*.

- Fields information:
	* Platform **master public key** MPK(1) => MPK that PHP Generator will use to generate addresses; the one related to electrum deterministic wallet and the one for obelisk-monitor range alert. (Only used if *One or multiple @BTC* is set to *ONE*)
	* One or multiple @BTC => Allowed values are *ONE* and *MULTIPLE* meaning whether each campaign has its own @BTC or if every transfer goes to your platform @BTC.
	* Transfer info => Message that will be displayed in checkout section previous to purchase. Here you can inform to your user that an email with instructions will be send.
	* FROM / SUBJECT / BODY => This is instructions email.

(1) The master public key is an interesting concept. A deterministic_wallet can be initialized with a master public key that allows generating all the public keys with deterministic_wallet::generate_public_key(), but not the corresponding private keys (through the secret parameter).

Imagine a small business owner who wants their staff to have access to deposit addresses in their wallet to accept payments from customers, but not the ability to access all the funds. Waiters in a restaurant can accept Bitcoin payments which only the shop owner can spend.

Another use-case is a website keeping their Bitcoins offline. They can accept payments into their offline wallet. Without access to their seed (which is kept offline), nobody can spend their Bitcoins.  

Version
----

0.0

Tech
-----------

*bitcoin_EDD_gateway* uses a number of open source projects to work properly:
* [Wordpress.org] - https://github.com/WordPress/WordPress
* [Easy-Digital-Downloads] - https://github.com/easydigitaldownloads/Easy-Digital-Downloads
* [Astoundify / crowdfunding] - https://github.com/Astoundify/crowdfunding
* [Obelisk / Unsystem] - https://github.com/caedesvvv/obelisk
* [Electrum.org] - https://electrum.org/download.html

Dependencies
--------------
- PHP platform address manager => elgg/fundraising-bitcoin(1)
- Deterministic wallet => electrum wallet (2)(a)
- Transaction monitor => obelisk-monitor (3)

  
(1) https://github.com/aleph1888/Coopfunding/tree/v05/mod/fundraising-bitcoin/lib

(2) http://libbitcoin.dyne.org/doc/crypto.html#deterministic-wallets

(a) A deterministic wallet can be backed up by copying the starting seed value to a secure location, and this only needs to be done once. If the wallet ever gets lost, all private and public keys can be regenerated from the initial seed.

(3) https://github.com/caedesvvv/obelisk-monitor


##### Calaways EDD gateways bundle. Configure Plugins. Instructions in following README.md files

* plugins/github/README.md


License
----

?


**Free Software, Hell Yeah!**
@BTC 1DNxbBeExzv7JvXgL6Up5BSUvuY4gE8q4A
