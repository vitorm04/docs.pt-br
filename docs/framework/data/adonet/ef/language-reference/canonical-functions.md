---
title: Funções canônicas
ms.date: 03/30/2017
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
ms.openlocfilehash: 11e22d527c4266f45ea5d26f2ec95926ebe46332
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185230"
---
# <a name="canonical-functions"></a><span data-ttu-id="e56eb-102">Funções canônicas</span><span class="sxs-lookup"><span data-stu-id="e56eb-102">Canonical Functions</span></span>

<span data-ttu-id="e56eb-103">Essa seção discute as funções canônicas que têm suporte por todos os provedores de dados e podem ser usadas por todas as tecnologias de consulta.</span><span class="sxs-lookup"><span data-stu-id="e56eb-103">This section discusses canonical functions that are supported by all data providers, and can be used by all querying technologies.</span></span> <span data-ttu-id="e56eb-104">As funções canônicas não podem ser estendidas por um provedor.</span><span class="sxs-lookup"><span data-stu-id="e56eb-104">Canonical functions cannot be extended by a provider.</span></span>  
  
 <span data-ttu-id="e56eb-105">Essas funções canônicas serão convertidas à funcionalidade da fonte de dados correspondente para o provedor.</span><span class="sxs-lookup"><span data-stu-id="e56eb-105">These canonical functions will be translated to the corresponding data source functionality for the provider.</span></span> <span data-ttu-id="e56eb-106">Isso permite as invocações da função expressas em um formulário comum nas fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="e56eb-106">This allows for function invocations expressed in a common form across data sources.</span></span>  
  
 <span data-ttu-id="e56eb-107">Como essas funções canônicas são independentes das fontes de dados, o argumento e os tipos de retorno de funções canônicas são definidos em termos de tipos no modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="e56eb-107">Because these canonical functions are independent of data sources, argument and return types of canonical functions are defined in terms of types in the conceptual model.</span></span> <span data-ttu-id="e56eb-108">Porém, algumas fontes de dados podem não dar suporte a todos os tipos no modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="e56eb-108">However, some data sources might not support all types in the conceptual model.</span></span>  
  
 <span data-ttu-id="e56eb-109">Quando as funções canônicas são usadas em uma consulta do [!INCLUDE[esql](../../../../../../includes/esql-md.md)], a função apropriada será chamada na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="e56eb-109">When canonical functions are used in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query, the appropriate function will be called at the data source.</span></span>  
  
 <span data-ttu-id="e56eb-110">Todas as funções canônicas têm as condições de erro e o comportamento de entrada nulo especificadas explicitamente.</span><span class="sxs-lookup"><span data-stu-id="e56eb-110">All canonical functions have both null-input behavior and error conditions explicitly specified.</span></span> <span data-ttu-id="e56eb-111">Os provedores de repositório devem estar em conformidade com esse comportamento, mas Entity Framework não impõe esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="e56eb-111">Store providers should comply with that behavior, but Entity Framework does not enforce this behavior.</span></span>  
  
 <span data-ttu-id="e56eb-112">Para cenários LINQ, as consultas no Entity Framework envolvem o mapeamento de métodos CLR para métodos na fonte de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="e56eb-112">For LINQ scenarios, queries against the Entity Framework involve mapping CLR methods to methods in the underlying data source.</span></span> <span data-ttu-id="e56eb-113">Os métodos CLR mapeiam para funções canônicas, de modo que um conjunto específico de métodos mapeará corretamente, independentemente da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="e56eb-113">The CLR methods map to canonical functions, so that a specific set of methods will correctly map, regardless of the data source.</span></span>  
  
