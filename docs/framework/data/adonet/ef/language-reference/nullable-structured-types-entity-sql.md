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
ms.workload: dotnet
ms.openlocfilehash: 3f294088e92951e964c3daa2a105b767bca1d288
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="nullable-structured-types-entity-sql"></a><span data-ttu-id="2053c-102">Tipos anuláveis estruturados (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="2053c-102">Nullable Structured Types (Entity SQL)</span></span>
<span data-ttu-id="2053c-103">Uma instância de `null` de um tipo estruturada é uma instância que não existe.</span><span class="sxs-lookup"><span data-stu-id="2053c-103">A `null` instance of a structured type is an instance that does not exist.</span></span> <span data-ttu-id="2053c-104">Isso é diferente de uma instância existente em que todas as propriedades têm valores de `null` .</span><span class="sxs-lookup"><span data-stu-id="2053c-104">This is different from an existing instance in which all properties have `null` values.</span></span>  
  
 <span data-ttu-id="2053c-105">Este tópico descreve os tipos estruturados anulável, incluindo que os tipos são anulável e que os padrões de código gerenciar instâncias de `null` de tipos anuláveis estruturados.</span><span class="sxs-lookup"><span data-stu-id="2053c-105">This topic describes the nullable structured types, including which types are nullable and which code patterns produce `null` instances of structured nullable types.</span></span>  
  
## <a name="kinds-of-nullable-structured-types"></a><span data-ttu-id="2053c-106">Tipos de tipos estruturados anulável</span><span class="sxs-lookup"><span data-stu-id="2053c-106">Kinds of Nullable Structured Types</span></span>  
 <span data-ttu-id="2053c-107">Existem três tipos de tipos anuláveis de framework:</span><span class="sxs-lookup"><span data-stu-id="2053c-107">There are three kinds of nullable structure types:</span></span>  
  
-   <span data-ttu-id="2053c-108">Tipos de linha.</span><span class="sxs-lookup"><span data-stu-id="2053c-108">Row types.</span></span>  
  
-   <span data-ttu-id="2053c-109">Tipos complexos.</span><span class="sxs-lookup"><span data-stu-id="2053c-109">Complex types.</span></span>  
  
-   <span data-ttu-id="2053c-110">Tipos de entidade.</span><span class="sxs-lookup"><span data-stu-id="2053c-110">Entity types.</span></span>  
  
## <a name="code-patterns-that-produce-null-instances-of-structured-types"></a><span data-ttu-id="2053c-111">Os padrões de código que gerenciar instâncias nulos Structured tipo</span><span class="sxs-lookup"><span data-stu-id="2053c-111">Code Patterns that Produce Null Instances of Structured Types</span></span>  
 <span data-ttu-id="2053c-112">Os seguintes cenários gerenciar instâncias de `null` :</span><span class="sxs-lookup"><span data-stu-id="2053c-112">The following scenarios produce `null` instances:</span></span>  
  
-   <span data-ttu-id="2053c-113">Na forma `null` como um tipo estruturada:</span><span class="sxs-lookup"><span data-stu-id="2053c-113">Shaping `null` as a structured type:</span></span>  
  
    ```  
    TREAT (NULL AS StructuredType)  
    ```  
  
-   <span data-ttu-id="2053c-114">Upcasting de um tipo base para um tipo derivado:</span><span class="sxs-lookup"><span data-stu-id="2053c-114">Upcasting of a base type to a derived type:</span></span>  
  
    ```  
    TREAT (BaseType AS DerivedType)  
    ```  
  
-   <span data-ttu-id="2053c-115">Externo join à condição falsa:</span><span class="sxs-lookup"><span data-stu-id="2053c-115">Outer join on false condition:</span></span>  
  
    ```  
    Collection1 LEFT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="2053c-116">--ou</span><span class="sxs-lookup"><span data-stu-id="2053c-116">--or</span></span>  
  
    ```  
    Collection1 RIGHT OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
     <span data-ttu-id="2053c-117">--ou</span><span class="sxs-lookup"><span data-stu-id="2053c-117">--or</span></span>  
  
    ```  
    Collection1 FULL OUTER JOIN Collection2  
    ON FalseCondition  
    ```  
  
-   <span data-ttu-id="2053c-118">Desreferenciando uma referência de `null` :</span><span class="sxs-lookup"><span data-stu-id="2053c-118">Dereferencing a `null` reference:</span></span>  
  
    ```  
    DEREF(NullRef)  
    ```  
  
-   <span data-ttu-id="2053c-119">Obtendo ANYELEMENT de uma coleção vazia:</span><span class="sxs-lookup"><span data-stu-id="2053c-119">Obtaining ANYELEMENT from an empty collection:</span></span>  
  
    ```  
    ANYELEMENT(EmptyCollection)  
    ```  
  
-   <span data-ttu-id="2053c-120">Verificar instâncias de `null` de tipos estruturados:</span><span class="sxs-lookup"><span data-stu-id="2053c-120">Checking for `null` instances of structured types:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2053c-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2053c-121">See Also</span></span>  
 [<span data-ttu-id="2053c-122">Visão geral do Entity SQL</span><span class="sxs-lookup"><span data-stu-id="2053c-122">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
