---
title: Transações distribuídas do Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 8e7530621254881402570b59b47a22052b40f2b5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54713231"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="1e379-102">Transações distribuídas do Oracle</span><span class="sxs-lookup"><span data-stu-id="1e379-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="1e379-103">O <xref:System.Data.OracleClient.OracleConnection> objeto automaticamente se inscreve em uma transação distribuída existente caso Determine que uma transação está ativa.</span><span class="sxs-lookup"><span data-stu-id="1e379-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="1e379-104">Inscrição automática de transação ocorre quando a conexão for aberto ou recuperado do pool de conexão.</span><span class="sxs-lookup"><span data-stu-id="1e379-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="1e379-105">Você pode desabilitar a inscrição automática em transações existentes especificando</span><span class="sxs-lookup"><span data-stu-id="1e379-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="1e379-106">como um parâmetro de cadeia de caracteres de conexão para um <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="1e379-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e379-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e379-107">See also</span></span>
- <span data-ttu-id="1e379-108">[Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md) (Oracle e ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="1e379-108">[Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)</span></span>
- <span data-ttu-id="1e379-109">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="1e379-109">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
