---
title: "Tipos anuláveis estruturados (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae006fa9-997e-45bb-8a04-a7f62026171e
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ac7405aea459d51154ac25171bc76d637a94bf81
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="232d5-102">Tipos anuláveis estruturados (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="232d5-102">Nullable Structured Types (Entity SQL)</span></span>
<span data-ttu-id="232d5-103">Uma instância de `null` de um tipo estruturada é uma instância que não existe.</span><span class="sxs-lookup"><span data-stu-id="232d5-103">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="232d5-104">Isso é diferente de uma instância existente em que todas as propriedades têm valores de `null` .</span><span class="sxs-lookup"><span data-stu-id="232d5-104">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="232d5-105">Este tópico descreve os tipos estruturados anulável, incluindo que os tipos são anulável e que os padrões de código gerenciar instâncias de `null` de tipos anuláveis estruturados.</span><span class="sxs-lookup"><span data-stu-id="232d5-105">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="232d5-106">Tipos de tipos estruturados anulável</span><span class="sxs-lookup"><span data-stu-id="232d5-106">Kinds of Nullable Structured Types</span></span>  
 <span data-ttu-id="232d5-107">Existem três tipos de tipos anuláveis de framework:</span><span class="sxs-lookup"><span data-stu-id="232d5-107">There are three kinds of nullable structure types:</span></span>  
  
-   <span data-ttu-id="232d5-108">Tipos de linha.</span><span class="sxs-lookup"><span data-stu-id="232d5-108">Row types.</span></span>  
  
-   <span data-ttu-id="232d5-109">Tipos complexos.</span><span class="sxs-lookup"><span data-stu-id="232d5-109">Complex types.</span></span>  
  
-   <span data-ttu-id="232d5-110">Tipos de entidade.</span><span class="sxs-lookup"><span data-stu-id="232d5-110">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="232d5-111">Os padrões de código que gerenciar instâncias nulos Structured tipo</span><span class="sxs-lookup"><span data-stu-id="232d5-111">Code Patterns that Produce Null Instances of Structured Types</span></span>  
 <span data-ttu-id="232d5-112">Os seguintes cenários gerenciar instâncias de `null` :</span><span class="sxs-lookup"><span data-stu-id="232d5-112">The following scenarios produce `null` instances:</span></span>  
  
-   <span data-ttu-id="232d5-113">Na forma `null` como um tipo estruturada:</span><span class="sxs-lookup"><span data-stu-id="232d5-113">Shaping `null` as a structured type:</span></span>  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
-   <span data-ttu-id="232d5-114">Upcasting de um tipo base para um tipo derivado:</span><span class="sxs-lookup"><span data-stu-id="232d5-114">Upcasting of a base type to a derived type:</span></span>  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
-   <span data-ttu-id="232d5-115">Externo join à condição falsa:</span><span class="sxs-lookup"><span data-stu-id="232d5-115">Outer join on false condition:</span></span>  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="232d5-116">--ou</span><span class="sxs-lookup"><span data-stu-id="232d5-116">--or</span></span>  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="232d5-117">--ou</span><span class="sxs-lookup"><span data-stu-id="232d5-117">--or</span></span>  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
-   <span data-ttu-id="232d5-118">Desreferenciando uma referência de `null` :</span><span class="sxs-lookup"><span data-stu-id="232d5-118">Dereferencing a `null` reference:</span></span>  
  
    ```  
    DEREF(NullRef)  
    ```  
  
-   <span data-ttu-id="232d5-119">Obtendo ANYELEMENT de uma coleção vazia:</span><span class="sxs-lookup"><span data-stu-id="232d5-119">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
-   <span data-ttu-id="232d5-120">Verificar instâncias de `null` de tipos estruturados:</span><span class="sxs-lookup"><span data-stu-id="232d5-120">Checking for `null` instances of structured types:</span></span>  
  
    ```csharp  
    ...  
    for (int i = 0; i < reader.FieldCount; i++)  
    {  
        if (reader.IsDBNull(i))  
        {  
            Console.WriteLine("[NULL]");  
        }  
        else  
        {  
            Console.WriteLine(reader.GetValue(i).ToString());  
        }  
    }  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="232d5-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="232d5-121">See Also</span></span>  
 [<span data-ttu-id="232d5-122">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="232d5-122">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
