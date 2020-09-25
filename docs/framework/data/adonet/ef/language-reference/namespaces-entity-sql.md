---
title: Namespaces (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 83991c21-60db-4af9-aca3-b416f6cae98e
ms.openlocfilehash: 7a53f8e7e70dbc9fa505f7f8619af10a0e44c331
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91197801"
---
# <a name="namespaces-entity-sql"></a><span data-ttu-id="1016d-102">Namespaces (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="1016d-102">Namespaces (Entity SQL)</span></span>

[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="1016d-103">apresenta namespaces para evitar conflitos de nome para identificadores globais como nomes de tipo, conjuntos de entidades, funções, e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="1016d-103">introduces namespaces to avoid name conflicts for global identifiers such as type names, entity sets, functions, and so on.</span></span> <span data-ttu-id="1016d-104">O suporte a namespace no [!INCLUDE[esql](../../../../../../includes/esql-md.md)] é semelhante ao suporte de namespace no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1016d-104">The namespace support in [!INCLUDE[esql](../../../../../../includes/esql-md.md)] is similar to the namespace support in the .NET Framework.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="1016d-105">fornece dois formulários que a cláusula group UTILIZAÇÃO: namespaces qualificadas (onde um alias mais curtas são fornecidas para o namespace), e namespaces não qualificado, como ilustrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1016d-105">provides two forms of the USING clause: qualified namespaces (where a shorter alias is provided for the namespace), and unqualified namespaces, as illustrated in the following example:</span></span>  
  
 `USING System.Data;`  
  
 `USING tsql = System.Data;`  
  
## <a name="name-resolution-rules"></a><span data-ttu-id="1016d-106">Regras de resolução de nomes</span><span class="sxs-lookup"><span data-stu-id="1016d-106">Name Resolution Rules</span></span>  

 <span data-ttu-id="1016d-107">Se um identificador não puder ser resolvido nos escopos locais, o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tentará localizar o nome nos escopos globais (os namespaces).</span><span class="sxs-lookup"><span data-stu-id="1016d-107">If an identifier cannot be resolved in the local scopes, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to locate the name in the global scopes (the namespaces).</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="1016d-108">tenta corresponder primeiro o identificador (prefixo) com uma namespaces qualificadas.</span><span class="sxs-lookup"><span data-stu-id="1016d-108">first tries to match the identifier (prefix) with one of the qualified namespaces.</span></span> <span data-ttu-id="1016d-109">Se houver uma correspondência, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] o tentará resolver o restante do identificador no namespace especificado.</span><span class="sxs-lookup"><span data-stu-id="1016d-109">If there is a match, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to resolve the rest of the identifier in the specified namespace.</span></span> <span data-ttu-id="1016d-110">Se nenhuma correspondência for encontrada, uma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="1016d-110">If no match is found, an exception is thrown.</span></span>  
  
 <span data-ttu-id="1016d-111">Em seguida, o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tenta pesquisar todos os namespaces não qualificados (especificados no prólogo) para o identificador.</span><span class="sxs-lookup"><span data-stu-id="1016d-111">Next, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] tries to search all unqualified namespaces (specified in the prolog) for the identifier.</span></span> <span data-ttu-id="1016d-112">Se o identificador pode ser localizado em exatamente um namespace, esse local é retornado.</span><span class="sxs-lookup"><span data-stu-id="1016d-112">If the identifier can be located in exactly one namespace, that location is returned.</span></span> <span data-ttu-id="1016d-113">Se mais de um namespace tiver uma correspondência para o identificador, uma exceção é lançada.</span><span class="sxs-lookup"><span data-stu-id="1016d-113">If more than one namespace has a match for that identifier, an exception is thrown.</span></span> <span data-ttu-id="1016d-114">Se nenhum namespace puder ser identificado para o identificador, o [!INCLUDE[esql](../../../../../../includes/esql-md.md)] passará o nome para o próximo escopo externo (o <xref:System.Data.Common.DbCommand> <xref:System.Data.Common.DbConnection> objeto ou), conforme ilustrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="1016d-114">If no namespace can be identified for the identifier, [!INCLUDE[esql](../../../../../../includes/esql-md.md)] passes the name onto the next outward scope (the <xref:System.Data.Common.DbCommand> or <xref:System.Data.Common.DbConnection> object), as illustrated in the following example:</span></span>  
  
```sql  
SELECT TREAT(p AS NamespaceName.Employee)  
FROM ContainerName.Person AS p  
WHERE p IS OF (NamespaceName.Employee)  
```  
  
## <a name="differences-from-the-net-framework"></a><span data-ttu-id="1016d-115">Diferenças do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1016d-115">Differences from the .NET Framework</span></span>  

 <span data-ttu-id="1016d-116">No .NET Framework, você pode usar namespaces parcialmente qualificados.</span><span class="sxs-lookup"><span data-stu-id="1016d-116">In the .NET Framework, you can use partially qualified namespaces.</span></span> [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="1016d-117">não permite isso.</span><span class="sxs-lookup"><span data-stu-id="1016d-117">does not allow this.</span></span>  
  
## <a name="adonet-usage"></a><span data-ttu-id="1016d-118">Uso do ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1016d-118">ADO.NET Usage</span></span>  

 <span data-ttu-id="1016d-119">Consultas são expressos por meio de objetos ADO.NET <xref:System.Data.Common.DbCommand> .</span><span class="sxs-lookup"><span data-stu-id="1016d-119">Queries are expressed through ADO.NET <xref:System.Data.Common.DbCommand> objects.</span></span> <span data-ttu-id="1016d-120">os objetos de<xref:System.Data.Common.DbCommand> podem ser compilados sobre objetos de <xref:System.Data.Common.DbConnection> .</span><span class="sxs-lookup"><span data-stu-id="1016d-120"><xref:System.Data.Common.DbCommand> objects can be built over <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="1016d-121">Namespaces também podem ser especificadas como parte de objetos de <xref:System.Data.Common.DbCommand> e de <xref:System.Data.Common.DbConnection> .</span><span class="sxs-lookup"><span data-stu-id="1016d-121">Namespaces can also be specified as part of the <xref:System.Data.Common.DbCommand> and <xref:System.Data.Common.DbConnection> objects.</span></span> <span data-ttu-id="1016d-122">Se [!INCLUDE[esql](../../../../../../includes/esql-md.md)] o não puder resolver um identificador dentro da própria consulta, os namespaces externos serão investigados (com base em regras semelhantes).</span><span class="sxs-lookup"><span data-stu-id="1016d-122">If [!INCLUDE[esql](../../../../../../includes/esql-md.md)] cannot resolve an identifier within the query itself, the external namespaces are probed (based on similar rules).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1016d-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="1016d-123">See also</span></span>

- [<span data-ttu-id="1016d-124">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1016d-124">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="1016d-125">Visão geral da Entity SQL</span><span class="sxs-lookup"><span data-stu-id="1016d-125">Entity SQL Overview</span></span>](entity-sql-overview.md)
