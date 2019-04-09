---
title: Definições de tipo (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 306b204a-ade5-47ef-95b5-c785d2da4a7e
ms.openlocfilehash: 2e068db0ce202c26cad36c8ed7adf0acdfb8e363
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096017"
---
# <a name="type-definitions-entity-sql"></a><span data-ttu-id="c6617-102">Definições de tipo (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="c6617-102">Type Definitions (Entity SQL)</span></span>
<span data-ttu-id="c6617-103">Uma definição de tipo é usada na instrução de declaração de uma função in-line de [!INCLUDE[esql](../../../../../../includes/esql-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="c6617-103">A type definition is used in the declaration statement of an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Inline function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6617-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="c6617-104">Remarks</span></span>  
 <span data-ttu-id="c6617-105">A instrução de declaração para uma função in-line consiste as [função](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) seguido pelo identificador que representa o nome da função (por exemplo, "MyAvg") seguido por uma lista de definições de parâmetro no parêntese (por palavra-chave exemplo, "a dívidas dívidas.</span><span class="sxs-lookup"><span data-stu-id="c6617-105">The declaration statement for an inline function consists of the [FUNCTION](../../../../../../docs/framework/data/adonet/ef/language-reference/function-entity-sql.md) keyword followed by the identifier representing the function name (for example, "MyAvg") followed by a parameter definition list in parenthesis (for example, "dues Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="c6617-106">A lista de definição de parâmetro consiste de zero ou mais definições de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c6617-106">The parameter definition list consists of zero or more parameter definitions.</span></span> <span data-ttu-id="c6617-107">Cada definição de parâmetro consiste em um identificador (o nome do parâmetro para a função, por exemplo, a dívidas “”) seguido por uma definição de tipo (por exemplo, “coleção (decimal) ").</span><span class="sxs-lookup"><span data-stu-id="c6617-107">Each parameter definition consists of an identifier (the name of the parameter to the function, for example, "dues") followed by a type definition (for example, "Collection(Decimal)").</span></span>  
  
 <span data-ttu-id="c6617-108">Definições de tipo podem ser qualquer:</span><span class="sxs-lookup"><span data-stu-id="c6617-108">The type definitions can be either:</span></span>  
  
-   <span data-ttu-id="c6617-109">O tipo identificador (por exemplo, “Int32” ou “AdventureWorks.Order”).</span><span class="sxs-lookup"><span data-stu-id="c6617-109">The type of the identifier (for example, "Int32" or "AdventureWorks.Order").</span></span>  
  
-   <span data-ttu-id="c6617-110">A palavra-chave `COLLECTION` seguido por outra definição de tipo no parêntese (por exemplo, “coleção (AdventureWorks.Order) ").</span><span class="sxs-lookup"><span data-stu-id="c6617-110">The keyword `COLLECTION` followed by another type definition in parenthesis (for example, "Collection(AdventureWorks.Order)").</span></span>  
  
-   <span data-ttu-id="c6617-111">A LINHA seguida por uma lista de definições de propriedade no parêntese (por exemplo, “linha de palavras-chave (x) AdventureWorks.Order ").</span><span class="sxs-lookup"><span data-stu-id="c6617-111">The keyword ROW followed by a list of property definitions in parenthesis (for example, "Row(x AdventureWorks.Order)").</span></span> <span data-ttu-id="c6617-112">Definições de propriedade tem um formato como "`identifier type_definition`, `identifier type_definition`,...".</span><span class="sxs-lookup"><span data-stu-id="c6617-112">Property definitions have a format such as "`identifier type_definition`, `identifier type_definition`, ...".</span></span>  
  
-   <span data-ttu-id="c6617-113">A referência seguido pelo tipo identificador no parêntese (por exemplo, “referência de palavras-chave (AdventureWorks.Order) ").</span><span class="sxs-lookup"><span data-stu-id="c6617-113">The keyword REF followed by the type of the identifier in parenthesis (for example, "Ref(AdventureWorks.Order)").</span></span> <span data-ttu-id="c6617-114">O operador de definição de tipo de referência requer um tipo de entidade como o argumento.</span><span class="sxs-lookup"><span data-stu-id="c6617-114">The REF type definition operator requires an entity type as the argument.</span></span> <span data-ttu-id="c6617-115">Você não pode especificar um tipo primitivo como o argumento.</span><span class="sxs-lookup"><span data-stu-id="c6617-115">You cannot specify a primitive type as the argument.</span></span>  
  
 <span data-ttu-id="c6617-116">Você também pode aninhar definições de tipo (por exemplo, “coleção (linha (referência de AdventureWorks.Order (x))").</span><span class="sxs-lookup"><span data-stu-id="c6617-116">You can also nest type definitions (for example, "Collection(Row(x Ref(AdventureWorks.Order)))").</span></span>  
  
 <span data-ttu-id="c6617-117">As opções de definição de tipo são:</span><span class="sxs-lookup"><span data-stu-id="c6617-117">The type definition options are:</span></span>  
  
-   `IdentifierName supported_type`<span data-ttu-id="c6617-118">, ou</span><span class="sxs-lookup"><span data-stu-id="c6617-118">, or</span></span>  
  
-   `IdentifierName` <span data-ttu-id="c6617-119">COLEÇÃO (`type_definition`), ou</span><span class="sxs-lookup"><span data-stu-id="c6617-119">COLLECTION(`type_definition`), or</span></span>  
  
-   `IdentifierName` <span data-ttu-id="c6617-120">LINHA (`property_definition`), ou</span><span class="sxs-lookup"><span data-stu-id="c6617-120">ROW(`property_definition`), or</span></span>  
  
-   `IdentifierName` <span data-ttu-id="c6617-121">REF (`supported_entity_type`)</span><span class="sxs-lookup"><span data-stu-id="c6617-121">REF(`supported_entity_type`)</span></span>  
  
 <span data-ttu-id="c6617-122">A opção de definição de propriedade é `IdentifierName type_definition`.</span><span class="sxs-lookup"><span data-stu-id="c6617-122">The property definition option is `IdentifierName type_definition`.</span></span>  
  
 <span data-ttu-id="c6617-123">Os tipos suportados são alguns tipos no namespace atual.</span><span class="sxs-lookup"><span data-stu-id="c6617-123">Supported types are any types in the current namespace.</span></span> <span data-ttu-id="c6617-124">Esses incluem a primitiva e os tipos de entidade.</span><span class="sxs-lookup"><span data-stu-id="c6617-124">These include both primitive and entity types.</span></span>  
  
 <span data-ttu-id="c6617-125">Os tipos de entidade suporte a apenas tipos de entidade no namespace atual.</span><span class="sxs-lookup"><span data-stu-id="c6617-125">Supported entity types refer to only entity types in the current namespace.</span></span> <span data-ttu-id="c6617-126">Não incluem tipos primitivos.</span><span class="sxs-lookup"><span data-stu-id="c6617-126">They do not include primitive types.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c6617-127">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c6617-127">Examples</span></span>  
 <span data-ttu-id="c6617-128">A seguir está um exemplo de uma definição de tipo simples.</span><span class="sxs-lookup"><span data-stu-id="c6617-128">The following is an example of a simple type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 EDM.Decimal) AS (  
   Round(p1)  
)  
MyRound(CAST(1.7 as EDM.Decimal))  
```  
  
 <span data-ttu-id="c6617-129">A seguir está um exemplo de uma definição de tipo de COLEÇÃO.</span><span class="sxs-lookup"><span data-stu-id="c6617-129">The following is an example of a COLLECTION type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Collection(EDM.Decimal)) AS (  
   Select Round(p1) from p1  
)  
MyRound({CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)})  
```  
  
 <span data-ttu-id="c6617-130">A seguir está um exemplo de uma definição de tipo de LINHA.</span><span class="sxs-lookup"><span data-stu-id="c6617-130">The following is an example of a ROW type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function MyRound(p1 Row(x EDM.Decimal)) AS (  
   Round(p1.x)  
)  
select MyRound(row(a as x)) from {CAST(1.7 as EDM.Decimal), CAST(2.7 as EDM.Decimal)} as a  
```  
  
 <span data-ttu-id="c6617-131">A seguir está um exemplo de uma definição de tipo de LINHA.</span><span class="sxs-lookup"><span data-stu-id="c6617-131">The following is an example of a REF type definition.</span></span>  
  
```  
USING Microsoft.Samples.Entity  
Function UnReference(p1 Ref(AdventureWorks.Order)) AS (  
   Deref(p1)  
)  
select Ref(x) from AdventureWorksEntities.SalesOrderHeaders as x  
```  
  
## <a name="see-also"></a><span data-ttu-id="c6617-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6617-132">See also</span></span>

- [<span data-ttu-id="c6617-133">Visão geral da Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c6617-133">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="c6617-134">Referência de Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c6617-134">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
