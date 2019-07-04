---
title: virtual – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 2568eed5a889f6c03e237875194b8adcb9334ef7
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401818"
---
# <a name="virtual-c-reference"></a><span data-ttu-id="e1455-102">virtual (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e1455-102">virtual (C# Reference)</span></span>

<span data-ttu-id="e1455-103">A palavra-chave `virtual` é usada para modificar uma declaração de método, propriedade, indexador ou evento e permitir que ela seja substituída em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="e1455-103">The `virtual` keyword is used to modify a method, property, indexer, or event declaration and allow for it to be overridden in a derived class.</span></span> <span data-ttu-id="e1455-104">Por exemplo, esse método pode ser substituído por qualquer classe que o herde:</span><span class="sxs-lookup"><span data-stu-id="e1455-104">For example, this method can be overridden by any class that inherits it:</span></span>

```csharp
public virtual double Area() 
{
    return x * y;
}
```

<span data-ttu-id="e1455-105">A implementação de um membro virtual pode ser alterada por um [membro de substituição](override.md) em uma classe derivada.</span><span class="sxs-lookup"><span data-stu-id="e1455-105">The implementation of a virtual member can be changed by an [overriding member](override.md) in a derived class.</span></span> <span data-ttu-id="e1455-106">Para obter mais informações sobre como usar a palavra-chave `virtual`, consulte [Controle de versão com as palavras-chave override e new](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) e [Quando usar as palavras-chave override e new](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="e1455-106">For more information about how to use the `virtual` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing When to Use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="e1455-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e1455-107">Remarks</span></span>

<span data-ttu-id="e1455-108">Quando um método virtual é invocado, o tipo de tempo de execução do objeto é verificado para um membro de substituição.</span><span class="sxs-lookup"><span data-stu-id="e1455-108">When a virtual method is invoked, the run-time type of the object is checked for an overriding member.</span></span> <span data-ttu-id="e1455-109">O membro de substituição na classe mais derivada é chamado, que pode ser o membro original, se nenhuma classe derivada tiver substituído o membro.</span><span class="sxs-lookup"><span data-stu-id="e1455-109">The overriding member in the most derived class is called, which might be the original member, if no derived class has overridden the member.</span></span>

<span data-ttu-id="e1455-110">Por padrão, os métodos não são virtuais.</span><span class="sxs-lookup"><span data-stu-id="e1455-110">By default, methods are non-virtual.</span></span> <span data-ttu-id="e1455-111">Você não pode substituir um método não virtual.</span><span class="sxs-lookup"><span data-stu-id="e1455-111">You cannot override a non-virtual method.</span></span>

<span data-ttu-id="e1455-112">Não é possível usar o modificador `virtual` com os modificadores `static`, `abstract`, `private` ou `override`.</span><span class="sxs-lookup"><span data-stu-id="e1455-112">You cannot use the `virtual` modifier with the `static`, `abstract`, `private`, or `override` modifiers.</span></span> <span data-ttu-id="e1455-113">O exemplo a seguir mostra uma propriedade virtual:</span><span class="sxs-lookup"><span data-stu-id="e1455-113">The following example shows a virtual property:</span></span>

[!code-csharp[csrefKeywordsModifiers#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#26)]

<span data-ttu-id="e1455-114">Propriedades virtuais se comportam como métodos abstratos, exceto pelas diferenças na sintaxe de declaração e chamada.</span><span class="sxs-lookup"><span data-stu-id="e1455-114">Virtual properties behave like abstract methods, except for the differences in declaration and invocation syntax.</span></span>

- <span data-ttu-id="e1455-115">É um erro usar o modificador `virtual` em uma propriedade estática.</span><span class="sxs-lookup"><span data-stu-id="e1455-115">It is an error to use the `virtual` modifier on a static property.</span></span>

- <span data-ttu-id="e1455-116">Uma propriedade herdada virtual pode ser substituída em uma classe derivada incluindo uma declaração de propriedade que usa o modificador `override`.</span><span class="sxs-lookup"><span data-stu-id="e1455-116">A virtual inherited property can be overridden in a derived class by including a property declaration that uses the `override` modifier.</span></span>

## <a name="example"></a><span data-ttu-id="e1455-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e1455-117">Example</span></span>

<span data-ttu-id="e1455-118">Neste exemplo, a classe `Shape` contém as duas coordenadas `x`, `y` e o método virtual `Area()`.</span><span class="sxs-lookup"><span data-stu-id="e1455-118">In this example, the `Shape` class contains the two coordinates `x`, `y`, and the `Area()` virtual method.</span></span> <span data-ttu-id="e1455-119">Classes de forma diferentes como `Circle`, `Cylinder` e `Sphere` herdam a classe `Shape` e a área de superfície é calculada para cada figura.</span><span class="sxs-lookup"><span data-stu-id="e1455-119">Different shape classes such as `Circle`, `Cylinder`, and `Sphere` inherit the `Shape` class, and the surface area is calculated for each figure.</span></span> <span data-ttu-id="e1455-120">Cada classe derivada tem a própria implementação de substituição do `Area()`.</span><span class="sxs-lookup"><span data-stu-id="e1455-120">Each derived class has its own override implementation of `Area()`.</span></span>

<span data-ttu-id="e1455-121">Observe que as classes herdadas `Circle`, `Sphere` e `Cylinder` usam construtores que inicializam a classe base, conforme mostrado na declaração a seguir.</span><span class="sxs-lookup"><span data-stu-id="e1455-121">Notice that the inherited classes `Circle`, `Sphere`, and `Cylinder` all use constructors that initialize the base class, as shown in the following declaration.</span></span>

```csharp
public Cylinder(double r, double h): base(r, h) {}
```

<span data-ttu-id="e1455-122">O programa a seguir calcula e exibe a área apropriada para cada figura invocando a implementação apropriada do método `Area()`, de acordo com o objeto que está associado ao método.</span><span class="sxs-lookup"><span data-stu-id="e1455-122">The following program calculates and displays the appropriate area for each figure by invoking the appropriate implementation of the `Area()` method, according to the object that is associated with the method.</span></span>

[!code-csharp[csrefKeywordsModifiers#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#23)]

## <a name="c-language-specification"></a><span data-ttu-id="e1455-123">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="e1455-123">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="e1455-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e1455-124">See also</span></span>

- [<span data-ttu-id="e1455-125">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e1455-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e1455-126">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e1455-126">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e1455-127">Modificadores</span><span class="sxs-lookup"><span data-stu-id="e1455-127">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="e1455-128">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="e1455-128">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="e1455-129">Polimorfismo</span><span class="sxs-lookup"><span data-stu-id="e1455-129">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
- [<span data-ttu-id="e1455-130">abstract</span><span class="sxs-lookup"><span data-stu-id="e1455-130">abstract</span></span>](abstract.md)
- [<span data-ttu-id="e1455-131">override</span><span class="sxs-lookup"><span data-stu-id="e1455-131">override</span></span>](override.md)
- [<span data-ttu-id="e1455-132">new (modificador)</span><span class="sxs-lookup"><span data-stu-id="e1455-132">new (modifier)</span></span>](new-modifier.md)
