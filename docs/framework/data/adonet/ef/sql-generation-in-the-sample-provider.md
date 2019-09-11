---
title: Geração SQL no provedor exemplo
ms.date: 03/30/2017
ms.assetid: e70f553d-4622-4627-928e-1aa2ee605d8e
ms.openlocfilehash: a59f1fecf85d63208c3388204c962b5838902ba7
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854322"
---
# <a name="sql-generation-in-the-sample-provider"></a><span data-ttu-id="da6c8-102">Geração SQL no provedor exemplo</span><span class="sxs-lookup"><span data-stu-id="da6c8-102">SQL Generation in the Sample Provider</span></span>
<span data-ttu-id="da6c8-103">O [provedor de exemplo Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstra os novos componentes dos provedores de dados ADO.NET que dão suporte ao Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="da6c8-103">The [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) demonstrates the new components of ADO.NET Data Providers that support the Entity Framework.</span></span>  <span data-ttu-id="da6c8-104">Trabalha com um base de dados do SQL Server 2005 e é implementado como um wrapper para o provedor de dados do ADO.NET .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="da6c8-104">It works with a SQL Server 2005 database and is implemented as a wrapper for the System.Data.SqlClient ADO.NET 2.0 Data Provider.</span></span>  
  
 <span data-ttu-id="da6c8-105">O módulo de geração SQL do provedor de exemplo (localizado sob a pasta de geração SQL, exceto para o arquivo DmlSqlGenerator.cs) usa uma entrada DbQueryCommandTree e gerencia um único instrução SQL SELECT.</span><span class="sxs-lookup"><span data-stu-id="da6c8-105">The SQL Generation module of the Sample Provider (located under the SQL Generation folder, except for the file DmlSqlGenerator.cs) takes an input DbQueryCommandTree and produces a single SQL SELECT statement.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="da6c8-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="da6c8-106">In This Section</span></span>  
 <span data-ttu-id="da6c8-107">Esta seção inclui os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="da6c8-107">This section includes the following topics:</span></span>  
  
 [<span data-ttu-id="da6c8-108">Arquitetura e design</span><span class="sxs-lookup"><span data-stu-id="da6c8-108">Architecture and Design</span></span>](architecture-and-design.md)  
  
 [<span data-ttu-id="da6c8-109">Passo a passo: Geração de SQL</span><span class="sxs-lookup"><span data-stu-id="da6c8-109">Walkthrough: SQL Generation</span></span>](walkthrough-sql-generation.md)  
  
## <a name="see-also"></a><span data-ttu-id="da6c8-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="da6c8-110">See also</span></span>

- [<span data-ttu-id="da6c8-111">Geração de SQL</span><span class="sxs-lookup"><span data-stu-id="da6c8-111">SQL Generation</span></span>](sql-generation.md)
