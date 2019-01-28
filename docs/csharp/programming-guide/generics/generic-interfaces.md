---
title: Interfaces genéricas – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generic interfaces
- generics [C#], interfaces
ms.assetid: a8fa49a1-6e78-4a09-87e5-84a0b9f5ffbe
ms.openlocfilehash: d0b9d35a7e814d8790ee57f1169f2b35f7c42536
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564205"
---
# <a name="generic-interfaces-c-programming-guide"></a><span data-ttu-id="9a312-102">Interfaces genéricas (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="9a312-102">Generic Interfaces (C# Programming Guide)</span></span>
<span data-ttu-id="9a312-103">Muitas vezes, é útil definir interfaces para classes de coleção genéricas ou para as classe genéricas que representam itens na coleção.</span><span class="sxs-lookup"><span data-stu-id="9a312-103">It is often useful to define interfaces either for generic collection classes, or for the generic classes that represent items in the collection.</span></span> <span data-ttu-id="9a312-104">Para classes genéricas, prefere-se usar interfaces genéricas, como <xref:System.IComparable%601> em vez de <xref:System.IComparable>, a fim de evitar operações de conversão boxing e unboxing em tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="9a312-104">The preference for generic classes is to use generic interfaces, such as <xref:System.IComparable%601> rather than <xref:System.IComparable>, in order to avoid boxing and unboxing operations on value types.</span></span> <span data-ttu-id="9a312-105">A biblioteca de classes .NET Framework define várias interfaces genéricas para uso com as classes de coleção no namespace <xref:System.Collections.Generic>.</span><span class="sxs-lookup"><span data-stu-id="9a312-105">The .NET Framework class library defines several generic interfaces for use with the collection classes in the <xref:System.Collections.Generic> namespace.</span></span>  
  
 <span data-ttu-id="9a312-106">Quando uma interface é especificada como uma restrição em um parâmetro de tipo, somente os tipos que implementam a interface podem ser usados.</span><span class="sxs-lookup"><span data-stu-id="9a312-106">When an interface is specified as a constraint on a type parameter, only types that implement the interface can be used.</span></span> <span data-ttu-id="9a312-107">O exemplo de código a seguir mostra uma classe `SortedList<T>` que deriva da classe `GenericList<T>`.</span><span class="sxs-lookup"><span data-stu-id="9a312-107">The following code example shows a `SortedList<T>` class that derives from the `GenericList<T>` class.</span></span> <span data-ttu-id="9a312-108">Para obter mais informações, consulte [Introdução aos Genéricos](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span><span class="sxs-lookup"><span data-stu-id="9a312-108">For more information, see [Introduction to Generics](../../../csharp/programming-guide/generics/introduction-to-generics.md).</span></span> <span data-ttu-id="9a312-109">`SortedList<T>` adiciona a restrição `where T : IComparable<T>`.</span><span class="sxs-lookup"><span data-stu-id="9a312-109">`SortedList<T>` adds the constraint `where T : IComparable<T>`.</span></span> <span data-ttu-id="9a312-110">Isso habilita o método `BubbleSort` em `SortedList<T>` a usar o método genérico <xref:System.IComparable%601.CompareTo%2A> em elementos de lista.</span><span class="sxs-lookup"><span data-stu-id="9a312-110">This enables the `BubbleSort` method in `SortedList<T>` to use the generic <xref:System.IComparable%601.CompareTo%2A> method on list elements.</span></span> <span data-ttu-id="9a312-111">Neste exemplo, os elementos de lista são uma classe simples, `Person`, que implementa `IComparable<Person>`.</span><span class="sxs-lookup"><span data-stu-id="9a312-111">In this example, list elements are a simple class, `Person`, that implements `IComparable<Person>`.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#29](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_1.cs)]  
  
 <span data-ttu-id="9a312-112">Várias interfaces podem ser especificadas como restrições em um único tipo, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9a312-112">Multiple interfaces can be specified as constraints on a single type, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#30](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_2.cs)]  
  
 <span data-ttu-id="9a312-113">Uma interface pode definir mais de um parâmetro de tipo, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9a312-113">An interface can define more than one type parameter, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#31](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_3.cs)]  
  
 <span data-ttu-id="9a312-114">As regras de herança que se aplicam às classes também se aplicam às interfaces:</span><span class="sxs-lookup"><span data-stu-id="9a312-114">The rules of inheritance that apply to classes also apply to interfaces:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#32](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_4.cs)]  
  
 <span data-ttu-id="9a312-115">Interfaces genéricas poderão herdar de interfaces não genéricas se a interface genérica for contravariante, o que significa que ela usa apenas seu parâmetro de tipo como um valor retornado.</span><span class="sxs-lookup"><span data-stu-id="9a312-115">Generic interfaces can inherit from non-generic interfaces if the generic interface is contravariant, which means it only uses its type parameter as a return value.</span></span> <span data-ttu-id="9a312-116">Na biblioteca de classes do .NET Framework, <xref:System.Collections.Generic.IEnumerable%601> herda de <xref:System.Collections.IEnumerable> porque <xref:System.Collections.Generic.IEnumerable%601> usa apenas `T` no valor retornado de <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> e no getter de propriedade <xref:System.Collections.Generic.IEnumerator%601.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="9a312-116">In the .NET Framework class library, <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable> because <xref:System.Collections.Generic.IEnumerable%601> only uses `T` in the return value of <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> and in the <xref:System.Collections.Generic.IEnumerator%601.Current%2A> property getter.</span></span>  
  
 <span data-ttu-id="9a312-117">Classes concretas podem implementar interfaces construídas fechadas, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9a312-117">Concrete classes can implement closed constructed interfaces, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#33](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_5.cs)]  
  
 <span data-ttu-id="9a312-118">Classes genéricas podem implementar interfaces genéricas ou interfaces construídas fechadas, contanto que a lista de parâmetros de classe forneça todos os argumentos exigidos pela interface, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="9a312-118">Generic classes can implement generic interfaces or closed constructed interfaces as long as the class parameter list supplies all arguments required by the interface, as follows:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#34](../../../csharp/programming-guide/generics/codesnippet/CSharp/generic-interfaces_6.cs)]  
  
 <span data-ttu-id="9a312-119">As regras que controlam a sobrecarga de método são as mesmas para métodos em classes genéricas, structs genéricos ou interfaces genéricas.</span><span class="sxs-lookup"><span data-stu-id="9a312-119">The rules that control method overloading are the same for methods within generic classes, generic structs, or generic interfaces.</span></span> <span data-ttu-id="9a312-120">Para obter mais informações, consulte [Métodos Genéricos](../../../csharp/programming-guide/generics/generic-methods.md).</span><span class="sxs-lookup"><span data-stu-id="9a312-120">For more information, see [Generic Methods](../../../csharp/programming-guide/generics/generic-methods.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a312-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a312-121">See also</span></span>

- [<span data-ttu-id="9a312-122">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="9a312-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="9a312-123">Introdução aos genéricos</span><span class="sxs-lookup"><span data-stu-id="9a312-123">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)
- [<span data-ttu-id="9a312-124">interface</span><span class="sxs-lookup"><span data-stu-id="9a312-124">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)
- [<span data-ttu-id="9a312-125">Genéricos</span><span class="sxs-lookup"><span data-stu-id="9a312-125">Generics</span></span>](~/docs/standard/generics/index.md)
