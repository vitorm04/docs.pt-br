---
title: "Executar junções externas esquerdas"
description: "Como executar junções externas esquerdas."
keywords: .NET, .NET Core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: d81f6e9df228dc6eec985253f53b70a95493ed42
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="perform-left-outer-joins"></a><span data-ttu-id="2d628-104">Executar junções externas esquerdas</span><span class="sxs-lookup"><span data-stu-id="2d628-104">Perform left outer joins</span></span>
<span data-ttu-id="2d628-105">Uma junção externa esquerda é uma junção em que cada elemento da primeira coleção é retornado, mesmo que ele tenha elementos correlacionados na segunda coleção.</span><span class="sxs-lookup"><span data-stu-id="2d628-105">A left outer join is a join in which each element of the first collection is returned, regardless of whether it has any correlated elements in the second collection.</span></span> <span data-ttu-id="2d628-106">É possível usar o LINQ para executar uma junção externa esquerda chamando o método <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> nos resultados de uma junção de grupo.</span><span class="sxs-lookup"><span data-stu-id="2d628-106">You can use LINQ to perform a left outer join by calling the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d628-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2d628-107">Example</span></span>  
 <span data-ttu-id="2d628-108">O exemplo a seguir demonstra como usar o método <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> nos resultados de uma junção de grupo para executar uma junção externa esquerda.</span><span class="sxs-lookup"><span data-stu-id="2d628-108">The following example demonstrates how to use the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join to perform a left outer join.</span></span>  
  
 <span data-ttu-id="2d628-109">A primeira etapa da produção de uma junção externa esquerda de duas coleções é executar uma junção interna usando uma junção de grupo.</span><span class="sxs-lookup"><span data-stu-id="2d628-109">The first step in producing a left outer join of two collections is to perform an inner join by using a group join.</span></span> <span data-ttu-id="2d628-110">(Consulte [Executar junções internas](perform-inner-joins.md) para obter uma explicação desse processo.) Neste exemplo, a lista de objetos `Person` é associada internamente à lista de objetos `Pet` com base em um objeto `Person` correspondente a `Pet.Owner`.</span><span class="sxs-lookup"><span data-stu-id="2d628-110">(See [Perform inner joins](perform-inner-joins.md) for an explanation of this process.) In this example, the list of `Person` objects is inner-joined to the list of `Pet` objects based on a `Person` object that matches `Pet.Owner`.</span></span>  
  
 <span data-ttu-id="2d628-111">A segunda etapa é incluir cada elemento da primeira coleção (esquerda) no conjunto de resultados, mesmo que esse elemento não tenha nenhuma correspondência na coleção direita.</span><span class="sxs-lookup"><span data-stu-id="2d628-111">The second step is to include each element of the first (left) collection in the result set even if that element has no matches in the right collection.</span></span> <span data-ttu-id="2d628-112">Isso é feito chamando <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> em cada sequência de elementos correspondentes da junção de grupo.</span><span class="sxs-lookup"><span data-stu-id="2d628-112">This is accomplished by calling <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> on each sequence of matching elements from the group join.</span></span> <span data-ttu-id="2d628-113">Neste exemplo, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> é chamado em cada sequência de objetos `Pet` correspondentes.</span><span class="sxs-lookup"><span data-stu-id="2d628-113">In this example, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> is called on each sequence of matching `Pet` objects.</span></span> <span data-ttu-id="2d628-114">O método retorna uma coleção que contém um valor padrão único se a sequência de objetos `Pet` correspondentes estiver vazia para qualquer objeto `Person`, garantindo assim que cada objeto `Person` seja representado no conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="2d628-114">The method returns a collection that contains a single, default value if the sequence of matching `Pet` objects is empty for any `Person` object, thereby ensuring that each `Person` object is represented in the result collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d628-115">O valor padrão para um tipo de referência é `null`; portanto, o exemplo procura uma referência nula antes de acessar cada elemento de cada coleção `Pet`.</span><span class="sxs-lookup"><span data-stu-id="2d628-115">The default value for a reference type is `null`; therefore, the example checks for a null reference before accessing each element of each `Pet` collection.</span></span>  
  
 <span data-ttu-id="2d628-116">[!code-cs[CsLINQProgJoining#7](../../../samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="2d628-116">[!code-cs[CsLINQProgJoining#7](../../../samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]</span></span>  
 
## <a name="see-also"></a><span data-ttu-id="2d628-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2d628-117">See also</span></span>  
 <span data-ttu-id="2d628-118"><xref:System.Linq.Enumerable.Join%2A></span><span class="sxs-lookup"><span data-stu-id="2d628-118"><xref:System.Linq.Enumerable.Join%2A></span></span>   
 <span data-ttu-id="2d628-119"><xref:System.Linq.Enumerable.GroupJoin%2A></span><span class="sxs-lookup"><span data-stu-id="2d628-119"><xref:System.Linq.Enumerable.GroupJoin%2A></span></span>   
 <span data-ttu-id="2d628-120">[Executar junções internas](perform-inner-joins.md) </span><span class="sxs-lookup"><span data-stu-id="2d628-120">[Perform inner joins](perform-inner-joins.md) </span></span>  
 <span data-ttu-id="2d628-121">[Executar junções agrupadas](perform-grouped-joins.md) </span><span class="sxs-lookup"><span data-stu-id="2d628-121">[Perform grouped joins](perform-grouped-joins.md) </span></span>  
 [<span data-ttu-id="2d628-122">Tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="2d628-122">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)   
 

