---
title: Procedimentos armazenados CLR
ms.date: 03/30/2017
ms.assetid: fd7eea9b-218a-4988-8c9a-8abcc6031c66
ms.openlocfilehash: c02efa3f0a91d176b626761335bd2d5a2b96b966
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917952"
---
# <a name="clr-stored-procedures"></a><span data-ttu-id="151a1-102">Procedimentos armazenados CLR</span><span class="sxs-lookup"><span data-stu-id="151a1-102">CLR Stored Procedures</span></span>
<span data-ttu-id="151a1-103">Os procedimentos armazenados são rotinas que não podem ser usadas em expressões escalares.</span><span class="sxs-lookup"><span data-stu-id="151a1-103">Stored procedures are routines that cannot be used in scalar expressions.</span></span> <span data-ttu-id="151a1-104">Eles podem retornar resultados tabulares e mensagens para o cliente, chamar a linguagem DDL e as instruções da linguagem DML, e retornar parâmetros de saída.</span><span class="sxs-lookup"><span data-stu-id="151a1-104">They can return tabular results and messages to the client, invoke data definition language (DDL) and data manipulation language (DML) statements, and return output parameters.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="151a1-105">O Microsoft Visual Basic não dá suporte a parâmetros de saída da mesma maneira que o Microsoft Visual C#.</span><span class="sxs-lookup"><span data-stu-id="151a1-105">Microsoft Visual Basic does not support output parameters in the same way that Microsoft Visual C# does.</span></span> <span data-ttu-id="151a1-106">Você deve especificar para passar o parâmetro por referência e aplicar o \<atributo out () > para representar um parâmetro de saída, como no seguinte:</span><span class="sxs-lookup"><span data-stu-id="151a1-106">You must specify to pass the parameter by reference and apply the \<Out()> attribute to represent an output parameter, as in the following:</span></span>  
  
```vb
Public Shared Sub ExecuteToClient( <Out()> ByRef number As Integer)  
```
  
<span data-ttu-id="151a1-107">Para obter informações mais detalhadas, consulte a versão da [documentação do SQL Server](/sql) para a versão do SQL Server que você está usando.</span><span class="sxs-lookup"><span data-stu-id="151a1-107">For more detailed information, see the version of [SQL Server documentation](/sql) for the version of SQL Server you're using.</span></span>
  
 <span data-ttu-id="151a1-108">**Documentação do SQL Server**</span><span class="sxs-lookup"><span data-stu-id="151a1-108">**SQL Server documentation**</span></span>

1. [<span data-ttu-id="151a1-109">Procedimentos armazenados CLR</span><span class="sxs-lookup"><span data-stu-id="151a1-109">CLR Stored Procedures</span></span>](https://go.microsoft.com/fwlink/?LinkId=115400)  
  
## <a name="see-also"></a><span data-ttu-id="151a1-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="151a1-110">See also</span></span>

- <span data-ttu-id="151a1-111">[Criando objetos SQL Server 2005 no código gerenciado](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="151a1-111">[Creating SQL Server 2005 Objects In Managed Code](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/6s0s2at1(v=vs.90))</span></span>
- <span data-ttu-id="151a1-112">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="151a1-112">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
