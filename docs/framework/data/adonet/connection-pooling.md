---
title: Pool de conexões
ms.date: 03/30/2017
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
ms.openlocfilehash: cba3311a15c8bc1c657b7a19e475047cafe9110f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627272"
---
# <a name="connection-pooling"></a><span data-ttu-id="1ea8f-102">Pool de conexões</span><span class="sxs-lookup"><span data-stu-id="1ea8f-102">Connection Pooling</span></span>
<span data-ttu-id="1ea8f-103">A conexão a uma fonte de dados pode ser um processo demorado.</span><span class="sxs-lookup"><span data-stu-id="1ea8f-103">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="1ea8f-104">Para minimizar o custo de abrir conexões, o ADO.NET usa uma técnica de otimização chamada *pooling de conexão*, que minimiza o custo de abrir e fechar conexões repetidamente.</span><span class="sxs-lookup"><span data-stu-id="1ea8f-104">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="1ea8f-105">O pool de conexões é manipulado de forma distinta para os provedores de dados .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1ea8f-105">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1ea8f-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="1ea8f-106">In This Section</span></span>  
 [<span data-ttu-id="1ea8f-107">Conexão do SQL Server (ADO.NET) do pool</span><span class="sxs-lookup"><span data-stu-id="1ea8f-107">SQL Server Connection Pooling (ADO.NET)</span></span>](../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)  
 <span data-ttu-id="1ea8f-108">Fornece uma visão geral de pooling de conexão e descreve como funciona o pooling de conexão no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="1ea8f-108">Provides an overview of connection pooling and describes how connection pooling works in SQL Server.</span></span>  
  
 [<span data-ttu-id="1ea8f-109">Conexão do Oracle, ODBC e OLE DB Pooling</span><span class="sxs-lookup"><span data-stu-id="1ea8f-109">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](../../../../docs/framework/data/adonet/ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="1ea8f-110">Descreve o pool de conexões para o Provedor de Dados .NET Framework para OLE DB, o Provedor de Dados .NET Framework para ODBC e o Provedor de Dados .NET Framework para Oracle.</span><span class="sxs-lookup"><span data-stu-id="1ea8f-110">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ea8f-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1ea8f-111">See also</span></span>
- <span data-ttu-id="1ea8f-112">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="1ea8f-112">[Retrieving and Modifying Data in ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)</span></span>
- <span data-ttu-id="1ea8f-113">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917) (Central de desenvolvedores do DataSet e de provedores gerenciados do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="1ea8f-113">[ADO.NET Managed Providers and DataSet Developer Center](https://go.microsoft.com/fwlink/?LinkId=217917)</span></span>
