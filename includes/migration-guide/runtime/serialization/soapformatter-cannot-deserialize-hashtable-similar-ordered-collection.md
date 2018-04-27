### <a name="soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a>SoapFormatter não pode desserializar Hashtable e objetos de coleção ordenados semelhantes

|   |   |
|---|---|
|Detalhes|O <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=name> não garante que objetos serializados em uma versão do .NET Framework serão desserializados com êxito em uma versão diferente. Especificamente, algumas coleções ordenadas (como <xref:System.Collections.Hashtable?displayProperty=name>) adicionaram membros entre 4.0 e 4.5, de modo que tais objetos desses tipos não podem ser desserializados com o .NET 4.0 se tiverem sido serializados com o .NET 4.5. Observe que se os dados serializados forem serializados e desserializados com a mesma versão do .NET Framework, nenhum problema ocorrerá.|
|Sugestão|A serialização <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=name> deve ser substituída pela serialização <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> ou <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> para resistir às alterações do .NET Framework.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|

