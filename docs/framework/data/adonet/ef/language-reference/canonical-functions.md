---
title: "Funções canônicas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bbcc9928-36ea-4dff-9e31-96549ffed958
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 1f676c88691f0ba80ca682d720adf649ab612cfb
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="canonical-functions"></a><span data-ttu-id="46cb0-102">Funções canônicas</span><span class="sxs-lookup"><span data-stu-id="46cb0-102">Canonical Functions</span></span>
<span data-ttu-id="46cb0-103">Essa seção discute as funções canônicas que têm suporte por todos os provedores de dados e podem ser usadas por todas as tecnologias de consulta.</span><span class="sxs-lookup"><span data-stu-id="46cb0-103">This section discusses canonical functions that are supported by all data providers, and can be used by all querying technologies.</span></span> <span data-ttu-id="46cb0-104">As funções canônicas não podem ser estendidas por um provedor.</span><span class="sxs-lookup"><span data-stu-id="46cb0-104">Canonical functions cannot be extended by a provider.</span></span>  
  
 <span data-ttu-id="46cb0-105">Essas funções canônicas serão convertidas à funcionalidade da fonte de dados correspondente para o provedor.</span><span class="sxs-lookup"><span data-stu-id="46cb0-105">These canonical functions will be translated to the corresponding data source functionality for the provider.</span></span> <span data-ttu-id="46cb0-106">Isso permite as invocações da função expressas em um formulário comum nas fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="46cb0-106">This allows for function invocations expressed in a common form across data sources.</span></span>  
  
 <span data-ttu-id="46cb0-107">Como essas funções canônicas são independentes das fontes de dados, o argumento e os tipos de retorno de funções canônicas são definidos em termos de tipos no modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="46cb0-107">Because these canonical functions are independent of data sources, argument and return types of canonical functions are defined in terms of types in the conceptual model.</span></span> <span data-ttu-id="46cb0-108">Porém, algumas fontes de dados podem não dar suporte a todos os tipos no modelo conceitual.</span><span class="sxs-lookup"><span data-stu-id="46cb0-108">However, some data sources might not support all types in the conceptual model.</span></span>  
  
 <span data-ttu-id="46cb0-109">Quando as funções canônicas são usadas em uma consulta do [!INCLUDE[esql](../../../../../../includes/esql-md.md)], a função apropriada será chamada na fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="46cb0-109">When canonical functions are used in an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query, the appropriate function will be called at the data source.</span></span>  
  
 <span data-ttu-id="46cb0-110">Todas as funções canônicas têm as condições de erro e o comportamento de entrada nulo especificadas explicitamente.</span><span class="sxs-lookup"><span data-stu-id="46cb0-110">All canonical functions have both null-input behavior and error conditions explicitly specified.</span></span> <span data-ttu-id="46cb0-111">Os provedores de repositório devem estar de acordo com esse comportamento, mas o [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] não impõem esse comportamento.</span><span class="sxs-lookup"><span data-stu-id="46cb0-111">Store providers should comply with that behavior, but [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] does not enforce this behavior.</span></span>  
  
 <span data-ttu-id="46cb0-112">Para cenários LINQ, consultas em relação a [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] envolver métodos CLR de mapeamento para métodos na fonte de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="46cb0-112">For LINQ scenarios, queries against the [!INCLUDE[adonet_ef](../../../../../../includes/adonet-ef-md.md)] involve mapping CLR methods to methods in the underlying data source.</span></span> <span data-ttu-id="46cb0-113">Os métodos CLR mapeiam para funções canônicas, de modo que um conjunto específico de métodos mapeará corretamente, independentemente da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="46cb0-113">The CLR methods map to canonical functions, so that a specific set of methods will correctly map, regardless of the data source.</span></span>  
  
