---
title: Convertendo tipos .NET em cadeias de caracteres
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: ca35af17a402dc901c02edf94099af1377e1160f
ms.sourcegitcommit: 279fb6e8d515df51676528a7424a1df2f0917116
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92687631"
---
# <a name="convert-net-types-to-strings"></a>Converter tipos .NET em cadeias de caracteres

Se você quiser converter um tipo .NET em uma cadeia de caracteres, use o método **ToString** . O método **ToString** retorna uma representação de cadeia de caracteres do tipo passado. A tabela a seguir lista os tipos .NET que retornam uma cadeia de caracteres em um formato que mapeia para as especificações XSD (esquema XML).  
  
|Tipo .NET|Tipo cadeia de caracteres retornado|  
|-------------------------|--------------------------|  
|Booliano|"true", "false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|Datetime|O formato é yyyy-MM-ddTHH:mm:sszzzzzz e seus subconjuntos.|  
|Timespan|O formato é PnYnMnTnHnMnS, por exemplo, `P2Y10M15DT10H30M20S` é uma duração de 2 anos, meses 10, 15 dias, 10hours, 30 minutos e 20 segundos.|  
  
## <a name="see-also"></a>Veja também

- [Conversão de tipos de dados XML](conversion-of-xml-data-types.md)
- [Convertendo cadeias de caracteres em tipos de dados .NET](converting-strings-to-dotnet-data-types.md)
