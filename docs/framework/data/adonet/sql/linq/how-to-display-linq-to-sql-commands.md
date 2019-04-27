---
title: 'Como: exibir comandos LINQ to SQL'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1decb05e-37ad-4ed6-ab2f-071eb4c4f628
ms.openlocfilehash: d71eaf834ebf36d462f8581f0074b2f6a90bae17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61903117"
---
# <a name="how-to-display-linq-to-sql-commands"></a><span data-ttu-id="cf53f-102">Como: exibir comandos LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="cf53f-102">How to: Display LINQ to SQL Commands</span></span>
<span data-ttu-id="cf53f-103">Use <xref:System.Data.Linq.DataContext.GetCommand%2A> para exibir comandos SQL e outras informações.</span><span class="sxs-lookup"><span data-stu-id="cf53f-103">Use <xref:System.Data.Linq.DataContext.GetCommand%2A> to display SQL commands and other information.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cf53f-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cf53f-104">Example</span></span>  
 <span data-ttu-id="cf53f-105">No exemplo a seguir, a janela do console exibe a saída de consulta, seguido pelos comandos SQL que são gerados, pelo tipo de comandos, e o tipo de conexão.</span><span class="sxs-lookup"><span data-stu-id="cf53f-105">In the following example, the console window displays the output from the query, followed by the SQL commands that are generated, the type of commands, and the type of connection.</span></span>  
  
 [!code-csharp[DLinqDebuggingSupport#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqDebuggingSupport/cs/Program.cs#3)]
 [!code-vb[DLinqDebuggingSupport#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqDebuggingSupport/vb/Module1.vb#3)]  
  
 <span data-ttu-id="cf53f-106">A saída aparecerá como se segue:</span><span class="sxs-lookup"><span data-stu-id="cf53f-106">Output appears as follows:</span></span>  
  
```  
Customers from London:  
    Thomas Hardy  
    Victoria Ashworth  
    Elizabeth Brown  
    Ann Devon  
    Simon Crowther  
    Marie Bertrand  
    Hari Kumar  
    Dominique Perrier  
```  
  
```  
Command Text:  
SELECT [t0].[CustomerID], [t0].[CompanyName], [t0].[ContactName], [t0].[ContactT  
itle], [t0].[Address], [t0].[City], [t0].[Region], [t0].[PostalCode], [t0].[Coun  
try], [t0].[Phone], [t0].[Fax]  
FROM [dbo].[Customers] AS [t0]  
WHERE [t0].[City] = @p0  
  
Command Type: Text  
  
Connection: System.Data.SqlClient.SqlConnection  
```  
  
## <a name="see-also"></a><span data-ttu-id="cf53f-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf53f-107">See also</span></span>

- [<span data-ttu-id="cf53f-108">Suporte à depuração</span><span class="sxs-lookup"><span data-stu-id="cf53f-108">Debugging Support</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/debugging-support.md)
