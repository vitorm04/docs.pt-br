---
title: Pool de conexões
description: Saiba mais sobre o pool de conexões, uma técnica de otimização que o ADO.NET usa para minimizar o custo de abrir conexões com fontes de dados.
ms.date: 03/30/2017
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
ms.openlocfilehash: f16b3ba733cce4a1efe72e3f4eee48a431a96fb7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198711"
---
# <a name="connection-pooling"></a><span data-ttu-id="7b162-103">Pool de conexões</span><span class="sxs-lookup"><span data-stu-id="7b162-103">Connection Pooling</span></span>

<span data-ttu-id="7b162-104">A conexão a uma fonte de dados pode ser um processo demorado.</span><span class="sxs-lookup"><span data-stu-id="7b162-104">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="7b162-105">Para minimizar o custo de abertura de conexões, o ADO.NET usa uma técnica de otimização chamada *pool de conexões*, que minimiza o custo de abertura e fechamento repetidas de conexões.</span><span class="sxs-lookup"><span data-stu-id="7b162-105">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="7b162-106">O pool de conexões é manipulado de forma distinta para os provedores de dados .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7b162-106">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7b162-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="7b162-107">In This Section</span></span>  

 [<span data-ttu-id="7b162-108">Pool de conexões do SQL Server (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="7b162-108">SQL Server Connection Pooling (ADO.NET)</span></span>](sql-server-connection-pooling.md)  
 <span data-ttu-id="7b162-109">Fornece uma visão geral do pool de conexões e descreve como o pool de conexões funciona no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="7b162-109">Provides an overview of connection pooling and describes how connection pooling works in SQL Server.</span></span>  
  
 [<span data-ttu-id="7b162-110">OLE DB, ODBC e pool de conexões Oracle</span><span class="sxs-lookup"><span data-stu-id="7b162-110">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="7b162-111">Descreve o pool de conexões para o Provedor de Dados .NET Framework para OLE DB, o Provedor de Dados .NET Framework para ODBC e o Provedor de Dados .NET Framework para Oracle.</span><span class="sxs-lookup"><span data-stu-id="7b162-111">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b162-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="7b162-112">See also</span></span>

- [<span data-ttu-id="7b162-113">Recuperando e modificando dados no ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7b162-113">Retrieving and Modifying Data in ADO.NET</span></span>](retrieving-and-modifying-data.md)
- [<span data-ttu-id="7b162-114">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7b162-114">ADO.NET Overview</span></span>](ado-net-overview.md)
