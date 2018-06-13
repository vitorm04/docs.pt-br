---
title: Implementação de interface explícita (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- explicit interfaces [C#]
- interfaces [C#], explicit
ms.assetid: 181c901f-0d4c-4f29-97fc-895079617bf2
ms.openlocfilehash: 7494f7d6a3897d56419f9d3aa96668fd9dab5f35
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331585"
---
# <a name="explicit-interface-implementation-c-programming-guide"></a><span data-ttu-id="850cf-102">Implementação de interface explícita (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="850cf-102">Explicit Interface Implementation (C# Programming Guide)</span></span>
<span data-ttu-id="850cf-103">Caso uma [classe](../../../csharp/language-reference/keywords/class.md) implemente duas interfaces que contêm um membro com a mesma assinatura, logo, implementar esse membro na classe fará com que as duas interfaces usem tal membro como sua implementação.</span><span class="sxs-lookup"><span data-stu-id="850cf-103">If a [class](../../../csharp/language-reference/keywords/class.md) implements two interfaces that contain a member with the same signature, then implementing that member on the class will cause both interfaces to use that member as their implementation.</span></span> <span data-ttu-id="850cf-104">No exemplo a seguir, todas as chamadas para `Paint` invocam o mesmo método.</span><span class="sxs-lookup"><span data-stu-id="850cf-104">In the following example, all the calls to `Paint` invoke the same method.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#39](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_1.cs)]  
  
 <span data-ttu-id="850cf-105">No entanto, se os dois membros de [interface](../../../csharp/language-reference/keywords/interface.md) não executarem a mesma função, isso pode levar a uma implementação incorreta de uma ou ambas as interfaces.</span><span class="sxs-lookup"><span data-stu-id="850cf-105">If the two [interface](../../../csharp/language-reference/keywords/interface.md) members do not perform the same function, however, this can lead to an incorrect implementation of one or both of the interfaces.</span></span> <span data-ttu-id="850cf-106">É possível implementar um membro de interface explicitamente — criando um membro de classe que seja chamado apenas por meio da interface e seja específico para essa interface.</span><span class="sxs-lookup"><span data-stu-id="850cf-106">It is possible to implement an interface member explicitly—creating a class member that is only called through the interface, and is specific to that interface.</span></span> <span data-ttu-id="850cf-107">Isso é realizado ao nomear o membro da classe com o nome da interface e um ponto final.</span><span class="sxs-lookup"><span data-stu-id="850cf-107">This is accomplished by naming the class member with the name of the interface and a period.</span></span> <span data-ttu-id="850cf-108">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="850cf-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_2.cs)]  
  
 <span data-ttu-id="850cf-109">O membro da classe `IControl.Paint` está disponível somente por meio da interface `IControl` e `ISurface.Paint` está disponível apenas por meio do `ISurface`.</span><span class="sxs-lookup"><span data-stu-id="850cf-109">The class member `IControl.Paint` is only available through the `IControl` interface, and `ISurface.Paint` is only available through `ISurface`.</span></span> <span data-ttu-id="850cf-110">Ambas as implementações de método são separadas e nenhuma delas está diretamente disponível na classe.</span><span class="sxs-lookup"><span data-stu-id="850cf-110">Both method implementations are separate, and neither is available directly on the class.</span></span> <span data-ttu-id="850cf-111">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="850cf-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_3.cs)]  
  
 <span data-ttu-id="850cf-112">A implementação explícita também é utilizada para resolver casos em que duas interfaces declaram membros diferentes com o mesmo nome, como uma propriedade e um método:</span><span class="sxs-lookup"><span data-stu-id="850cf-112">Explicit implementation is also used to resolve cases where two interfaces each declare different members of the same name such as a property and a method:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_4.cs)]  
  
 <span data-ttu-id="850cf-113">Para implementar as duas interfaces, é necessário que uma classe use a implementação explícita para a propriedade P, o método P ou ambos, a fim de evitar um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="850cf-113">To implement both interfaces, a class has to use explicit implementation either for the property P, or the method P, or both, to avoid a compiler error.</span></span> <span data-ttu-id="850cf-114">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="850cf-114">For example:</span></span>  
  
 [!code-csharp[csProgGuideInheritance#43](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/explicit-interface-implementation_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="850cf-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="850cf-115">See Also</span></span>  
 [<span data-ttu-id="850cf-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="850cf-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="850cf-117">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="850cf-117">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="850cf-118">Interfaces</span><span class="sxs-lookup"><span data-stu-id="850cf-118">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)  
 [<span data-ttu-id="850cf-119">Herança</span><span class="sxs-lookup"><span data-stu-id="850cf-119">Inheritance</span></span>](../../../csharp/programming-guide/classes-and-structs/inheritance.md)
