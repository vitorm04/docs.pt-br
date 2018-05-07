---
title: Funcionalidade sem suporte
ms.date: 03/30/2017
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
ms.openlocfilehash: c4ed52a43fe9cf04c8015aad9247e9f2eb2481e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="unsupported-functionality"></a>Funcionalidade sem suporte
Em LINQ to SQL, a seguinte funcionalidade do SQL não pode ser expostas pela conversão do Common Language Runtime existente (CLR) e construtores do.NET Framework:  
  
-   `STDDEV`  
  
-   `LIKE`  
  
     Embora `LIKE` não é com a conversão direta, a funcionalidade semelhante existido na classe de <xref:System.Data.Linq.SqlClient.SqlMethods> . Para obter mais informações, consulte <xref:System.Data.Linq.SqlClient.SqlMethods.Like%2A?displayProperty=nameWithType>.  
  
-   `DATEDIFF`  
  
     LINQ to SQL limitou suporte para `DATEDIFF`. Funcionalidade semelhante existe na classe de <xref:System.Data.Linq.SqlClient.SqlMethods> .  
  
-   `ROUND`  
  
     LINQ to SQL limitou suporte para `ROUND`. Para obter mais informações, consulte [métodos de System. Math](system-math-methods.md).  
  
## <a name="see-also"></a>Consulte também  
 [Funções e tipos de dados](data-types-and-functions.md)
