---
title: Armazenamento em cache do plano de consulta (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 90b0c685-5ef2-461b-98b4-c3c0a2b253c7
ms.openlocfilehash: ca95f3aed5c092247a97bbfe5b0237a45b95ae16
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249291"
---
# <a name="query-plan-caching-entity-sql"></a><span data-ttu-id="6eb82-102">Armazenamento em cache do plano de consulta (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6eb82-102">Query Plan Caching (Entity SQL)</span></span>
<span data-ttu-id="6eb82-103">Sempre que uma tentativa de executar uma consulta é feita, o pipeline de consulta pesquisa seu cache do plano de consulta para ver se a consulta exata já está compilada e disponível.</span><span class="sxs-lookup"><span data-stu-id="6eb82-103">Whenever an attempt to execute a query is made, the query pipeline looks up its query plan cache to see whether the exact query is already compiled and available.</span></span> <span data-ttu-id="6eb82-104">Em caso afirmativo, reutiliza o plano armazenado em cachê em vez de criar um novo.</span><span class="sxs-lookup"><span data-stu-id="6eb82-104">If so, it reuses the cached plan rather than building a new one.</span></span> <span data-ttu-id="6eb82-105">Se uma correspondência não for encontrada no cache do plano de consulta, a consulta é criada e armazenadas em cachê.</span><span class="sxs-lookup"><span data-stu-id="6eb82-105">If a match is not found in the query plan cache, the query is compiled and cached.</span></span> <span data-ttu-id="6eb82-106">Uma consulta é identificada por sua coleção de texto e o parâmetro de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] (nomes e tipos).</span><span class="sxs-lookup"><span data-stu-id="6eb82-106">A query is identified by its [!INCLUDE[esql](../../../../../../includes/esql-md.md)] text and parameter collection (names and types).</span></span> <span data-ttu-id="6eb82-107">Todas as comparações de texto diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="6eb82-107">All text comparisons are case-sensitive.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="6eb82-108">Configuração</span><span class="sxs-lookup"><span data-stu-id="6eb82-108">Configuration</span></span>  
 <span data-ttu-id="6eb82-109">O cachê do plano de consulta é configurável com <xref:System.Data.EntityClient.EntityCommand>.</span><span class="sxs-lookup"><span data-stu-id="6eb82-109">Query plan caching is configurable through the <xref:System.Data.EntityClient.EntityCommand>.</span></span>  
  
 <span data-ttu-id="6eb82-110">Para ativar ou desativar a consulta planejar o cachê com <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, defina essa propriedade como `true` ou a `false`.</span><span class="sxs-lookup"><span data-stu-id="6eb82-110">To enable or disable query plan caching through <xref:System.Data.EntityClient.EntityCommand.EnablePlanCaching%2A?displayProperty=nameWithType>, set this property to `true` or `false`.</span></span> <span data-ttu-id="6eb82-111">Desativar o cachê de fundo para consultas dinâmicos individuais que são improvável de ser usado mais uma vez em melhora o desempenho.</span><span class="sxs-lookup"><span data-stu-id="6eb82-111">Disabling plan caching for individual dynamic queries that are unlikely to be used more then once improves performance.</span></span>  
  
 <span data-ttu-id="6eb82-112">Você pode ativar o cachê do plano de consulta com <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span><span class="sxs-lookup"><span data-stu-id="6eb82-112">You can enable query plan caching through <xref:System.Data.Objects.ObjectQuery.EnablePlanCaching%2A>.</span></span>  
  
