---
title: Procedimentos armazenados CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: 1459ebc9c24875bcd7e8b0d711d710c514df0dd4
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/12/2019
ms.locfileid: "56093860"
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="64348-102">Procedimentos armazenados CLR</span><span class="sxs-lookup"><span data-stu-id="64348-102">CLR Stored Procedures</span></span>
<span data-ttu-id="64348-103">Os procedimentos armazenados são rotinas que não podem ser usadas em expressões escalares.</span><span class="sxs-lookup"><span data-stu-id="64348-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="64348-104">Eles podem retornar resultados tabulares e mensagens para o cliente, chamar a linguagem DDL e as instruções da linguagem DML, e retornar parâmetros de saída.</span><span class="sxs-lookup"><span data-stu-id="64348-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="64348-105">O Microsoft Visual Basic não dá suporte a parâmetros de saída da mesma maneira que o Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="64348-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="64348-106">Você deve especificar para passar o parâmetro por referência e aplicar o \<out () > atributo para representar um parâmetro de saída, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="64348-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
<span data-ttu-id="64348-107">Para obter mais informações, consulte a versão do [documentação do SQL Server](/sql) para a versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="64348-107">For more detailed information, see the version of [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="64348-108">**Documentação do SQL Server**</span><span class="sxs-lookup"><span data-stu-id="64348-108">**SQL Server documentation**</span></span>

1. [<span data-ttu-id="64348-109">Procedimentos armazenados CLR</span><span class="sxs-lookup"><span data-stu-id="64348-109">CLR Stored Procedures</span></span>](https://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a><span data-ttu-id="64348-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64348-110">See also</span></span>
- <span data-ttu-id="64348-111">[Criando objetos do SQL Server 2005 em código gerenciado](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="64348-111">[Creating SQL Server 2005 Objects In Managed Code](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span></span>
- <span data-ttu-id="64348-112">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="64348-112">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
