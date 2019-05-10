---
title: Funcionalidade sem suporte
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: fb030a5f212be71d99b66f101e5e8411fbe4de33
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64618137"
---
# <a name="unsupported-functionality"></a>Funcionalidade sem suporte
Em LINQ to SQL, a seguinte funcionalidade do SQL não pode ser expostas pela conversão do Common Language Runtime existente (CLR) e construtores do.NET Framework:  
  
- `STDDEV`  
  
- `LIKE`  
  
     Embora `LIKE` não é com a conversão direta, a funcionalidade semelhante existido na classe de <xref:System.Data.Linq.SqlClient.SqlMethods> . Para obter mais informações, consulte <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.  
  
- `DATEDIFF`  
  
     LINQ to SQL limitou suporte para `DATEDIFF`. Funcionalidade semelhante existe na classe de <xref:System.Data.Linq.SqlClient.SqlMethods> .  
  
- `ROUND`  
  
     LINQ to SQL limitou suporte para `ROUND`. Para obter mais informações, consulte [métodos de System. Math](system-math-methods.md).  
  
## <a name="see-also"></a>Consulte também

- [Funções e tipos de dados](data-types-and-functions.md)
