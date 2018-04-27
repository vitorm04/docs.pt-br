### <a name="xml-schema-validation-is-stricter"></a>A validação do esquema XML está mais rigorosa

|   |   |
|---|---|
|Detalhes|No .NET Framework 4.5, a validação do esquema XML está mais rigorosa. Se você usar xsd:anyURI para validar um URI como um protocolo mailto, a validação falhará se houver espaços no URI. Nas versões anteriores do .NET Framework, a validação foi bem-sucedida. A alteração afeta somente aplicativos destinados ao .NET Framework 4.5.|
|Sugestão|Se for necessária uma validação menos rigorosa do .NET Framework 4.0, o aplicativo de validação poderá se destinar à versão 4.0 do .NET Framework. No entanto, ao destinar para o .NET 4.5, é necessário revisar o código para se certificar de que URIs inválidos (com espaços) não são esperados como valores de atributo com o tipo de dados anyURI.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Redirecionando|

