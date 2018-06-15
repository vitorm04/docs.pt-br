### <a name="netdatacontractserializer-fails-to-deserialize-a-concurrentdictionary-serialized-with-a-different-net-version"></a>NetDataContractSerializer falha ao desserializar um ConcurrentDictionary serializado com uma versão diferente do .NET

|   |   |
|---|---|
|Detalhes|Por design, o <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> poderá ser usado somente se as extremidades de serialização e desserialização compartilharem os mesmos tipos CLR. Portanto, não há garantia de que um objeto serializado com uma versão do .NET Framework poderá ser desserializado com uma versão diferente.<xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> é um tipo que não será desserializado corretamente se for serializado com o .NET Framework 4.5 ou anterior e for desserializado com o .NET Framework 4.5.1 ou posterior.|
|Sugestão|Há uma série de possíveis soluções alternativas para esse problema:<ul><li>Atualizar o computador de serialização para usar o .NET Framework 4.5.1 também.</li><li>Usar <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> em vez de <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name>, pois ele não espera os mesmos tipos CLR nas extremidades de serialização e desserialização.</li><li>Usar <xref:System.Collections.Generic.Dictionary%602?displayProperty=name> em vez de <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name>, uma vez que ele não apresenta essa quebra específica entre 4.5 e &gt;4.5.1.</li></ul>|
|Escopo|Secundário|
|Versão|4.5.1|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li></ul>|

