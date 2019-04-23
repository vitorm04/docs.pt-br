---
ms.openlocfilehash: 4cc91e7c6054fdb8e96cecf7120df5b9f25de56c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59803200"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a>Os catálogos do MEF implementam IEnumerable e, portanto, não podem mais ser usados para criar um serializador

|   |   |
|---|---|
|Detalhes|A partir do .NET Framework 4.5, os catálogos do MEF implementam IEnumerable e, portanto, não podem mais ser usados para criar um serializador (objeto <xref:System.Xml.Serialization.XmlSerializer?displayProperty=name>). Tentar serializar um catálogo de MEF gera uma exceção.|
|Sugestão|Não é mais possível usar o MEF para criar um serializador|
|Escopo|Principal|
|Versão|4.5|
|Tipo|Tempo de execução|
