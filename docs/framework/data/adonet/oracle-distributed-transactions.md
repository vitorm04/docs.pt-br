---
title: Transações distribuídas do Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: a21134c3283d3d9d8d7660eecaaf74d60ecf6662
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166515"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="4f20e-102">Transações distribuídas do Oracle</span><span class="sxs-lookup"><span data-stu-id="4f20e-102">Oracle Distributed Transactions</span></span>

<span data-ttu-id="4f20e-103">O <xref:System.Data.OracleClient.OracleConnection> objeto será automaticamente inscrito em uma transação distribuída existente se determinar que uma transação está ativa.</span><span class="sxs-lookup"><span data-stu-id="4f20e-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="4f20e-104">A inscrição de transação automática ocorre quando a conexão é aberta ou recuperada do pool de conexões.</span><span class="sxs-lookup"><span data-stu-id="4f20e-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="4f20e-105">Você pode desabilitar a inscrição automática em transações existentes especificando</span><span class="sxs-lookup"><span data-stu-id="4f20e-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```csharp  
Enlist=false  
```  
  
 <span data-ttu-id="4f20e-106">como um parâmetro de cadeia de conexão para um <xref:System.Data.OracleClient.OracleConnection> .</span><span class="sxs-lookup"><span data-stu-id="4f20e-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f20e-107">Confira também</span><span class="sxs-lookup"><span data-stu-id="4f20e-107">See also</span></span>

- [<span data-ttu-id="4f20e-108">Oracle e ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4f20e-108">Oracle and ADO.NET</span></span>](oracle-and-adonet.md)
- [<span data-ttu-id="4f20e-109">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="4f20e-109">ADO.NET Overview</span></span>](ado-net-overview.md)
