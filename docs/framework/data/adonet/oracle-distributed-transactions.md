---
title: Transações distribuídas do Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: a3b8a50b42b945a0cdc1cbfbc4cc9eab835e90e4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43505393"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="c7caf-102">Transações distribuídas do Oracle</span><span class="sxs-lookup"><span data-stu-id="c7caf-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="c7caf-103">O <xref:System.Data.OracleClient.OracleConnection> objeto automaticamente se inscreve em uma transação distribuída existente caso Determine que uma transação está ativa.</span><span class="sxs-lookup"><span data-stu-id="c7caf-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="c7caf-104">Inscrição automática de transação ocorre quando a conexão for aberto ou recuperado do pool de conexão.</span><span class="sxs-lookup"><span data-stu-id="c7caf-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="c7caf-105">Você pode desabilitar a inscrição automática em transações existentes especificando</span><span class="sxs-lookup"><span data-stu-id="c7caf-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="c7caf-106">como um parâmetro de cadeia de caracteres de conexão para um <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="c7caf-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7caf-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c7caf-107">See Also</span></span>  
 <span data-ttu-id="c7caf-108">[Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md) (Oracle e ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="c7caf-108">[Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)</span></span>  
 <span data-ttu-id="c7caf-109">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="c7caf-109">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
