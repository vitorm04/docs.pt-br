---
title: Escrevendo um provedor de dados do Entity Framework
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 50c0555d84c5b5f180c8c49a8419e8a414a4befe
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43863395"
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="4122a-102">Escrevendo um provedor de dados do Entity Framework</span><span class="sxs-lookup"><span data-stu-id="4122a-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="4122a-103">Esta seção discute como escrever um [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provedor para dar suporte a uma fonte de dados diferente do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4122a-103">This section discusses how to write an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider to support a data source other than SQL Server.</span></span> <span data-ttu-id="4122a-104">O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] inclui um provedor que dá suporte ao SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4122a-104">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] includes a provider that supports SQL Server.</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="4122a-105">Introdução ao modelo de provedor de Entity Framework</span><span class="sxs-lookup"><span data-stu-id="4122a-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="4122a-106">O [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] é independente de banco de dados e você pode escrever um provedor usando o modelo do provedor do ADO.NET para se conectar a um conjunto de várias fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="4122a-106">The [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="4122a-107">O provedor de dados do Entity Framework (compilado usando o modelo do provedor de dados do ADO.NET) executa as seguintes funções:</span><span class="sxs-lookup"><span data-stu-id="4122a-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
-   <span data-ttu-id="4122a-108">Mapeia tipos primitivos de EDM (Modelo de Dados de Entidade) para os tipos de provedor.</span><span class="sxs-lookup"><span data-stu-id="4122a-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
-   <span data-ttu-id="4122a-109">Expõe funções específicas do provedor.</span><span class="sxs-lookup"><span data-stu-id="4122a-109">Exposes provider-specific functions.</span></span>  
  
-   <span data-ttu-id="4122a-110">Gera comandos específicos de provedor para um determinado DbQueryCommandTree para dar suporte a consultas do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4122a-110">Generates provider-specific commands for a given DbQueryCommandTree to support [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] queries.</span></span>  
  
-   <span data-ttu-id="4122a-111">Gera comandos de atualização específicos do provedor para um determinado DbModificationCommandTree para dar suporte a atualizações por meio do [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4122a-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].</span></span>  
  
-   <span data-ttu-id="4122a-112">Expõe arquivos de mapeamento para a definição do esquema de armazenamento, para dar suporte à geração de um modelo baseado em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="4122a-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
-   <span data-ttu-id="4122a-113">Expõe metadados (tabelas e exibições, por exemplo) por meio de um modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="4122a-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="4122a-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="4122a-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](../../../../../docs/framework/data/adonet/ef/media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="4122a-115">Amostra</span><span class="sxs-lookup"><span data-stu-id="4122a-115">Sample</span></span>  
 <span data-ttu-id="4122a-116">Consulte a [provedor de exemplo do Entity Framework](https://go.microsoft.com/fwlink/?LinkId=180616) para obter um exemplo de um [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provedor que dá suporte a uma fonte de dados diferente do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="4122a-116">See the [Entity Framework Sample Provider](https://go.microsoft.com/fwlink/?LinkId=180616) for a sample of an [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)] provider that supports a data source other than SQL Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4122a-117">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="4122a-117">In This Section</span></span>  
 [<span data-ttu-id="4122a-118">Geração de SQL</span><span class="sxs-lookup"><span data-stu-id="4122a-118">SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/sql-generation.md)  
  
 [<span data-ttu-id="4122a-119">Geração de SQL de modificação</span><span class="sxs-lookup"><span data-stu-id="4122a-119">Modification SQL Generation</span></span>](../../../../../docs/framework/data/adonet/ef/modification-sql-generation.md)  
  
 [<span data-ttu-id="4122a-120">Especificação do manifesto do provedor</span><span class="sxs-lookup"><span data-stu-id="4122a-120">Provider Manifest Specification</span></span>](../../../../../docs/framework/data/adonet/ef/provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="4122a-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4122a-121">See Also</span></span>  
 [<span data-ttu-id="4122a-122">Trabalhando com Provedores de Dados</span><span class="sxs-lookup"><span data-stu-id="4122a-122">Working with Data Providers</span></span>](../../../../../docs/framework/data/adonet/ef/working-with-data-providers.md)
