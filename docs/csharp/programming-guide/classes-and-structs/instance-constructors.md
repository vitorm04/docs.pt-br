---
title: "Construtores de instâncias (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f93f622d5bf99ab7e8b1d8338192ff58472813dd
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="instance-constructors-c-programming-guide"></a><span data-ttu-id="1467f-102">Construtores de instâncias (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="1467f-102">Instance Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="1467f-103">Os construtores de instância são usados para criar e inicializar quaisquer variáveis de membro de instância quando você usa a expressão [new](../../../csharp/language-reference/keywords/new.md) para criar um objeto de uma [classe](../../../csharp/language-reference/keywords/class.md).</span><span class="sxs-lookup"><span data-stu-id="1467f-103">Instance constructors are used to create and initialize any instance member variables when you use the [new](../../../csharp/language-reference/keywords/new.md) expression to create an object of a [class](../../../csharp/language-reference/keywords/class.md).</span></span> <span data-ttu-id="1467f-104">Para inicializar uma classe [estática](../../../csharp/language-reference/keywords/static.md) ou variáveis estáticas em uma classe não estática, é necessário definir um construtor estático.</span><span class="sxs-lookup"><span data-stu-id="1467f-104">To initialize a [static](../../../csharp/language-reference/keywords/static.md) class, or static variables in a non-static class, you must define a static constructor.</span></span> <span data-ttu-id="1467f-105">Para obter mais informações, consulte [Construtores estáticos](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="1467f-105">For more information, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
 <span data-ttu-id="1467f-106">O exemplo a seguir mostra um construtor de instância:</span><span class="sxs-lookup"><span data-stu-id="1467f-106">The following example shows an instance constructor:</span></span>  
  
 <span data-ttu-id="1467f-107">[!code-cs[csProgGuideObjects#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="1467f-107">[!code-cs[csProgGuideObjects#5](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_1.cs)]</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1467f-108">Para maior clareza, essa classe contém campos públicos.</span><span class="sxs-lookup"><span data-stu-id="1467f-108">For clarity, this class contains public fields.</span></span> <span data-ttu-id="1467f-109">O uso de campos públicos não é uma prática de programação recomendada, porque permite que qualquer acesso de programa não restrito e não verificado a trabalhos internos de um objeto.</span><span class="sxs-lookup"><span data-stu-id="1467f-109">The use of public fields is not a recommended programming practice because it allows any method anywhere in a program unrestricted and unverified access to an object's inner workings.</span></span> <span data-ttu-id="1467f-110">Geralmente os membros de dados devem ser privados e devem ser acessados apenas por meio de propriedades e métodos de classe.</span><span class="sxs-lookup"><span data-stu-id="1467f-110">Data members should generally be private, and should be accessed only through class methods and properties.</span></span>  
  
 <span data-ttu-id="1467f-111">Esse construtor de instância é chamado sempre que um objeto com base na classe `CoOrds` é criado.</span><span class="sxs-lookup"><span data-stu-id="1467f-111">This instance constructor is called whenever an object based on the `CoOrds` class is created.</span></span> <span data-ttu-id="1467f-112">Um construtor como este, que não usa nenhum argumento, é chamado um *construtor padrão*.</span><span class="sxs-lookup"><span data-stu-id="1467f-112">A constructor like this one, which takes no arguments, is called a *default constructor*.</span></span> <span data-ttu-id="1467f-113">No entanto, geralmente é útil fornecer construtores adicionais.</span><span class="sxs-lookup"><span data-stu-id="1467f-113">However, it is often useful to provide additional constructors.</span></span> <span data-ttu-id="1467f-114">Por exemplo, podemos adicionar um construtor à classe `CoOrds` que nos permite especificar os valores iniciais para os membros de dados:</span><span class="sxs-lookup"><span data-stu-id="1467f-114">For example, we can add a constructor to the `CoOrds` class that allows us to specify the initial values for the data members:</span></span>  
  
 <span data-ttu-id="1467f-115">[!code-cs[csProgGuideObjects#76](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="1467f-115">[!code-cs[csProgGuideObjects#76](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_2.cs)]</span></span>  
  
 <span data-ttu-id="1467f-116">Isso permite que objetos `CoOrd` sejam criados com os valores iniciais padrão ou específicos, como este:</span><span class="sxs-lookup"><span data-stu-id="1467f-116">This allows `CoOrd` objects to be created with default or specific initial values, like this:</span></span>  
  
 <span data-ttu-id="1467f-117">[!code-cs[csProgGuideObjects#77](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="1467f-117">[!code-cs[csProgGuideObjects#77](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_3.cs)]</span></span>  
  
 <span data-ttu-id="1467f-118">Se uma classe não tem um construtor, um construtor padrão é gerado automaticamente e os valores padrão são usados para inicializar os campos de objeto.</span><span class="sxs-lookup"><span data-stu-id="1467f-118">If a class does not have a constructor, a default constructor is automatically generated and default values are used to initialize the object fields.</span></span> <span data-ttu-id="1467f-119">Por exemplo, um [int](../../../csharp/language-reference/keywords/int.md) é inicializada como 0.</span><span class="sxs-lookup"><span data-stu-id="1467f-119">For example, an [int](../../../csharp/language-reference/keywords/int.md) is initialized to 0.</span></span> <span data-ttu-id="1467f-120">Para obter mais informações sobre valores padrão, consulte [Tabela de valores padrão](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="1467f-120">For more information on default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="1467f-121">Portanto, como construtor padrão da classe `CoOrds` inicializa todos os membros de dados como zero, ele pode ser totalmente removido sem alterar a maneira como a classe funciona.</span><span class="sxs-lookup"><span data-stu-id="1467f-121">Therefore, because the `CoOrds` class default constructor initializes all data members to zero, it can be removed altogether without changing how the class works.</span></span> <span data-ttu-id="1467f-122">Um exemplo completo que usa vários construtores é fornecido no Exemplo 1 posteriormente neste tópico e um exemplo de um construtor gerado automaticamente é fornecido no Exemplo 2.</span><span class="sxs-lookup"><span data-stu-id="1467f-122">A complete example using multiple constructors is provided in Example 1 later in this topic, and an example of an automatically generated constructor is provided in Example 2.</span></span>  
  
 <span data-ttu-id="1467f-123">Construtores de instância também podem ser usados para chamar os construtores de instância de classes base.</span><span class="sxs-lookup"><span data-stu-id="1467f-123">Instance constructors can also be used to call the instance constructors of base classes.</span></span> <span data-ttu-id="1467f-124">O construtor de classe pode invocar o construtor da classe base por meio do inicializador, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="1467f-124">The class constructor can invoke the constructor of the base class through the initializer, as follows:</span></span>  
  
 <span data-ttu-id="1467f-125">[!code-cs[csProgGuideObjects#78](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="1467f-125">[!code-cs[csProgGuideObjects#78](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_4.cs)]</span></span>  
  
 <span data-ttu-id="1467f-126">Neste exemplo, a classe `Circle` passa valores que representam o raio e a altura do construtor fornecido pelo `Shape` do qual `Circle` é derivado.</span><span class="sxs-lookup"><span data-stu-id="1467f-126">In this example, the `Circle` class passes values representing radius and height to the constructor provided by `Shape` from which `Circle` is derived.</span></span> <span data-ttu-id="1467f-127">Um exemplo completo que usa `Shape` e `Circle` é exibido neste tópico como Exemplo 3.</span><span class="sxs-lookup"><span data-stu-id="1467f-127">A complete example using `Shape` and `Circle` appears in this topic as Example 3.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="1467f-128">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="1467f-128">Example 1</span></span>  
 <span data-ttu-id="1467f-129">O exemplo a seguir demonstra uma classe com dois construtores de classe, um sem argumentos e outro com dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="1467f-129">The following example demonstrates a class with two class constructors, one without arguments and one with two arguments.</span></span>  
  
 <span data-ttu-id="1467f-130">[!code-cs[csProgGuideObjects#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="1467f-130">[!code-cs[csProgGuideObjects#4](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_5.cs)]</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="1467f-131">Exemplo 2</span><span class="sxs-lookup"><span data-stu-id="1467f-131">Example 2</span></span>  
 <span data-ttu-id="1467f-132">Neste exemplo, a classe `Person` não tem nenhum construtor. Nesse caso, um construtor padrão é fornecido automaticamente e os campos são inicializados com seus valores padrão.</span><span class="sxs-lookup"><span data-stu-id="1467f-132">In this example, the class `Person` does not have any constructors, in which case, a default constructor is automatically provided and the fields are initialized to their default values.</span></span>  
  
 <span data-ttu-id="1467f-133">[!code-cs[csProgGuideObjects#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="1467f-133">[!code-cs[csProgGuideObjects#8](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_6.cs)]</span></span>  
  
 <span data-ttu-id="1467f-134">Observe que o valor padrão de `age` é `0` e o valor padrão de `name` é `null`.</span><span class="sxs-lookup"><span data-stu-id="1467f-134">Notice that the default value of `age` is `0` and the default value of `name` is `null`.</span></span> <span data-ttu-id="1467f-135">Para obter mais informações sobre valores padrão, consulte [Tabela de valores padrão](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="1467f-135">For more information on default values, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>  
  
## <a name="example-3"></a><span data-ttu-id="1467f-136">Exemplo 3:</span><span class="sxs-lookup"><span data-stu-id="1467f-136">Example 3</span></span>  
 <span data-ttu-id="1467f-137">O exemplo a seguir demonstra como usar o inicializador de classe base.</span><span class="sxs-lookup"><span data-stu-id="1467f-137">The following example demonstrates using the base class initializer.</span></span> <span data-ttu-id="1467f-138">A classe `Circle` é derivada da classe geral `Shape` e a classe `Cylinder` é derivada da classe `Circle`.</span><span class="sxs-lookup"><span data-stu-id="1467f-138">The `Circle` class is derived from the general class `Shape`, and the `Cylinder` class is derived from the `Circle` class.</span></span> <span data-ttu-id="1467f-139">O construtor em cada classe derivada está usando seu inicializador de classe base.</span><span class="sxs-lookup"><span data-stu-id="1467f-139">The constructor on each derived class is using its base class initializer.</span></span>  
  
 <span data-ttu-id="1467f-140">[!code-cs[csProgGuideObjects#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="1467f-140">[!code-cs[csProgGuideObjects#9](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/instance-constructors_7.cs)]</span></span>  
  
 <span data-ttu-id="1467f-141">Para obter mais exemplos sobre a invocação de construtores de classe base, consulte [virtual](../../../csharp/language-reference/keywords/virtual.md), [override](../../../csharp/language-reference/keywords/override.md) e [base](../../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="1467f-141">For more examples on invoking the base class constructors, see [virtual](../../../csharp/language-reference/keywords/virtual.md), [override](../../../csharp/language-reference/keywords/override.md), and [base](../../../csharp/language-reference/keywords/base.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1467f-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1467f-142">See Also</span></span>  
 <span data-ttu-id="1467f-143">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="1467f-143">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="1467f-144">[Classes e structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span><span class="sxs-lookup"><span data-stu-id="1467f-144">[Classes and Structs](../../../csharp/programming-guide/classes-and-structs/index.md) </span></span>  
 <span data-ttu-id="1467f-145">[Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span><span class="sxs-lookup"><span data-stu-id="1467f-145">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span></span>  
 <span data-ttu-id="1467f-146">[Finalizadores](../../../csharp/programming-guide/classes-and-structs/destructors.md) </span><span class="sxs-lookup"><span data-stu-id="1467f-146">[Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md) </span></span>  
 [<span data-ttu-id="1467f-147">static</span><span class="sxs-lookup"><span data-stu-id="1467f-147">static</span></span>](../../../csharp/language-reference/keywords/static.md)