## <a name="canonical-functions-namespace"></a><span data-ttu-id="46cb0-114">Namespace de funções canônicas</span><span class="sxs-lookup"><span data-stu-id="46cb0-114">Canonical Functions Namespace</span></span>  
 <span data-ttu-id="46cb0-115">O namespace para a função canônica é <xref:System.Data.Metadata.Edm>.</span><span class="sxs-lookup"><span data-stu-id="46cb0-115">The namespace for canonical function is <xref:System.Data.Metadata.Edm>.</span></span> <span data-ttu-id="46cb0-116">O namespace <xref:System.Data.Metadata.Edm> é incluído automaticamente em todas as consultas.</span><span class="sxs-lookup"><span data-stu-id="46cb0-116">The <xref:System.Data.Metadata.Edm> namespace is automatically included in all queries.</span></span> <span data-ttu-id="46cb0-117">No entanto, se outro namespace for importado e contiver uma função com o mesmo nome de uma função canônica (no namespace <xref:System.Data.Metadata.Edm>), você deverá especificar o namespace.</span><span class="sxs-lookup"><span data-stu-id="46cb0-117">However, if another namespace is imported that contains a function with the same name as a canonical function (in the <xref:System.Data.Metadata.Edm> namespace), you must specify the namespace.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="46cb0-118">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="46cb0-118">In This Section</span></span>  
 [<span data-ttu-id="46cb0-119">Funções canônicas agregadas</span><span class="sxs-lookup"><span data-stu-id="46cb0-119">Aggregate Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)  
 <span data-ttu-id="46cb0-120">Discute funções canônicas de agregação de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46cb0-120">Discusses aggregate [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="46cb0-121">Funções canônicas matemáticas</span><span class="sxs-lookup"><span data-stu-id="46cb0-121">Math Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/math-canonical-functions.md)  
 <span data-ttu-id="46cb0-122">Discute funções canônicas matemáticas de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46cb0-122">Discusses math [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="46cb0-123">Funções canônicas de cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="46cb0-123">String Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/string-canonical-functions.md)  
 <span data-ttu-id="46cb0-124">Discute funções canônicas de cadeias de caracteres de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46cb0-124">Discusses string [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="46cb0-125">Funções canônicas de data e hora</span><span class="sxs-lookup"><span data-stu-id="46cb0-125">Date and Time Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/date-and-time-canonical-functions.md)  
 <span data-ttu-id="46cb0-126">Discute funções canônicas de data e hora de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46cb0-126">Discusses date and time [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="46cb0-127">Funções canônicas bit a bit</span><span class="sxs-lookup"><span data-stu-id="46cb0-127">Bitwise Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/bitwise-canonical-functions.md)  
 <span data-ttu-id="46cb0-128">Discute funções canônicas bit a bit de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46cb0-128">Discusses bitwise [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="46cb0-129">Funções espaciais</span><span class="sxs-lookup"><span data-stu-id="46cb0-129">Spatial Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/spatial-functions.md)  
 <span data-ttu-id="46cb0-130">Discute funções canônicas espaciais de [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="46cb0-130">Discusses Spatial [!INCLUDE[esql](../../../../../../includes/esql-md.md)] canonical functions.</span></span>  
  
 [<span data-ttu-id="46cb0-131">Outras funções canônicas</span><span class="sxs-lookup"><span data-stu-id="46cb0-131">Other Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/other-canonical-functions.md)  
 <span data-ttu-id="46cb0-132">Discute as funções não classificadas como bit a bit, data/hora, cadeia de caracteres, matemática ou de agregação.</span><span class="sxs-lookup"><span data-stu-id="46cb0-132">Discusses functions not classified as bitwise, date/time, string, math, or aggregate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46cb0-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="46cb0-133">See Also</span></span>  
 [<span data-ttu-id="46cb0-134">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="46cb0-134">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="46cb0-135">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="46cb0-135">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="46cb0-136">Mapeamento de funções canônicas de modelo conceitual para o SQL Server</span><span class="sxs-lookup"><span data-stu-id="46cb0-136">Conceptual Model Canonical to SQL Server Functions Mapping</span></span>](../../../../../../docs/framework/data/adonet/ef/conceptual-model-canonical-to-sql-server-functions-mapping.md)  
 [<span data-ttu-id="46cb0-137">Funções definidas pelo usuário</span><span class="sxs-lookup"><span data-stu-id="46cb0-137">User-Defined Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/user-defined-functions-entity-sql.md)