## <a name="canonical-functions-namespace"></a><span data-ttu-id="e56eb-114">Namespace de funções canônicas</span><span class="sxs-lookup"><span data-stu-id="e56eb-114">Canonical Functions Namespace</span></span>  

 <span data-ttu-id="e56eb-115">O namespace para a função canônica é <xref:System.Data.Metadata.Edm>.</span><span class="sxs-lookup"><span data-stu-id="e56eb-115">The namespace for canonical function is <xref:System.Data.Metadata.Edm>.</span></span> <span data-ttu-id="e56eb-116">O namespace <xref:System.Data.Metadata.Edm> é incluído automaticamente em todas as consultas.</span><span class="sxs-lookup"><span data-stu-id="e56eb-116">The <xref:System.Data.Metadata.Edm> namespace is automatically included in all queries.</span></span> <span data-ttu-id="e56eb-117">No entanto, se outro namespace for importado e contiver uma função com o mesmo nome de uma função canônica (no namespace <xref:System.Data.Metadata.Edm>), você deverá especificar o namespace.</span><span class="sxs-lookup"><span data-stu-id="e56eb-117">However, if another namespace is imported that contains a function with the same name as a canonical function (in the <xref:System.Data.Metadata.Edm> namespace), you must specify the namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e56eb-118">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e56eb-118">In This Section</span></span>  

 [<span data-ttu-id="e56eb-119">Funções agregadas canônicas</span><span class="sxs-lookup"><span data-stu-id="e56eb-119">Aggregate Canonical Functions</span></span>](aggregate-canonical-functions.md)  
 <span data-ttu-id="e56eb-120">Discute funções canônicas de agregação de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e56eb-120">Discusses aggregate [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="e56eb-121">Funções canônicas matemáticas</span><span class="sxs-lookup"><span data-stu-id="e56eb-121">Math Canonical Functions</span></span>](math-canonical-functions.md)  
 <span data-ttu-id="e56eb-122">Discute funções canônicas matemáticas de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e56eb-122">Discusses math [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="e56eb-123">Funções canônicas de cadeias de caracteres</span><span class="sxs-lookup"><span data-stu-id="e56eb-123">String Canonical Functions</span></span>](string-canonical-functions.md)  
 <span data-ttu-id="e56eb-124">Discute funções canônicas de cadeias de caracteres de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e56eb-124">Discusses string [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="e56eb-125">Funções canônicas de data e hora</span><span class="sxs-lookup"><span data-stu-id="e56eb-125">Date and Time Canonical Functions</span></span>](date-and-time-canonical-functions.md)  
 <span data-ttu-id="e56eb-126">Discute funções canônicas de data e hora de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e56eb-126">Discusses date and time [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="e56eb-127">Funções canônicas bit a bit</span><span class="sxs-lookup"><span data-stu-id="e56eb-127">Bitwise Canonical Functions</span></span>](bitwise-canonical-functions.md)  
 <span data-ttu-id="e56eb-128">Discute funções canônicas bit a bit de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e56eb-128">Discusses bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="e56eb-129">Funções espaciais</span><span class="sxs-lookup"><span data-stu-id="e56eb-129">Spatial Functions</span></span>](spatial-functions.md)  
 <span data-ttu-id="e56eb-130">Discute funções canônicas espaciais de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e56eb-130">Discusses Spatial [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="e56eb-131">Outras funções canônicas</span><span class="sxs-lookup"><span data-stu-id="e56eb-131">Other Canonical Functions</span></span>](other-canonical-functions.md)  
 <span data-ttu-id="e56eb-132">Discute as funções não classificadas como bit a bit, data/hora, cadeia de caracteres, matemática ou de agregação.</span><span class="sxs-lookup"><span data-stu-id="e56eb-132">Discusses functions not classified as bitwise, date/time, string, math, or aggregate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e56eb-133">Veja também</span><span class="sxs-lookup"><span data-stu-id="e56eb-133">See also</span></span>

- [<span data-ttu-id="e56eb-134">Visão geral da Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e56eb-134">Entity SQL Overview</span></span>](entity-sql-overview.md)
- [<span data-ttu-id="e56eb-135">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e56eb-135">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="e56eb-136">Modelo conceitual canônico a mapeamento de funções do SQL Server</span><span class="sxs-lookup"><span data-stu-id="e56eb-136">Conceptual Model Canonical to SQL Server Functions Mapping</span></span>](../conceptual-model-canonical-to-sql-server-functions-mapping.md)
- [<span data-ttu-id="e56eb-137">Funções definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="e56eb-137">User-Defined Functions</span></span>](user-defined-functions-entity-sql.md)
