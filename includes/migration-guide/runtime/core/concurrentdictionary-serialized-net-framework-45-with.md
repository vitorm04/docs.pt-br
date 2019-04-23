---
ms.openlocfilehash: f9d7b8d22818245b96cafffe3732bdfe82ff69d8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803183"
---
### <a name="a-concurrentdictionary-serialized-in-net-framework-45-with-netdatacontractserializer-cannot-be-deserialized-by-net-framework-451-or-452"></a>Um ConcurrentDictionary serializado no .NET Framework 4.5 com NetDataContractSerializer não pode ser desserializado pelo .NET Framework 4.5.1 ou 4.5.2

|   |   |
|---|---|
|Detalhes|Devido a alterações internas no tipo, objetos <xref:System.Collections.Concurrent.ConcurrentDictionary%602> serializados com o .NET Framework 4.5 usando o <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name> não podem ser desserializados no .NET Framework 4.5.1 ou no .NET Framework 4.5.2. Observe que mover-se no outro sentido (serializar com o .NET Framework 4.5.x e desserializar com o .NET Framework 4.5) funciona. Da mesma forma, todas as serializações entre versões 4. x funcionam com o .NET Framework 4.6. A possibilidade de serializar e desserializar com uma única versão do .NET Framework não é afetada.|
|Sugestão|Se for necessário serializar e desserializar um <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=name> entre o .NET Framework 4.5 e o .NET Framework 4.5.1/4.5.2, um serializador alternativo como o serializador <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=name> ou <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=name> deve ser usado em vez do <xref:System.Runtime.Serialization.NetDataContractSerializer?displayProperty=name>. Como alternativa, uma vez que esse problema é resolvido no .NET Framework 4.6, isso pode ser solucionado com a atualização para essa versão do .NET Framework.|
|Escopo|Secundário|
|Versão|4.5.1|
|Tipo|Tempo de execução|
