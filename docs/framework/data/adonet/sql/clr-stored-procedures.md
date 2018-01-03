---
title: Procedimentos armazenados CLR
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: dfed0124c33c90427c9b888f5aa7bb191aea0400
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="clr-stored-procedures"></a>Procedimentos armazenados CLR
Os procedimentos armazenados são rotinas que não podem ser usadas em expressões escalares. Eles podem retornar resultados tabulares e mensagens para o cliente, chamar a linguagem DDL e as instruções da linguagem DML, e retornar parâmetros de saída.  
  
> [!NOTE]
>  O Microsoft Visual Basic não dá suporte a parâmetros de saída da mesma maneira que o Microsoft Visual C#. Você deve especificar para passar o parâmetro por referência e aplicar o \<out () > atributo para representar um parâmetro de saída, como no exemplo a seguir:  
  
```  
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```  
  
 Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.  
  
 **SQL Server Books Online** (Guias online do SQL Server)  
  
1.  [Procedimentos armazenados CLR](http://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a>Consulte também  
 [Criando objetos do SQL Server 2005 em código gerenciado](http://msdn.microsoft.com/en-us/5358a825-e19b-49aa-8214-674ce5fed1da)  
 [ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)
