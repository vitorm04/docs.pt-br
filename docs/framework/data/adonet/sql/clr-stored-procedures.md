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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 2259574ef96c17dae4c24be549e28dcb03aaa283
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="5c6a3-102">Procedimentos armazenados CLR</span><span class="sxs-lookup"><span data-stu-id="5c6a3-102">CLR Stored Procedures</span></span>
<span data-ttu-id="5c6a3-103">Os procedimentos armazenados são rotinas que não podem ser usadas em expressões escalares.</span><span class="sxs-lookup"><span data-stu-id="5c6a3-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="5c6a3-104">Eles podem retornar resultados tabulares e mensagens para o cliente, chamar a linguagem DDL e as instruções da linguagem DML, e retornar parâmetros de saída.</span><span class="sxs-lookup"><span data-stu-id="5c6a3-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c6a3-105">O Microsoft Visual Basic não dá suporte a parâmetros de saída da mesma maneira que o Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="5c6a3-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="5c6a3-106">Você deve especificar para passar o parâmetro por referência e aplicar o \<out () > atributo para representar um parâmetro de saída, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="5c6a3-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```  
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```  
  
 <span data-ttu-id="5c6a3-107">Para obter informações detalhadas, consulte a versão dos Manuais Online do SQL Server da versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="5c6a3-107">For more detailed information, see the version of SQL Server Books Online for the version of SQL Server you are using.</span></span>  
  
 <span data-ttu-id="5c6a3-108">**SQL Server Books Online** (Guias online do SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5c6a3-108">**SQL Server Books Online**</span></span>  
  
1.  [<span data-ttu-id="5c6a3-109">Procedimentos armazenados CLR</span><span class="sxs-lookup"><span data-stu-id="5c6a3-109">CLR Stored Procedures</span></span>](http://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a><span data-ttu-id="5c6a3-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5c6a3-110">See Also</span></span>  
 [<span data-ttu-id="5c6a3-111">Criando objetos do SQL Server 2005 em código gerenciado</span><span class="sxs-lookup"><span data-stu-id="5c6a3-111">Creating SQL Server 2005 Objects In Managed Code</span></span>](http://msdn.microsoft.com/library/5358a825-e19b-49aa-8214-674ce5fed1da)  
 <span data-ttu-id="5c6a3-112">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="5c6a3-112">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
