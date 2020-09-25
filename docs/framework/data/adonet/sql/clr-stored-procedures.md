---
title: Procedimentos armazenados CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: aa14c96ed226ac80a9613d3e229f35dbf5085f3b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91173608"
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="449a4-102">Procedimentos armazenados CLR</span><span class="sxs-lookup"><span data-stu-id="449a4-102">CLR Stored Procedures</span></span>

<span data-ttu-id="449a4-103">Os procedimentos armazenados são rotinas que não podem ser usadas em expressões escalares.</span><span class="sxs-lookup"><span data-stu-id="449a4-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="449a4-104">Eles podem retornar resultados tabulares e mensagens para o cliente, chamar a linguagem DDL e as instruções da linguagem DML, e retornar parâmetros de saída.</span><span class="sxs-lookup"><span data-stu-id="449a4-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="449a4-105">O Microsoft Visual Basic não dá suporte a parâmetros de saída da mesma maneira que o Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="449a4-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="449a4-106">Você deve especificar para passar o parâmetro por referência e aplicar o \<Out()> atributo para representar um parâmetro de saída, como no seguinte:</span><span class="sxs-lookup"><span data-stu-id="449a4-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
<span data-ttu-id="449a4-107">Para obter informações mais detalhadas, consulte a versão da [documentação do SQL Server](/sql) para a versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="449a4-107">For more detailed information, see the version of [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="449a4-108">**Documentação do SQL Server**</span><span class="sxs-lookup"><span data-stu-id="449a4-108">**SQL Server documentation**</span></span>

1. <span data-ttu-id="449a4-109">[Procedimentos armazenados CLR](/previous-versions/sql/sql-server-2008/ms131094(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="449a4-109">[CLR Stored Procedures](/previous-versions/sql/sql-server-2008/ms131094(v=sql.100))</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="449a4-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="449a4-110">See also</span></span>

- <span data-ttu-id="449a4-111">[Criando objetos SQL Server 2005 no código gerenciado](/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="449a4-111">[Creating SQL Server 2005 Objects In Managed Code](/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span></span>
- [<span data-ttu-id="449a4-112">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="449a4-112">ADO.NET Overview</span></span>](../ado-net-overview.md)
