---
title: Pool de conexões
description: Saiba mais sobre o pool de conexões, uma técnica de otimização que o ADO.NET usa para minimizar o custo de abrir conexões com fontes de dados.
ms.date: 03/30/2017
ms.assetid: 955c057f-aea8-4ba8-aa6d-e3dfa18ba8d5
ms.openlocfilehash: b8f89dfda7edbde14dbb5945f10f2284ac43c3d8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287084"
---
# <a name="connection-pooling"></a><span data-ttu-id="d0e66-103">Pool de conexões</span><span class="sxs-lookup"><span data-stu-id="d0e66-103">Connection Pooling</span></span>
<span data-ttu-id="d0e66-104">A conexão a uma fonte de dados pode ser um processo demorado.</span><span class="sxs-lookup"><span data-stu-id="d0e66-104">Connecting to a data source can be time consuming.</span></span> <span data-ttu-id="d0e66-105">Para minimizar o custo de abertura de conexões, o ADO.NET usa uma técnica de otimização chamada *pool de conexões*, que minimiza o custo de abertura e fechamento repetidas de conexões.</span><span class="sxs-lookup"><span data-stu-id="d0e66-105">To minimize the cost of opening connections, ADO.NET uses an optimization technique called *connection pooling*, which minimizes the cost of repeatedly opening and closing connections.</span></span> <span data-ttu-id="d0e66-106">O pool de conexões é manipulado de forma distinta para os provedores de dados .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d0e66-106">Connection pooling is handled differently for the .NET Framework data providers.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d0e66-107">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="d0e66-107">In This Section</span></span>  
 [<span data-ttu-id="d0e66-108">Pool de conexões do SQL Server (ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="d0e66-108">SQL Server Connection Pooling (ADO.NET)</span></span>](sql-server-connection-pooling.md)  
 <span data-ttu-id="d0e66-109">Fornece uma visão geral do pool de conexões e descreve como o pool de conexões funciona no SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d0e66-109">Provides an overview of connection pooling and describes how connection pooling works in SQL Server.</span></span>  
  
 [<span data-ttu-id="d0e66-110">Conexão do Oracle, ODBC e OLE DB Pooling</span><span class="sxs-lookup"><span data-stu-id="d0e66-110">OLE DB, ODBC, and Oracle Connection Pooling</span></span>](ole-db-odbc-and-oracle-connection-pooling.md)  
 <span data-ttu-id="d0e66-111">Descreve o pool de conexões para o Provedor de Dados .NET Framework para OLE DB, o Provedor de Dados .NET Framework para ODBC e o Provedor de Dados .NET Framework para Oracle.</span><span class="sxs-lookup"><span data-stu-id="d0e66-111">Describes connection pooling for the .NET Framework Data Provider for OLE DB, the .NET Framework Data Provider for ODBC, and the .NET Framework Data Provider for Oracle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0e66-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="d0e66-112">See also</span></span>

- <span data-ttu-id="d0e66-113">[Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md) (Recuperando e modificando dados no ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="d0e66-113">[Retrieving and Modifying Data in ADO.NET](retrieving-and-modifying-data.md)</span></span>
- [<span data-ttu-id="d0e66-114">Visão geral do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="d0e66-114">ADO.NET Overview</span></span>](ado-net-overview.md)
