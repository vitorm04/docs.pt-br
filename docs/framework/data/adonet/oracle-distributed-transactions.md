---
title: Transações distribuídas do Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 4af1c98818f1929850c5ae78892c64993a93d4d2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771950"
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="e0c8d-102">Transações distribuídas do Oracle</span><span class="sxs-lookup"><span data-stu-id="e0c8d-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="e0c8d-103">O <xref:System.Data.OracleClient.OracleConnection> objeto automaticamente se inscreve em uma transação distribuída existente caso Determine que uma transação está ativa.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="e0c8d-104">Inscrição automática de transação ocorre quando a conexão for aberto ou recuperado do pool de conexão.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="e0c8d-105">Você pode desabilitar a inscrição automática em transações existentes especificando</span><span class="sxs-lookup"><span data-stu-id="e0c8d-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="e0c8d-106">como um parâmetro de cadeia de caracteres de conexão para um <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="e0c8d-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0c8d-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0c8d-107">See also</span></span>

- <span data-ttu-id="e0c8d-108">[Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md) (Oracle e ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="e0c8d-108">[Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)</span></span>
- <span data-ttu-id="e0c8d-109">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="e0c8d-109">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
