---
title: Transações distribuídas do Oracle
ms.date: 03/30/2017
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
ms.openlocfilehash: 0e9dcb30eb1962071d7154d4bbf929871c8a12d2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="55402-102">Transações distribuídas do Oracle</span><span class="sxs-lookup"><span data-stu-id="55402-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="55402-103">O <xref:System.Data.OracleClient.OracleConnection> objeto inscreve automaticamente em uma transação distribuída existente se ela determina se uma transação está ativa.</span><span class="sxs-lookup"><span data-stu-id="55402-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="55402-104">Inscrição de transação automática ocorre quando a conexão está aberta ou recuperado do pool de conexão.</span><span class="sxs-lookup"><span data-stu-id="55402-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="55402-105">Você pode desabilitar a inscrição automática em transações, especificando</span><span class="sxs-lookup"><span data-stu-id="55402-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="55402-106">como um parâmetro de cadeia de caracteres de conexão para um <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="55402-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55402-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55402-107">See Also</span></span>  
 <span data-ttu-id="55402-108">[Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md) (Oracle e ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="55402-108">[Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)</span></span>  
 <span data-ttu-id="55402-109">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="55402-109">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
