---
title: Geração SQL no provedor exemplo
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: cba1cec6d7ef0fdf8d4d4cf6c8e44fb325cf6447
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43556199"
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="ea763-102">Geração SQL no provedor exemplo</span><span class="sxs-lookup"><span data-stu-id="ea763-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="ea763-103">O [provedor de exemplo do Entity Framework](https://go.microsoft.com/fwlink/?LinkId=180616) demonstra os novos componentes de provedores de dados ADO.NET que dão suporte a [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ea763-103">The [Entity Framework Sample Provider](https://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="ea763-104">Trabalha com um base de dados do SQL Server 2005 e é implementado como um wrapper para o provedor de dados do ADO.NET .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="ea763-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="ea763-105">O módulo de geração SQL do provedor de exemplo (localizado sob a pasta de geração SQL, exceto para o arquivo DmlSqlGenerator.cs) usa uma entrada DbQueryCommandTree e gerencia um único instrução SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="ea763-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ea763-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ea763-106">In This Section</span></span>  
 <span data-ttu-id="ea763-107">Esta seção inclui os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="ea763-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="ea763-108">Arquitetura e design</span><span class="sxs-lookup"><span data-stu-id="ea763-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="ea763-109">Passo a passo: geração de SQL</span><span class="sxs-lookup"><span data-stu-id="ea763-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="ea763-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea763-110">See Also</span></span>  
 [<span data-ttu-id="ea763-111">Geração de SQL</span><span class="sxs-lookup"><span data-stu-id="ea763-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
