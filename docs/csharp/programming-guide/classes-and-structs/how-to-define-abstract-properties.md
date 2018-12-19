---
title: 'Como: definir propriedades abstract – Guia de Programação em C#'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: 70f344fb4e5a74940219688190324beb8183d32b
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237305"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a><span data-ttu-id="64ab3-102">Como: definir propriedades abstract (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="64ab3-102">How to: Define Abstract Properties (C# Programming Guide)</span></span>
<span data-ttu-id="64ab3-103">O exemplo a seguir mostra como definir propriedades [abstract](../../../csharp/language-reference/keywords/abstract.md).</span><span class="sxs-lookup"><span data-stu-id="64ab3-103">The following example shows how to define [abstract](../../../csharp/language-reference/keywords/abstract.md) properties.</span></span> <span data-ttu-id="64ab3-104">Uma declaração de propriedade abstract não fornece uma implementação dos acessadores da propriedade – ela declara que a classe dá suporte às propriedades, mas deixa a implementação do acessador para classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="64ab3-104">An abstract property declaration does not provide an implementation of the property accessors -- it declares that the class supports properties, but leaves the accessor implementation to derived classes.</span></span> <span data-ttu-id="64ab3-105">O exemplo a seguir demonstra como implementar as propriedades abstract herdadas de uma classe base.</span><span class="sxs-lookup"><span data-stu-id="64ab3-105">The following example demonstrates how to implement the abstract properties inherited from a base class.</span></span>  
  
 <span data-ttu-id="64ab3-106">Esse exemplo consiste em três arquivos, cada um deles é compilado individualmente e seu assembly resultante é referenciado pela próxima compilação:</span><span class="sxs-lookup"><span data-stu-id="64ab3-106">This sample consists of three files, each of which is compiled individually and its resulting assembly is referenced by the next compilation:</span></span>  
  
-   <span data-ttu-id="64ab3-107">abstractshape.cs: a classe `Shape` que contém uma propriedade abstract `Area`.</span><span class="sxs-lookup"><span data-stu-id="64ab3-107">abstractshape.cs: the `Shape` class that contains an abstract `Area` property.</span></span>  
  
-   <span data-ttu-id="64ab3-108">shapes.cs: as subclasses da classe `Shape`.</span><span class="sxs-lookup"><span data-stu-id="64ab3-108">shapes.cs: The subclasses of the `Shape` class.</span></span>  
  
-   <span data-ttu-id="64ab3-109">shapetest.cs: um programa de teste para exibir as áreas de alguns objetos derivados de `Shape`.</span><span class="sxs-lookup"><span data-stu-id="64ab3-109">shapetest.cs: A test program to display the areas of some `Shape`-derived objects.</span></span>  
  
 <span data-ttu-id="64ab3-110">Para compilar o exemplo, use o comando a seguir:</span><span class="sxs-lookup"><span data-stu-id="64ab3-110">To compile the example, use the following command:</span></span>  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 <span data-ttu-id="64ab3-111">Isso criará o arquivo executável shapetest.exe.</span><span class="sxs-lookup"><span data-stu-id="64ab3-111">This will create the executable file shapetest.exe.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64ab3-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64ab3-112">Example</span></span>  
 <span data-ttu-id="64ab3-113">Esse arquivo declara a classe `Shape` que contém a propriedade `Area` do tipo `double`.</span><span class="sxs-lookup"><span data-stu-id="64ab3-113">This file declares the `Shape` class that contains the `Area` property of the type `double`.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_1.cs)]  
  
-   <span data-ttu-id="64ab3-114">Os modificadores da propriedade são colocados na própria declaração de propriedade.</span><span class="sxs-lookup"><span data-stu-id="64ab3-114">Modifiers on the property are placed on the property declaration itself.</span></span> <span data-ttu-id="64ab3-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="64ab3-115">For example:</span></span>  
  
    ```csharp  
    public abstract double Area  
    ```  
  
-   <span data-ttu-id="64ab3-116">Ao declarar uma propriedade abstract (como `Area` neste exemplo), você simplesmente indica quais acessadores de propriedade estão disponíveis, mas não os implementa.</span><span class="sxs-lookup"><span data-stu-id="64ab3-116">When declaring an abstract property (such as `Area` in this example), you simply indicate what property accessors are available, but do not implement them.</span></span> <span data-ttu-id="64ab3-117">Neste exemplo, apenas um acessador [get](../../../csharp/language-reference/keywords/get.md) está disponível, assim, a propriedade é somente leitura.</span><span class="sxs-lookup"><span data-stu-id="64ab3-117">In this example, only a [get](../../../csharp/language-reference/keywords/get.md) accessor is available, so the property is read-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64ab3-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64ab3-118">Example</span></span>  
 <span data-ttu-id="64ab3-119">O código a seguir mostra três subclasses de `Shape` e como elas substituem a propriedade `Area` para fornecer sua própria implementação.</span><span class="sxs-lookup"><span data-stu-id="64ab3-119">The following code shows three subclasses of `Shape` and how they override the `Area` property to provide their own implementation.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="64ab3-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="64ab3-120">Example</span></span>  
 <span data-ttu-id="64ab3-121">O código a seguir mostra um programa de teste que cria uma quantidade de objetos derivados de `Shape` e imprime suas áreas.</span><span class="sxs-lookup"><span data-stu-id="64ab3-121">The following code shows a test program that creates a number of `Shape`-derived objects and prints out their areas.</span></span>  
  
 [!code-csharp[csProgGuideInheritance#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="64ab3-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="64ab3-122">See Also</span></span>

- [<span data-ttu-id="64ab3-123">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="64ab3-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="64ab3-124">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="64ab3-124">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [<span data-ttu-id="64ab3-125">Classes e membros de classes abstract e sealed</span><span class="sxs-lookup"><span data-stu-id="64ab3-125">Abstract and Sealed Classes and Class Members</span></span>](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [<span data-ttu-id="64ab3-126">Propriedades</span><span class="sxs-lookup"><span data-stu-id="64ab3-126">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- <span data-ttu-id="64ab3-127">[Como: criar e usar assemblies usando a linha de comando](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="64ab3-127">[How to: Create and Use Assemblies Using the Command Line](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)</span></span>
