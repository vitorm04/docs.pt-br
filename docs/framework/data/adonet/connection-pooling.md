---
title: "Pool de conexões"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 5082adda3c03bfbc40eafb174513a39fe17a3da8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="connection-pooling"></a><span data-ttu-id="e6d07-102">Pool de conexões</span><span class="sxs-lookup"><span data-stu-id="e6d07-102">Connection Pooling</span></span>
<span data-ttu-id="e6d07-103">A conexão a uma fonte de dados pode ser um processo demorado.</span><span class="sxs-lookup"><span data-stu-id="e6d07-103">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="e6d07-104">Para minimizar o custo de abrir conexões, ADO.NET usa uma técnica de otimização chamada *pooling de conexão*, que minimiza o custo de abertura e fechamento de conexões repetidamente.</span><span class="sxs-lookup"><span data-stu-id="e6d07-104">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="e6d07-105">O pool de conexões é manipulado de forma distinta para os provedores de dados .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e6d07-105">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e6d07-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e6d07-106">In This Section</span></span>  
 [<span data-ttu-id="e6d07-107">Conexão do SQL Server (ADO.NET) do pool</span><span class="sxs-lookup"><span data-stu-id="e6d07-107">SQL Server Connection Pooling (ADO.NET)</span></span>](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)  
 <span data-ttu-id="e6d07-108">Fornece uma visão geral do pool de conexões e descreve como o pool funciona no [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e6d07-108">Provides an overview of connection pooling and describes how connection pooling works in [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="e6d07-109">Conexão do Oracle, ODBC e OLE DB Pooling</span><span class="sxs-lookup"><span data-stu-id="e6d07-109">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="e6d07-110">Descreve o pool de conexões para o Provedor de Dados .NET Framework para OLE DB, o Provedor de Dados .NET Framework para ODBC e o Provedor de Dados .NET Framework para Oracle.</span><span class="sxs-lookup"><span data-stu-id="e6d07-110">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6d07-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6d07-111">See Also</span></span>  
 <span data-ttu-id="e6d07-112">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="e6d07-112">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)</span></span>  
 <span data-ttu-id="e6d07-113">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="e6d07-113">[ADO.NET Managed Providers and DataSet Developer Center](http://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
