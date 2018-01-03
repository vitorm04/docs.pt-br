---
title: "Transações distribuídas do Oracle"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c340ca81-ef79-402f-b204-c5156b890fe5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 104befd25d30d050fee0a053a413b13fe6d1fc51
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="oracle-distributed-transactions"></a><span data-ttu-id="d87fe-102">Transações distribuídas do Oracle</span><span class="sxs-lookup"><span data-stu-id="d87fe-102">Oracle Distributed Transactions</span></span>
<span data-ttu-id="d87fe-103">O <xref:System.Data.OracleClient.OracleConnection> objeto inscreve automaticamente em uma transação distribuída existente se ela determina se uma transação está ativa.</span><span class="sxs-lookup"><span data-stu-id="d87fe-103">The <xref:System.Data.OracleClient.OracleConnection> object automatically enlists in an existing distributed transaction if it determines that a transaction is active.</span></span> <span data-ttu-id="d87fe-104">Inscrição de transação automática ocorre quando a conexão está aberta ou recuperado do pool de conexão.</span><span class="sxs-lookup"><span data-stu-id="d87fe-104">Automatic transaction enlistment occurs when the connection is opened or retrieved from the connection pool.</span></span> <span data-ttu-id="d87fe-105">Você pode desabilitar a inscrição automática em transações, especificando</span><span class="sxs-lookup"><span data-stu-id="d87fe-105">You can disable auto-enlistment in existing transactions by specifying</span></span>  
  
```  
Enlist=false  
```  
  
 <span data-ttu-id="d87fe-106">como um parâmetro de cadeia de caracteres de conexão para um <xref:System.Data.OracleClient.OracleConnection>.</span><span class="sxs-lookup"><span data-stu-id="d87fe-106">as a connection string parameter for an <xref:System.Data.OracleClient.OracleConnection>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d87fe-107">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d87fe-107">See Also</span></span>  
 <span data-ttu-id="d87fe-108">[Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md) (Oracle e ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="d87fe-108">[Oracle and ADO.NET](../../../../docs/framework/data/adonet/oracle-and-adonet.md)</span></span>  
 <span data-ttu-id="d87fe-109">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="d87fe-109">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
