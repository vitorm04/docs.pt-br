---
title: Criar um grupo aninhado
description: Como criar um grupo aninhado.
ms.date: 12/1/2016
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.openlocfilehash: dd1158bfa1456342fe8967aed5e02ecebae591c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273137"
---
# <a name="create-a-nested-group"></a><span data-ttu-id="ffcf1-103">Criar um grupo aninhado</span><span class="sxs-lookup"><span data-stu-id="ffcf1-103">Create a nested group</span></span>

<span data-ttu-id="ffcf1-104">O exemplo a seguir mostra como criar grupos aninhados em uma expressão de consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="ffcf1-104">The following example shows how to create nested groups in a LINQ query expression.</span></span> <span data-ttu-id="ffcf1-105">Cada grupo que é criado de acordo com o ano do aluno ou nível de ensino, é subdividido em grupos com base nos nomes das pessoas.</span><span class="sxs-lookup"><span data-stu-id="ffcf1-105">Each group that is created according to student year or grade level is then further subdivided into groups based on the individuals' names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffcf1-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ffcf1-106">Example</span></span>

 > [!NOTE]
 > <span data-ttu-id="ffcf1-107">Este exemplo contém referências a objetos que são definidos no código de exemplo em [Consultar uma coleção de objetos](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="ffcf1-107">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span> 

 [!code-csharp[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]  
  
 <span data-ttu-id="ffcf1-108">Observe que três loops `foreach` aninhados são necessários para iterar sobre os elementos internos de um grupo aninhado.</span><span class="sxs-lookup"><span data-stu-id="ffcf1-108">Note that three nested `foreach` loops are required to iterate over the inner elements of a nested group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ffcf1-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ffcf1-109">See also</span></span>  
 [<span data-ttu-id="ffcf1-110">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="ffcf1-110">LINQ Query Expressions</span></span>](index.md)
