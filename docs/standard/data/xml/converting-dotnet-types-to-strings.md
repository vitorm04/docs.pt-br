---
title: Convertendo tipos do .NET Framework para cadeias de caracteres
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 59e288a756a022763bae2235964a8b25a9d72bd1
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/29/2018
ms.locfileid: "47399642"
---
# <a name="converting-net-framework-types-to-strings"></a>Convertendo tipos do .NET Framework para cadeias de caracteres
Se você deseja converter um tipo do .NET Framework em uma cadeia de caracteres, use o método **ToString**. O método **ToString** retorna uma representação de cadeia de caracteres do tipo passado. A tabela a seguir lista os tipos do.NET Framework que retorna uma cadeia de caracteres em um formato que mapeia a (XSD) de esquema XML as especificações.  
  
|Tipo do .NET Framework|Tipo cadeia de caracteres retornado|  
|-------------------------|--------------------------|  
|Boolean|"true", "false"|  
|Single.PositiveInfinity|"INF"|  
|Single.NegativeInfinity|"-INF"|  
|Double.PositiveInfinity|"INF"|  
|Double.NegativeInfinity|"-INF"|  
|DateTime|O formato é yyyy-MM-ddTHH:mm:sszzzzzz e seus subconjuntos.|  
|Timespan|O formato é PnYnMnTnHnMnS, por exemplo, `P2Y10M15DT10H30M20S` é uma duração de 2 anos, meses 10, 15 dias, 10hours, 30 minutos e 20 segundos.|  
  
## <a name="see-also"></a>Consulte também

- [Conversão de tipos de dados XML](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
- [Convertendo cadeias de caracteres para tipos de dados do .NET Framework](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)
