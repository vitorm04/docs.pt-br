---
title: Criar um grupo aninhado
description: Como criar um grupo aninhado.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: 232aa46d975d7c338bbc776e3867f2e566601fde
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/18/2017
---
# <a name="create-a-nested-group"></a><span data-ttu-id="bed8b-104">Criar um grupo aninhado</span><span class="sxs-lookup"><span data-stu-id="bed8b-104">Create a nested group</span></span>

<span data-ttu-id="bed8b-105">O exemplo a seguir mostra como criar grupos aninhados em uma expressão de consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="bed8b-105">The following example shows how to create nested groups in a LINQ query expression.</span></span> <span data-ttu-id="bed8b-106">Cada grupo que é criado de acordo com o ano do aluno ou nível de ensino, é subdividido em grupos com base nos nomes das pessoas.</span><span class="sxs-lookup"><span data-stu-id="bed8b-106">Each group that is created according to student year or grade level is then further subdivided into groups based on the individuals' names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bed8b-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bed8b-107">Example</span></span>

 > [!NOTE]
 > <span data-ttu-id="bed8b-108">Este exemplo contém referências a objetos que são definidos no código de exemplo em [Consultar uma coleção de objetos](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="bed8b-108">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span> 

 [!code-csharp[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]  
  
 <span data-ttu-id="bed8b-109">Observe que três loops `foreach` aninhados são necessários para iterar sobre os elementos internos de um grupo aninhado.</span><span class="sxs-lookup"><span data-stu-id="bed8b-109">Note that three nested `foreach` loops are required to iterate over the inner elements of a nested group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bed8b-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bed8b-110">See also</span></span>  
 [<span data-ttu-id="bed8b-111">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="bed8b-111">LINQ Query Expressions</span></span>](index.md)
