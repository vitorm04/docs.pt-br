---
title: Implementação de interface explícita – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: 75b031773f8ac34b04f68ec01b12cd9263413bc3
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200137"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="088ce-102">Implementação de interface explícita (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="088ce-102">Explicit Interface Implementation (C# Programming Guide)</span></span>
<span data-ttu-id="088ce-103">Caso uma [classe](../../../csharp/language-reference/keywords/class.md) implemente duas interfaces que contêm um membro com a mesma assinatura, logo, implementar esse membro na classe fará com que as duas interfaces usem tal membro como sua implementação.</span><span class="sxs-lookup"><span data-stu-id="088ce-103">If a [class](../../../csharp/language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="088ce-104">No exemplo a seguir, todas as chamadas para `Paint` invocam o mesmo método.</span><span class="sxs-lookup"><span data-stu-id="088ce-104">In the following example, all the calls to `Paint` invoke the same method.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#39)]  
  
 <span data-ttu-id="088ce-105">No entanto, se os dois membros de [interface](../../../csharp/language-reference/keywords/interface.md) não executarem a mesma função, isso pode levar a uma implementação incorreta de uma ou ambas as interfaces.</span><span class="sxs-lookup"><span data-stu-id="088ce-105">If the two [interface](../../../csharp/language-reference/keywords/interface.md) members do not perform the same function, however, this can lead to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="088ce-106">É possível implementar um membro de interface explicitamente — criando um membro de classe que seja chamado apenas por meio da interface e seja específico para essa interface.</span><span class="sxs-lookup"><span data-stu-id="088ce-106">It is possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="088ce-107">Isso é realizado ao nomear o membro da classe com o nome da interface e um ponto final.</span><span class="sxs-lookup"><span data-stu-id="088ce-107">This is accomplished by naming the class member with the name of the interface and a period.</span></span> <span data-ttu-id="088ce-108">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="088ce-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#40)]  
  
 <span data-ttu-id="088ce-109">O membro da classe `IControl.Paint` está disponível somente por meio da interface `IControl` e `ISurface.Paint` está disponível apenas por meio do `ISurface`.</span><span class="sxs-lookup"><span data-stu-id="088ce-109">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="088ce-110">Ambas as implementações de método são separadas e nenhuma delas está diretamente disponível na classe.</span><span class="sxs-lookup"><span data-stu-id="088ce-110">Both method implementations are separate, and neither is available directly on the class.</span></span> <span data-ttu-id="088ce-111">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="088ce-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#41)]  
  
 <span data-ttu-id="088ce-112">A implementação explícita também é utilizada para resolver casos em que duas interfaces declaram membros diferentes com o mesmo nome, como uma propriedade e um método:</span><span class="sxs-lookup"><span data-stu-id="088ce-112">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#42)]  
  
 <span data-ttu-id="088ce-113">Para implementar as duas interfaces, é necessário que uma classe use a implementação explícita para a propriedade P, o método P ou ambos, a fim de evitar um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="088ce-113">To implement both interfaces, a class has to use explicit implementation either for the property P, or the method P, or both, to avoid a compiler error.</span></span> <span data-ttu-id="088ce-114">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="088ce-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#43](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#43)]  
  
## <a name="see-also"></a><span data-ttu-id="088ce-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="088ce-115">See also</span></span>

- [<span data-ttu-id="088ce-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="088ce-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="088ce-117">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="088ce-117">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="088ce-118">Interfaces</span><span class="sxs-lookup"><span data-stu-id="088ce-118">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
- [<span data-ttu-id="088ce-119">Herança</span><span class="sxs-lookup"><span data-stu-id="088ce-119">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
