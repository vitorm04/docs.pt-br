---
title: "Geração SQL no provedor exemplo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 853bf55f96be3adeba11ff14e36fd56631536b69
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="3f33a-102">Geração SQL no provedor exemplo</span><span class="sxs-lookup"><span data-stu-id="3f33a-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="3f33a-103">O [provedor do Entity Framework exemplo](http://go.microsoft.com/fwlink/?LinkId=180616) demonstra os novos componentes ADO.NET de provedores de dados que oferecem suporte a [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f33a-103">The [Entity Framework Sample Provider](http://go.microsoft.com/fwlink/?LinkId=180616) demonstrates the new components of ADO.NET Data Providers that support the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  <span data-ttu-id="3f33a-104">Trabalha com um base de dados do SQL Server 2005 e é implementado como um wrapper para o provedor de dados do ADO.NET .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="3f33a-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="3f33a-105">O módulo de geração SQL do provedor de exemplo (localizado sob a pasta de geração SQL, exceto para o arquivo DmlSqlGenerator.cs) usa uma entrada DbQueryCommandTree e gerencia um único instrução SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="3f33a-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3f33a-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="3f33a-106">In This Section</span></span>  
 <span data-ttu-id="3f33a-107">Esta seção inclui os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="3f33a-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="3f33a-108">Arquitetura e design</span><span class="sxs-lookup"><span data-stu-id="3f33a-108">Architecture and Design</span></span>](../../../../../docs/framework/data/adonet/ef/architecture-and-design.md)  
  
 [<span data-ttu-id="3f33a-109">Passo a passo: geração de SQL</span><span class="sxs-lookup"><span data-stu-id="3f33a-109">Walkthrough: SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="3f33a-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3f33a-110">See Also</span></span>  
 [<span data-ttu-id="3f33a-111">Geração de SQL</span><span class="sxs-lookup"><span data-stu-id="3f33a-111">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)
