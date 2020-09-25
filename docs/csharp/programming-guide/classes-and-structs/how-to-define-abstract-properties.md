---
title: Como definir propriedades abstratas – guia de programação C#
description: Saiba como definir propriedades abstratas em C#. Declarar uma propriedade abstract significa que uma classe oferece suporte a uma propriedade. As classes derivadas implementam acessadores.
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: 01af1446097bbed25874b45d57a5dde85ae63891
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91199153"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="b6dcf-105">Como definir propriedades abstratas (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="b6dcf-105">How to define abstract properties (C# Programming Guide)</span></span>

<span data-ttu-id="b6dcf-106">O exemplo a seguir mostra como definir propriedades [abstract](../../language-reference/keywords/abstract.md).</span><span class="sxs-lookup"><span data-stu-id="b6dcf-106">The following example shows how to define [abstract](../../language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="b6dcf-107">Uma declaração de propriedade abstract não fornece uma implementação dos acessadores da propriedade – ela declara que a classe dá suporte às propriedades, mas deixa a implementação do acessador para classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="b6dcf-107">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="b6dcf-108">O exemplo a seguir demonstra como implementar as propriedades abstract herdadas de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="b6dcf-108">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="b6dcf-109">Esse exemplo consiste em três arquivos, cada um deles é compilado individualmente e seu assembly resultante é referenciado pela próxima compilação:</span><span class="sxs-lookup"><span data-stu-id="b6dcf-109">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
- <span data-ttu-id="b6dcf-110">abstractshape.cs: a classe `Shape` que contém uma propriedade abstract `Area`.</span><span class="sxs-lookup"><span data-stu-id="b6dcf-110">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
- <span data-ttu-id="b6dcf-111">shapes.cs: as subclasses da classe `Shape`.</span><span class="sxs-lookup"><span data-stu-id="b6dcf-111">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
- <span data-ttu-id="b6dcf-112">shapetest.cs: um programa de teste para exibir as áreas de alguns objetos derivados de `Shape`.</span><span class="sxs-lookup"><span data-stu-id="b6dcf-112">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="b6dcf-113">Para compilar o exemplo, use o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="b6dcf-113">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="b6dcf-114">Isso criará o arquivo executável shapetest.exe.</span><span class="sxs-lookup"><span data-stu-id="b6dcf-114">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6dcf-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b6dcf-115">Example</span></span>  

 <span data-ttu-id="b6dcf-116">Esse arquivo declara a classe `Shape` que contém a propriedade `Area` do tipo `double`.</span><span class="sxs-lookup"><span data-stu-id="b6dcf-116">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- <span data-ttu-id="b6dcf-117">Os modificadores da propriedade são colocados na própria declaração de propriedade.</span><span class="sxs-lookup"><span data-stu-id="b6dcf-117">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="b6dcf-118">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b6dcf-118">For example:</span></span>  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- <span data-ttu-id="b6dcf-119">Ao declarar uma propriedade abstract (como `Area` neste exemplo), você simplesmente indica quais acessadores de propriedade estão disponíveis, mas não os implementa.</span><span class="sxs-lookup"><span data-stu-id="b6dcf-119">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="b6dcf-120">Neste exemplo, apenas um acessador [get](../../language-reference/keywords/get.md) está disponível, assim, a propriedade é somente leitura.</span><span class="sxs-lookup"><span data-stu-id="b6dcf-120">In this example, only a [get](../../language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6dcf-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b6dcf-121">Example</span></span>  

 <span data-ttu-id="b6dcf-122">O código a seguir mostra três subclasses de `Shape` e como elas substituem a propriedade `Area` para fornecer sua própria implementação.</span><span class="sxs-lookup"><span data-stu-id="b6dcf-122">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a><span data-ttu-id="b6dcf-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b6dcf-123">Example</span></span>  

 <span data-ttu-id="b6dcf-124">O código a seguir mostra um programa de teste que cria uma quantidade de objetos derivados de `Shape` e imprime suas áreas.</span><span class="sxs-lookup"><span data-stu-id="b6dcf-124">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a><span data-ttu-id="b6dcf-125">Veja também</span><span class="sxs-lookup"><span data-stu-id="b6dcf-125">See also</span></span>

- [<span data-ttu-id="b6dcf-126">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="b6dcf-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b6dcf-127">Classes e structs</span><span class="sxs-lookup"><span data-stu-id="b6dcf-127">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="b6dcf-128">Classes e membros de classes abstract e sealed</span><span class="sxs-lookup"><span data-stu-id="b6dcf-128">Abstract and Sealed Classes and Class Members</span></span>](./abstract-and-sealed-classes-and-class-members.md)
- [<span data-ttu-id="b6dcf-129">Propriedades</span><span class="sxs-lookup"><span data-stu-id="b6dcf-129">Properties</span></span>](./properties.md)
