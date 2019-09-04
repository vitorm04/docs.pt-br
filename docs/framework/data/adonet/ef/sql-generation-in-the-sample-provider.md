---
title: Geração SQL no provedor exemplo
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: d0e058cdc4dd3f7a1a04ab6eea5acf4d3deabb89
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248508"
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="271c8-102">Geração SQL no provedor exemplo</span><span class="sxs-lookup"><span data-stu-id="271c8-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="271c8-103">O [provedor de exemplo Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstra os novos componentes dos provedores de dados do ADO.NET [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]que dão suporte ao.</span><span class="sxs-lookup"><span data-stu-id="271c8-103">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="271c8-104">Trabalha com um base de dados do SQL Server 2005 e é implementado como um wrapper para o provedor de dados do ADO.NET .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="271c8-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="271c8-105">O módulo de geração SQL do provedor de exemplo (localizado sob a pasta de geração SQL, exceto para o arquivo DmlSqlGenerator.cs) usa uma entrada DbQueryCommandTree e gerencia um único instrução SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="271c8-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="271c8-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="271c8-106">In This Section</span></span>  
 <span data-ttu-id="271c8-107">Esta seção inclui os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="271c8-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="271c8-108">Arquitetura e design</span><span class="sxs-lookup"><span data-stu-id="271c8-108">Architecture and Design</span></span>](architecture-and-design.md)  
  
 [<span data-ttu-id="271c8-109">Passo a passo: Geração de SQL</span><span class="sxs-lookup"><span data-stu-id="271c8-109">Walkthrough: SQL Generation</span></span>](walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="271c8-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="271c8-110">See also</span></span>

- [<span data-ttu-id="271c8-111">Geração de SQL</span><span class="sxs-lookup"><span data-stu-id="271c8-111">SQL Generation</span></span>](sql-generation.md)
