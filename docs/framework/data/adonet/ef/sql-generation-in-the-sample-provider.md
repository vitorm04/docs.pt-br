---
title: Geração SQL no provedor exemplo
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: 88223930b65ccec9d030104c62d8b4b2e77ddbe2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079404"
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="a5169-102">Geração SQL no provedor exemplo</span><span class="sxs-lookup"><span data-stu-id="a5169-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="a5169-103">O [provedor de exemplo do Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstra os novos componentes de provedores de dados ADO.NET que dão suporte a [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a5169-103">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="a5169-104">Trabalha com um base de dados do SQL Server 2005 e é implementado como um wrapper para o provedor de dados do ADO.NET .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="a5169-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="a5169-105">O módulo de geração SQL do provedor de exemplo (localizado sob a pasta de geração SQL, exceto para o arquivo DmlSqlGenerator.cs) usa uma entrada DbQueryCommandTree e gerencia um único instrução SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="a5169-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a5169-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="a5169-106">In This Section</span></span>  
 <span data-ttu-id="a5169-107">Esta seção inclui os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="a5169-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="a5169-108">Arquitetura e design</span><span class="sxs-lookup"><span data-stu-id="a5169-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="a5169-109">Passo a passo: Geração SQL</span><span class="sxs-lookup"><span data-stu-id="a5169-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="a5169-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a5169-110">See also</span></span>

- [<span data-ttu-id="a5169-111">Geração SQL</span><span class="sxs-lookup"><span data-stu-id="a5169-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
