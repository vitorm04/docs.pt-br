### <a name="deserialization-of-objects-across-appdomains-can-fail"></a>Desserialização de objetos em domínios de aplicativo podem falhar

|   |   |
|---|---|
|Detalhes|Em alguns casos, quando um aplicativo usa dois ou mais domínios de aplicativo com bases de aplicativo diferentes, a tentativa de desserializar objetos no contexto da chamada lógica nos domínios de aplicativo aciona uma exceção.|
|Sugestão|Consulte [Mitigação: desserialização de objetos em domínios de aplicativos](~/docs/framework/migration-guide/mitigation-deserialization-of-objects-across-app-domains.md).|
|Escopo|Microsoft Edge|
|Versão|4.5.1|
|Tipo|Tempo de execução|

