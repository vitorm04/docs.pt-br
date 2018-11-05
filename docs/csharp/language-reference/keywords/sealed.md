---
title: Modificador sealed (referência do C#)
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: cf6b85e2a04870b454b3bfea4d534680d22da8d1
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188580"
---
# <a name="sealed-c-reference"></a><span data-ttu-id="0d884-102">sealed (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="0d884-102">sealed (C# Reference)</span></span>

<span data-ttu-id="0d884-103">Quando aplicado a uma classe, o modificador `sealed` impede que outras classes herdem dela.</span><span class="sxs-lookup"><span data-stu-id="0d884-103">When applied to a class, the `sealed` modifier prevents other classes from inheriting from it.</span></span> <span data-ttu-id="0d884-104">No exemplo a seguir, a classe `B` herda da classe `A`, mas nenhuma classe pode herdar da classe `B`.</span><span class="sxs-lookup"><span data-stu-id="0d884-104">In the following example, class `B` inherits from class `A`, but no class can inherit from class `B`.</span></span>

```csharp
class A {}
sealed class B : A {}
```

<span data-ttu-id="0d884-105">Você também pode usar o modificador `sealed` em um método ou propriedade que substitui um método ou propriedade virtual em uma classe base.</span><span class="sxs-lookup"><span data-stu-id="0d884-105">You can also use the `sealed` modifier on a method or property that overrides a virtual method or property in a base class.</span></span> <span data-ttu-id="0d884-106">Com isso, você pode permitir que classes sejam derivadas de sua classe e impedir que substituam métodos ou propriedades virtuais.</span><span class="sxs-lookup"><span data-stu-id="0d884-106">This enables you to allow classes to derive from your class and prevent them from overriding specific virtual methods or properties.</span></span>

## <a name="example"></a><span data-ttu-id="0d884-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d884-107">Example</span></span>

<span data-ttu-id="0d884-108">No exemplo a seguir, `Z` herda de `Y`, mas `Z` não pode substituir a função virtual `F` declarada em `X` e lacrada em `Y`.</span><span class="sxs-lookup"><span data-stu-id="0d884-108">In the following example, `Z` inherits from `Y` but `Z` cannot override the virtual function `F` that is declared in `X` and sealed in `Y`.</span></span>

[!code-csharp[csrefKeywordsModifiers#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#16)]

<span data-ttu-id="0d884-109">Quando define novos métodos ou propriedades em uma classe, você pode impedir que classes derivadas as substituam ao não declará-las como [virtuais](virtual.md).</span><span class="sxs-lookup"><span data-stu-id="0d884-109">When you define new methods or properties in a class, you can prevent deriving classes from overriding them by not declaring them as [virtual](virtual.md).</span></span>

<span data-ttu-id="0d884-110">É um erro usar o modificador [abstract](abstract.md) com uma classe selada, porque uma classe abstrata deve ser herdada por uma classe que fornece uma implementação dos métodos ou propriedades abstratas.</span><span class="sxs-lookup"><span data-stu-id="0d884-110">It is an error to use the [abstract](abstract.md) modifier with a sealed class, because an abstract class must be inherited by a class that provides an implementation of the abstract methods or properties.</span></span>

<span data-ttu-id="0d884-111">Quando aplicado a um método ou propriedade, o modificador `sealed` sempre deve ser usado com [override](override.md).</span><span class="sxs-lookup"><span data-stu-id="0d884-111">When applied to a method or property, the `sealed` modifier must always be used with [override](override.md).</span></span>

<span data-ttu-id="0d884-112">Como structs são lacrados implicitamente, eles não podem ser herdados.</span><span class="sxs-lookup"><span data-stu-id="0d884-112">Because structs are implicitly sealed, they cannot be inherited.</span></span>

<span data-ttu-id="0d884-113">Para obter mais informações, consulte [Herança](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="0d884-113">For more information, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="0d884-114">Para obter mais exemplos, consulte [Classes e membros de classes abstratas e lacradas](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="0d884-114">For more examples, see [Abstract and Sealed Classes and Class Members](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).</span></span>

## <a name="example"></a><span data-ttu-id="0d884-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0d884-115">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#17)]

<span data-ttu-id="0d884-116">No exemplo anterior, você pode tentar herdar da classe lacrada usando a instrução a seguir:</span><span class="sxs-lookup"><span data-stu-id="0d884-116">In the previous example, you might try to inherit from the sealed class by using the following statement:</span></span>

`class MyDerivedC: SealedClass {}   // Error`

<span data-ttu-id="0d884-117">O resultado é uma mensagem de erro:</span><span class="sxs-lookup"><span data-stu-id="0d884-117">The result is an error message:</span></span>

`'MyDerivedC': cannot derive from sealed type 'SealedClass'`

## <a name="c-language-specification"></a><span data-ttu-id="0d884-118">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="0d884-118">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="remarks"></a><span data-ttu-id="0d884-119">Comentários</span><span class="sxs-lookup"><span data-stu-id="0d884-119">Remarks</span></span>

<span data-ttu-id="0d884-120">Para determinar se deve lacrar uma classe, método ou propriedade, geralmente você deve considerar os dois pontos a seguir:</span><span class="sxs-lookup"><span data-stu-id="0d884-120">To determine whether to seal a class, method, or property, you should generally consider the following two points:</span></span>

- <span data-ttu-id="0d884-121">Os possíveis benefícios que as classes derivadas podem obter por meio da capacidade de personalizar a sua classe.</span><span class="sxs-lookup"><span data-stu-id="0d884-121">The potential benefits that deriving classes might gain through the ability to customize your class.</span></span>

- <span data-ttu-id="0d884-122">O potencial de as classes derivadas modificarem suas classes de forma que elas deixem de funcionar corretamente ou como esperado.</span><span class="sxs-lookup"><span data-stu-id="0d884-122">The potential that deriving classes could modify your classes in such a way that they would no longer work correctly or as expected.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d884-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d884-123">See also</span></span>

- [<span data-ttu-id="0d884-124">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="0d884-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="0d884-125">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="0d884-125">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="0d884-126">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="0d884-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="0d884-127">Classes static e membros de classes static</span><span class="sxs-lookup"><span data-stu-id="0d884-127">Static Classes and Static Class Members</span></span>](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [<span data-ttu-id="0d884-128">Classes e membros de classes abstract e sealed</span><span class="sxs-lookup"><span data-stu-id="0d884-128">Abstract and Sealed Classes and Class Members</span></span>](../../programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="0d884-129">Modificadores de acesso</span><span class="sxs-lookup"><span data-stu-id="0d884-129">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="0d884-130">Modificadores</span><span class="sxs-lookup"><span data-stu-id="0d884-130">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="0d884-131">override</span><span class="sxs-lookup"><span data-stu-id="0d884-131">override</span></span>](override.md)
- [<span data-ttu-id="0d884-132">virtual</span><span class="sxs-lookup"><span data-stu-id="0d884-132">virtual</span></span>](virtual.md)