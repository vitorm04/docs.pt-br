---
title: Transações distribuídas do Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: edd06b94ce4157e90d334ee7feac2a449f7ee74b
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040473"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="d5528-102">Transações distribuídas do Oracle</span><span class="sxs-lookup"><span data-stu-id="d5528-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="d5528-103">O objeto <xref:System.Data.OracleClient.OracleConnection> será automaticamente inscrito em uma transação distribuída existente se determinar que uma transação está ativa.</span><span class="sxs-lookup"><span data-stu-id="d5528-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="d5528-104">A inscrição de transação automática ocorre quando a conexão é aberta ou recuperada do pool de conexões.</span><span class="sxs-lookup"><span data-stu-id="d5528-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="d5528-105">Você pode desabilitar a inscrição automática em transações existentes especificando</span><span class="sxs-lookup"><span data-stu-id="d5528-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```csharp  
Enlist=false  
```  
  
 <span data-ttu-id="d5528-106">como um parâmetro de cadeia de conexão para um <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="d5528-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5528-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d5528-107">See also</span></span>

- <span data-ttu-id="d5528-108">[Oracle and ADO.NET](oracle-and-adonet.md) (Oracle e ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="d5528-108">[Oracle and ADO.NET](oracle-and-adonet.md)</span></span>
- <span data-ttu-id="d5528-109">[ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="d5528-109">[ADO.NET Overview](ado-net-overview.md)</span></span>
