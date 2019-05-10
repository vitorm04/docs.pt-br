---
title: Armazenamento em cache do plano de consulta (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: 9b809962e11ee74a99f736769b47bf3052af5e8a
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64641461"
---
# <a name="query-plan-caching-entity-sql"></a><span data-ttu-id="3cd58-102">Armazenamento em cache do plano de consulta (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="3cd58-102">Query Plan Caching (Entity SQL)</span></span>
<span data-ttu-id="3cd58-103">Sempre que uma tentativa de executar uma consulta é feita, o pipeline de consulta pesquisa seu cache do plano de consulta para ver se a consulta exata já está compilada e disponível.</span><span class="sxs-lookup"><span data-stu-id="3cd58-103">Whenever an attempt to execute a query is made, the query pipeline looks up its query plan cache to see whether the exact query is already compiled and available.</span></span> <span data-ttu-id="3cd58-104">Em caso afirmativo, reutiliza o plano armazenado em cachê em vez de criar um novo.</span><span class="sxs-lookup"><span data-stu-id="3cd58-104">If so, it reuses the cached plan rather than building a new one.</span></span> <span data-ttu-id="3cd58-105">Se uma correspondência não for encontrada no cache do plano de consulta, a consulta é criada e armazenadas em cachê.</span><span class="sxs-lookup"><span data-stu-id="3cd58-105">If a match is not found in the query plan cache, the query is compiled and cached.</span></span> <span data-ttu-id="3cd58-106">Uma consulta é identificada por sua coleção de texto e o parâmetro de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (nomes e tipos).</span><span class="sxs-lookup"><span data-stu-id="3cd58-106">A query is identified by its [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text and parameter collection (names and types).</span></span> <span data-ttu-id="3cd58-107">Todas as comparações de texto diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="3cd58-107">All text comparisons are case-sensitive.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="3cd58-108">Configuração</span><span class="sxs-lookup"><span data-stu-id="3cd58-108">Configuration</span></span>  
 <span data-ttu-id="3cd58-109">O cachê do plano de consulta é configurável com <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="3cd58-109">Query plan caching is configurable through the <xref:System.Data.EntityClient.EntityCommand>.</span></span>  
  
 <span data-ttu-id="3cd58-110">Para ativar ou desativar a consulta planejar o cachê com <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, defina essa propriedade como `true` ou a `false`.</span><span class="sxs-lookup"><span data-stu-id="3cd58-110">To enable or disable query plan caching through <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, set this property to `true` or `false`.</span></span> <span data-ttu-id="3cd58-111">Desativar o cachê de fundo para consultas dinâmicos individuais que são improvável de ser usado mais uma vez em melhora o desempenho.</span><span class="sxs-lookup"><span data-stu-id="3cd58-111">Disabling plan caching for individual dynamic queries that are unlikely to be used more then once improves performance.</span></span>  
  
 <span data-ttu-id="3cd58-112">Você pode ativar o cachê do plano de consulta com <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span><span class="sxs-lookup"><span data-stu-id="3cd58-112">You can enable query plan caching through <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span></span>  
  
## <a name="recommended-practice"></a><span data-ttu-id="3cd58-113">Prática recomendada</span><span class="sxs-lookup"><span data-stu-id="3cd58-113">Recommended Practice</span></span>  
 <span data-ttu-id="3cd58-114">Consultas dinâmicos devem ser evitadas, geralmente.</span><span class="sxs-lookup"><span data-stu-id="3cd58-114">Dynamic queries should be avoided, in general.</span></span> <span data-ttu-id="3cd58-115">O exemplo a seguir dinâmica de consulta é vulnerável a ataques de injeção SQL, porque recebe entrada do usuário diretamente sem qualquer validação.</span><span class="sxs-lookup"><span data-stu-id="3cd58-115">The following dynamic query example is vulnerable to SQL injection attacks, because it takes user input directly without any validation.</span></span>  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 <span data-ttu-id="3cd58-116">Se você usar consultas gerados dinamicamente, considere desativar o cachê do plano de consulta para evitar desnecessário consumo de memória para as entradas de cache que são improvável de ser reutilizado.</span><span class="sxs-lookup"><span data-stu-id="3cd58-116">If you do use dynamically generated queries, consider disabling query plan caching to avoid unnecessary memory consumption for cache entries that are unlikely to be reused.</span></span>  
  
 <span data-ttu-id="3cd58-117">Consulte o cachê de fundo em consultas estáticos e consultas parametrizadas podem fornecer benefícios de desempenho.</span><span class="sxs-lookup"><span data-stu-id="3cd58-117">Query plan caching on static queries and parameterized queries can provide performance benefits.</span></span> <span data-ttu-id="3cd58-118">A seguir está um exemplo de uma consulta estático:</span><span class="sxs-lookup"><span data-stu-id="3cd58-118">The following is an example of a static query:</span></span>  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 <span data-ttu-id="3cd58-119">Para que as consultas são igualadas corretamente pelo cache do plano de consulta, devem estar de acordo com os seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="3cd58-119">For queries to be matched properly by the query plan cache, they should comply with the following requirements:</span></span>  
  
- <span data-ttu-id="3cd58-120">O texto da consulta deve ser um padrão constante, de preferência um cadeia de caracteres constante ou um recurso.</span><span class="sxs-lookup"><span data-stu-id="3cd58-120">Query text should be a constant pattern, preferably a constant string or a resource.</span></span>  
  
- <span data-ttu-id="3cd58-121"><xref:System.Data.EntityClient.EntityParameter> ou <xref:System.Data.Objects.ObjectParameter> devem ser usados em qualquer lugar que um valor de fornecido deve ser passado.</span><span class="sxs-lookup"><span data-stu-id="3cd58-121"><xref:System.Data.EntityClient.EntityParameter> or <xref:System.Data.Objects.ObjectParameter> should be used wherever a user-supplied value must be passed.</span></span>  
  
 <span data-ttu-id="3cd58-122">Você deve evitar os seguintes padrões de consulta, que consomem desnecessariamente slots no cache do plano de consulta:</span><span class="sxs-lookup"><span data-stu-id="3cd58-122">You should avoid the following query patterns, which unnecessarily consume slots in the query plan cache:</span></span>  
  
- <span data-ttu-id="3cd58-123">Alterações em caso de letra em texto.</span><span class="sxs-lookup"><span data-stu-id="3cd58-123">Changes to letter case in the text.</span></span>  
  
- <span data-ttu-id="3cd58-124">Alterações no espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="3cd58-124">Changes to white space.</span></span>  
  
- <span data-ttu-id="3cd58-125">Alterações em valores literais.</span><span class="sxs-lookup"><span data-stu-id="3cd58-125">Changes to literal values.</span></span>  
  
- <span data-ttu-id="3cd58-126">Alterações ao texto dentro de comentários.</span><span class="sxs-lookup"><span data-stu-id="3cd58-126">Changes to text inside comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cd58-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3cd58-127">See also</span></span>

- [<span data-ttu-id="3cd58-128">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3cd58-128">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
