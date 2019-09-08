---
title: Pool de conexões
ms.date: 03/30/2017
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
ms.openlocfilehash: c431011cf57fd9ef79c2f0a099ab1080116c571f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786713"
---
# <a name="connection-pooling"></a><span data-ttu-id="0df60-102">Pool de conexões</span><span class="sxs-lookup"><span data-stu-id="0df60-102">Connection Pooling</span></span>
<span data-ttu-id="0df60-103">A conexão a uma fonte de dados pode ser um processo demorado.</span><span class="sxs-lookup"><span data-stu-id="0df60-103">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="0df60-104">Para minimizar o custo de abertura de conexões, o ADO.NET usa uma técnica de otimização chamada *pool de conexões*, que minimiza o custo de abertura e fechamento repetidas de conexões.</span><span class="sxs-lookup"><span data-stu-id="0df60-104">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="0df60-105">O pool de conexões é manipulado de forma distinta para os provedores de dados .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0df60-105">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0df60-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="0df60-106">In This Section</span></span>  
 [<span data-ttu-id="0df60-107">Conexão do SQL Server (ADO.NET) do pool</span><span class="sxs-lookup"><span data-stu-id="0df60-107">SQL Server Connection Pooling (ADO.NET)</span></span>](sql-server-connection-pooling.md)  
 <span data-ttu-id="0df60-108">Fornece uma visão geral do pool de conexões e descreve como o pool de conexões funciona no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0df60-108">Provides an overview of connection pooling and describes how connection pooling works in SQL Server.</span></span>  
  
 [<span data-ttu-id="0df60-109">Conexão do Oracle, ODBC e OLE DB Pooling</span><span class="sxs-lookup"><span data-stu-id="0df60-109">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="0df60-110">Descreve o pool de conexões para o Provedor de Dados .NET Framework para OLE DB, o Provedor de Dados .NET Framework para ODBC e o Provedor de Dados .NET Framework para Oracle.</span><span class="sxs-lookup"><span data-stu-id="0df60-110">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0df60-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0df60-111">See also</span></span>

- <span data-ttu-id="0df60-112">[Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="0df60-112">[Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md)</span></span>
- <span data-ttu-id="0df60-113">[ADO.NET Overview](ado-net-overview.md) (Visão geral do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="0df60-113">[ADO.NET Overview](ado-net-overview.md)</span></span>