## <a name="recommended-practice"></a><span data-ttu-id="6eb82-113">Prática recomendada</span><span class="sxs-lookup"><span data-stu-id="6eb82-113">Recommended Practice</span></span>  
 <span data-ttu-id="6eb82-114">Consultas dinâmicos devem ser evitadas, geralmente.</span><span class="sxs-lookup"><span data-stu-id="6eb82-114">Dynamic queries should be avoided, in general.</span></span> <span data-ttu-id="6eb82-115">O exemplo a seguir dinâmica de consulta é vulnerável a ataques de injeção SQL, porque recebe entrada do usuário diretamente sem qualquer validação.</span><span class="sxs-lookup"><span data-stu-id="6eb82-115">The following dynamic query example is vulnerable to SQL injection attacks, because it takes user input directly without any validation.</span></span>  
  
 `"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp WHERE sp.EmployeeID = " + employeeTextBox.Text;`  
  
 <span data-ttu-id="6eb82-116">Se você usar consultas gerados dinamicamente, considere desativar o cachê do plano de consulta para evitar desnecessário consumo de memória para as entradas de cache que são improvável de ser reutilizado.</span><span class="sxs-lookup"><span data-stu-id="6eb82-116">If you do use dynamically generated queries, consider disabling query plan caching to avoid unnecessary memory consumption for cache entries that are unlikely to be reused.</span></span>  
  
 <span data-ttu-id="6eb82-117">Consulte o cachê de fundo em consultas estáticos e consultas parametrizadas podem fornecer benefícios de desempenho.</span><span class="sxs-lookup"><span data-stu-id="6eb82-117">Query plan caching on static queries and parameterized queries can provide performance benefits.</span></span> <span data-ttu-id="6eb82-118">A seguir está um exemplo de uma consulta estático:</span><span class="sxs-lookup"><span data-stu-id="6eb82-118">The following is an example of a static query:</span></span>  
  
```  
"SELECT sp.SalesYTD FROM AdventureWorksEntities.SalesPerson as sp";  
```  
  
 <span data-ttu-id="6eb82-119">Para que as consultas são igualadas corretamente pelo cache do plano de consulta, devem estar de acordo com os seguintes requisitos:</span><span class="sxs-lookup"><span data-stu-id="6eb82-119">For queries to be matched properly by the query plan cache, they should comply with the following requirements:</span></span>  
  
- <span data-ttu-id="6eb82-120">O texto da consulta deve ser um padrão constante, de preferência um cadeia de caracteres constante ou um recurso.</span><span class="sxs-lookup"><span data-stu-id="6eb82-120">Query text should be a constant pattern, preferably a constant string or a resource.</span></span>  
  
- <span data-ttu-id="6eb82-121"><xref:System.Data.EntityClient.EntityParameter> ou <xref:System.Data.Objects.ObjectParameter> devem ser usados em qualquer lugar que um valor de fornecido deve ser passado.</span><span class="sxs-lookup"><span data-stu-id="6eb82-121"><xref:System.Data.EntityClient.EntityParameter> or <xref:System.Data.Objects.ObjectParameter> should be used wherever a user-supplied value must be passed.</span></span>  
  
 <span data-ttu-id="6eb82-122">Você deve evitar os seguintes padrões de consulta, que consomem desnecessariamente slots no cache do plano de consulta:</span><span class="sxs-lookup"><span data-stu-id="6eb82-122">You should avoid the following query patterns, which unnecessarily consume slots in the query plan cache:</span></span>  
  
- <span data-ttu-id="6eb82-123">Alterações em caso de letra em texto.</span><span class="sxs-lookup"><span data-stu-id="6eb82-123">Changes to letter case in the text.</span></span>  
  
- <span data-ttu-id="6eb82-124">Alterações no espaço em branco.</span><span class="sxs-lookup"><span data-stu-id="6eb82-124">Changes to white space.</span></span>  
  
- <span data-ttu-id="6eb82-125">Alterações em valores literais.</span><span class="sxs-lookup"><span data-stu-id="6eb82-125">Changes to literal values.</span></span>  
  
- <span data-ttu-id="6eb82-126">Alterações ao texto dentro de comentários.</span><span class="sxs-lookup"><span data-stu-id="6eb82-126">Changes to text inside comments.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eb82-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6eb82-127">See also</span></span>

- [<span data-ttu-id="6eb82-128">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6eb82-128">Entity SQL Overview</span></span>](entity-sql-overview.md)
