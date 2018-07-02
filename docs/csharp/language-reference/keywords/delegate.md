---
title: delegate (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- delegate_CSharpKeyword
- delegate
- CS0123
helpviewer_keywords:
- delegate keyword [C#]
- function pointers [C#]
ms.assetid: 0bb8cb6d-2f87-47c7-9d1f-d65c1cd01e9f
ms.openlocfilehash: ba1cfdcc56b3d2301a07ffa4af793e7002da21bb
ms.sourcegitcommit: ed7b4b9b77d35e94a35a2634e8c874f46603fb2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36948417"
---
# <a name="delegate-c-reference"></a><span data-ttu-id="e1544-102">delegate (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e1544-102">delegate (C# Reference)</span></span>

<span data-ttu-id="e1544-103">A declaração de um tipo de delegado é semelhante a uma assinatura de método.</span><span class="sxs-lookup"><span data-stu-id="e1544-103">The declaration of a delegate type is similar to a method signature.</span></span> <span data-ttu-id="e1544-104">Ela tem um valor retornado e parâmetros de qualquer tipo:</span><span class="sxs-lookup"><span data-stu-id="e1544-104">It has a return value and any number of parameters of any type:</span></span>

```csharp
public delegate void TestDelegate(string message);
public delegate int TestDelegate(MyType m, long num);
```

<span data-ttu-id="e1544-105">Um `delegate` é um tipo de referência que pode ser usado para encapsular um método nomeado ou anônimo.</span><span class="sxs-lookup"><span data-stu-id="e1544-105">A `delegate` is a reference type that can be used to encapsulate a named or an anonymous method.</span></span> <span data-ttu-id="e1544-106">Representantes são semelhantes a ponteiros de função em C++. No entanto, os representantes são fortemente tipados e seguros.</span><span class="sxs-lookup"><span data-stu-id="e1544-106">Delegates are similar to function pointers in C++; however, delegates are type-safe and secure.</span></span> <span data-ttu-id="e1544-107">Para aplicativos de representantes, consulte [Representantes](../../../csharp/programming-guide/delegates/index.md) e [Representantes genéricos](../../../csharp/programming-guide/generics/generic-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="e1544-107">For applications of delegates, see [Delegates](../../../csharp/programming-guide/delegates/index.md) and [Generic Delegates](../../../csharp/programming-guide/generics/generic-delegates.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="e1544-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="e1544-108">Remarks</span></span>

<span data-ttu-id="e1544-109">Os representantes são a base dos [Eventos](../../../csharp/programming-guide/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="e1544-109">Delegates are the basis for [Events](../../../csharp/programming-guide/events/index.md).</span></span>

<span data-ttu-id="e1544-110">Um delegado pode ser instanciado associando-o a um método nomeado ou anônimo.</span><span class="sxs-lookup"><span data-stu-id="e1544-110">A delegate can be instantiated by associating it either with a named or anonymous method.</span></span> <span data-ttu-id="e1544-111">Para obter mais informações, consulte [Métodos anônimos](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) e [Métodos nomeados](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="e1544-111">For more information, see [Named Methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md) and [Anonymous Methods](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md).</span></span>

<span data-ttu-id="e1544-112">O delegado deve ser instanciado com um método ou expressão lambda que tenha um tipo de retorno compatível e parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="e1544-112">The delegate must be instantiated with a method or lambda expression that has a compatible return type and input parameters.</span></span> <span data-ttu-id="e1544-113">Para obter mais informações sobre o grau de variação permitido na assinatura do método, consulte [Variação em representantes](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="e1544-113">For more information on the degree of variance that is allowed in the method signature, see [Variance in Delegates](../../programming-guide/concepts/covariance-contravariance/using-variance-in-delegates.md).</span></span> <span data-ttu-id="e1544-114">Para uso com métodos anônimos, o delegado e o código a ser associado a ele são declarados juntos.</span><span class="sxs-lookup"><span data-stu-id="e1544-114">For use with anonymous methods, the delegate and the code to be associated with it are declared together.</span></span> <span data-ttu-id="e1544-115">As duas formas de instanciar representantes são discutidas nesta seção.</span><span class="sxs-lookup"><span data-stu-id="e1544-115">Both ways of instantiating delegates are discussed in this section.</span></span>

## <a name="example"></a><span data-ttu-id="e1544-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1544-116">Example</span></span>

[!code-csharp[csrefKeywordsTypes#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#8)]

## <a name="c-language-specification"></a><span data-ttu-id="e1544-117">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e1544-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e1544-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1544-118">See also</span></span>

[<span data-ttu-id="e1544-119">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e1544-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
[<span data-ttu-id="e1544-120">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e1544-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
[<span data-ttu-id="e1544-121">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="e1544-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
[<span data-ttu-id="e1544-122">Tipos de referência</span><span class="sxs-lookup"><span data-stu-id="e1544-122">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
[<span data-ttu-id="e1544-123">Delegados</span><span class="sxs-lookup"><span data-stu-id="e1544-123">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
[<span data-ttu-id="e1544-124">Eventos</span><span class="sxs-lookup"><span data-stu-id="e1544-124">Events</span></span>](../../../csharp/programming-guide/events/index.md)  
[<span data-ttu-id="e1544-125">Delegados com métodos nomeados vs. métodos anônimos</span><span class="sxs-lookup"><span data-stu-id="e1544-125">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)  
[<span data-ttu-id="e1544-126">Métodos anônimos</span><span class="sxs-lookup"><span data-stu-id="e1544-126">Anonymous Methods</span></span>](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)
