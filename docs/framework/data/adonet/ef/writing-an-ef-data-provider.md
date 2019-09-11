---
title: Escrevendo um provedor de dados do Entity Framework
ms.date: 03/30/2017
ms.assetid: 092e88c4-a301-453a-b5c3-5740c6575a9f
ms.openlocfilehash: 29aa8cb1c6b31d9ada6b01860d76bcf03d37416c
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854167"
---
# <a name="writing-an-entity-framework-data-provider"></a><span data-ttu-id="cb24e-102">Escrevendo um provedor de dados do Entity Framework</span><span class="sxs-lookup"><span data-stu-id="cb24e-102">Writing an Entity Framework Data Provider</span></span>
<span data-ttu-id="cb24e-103">Esta seção discute como gravar um provedor de Entity Framework para dar suporte a uma fonte de dados diferente de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cb24e-103">This section discusses how to write an Entity Framework provider to support a data source other than SQL Server.</span></span> <span data-ttu-id="cb24e-104">O Entity Framework inclui um provedor que oferece suporte a SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cb24e-104">The Entity Framework includes a provider that supports SQL Server.</span></span>  
  
## <a name="introducing-the-entity-framework-provider-model"></a><span data-ttu-id="cb24e-105">Introdução ao modelo de provedor de Entity Framework</span><span class="sxs-lookup"><span data-stu-id="cb24e-105">Introducing the Entity Framework Provider Model</span></span>  
 <span data-ttu-id="cb24e-106">O Entity Framework é independente de banco de dados e você pode escrever um provedor usando o modelo de provedor ADO.NET para se conectar a um conjunto diversificado de fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="cb24e-106">The Entity Framework is database independent, and you can write a provider by using the ADO.NET Provider Model to connect to a diverse set of data sources.</span></span>  
  
 <span data-ttu-id="cb24e-107">O provedor de dados do Entity Framework (compilado usando o modelo do provedor de dados do ADO.NET) executa as seguintes funções:</span><span class="sxs-lookup"><span data-stu-id="cb24e-107">The Entity Framework data provider (built using the ADO.NET Data Provider model) performs the following functions:</span></span>  
  
- <span data-ttu-id="cb24e-108">Mapeia tipos primitivos de EDM (Modelo de Dados de Entidade) para os tipos de provedor.</span><span class="sxs-lookup"><span data-stu-id="cb24e-108">Maps Entity Data Model (EDM) primitive types to provider types.</span></span>  
  
- <span data-ttu-id="cb24e-109">Expõe funções específicas do provedor.</span><span class="sxs-lookup"><span data-stu-id="cb24e-109">Exposes provider-specific functions.</span></span>  
  
- <span data-ttu-id="cb24e-110">Gera comandos específicos do provedor para um determinado DbQueryCommandTree para dar suporte a consultas Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="cb24e-110">Generates provider-specific commands for a given DbQueryCommandTree to support Entity Framework queries.</span></span>  
  
- <span data-ttu-id="cb24e-111">Gera comandos de atualização específicos do provedor para um determinado DbModificationCommandTree para dar suporte a atualizações por meio do Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="cb24e-111">Generates provider-specific update commands for a given DbModificationCommandTree to support updates through the Entity Framework.</span></span>  
  
- <span data-ttu-id="cb24e-112">Expõe arquivos de mapeamento para a definição do esquema de armazenamento, para dar suporte à geração de um modelo baseado em um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="cb24e-112">Exposes mapping files for the store schema definition, to support generation of a model based on a database.</span></span>  
  
- <span data-ttu-id="cb24e-113">Expõe metadados (tabelas e exibições, por exemplo) por meio de um modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="cb24e-113">Exposes metadata (tables and views, for example) via a conceptual model.</span></span>  
  
 <span data-ttu-id="cb24e-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span><span class="sxs-lookup"><span data-stu-id="cb24e-114">![b42a7a5c&#45;0ac0&#45;4911&#45;86be&#45;0460a78760ba](./media/b42a7a5c-0ac0-4911-86be-0460a78760ba.gif "b42a7a5c-0ac0-4911-86be-0460a78760ba")</span></span>  
  
## <a name="sample"></a><span data-ttu-id="cb24e-115">Amostra</span><span class="sxs-lookup"><span data-stu-id="cb24e-115">Sample</span></span>  
 <span data-ttu-id="cb24e-116">Consulte o [provedor de exemplo Entity Framework](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) para obter um exemplo de um provedor de Entity Framework que dá suporte a uma fonte de dados diferente de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="cb24e-116">See the [Entity Framework Sample Provider](https://code.msdn.microsoft.com/windowsdesktop/Entity-Framework-Sample-6a9801d0) for a sample of an Entity Framework provider that supports a data source other than SQL Server.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cb24e-117">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="cb24e-117">In This Section</span></span>  
 [<span data-ttu-id="cb24e-118">Geração de SQL</span><span class="sxs-lookup"><span data-stu-id="cb24e-118">SQL Generation</span></span>](sql-generation.md)  
  
 [<span data-ttu-id="cb24e-119">Geração de SQL de modificação</span><span class="sxs-lookup"><span data-stu-id="cb24e-119">Modification SQL Generation</span></span>](modification-sql-generation.md)  
  
 [<span data-ttu-id="cb24e-120">Especificação do manifesto do provedor</span><span class="sxs-lookup"><span data-stu-id="cb24e-120">Provider Manifest Specification</span></span>](provider-manifest-specification.md)  
  
## <a name="see-also"></a><span data-ttu-id="cb24e-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb24e-121">See also</span></span>

- [<span data-ttu-id="cb24e-122">Trabalhando com Provedores de Dados</span><span class="sxs-lookup"><span data-stu-id="cb24e-122">Working with Data Providers</span></span>](working-with-data-providers.md)
