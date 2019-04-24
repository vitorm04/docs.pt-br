---
ms.openlocfilehash: 6ed7438a7f6e7710fcce03c8260a1360143f8d93
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59235044"
---
### <a name="soapformatter-cannot-deserialize-hashtable-and-similar-ordered-collection-objects"></a>SoapFormatter não pode desserializar Hashtable e objetos de coleção ordenados semelhantes

|   |   |
|---|---|
|Detalhes|O <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=name> não garante que objetos serializados em uma versão do .NET Framework serão desserializados com êxito em uma versão diferente. Especificamente, algumas coleções ordenadas (como <xref:System.Collections.Hashtable?displayProperty=name>) tiveram membros adicionados entre a 4.0 e a 4.5, portanto, os objetos desses tipos não poderão ser desserializados com o .NET Framework 4.0 se tiverem sido serializados com o .NET Framework 4.5. Observe que se os dados serializados forem serializados e desserializados com a mesma versão do .NET Framework, nenhum problema ocorrerá.|
|Sugestão|A serialização <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter?displayProperty=name> deve ser substituída pela serialização <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> ou <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> para resistir às alterações do .NET Framework.|
|Escopo|Secundário|
|Versão|4.5|
|Tipo|Tempo de execução|
|APIs afetadas|<ul><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Serialize(System.IO.Stream,System.Object,System.Runtime.Remoting.Messaging.Header[])?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream)?displayProperty=nameWithType></li><li><xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter.Deserialize(System.IO.Stream,System.Runtime.Remoting.Messaging.HeaderHandler)?displayProperty=nameWithType></li></ul>|
