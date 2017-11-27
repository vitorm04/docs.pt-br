---
title: Sistema de tipo (Entity SQL)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: b951a51c4a9daee44ba55aa3589900ca4cad188a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="type-system-entity-sql"></a><span data-ttu-id="b592c-102">Sistema de tipo (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="b592c-102">Type System (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="b592c-103">dá suporte a uma variedade de tipos:</span><span class="sxs-lookup"><span data-stu-id="b592c-103"> supports a number of types:</span></span>  
  
-   <span data-ttu-id="b592c-104">A primitiva) tipos simples (como `Int32` e `String.`</span><span class="sxs-lookup"><span data-stu-id="b592c-104">Primitive (simple) types such as `Int32` and `String.`</span></span>  
  
-   <span data-ttu-id="b592c-105">Tipos de substantivo que são definidos no esquema, como <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, e <xref:System.Data.Metadata.Edm.RelationshipType>.</span><span class="sxs-lookup"><span data-stu-id="b592c-105">Nominal types that are defined in the schema, such as <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, and <xref:System.Data.Metadata.Edm.RelationshipType>.</span></span>  
  
-   <span data-ttu-id="b592c-106">Tipos anônimos que não são definidos no esquema explicitamente: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, e <xref:System.Data.Metadata.Edm.RefType>.</span><span class="sxs-lookup"><span data-stu-id="b592c-106">Anonymous types that are not defined in the schema explicitly: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, and <xref:System.Data.Metadata.Edm.RefType>.</span></span>  
  
 <span data-ttu-id="b592c-107">Esta seção discute os tipos anônimos que não são definidos no esquema explicitamente mas é suportada por [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b592c-107">This section discusses the anonymous types that are not defined in the schema explicitly but are supported by [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span></span> <span data-ttu-id="b592c-108">Para obter informações sobre tipos primitivos e nominais, consulte [tipos de modelo conceitual (CSDL)](http://msdn.microsoft.com/en-us/987b995f-e429-4569-9559-b4146744def4).</span><span class="sxs-lookup"><span data-stu-id="b592c-108">For information on primitive and nominal types, see [Conceptual Model Types (CSDL)](http://msdn.microsoft.com/en-us/987b995f-e429-4569-9559-b4146744def4).</span></span>  
  
## <a name="rows"></a><span data-ttu-id="b592c-109">Linhas</span><span class="sxs-lookup"><span data-stu-id="b592c-109">Rows</span></span>  
 <span data-ttu-id="b592c-110">A estrutura de uma linha depende da sequência de membros tipados e nomeados em que a linha consiste.</span><span class="sxs-lookup"><span data-stu-id="b592c-110">The structure of a row depends on the sequence of typed and named members that the row consists of.</span></span> <span data-ttu-id="b592c-111">Um tipo de linha não tem nenhuma identidade e não pode ser herdada de.</span><span class="sxs-lookup"><span data-stu-id="b592c-111">A row type has no identity and cannot be inherited from.</span></span> <span data-ttu-id="b592c-112">As instâncias do mesmo tipo de linha são equivalentes se os membros são equivalentes respectivamente.</span><span class="sxs-lookup"><span data-stu-id="b592c-112">Instances of the same row type are equivalent if the members are respectively equivalent.</span></span> <span data-ttu-id="b592c-113">As linhas não têm nenhum comportamento além de sua equivalência estrutural e não têm equivalentes em Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="b592c-113">Rows have no behavior beyond their structural equivalence and have no equivalent in the common language runtime.</span></span> <span data-ttu-id="b592c-114">Consultas podem resultar em estruturas que contêm linhas ou coleções de linhas.</span><span class="sxs-lookup"><span data-stu-id="b592c-114">Queries can result in structures that contain rows or collections of rows.</span></span> <span data-ttu-id="b592c-115">API que associação entre as consultas de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] e o idioma de host define como as linhas são feitas na consulta que gerou o resultado.</span><span class="sxs-lookup"><span data-stu-id="b592c-115">The API binding between the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries and the host language defines how rows are realized in the query that produced the result.</span></span> <span data-ttu-id="b592c-116">Para obter informações sobre como construir uma instância de linha, consulte [construindo tipos](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b592c-116">For information on how to construct a row instance, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
## <a name="collections"></a><span data-ttu-id="b592c-117">Coleções</span><span class="sxs-lookup"><span data-stu-id="b592c-117">Collections</span></span>  
 <span data-ttu-id="b592c-118">Os tipos de coleção representam zero ou mais instâncias de outros objetos.</span><span class="sxs-lookup"><span data-stu-id="b592c-118">Collection types represent zero or more instances of other objects.</span></span> <span data-ttu-id="b592c-119">Para obter informações sobre como construir a coleção, consulte [construindo tipos](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="b592c-119">For information on how to construct collection, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="b592c-120">Referências</span><span class="sxs-lookup"><span data-stu-id="b592c-120">References</span></span>  
 <span data-ttu-id="b592c-121">Uma referência é um ponteiro a uma entidade lógica específica em um conjunto de entidades específico.</span><span class="sxs-lookup"><span data-stu-id="b592c-121">A reference is a logical pointer to a specific entity in a specific entity set.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)]<span data-ttu-id="b592c-122"> oferece suporte aos seguintes operadores para construir, deconstruct, e navegar com referências:</span><span class="sxs-lookup"><span data-stu-id="b592c-122"> supports the following operators to construct, deconstruct, and navigate through references:</span></span>  
  
-   [<span data-ttu-id="b592c-123">REF</span><span class="sxs-lookup"><span data-stu-id="b592c-123">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
  
-   [<span data-ttu-id="b592c-124">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="b592c-124">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
  
-   [<span data-ttu-id="b592c-125">CHAVE</span><span class="sxs-lookup"><span data-stu-id="b592c-125">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
  
-   [<span data-ttu-id="b592c-126">DEREF</span><span class="sxs-lookup"><span data-stu-id="b592c-126">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
  
 <span data-ttu-id="b592c-127">Você pode navegar com uma referência usando o operador de acesso a membro (ponto) (`.`).</span><span class="sxs-lookup"><span data-stu-id="b592c-127">You can navigate through a reference by using the member access (dot) operator(`.`).</span></span> <span data-ttu-id="b592c-128">O trecho de código a seguir na propriedade id (ordem) para navegar através da propriedade de r (referência).</span><span class="sxs-lookup"><span data-stu-id="b592c-128">The following snippet extracts the Id property (of Order) by navigating through the r (reference) property.</span></span>  
  
```  
select o2.r.Id   
from (select ref(o) as r from LOB.Orders as o) as o2   
```  
  
 <span data-ttu-id="b592c-129">Se o valor de referência é zero, ou se o destino de referência não existir, o resultado é nulo.</span><span class="sxs-lookup"><span data-stu-id="b592c-129">If the reference value is null, or if the target of the reference does not exist, the result is null.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b592c-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b592c-130">See Also</span></span>  
 [<span data-ttu-id="b592c-131">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b592c-131">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)  
 [<span data-ttu-id="b592c-132">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="b592c-132">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="b592c-133">CONVERSÃO</span><span class="sxs-lookup"><span data-stu-id="b592c-133">CAST</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)  
 <span data-ttu-id="b592c-134">[CSDL, SSDL, and MSL Specifications](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md) (Especificações CSDL, SSDL e MSL)</span><span class="sxs-lookup"><span data-stu-id="b592c-134">[CSDL, SSDL, and MSL Specifications](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)</span></span>
