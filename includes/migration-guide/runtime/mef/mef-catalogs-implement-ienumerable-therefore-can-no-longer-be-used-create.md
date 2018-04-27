### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>Os catálogos do MEF implementam IEnumerable e, portanto, não podem mais ser usados para criar um serializador

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.5, os catálogos do MEF implementam IEnumerable e, portanto, não podem mais ser usados para criar um serializador (objeto <xref:System.Xml.Serialization.XmlSerializer?displayProperty=name>). Tentar serializar um catálogo de MEF gera uma exceção.|
|Sugestão|Não é mais possível usar o MEF para criar um serializador|
|Escopo|Principal|
|Versão|4.5|
|Tipo|Tempo de execução|

