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
ms.openlocfilehash: 6dd8ccebd278fdc36c536c49f7f1d4262b2de8c1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
