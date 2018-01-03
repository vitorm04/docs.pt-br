---
title: Funcionalidade sem suporte
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e480cfb5-697e-42c8-bed5-9264c945c4f9
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 244d9ee7accd3686729542d0f0a15966bcde7b78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
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
