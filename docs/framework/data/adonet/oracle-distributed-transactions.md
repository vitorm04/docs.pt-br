---
title: Transações distribuídas do Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 6f910f1dbbe448352c0edd5d1b80df659ac453d4
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795153"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="e693f-102">Transações distribuídas do Oracle</span><span class="sxs-lookup"><span data-stu-id="e693f-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="e693f-103">O <xref:System.Data.OracleClient.OracleConnection> objeto será automaticamente inscrito em uma transação distribuída existente se determinar que uma transação está ativa.</span><span class="sxs-lookup"><span data-stu-id="e693f-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="e693f-104">A inscrição de transação automática ocorre quando a conexão é aberta ou recuperada do pool de conexões.</span><span class="sxs-lookup"><span data-stu-id="e693f-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="e693f-105">Você pode desabilitar a inscrição automática em transações existentes especificando</span><span class="sxs-lookup"><span data-stu-id="e693f-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="e693f-106">como um parâmetro de cadeia de conexão <xref:System.Data.OracleClient.OracleConnection>para um.</span><span class="sxs-lookup"><span data-stu-id="e693f-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e693f-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e693f-107">See also</span></span>

- <span data-ttu-id="e693f-108">[Oracle and ADO.NET](oracle-and-adonet.md) (Oracle e ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="e693f-108">[Oracle and ADO.NET](oracle-and-adonet.md)</span></span>
- <span data-ttu-id="e693f-109">[ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="e693f-109">[ADO.NET Overview](ado-net-overview.md)</span></span>
