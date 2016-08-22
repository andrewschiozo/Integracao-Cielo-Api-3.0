# Cielo-API-3.0

Projeto em .NET para integração com a API de pagamento Cielo API 3.0.

Exemplo de uso em ambiente SANDBOX:

```
var api = new CieloApi(CieloEnvironment.Sandbox, Merchant.Sandbox);
var merchantOrderId = new Random().Next();
var customer = new Customer("Fulano da Silva");
var cardExpirationDate = new DateTime(DateTime.Now.Year + 1, 12, 1);
var creditCard = new CreditCard(SandboxCreditCard.Authorized1, "Teste Holder", cardExpirationDate, "123", Enums.CardBrand.Visa);
var payment = new Payment(15700, Enums.Currency.BRL, 1, true, ".Net Test Project", creditCard);
var transaction = new Transaction(merchantOrderId.ToString(), customer, payment);

var returnTransaction = api.CreateTransaction(Guid.NewGuid(), transaction);
```

Documentação da API: http://developercielo.github.io/Webservice-3.0/