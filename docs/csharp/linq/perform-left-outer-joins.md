---
title: Executar junções externas esquerdas (LINQ em C#)
description: Saiba como executar junções externas esquerdas usando o LINQ em C#.
ms.date: 12/1/2016
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: 329fe9e17640931c5eb39b33b791a7a77a6f7b89
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506590"
---
# <a name="perform-left-outer-joins"></a><span data-ttu-id="e2d27-103">Executar junções externas esquerdas</span><span class="sxs-lookup"><span data-stu-id="e2d27-103">Perform left outer joins</span></span>

<span data-ttu-id="e2d27-104">Uma junção externa esquerda é uma junção em que cada elemento da primeira coleção é retornado, mesmo que ele tenha elementos correlacionados na segunda coleção.</span><span class="sxs-lookup"><span data-stu-id="e2d27-104">A left outer join is a join in which each element of the first collection is returned, regardless of whether it has any correlated elements in the second collection.</span></span> <span data-ttu-id="e2d27-105">É possível usar o LINQ para executar uma junção externa esquerda chamando o método <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> nos resultados de uma junção de grupo.</span><span class="sxs-lookup"><span data-stu-id="e2d27-105">You can use LINQ to perform a left outer join by calling the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join.</span></span>

## <a name="example"></a><span data-ttu-id="e2d27-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e2d27-106">Example</span></span>

<span data-ttu-id="e2d27-107">O exemplo a seguir demonstra como usar o método <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> nos resultados de uma junção de grupo para executar uma junção externa esquerda.</span><span class="sxs-lookup"><span data-stu-id="e2d27-107">The following example demonstrates how to use the <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> method on the results of a group join to perform a left outer join.</span></span>

<span data-ttu-id="e2d27-108">A primeira etapa da produção de uma junção externa esquerda de duas coleções é executar uma junção interna usando uma junção de grupo.</span><span class="sxs-lookup"><span data-stu-id="e2d27-108">The first step in producing a left outer join of two collections is to perform an inner join by using a group join.</span></span> <span data-ttu-id="e2d27-109">(Consulte [Executar junções internas](perform-inner-joins.md) para obter uma explicação desse processo.) Neste exemplo, a lista de objetos `Person` é associada internamente à lista de objetos `Pet` com base em um objeto `Person` correspondente a `Pet.Owner`.</span><span class="sxs-lookup"><span data-stu-id="e2d27-109">(See [Perform inner joins](perform-inner-joins.md) for an explanation of this process.) In this example, the list of `Person` objects is inner-joined to the list of `Pet` objects based on a `Person` object that matches `Pet.Owner`.</span></span>

<span data-ttu-id="e2d27-110">A segunda etapa é incluir cada elemento da primeira coleção (esquerda) no conjunto de resultados, mesmo que esse elemento não tenha nenhuma correspondência na coleção direita.</span><span class="sxs-lookup"><span data-stu-id="e2d27-110">The second step is to include each element of the first (left) collection in the result set even if that element has no matches in the right collection.</span></span> <span data-ttu-id="e2d27-111">Isso é feito chamando <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> em cada sequência de elementos correspondentes da junção de grupo.</span><span class="sxs-lookup"><span data-stu-id="e2d27-111">This is accomplished by calling <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> on each sequence of matching elements from the group join.</span></span> <span data-ttu-id="e2d27-112">Neste exemplo, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> é chamado em cada sequência de objetos `Pet` correspondentes.</span><span class="sxs-lookup"><span data-stu-id="e2d27-112">In this example, <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> is called on each sequence of matching `Pet` objects.</span></span> <span data-ttu-id="e2d27-113">O método retorna uma coleção que contém um valor padrão único se a sequência de objetos `Pet` correspondentes estiver vazia para qualquer objeto `Person`, garantindo assim que cada objeto `Person` seja representado no conjunto de resultados.</span><span class="sxs-lookup"><span data-stu-id="e2d27-113">The method returns a collection that contains a single, default value if the sequence of matching `Pet` objects is empty for any `Person` object, thereby ensuring that each `Person` object is represented in the result collection.</span></span>

> [!NOTE]
> <span data-ttu-id="e2d27-114">O valor padrão para um tipo de referência é `null`; portanto, o exemplo procura uma referência nula antes de acessar cada elemento de cada coleção `Pet`.</span><span class="sxs-lookup"><span data-stu-id="e2d27-114">The default value for a reference type is `null`; therefore, the example checks for a null reference before accessing each element of each `Pet` collection.</span></span>

[!code-csharp[CsLINQProgJoining#7](~/samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]

## <a name="see-also"></a><span data-ttu-id="e2d27-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2d27-115">See also</span></span>

- <xref:System.Linq.Enumerable.Join%2A>  
- <xref:System.Linq.Enumerable.GroupJoin%2A>  
- [<span data-ttu-id="e2d27-116">Executar junções internas</span><span class="sxs-lookup"><span data-stu-id="e2d27-116">Perform inner joins</span></span>](perform-inner-joins.md)  
- [<span data-ttu-id="e2d27-117">Executar junções agrupadas</span><span class="sxs-lookup"><span data-stu-id="e2d27-117">Perform grouped joins</span></span>](perform-grouped-joins.md)  
- [<span data-ttu-id="e2d27-118">Tipos anônimos</span><span class="sxs-lookup"><span data-stu-id="e2d27-118">Anonymous types</span></span>](../programming-guide/classes-and-structs/anonymous-types.md)  