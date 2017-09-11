---
title: Criar um grupo aninhado
description: Como criar um grupo aninhado.
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: e9f00708-362e-4d13-98c5-d77549347ba0
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 361ac1f224c6eef292fcf8434c7e465c9448b19c
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="create-a-nested-group"></a><span data-ttu-id="6b319-104">Criar um grupo aninhado</span><span class="sxs-lookup"><span data-stu-id="6b319-104">Create a nested group</span></span>

<span data-ttu-id="6b319-105">O exemplo a seguir mostra como criar grupos aninhados em uma expressão de consulta LINQ.</span><span class="sxs-lookup"><span data-stu-id="6b319-105">The following example shows how to create nested groups in a LINQ query expression.</span></span> <span data-ttu-id="6b319-106">Cada grupo que é criado de acordo com o ano do aluno ou nível de ensino, é subdividido em grupos com base nos nomes das pessoas.</span><span class="sxs-lookup"><span data-stu-id="6b319-106">Each group that is created according to student year or grade level is then further subdivided into groups based on the individuals' names.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b319-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6b319-107">Example</span></span>

 > [!NOTE]
 > <span data-ttu-id="6b319-108">Este exemplo contém referências a objetos que são definidos no código de exemplo em [Consultar uma coleção de objetos](query-a-collection-of-objects.md).</span><span class="sxs-lookup"><span data-stu-id="6b319-108">This example contains references to objects that are defined in the sample code in [Query a collection of objects](query-a-collection-of-objects.md).</span></span> 

 <span data-ttu-id="6b319-109">[!code-cs[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6b319-109">[!code-cs[csProgGuideLINQ#24](../../../samples/snippets/csharp/concepts/linq/how-to-create-a-nested-group_1.cs)]</span></span>  
  
 <span data-ttu-id="6b319-110">Observe que três loops `foreach` aninhados são necessários para iterar sobre os elementos internos de um grupo aninhado.</span><span class="sxs-lookup"><span data-stu-id="6b319-110">Note that three nested `foreach` loops are required to iterate over the inner elements of a nested group.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b319-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6b319-111">See also</span></span>  
 [<span data-ttu-id="6b319-112">Expressões de consulta LINQ</span><span class="sxs-lookup"><span data-stu-id="6b319-112">LINQ Query Expressions</span></span>](index.md)

