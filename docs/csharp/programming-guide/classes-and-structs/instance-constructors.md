---
title: Construtores de instâncias – Guia de Programação em C#
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], instance constructors
- instance constructors [C#]
ms.assetid: 24663779-c1e5-4af4-a942-ca554e4c542d
ms.openlocfilehash: 621b8ca7510b0b9916c9c46f201ff77402c3c655
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75964720"
---
# <a name="instance-constructors-c-programming-guide"></a><span data-ttu-id="b1a48-102">Construtores de instâncias (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="b1a48-102">Instance Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="b1a48-103">Os construtores de instância são usados para criar e inicializar quaisquer variáveis de membro de instância quando você usa a expressão [new](../../language-reference/operators/new-operator.md) para criar um objeto de uma [classe](../../language-reference/keywords/class.md).</span><span class="sxs-lookup"><span data-stu-id="b1a48-103">Instance constructors are used to create and initialize any instance member variables when you use the [new](../../language-reference/operators/new-operator.md) expression to create an object of a [class](../../language-reference/keywords/class.md).</span></span> <span data-ttu-id="b1a48-104">Para inicializar uma classe [estática](../../language-reference/keywords/static.md) ou variáveis estáticas em uma classe não estática, defina um construtor estático.</span><span class="sxs-lookup"><span data-stu-id="b1a48-104">To initialize a [static](../../language-reference/keywords/static.md) class, or static variables in a non-static class, you define a static constructor.</span></span> <span data-ttu-id="b1a48-105">Para obter mais informações, consulte [Construtores estáticos](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="b1a48-105">For more information, see [Static Constructors](./static-constructors.md).</span></span>  
  
 <span data-ttu-id="b1a48-106">O exemplo a seguir mostra um construtor de instância:</span><span class="sxs-lookup"><span data-stu-id="b1a48-106">The following example shows an instance constructor:</span></span>  
  
 [!code-csharp[csProgGuideObjects#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#5)]  
  
> [!NOTE]
> <span data-ttu-id="b1a48-107">Para maior clareza, essa classe contém campos públicos.</span><span class="sxs-lookup"><span data-stu-id="b1a48-107">For clarity, this class contains public fields.</span></span> <span data-ttu-id="b1a48-108">O uso de campos públicos não é uma prática de programação recomendada, porque permite que qualquer acesso de programa não restrito e não verificado a trabalhos internos de um objeto.</span><span class="sxs-lookup"><span data-stu-id="b1a48-108">The use of public fields is not a recommended programming practice because it allows any method anywhere in a program unrestricted and unverified access to an object's inner workings.</span></span> <span data-ttu-id="b1a48-109">Geralmente os membros de dados devem ser privados e devem ser acessados apenas por meio de propriedades e métodos de classe.</span><span class="sxs-lookup"><span data-stu-id="b1a48-109">Data members should generally be private, and should be accessed only through class methods and properties.</span></span>  
  
 <span data-ttu-id="b1a48-110">Esse construtor de instância é chamado sempre que um objeto com base na classe `Coords` é criado.</span><span class="sxs-lookup"><span data-stu-id="b1a48-110">This instance constructor is called whenever an object based on the `Coords` class is created.</span></span> <span data-ttu-id="b1a48-111">Um construtor como este, que não usa nenhum argumento, é chamado um *construtor sem parâmetros*.</span><span class="sxs-lookup"><span data-stu-id="b1a48-111">A constructor like this one, which takes no arguments, is called a *parameterless constructor*.</span></span> <span data-ttu-id="b1a48-112">No entanto, geralmente é útil fornecer construtores adicionais.</span><span class="sxs-lookup"><span data-stu-id="b1a48-112">However, it is often useful to provide additional constructors.</span></span> <span data-ttu-id="b1a48-113">Por exemplo, podemos adicionar um construtor à classe `Coords` que nos permite especificar os valores iniciais para os membros de dados:</span><span class="sxs-lookup"><span data-stu-id="b1a48-113">For example, we can add a constructor to the `Coords` class that allows us to specify the initial values for the data members:</span></span>  
  
 [!code-csharp[csProgGuideObjects#76](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#76)]  
  
 <span data-ttu-id="b1a48-114">Isso permite que objetos `Coords` sejam criados com os valores iniciais padrão ou específicos, como este:</span><span class="sxs-lookup"><span data-stu-id="b1a48-114">This allows `Coords` objects to be created with default or specific initial values, like this:</span></span>  
  
 [!code-csharp[csProgGuideObjects#77](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#77)]  
  
 <span data-ttu-id="b1a48-115">Se uma classe não tiver um construtor, um construtor sem parâmetros será gerado automaticamente e os valores padrão serão usados para inicializar os campos de objeto.</span><span class="sxs-lookup"><span data-stu-id="b1a48-115">If a class does not have a constructor, a parameterless constructor is automatically generated and default values are used to initialize the object fields.</span></span> <span data-ttu-id="b1a48-116">Por exemplo, um [int](../../language-reference/builtin-types/integral-numeric-types.md) é inicializada como 0.</span><span class="sxs-lookup"><span data-stu-id="b1a48-116">For example, an [int](../../language-reference/builtin-types/integral-numeric-types.md) is initialized to 0.</span></span> <span data-ttu-id="b1a48-117">Para obter informações sobre os valores padrão do tipo, consulte [Valores padrão dos tipos C#](../../language-reference/builtin-types/default-values.md).</span><span class="sxs-lookup"><span data-stu-id="b1a48-117">For information about the type default values, see [Default values of C# types](../../language-reference/builtin-types/default-values.md).</span></span> <span data-ttu-id="b1a48-118">Portanto, como construtor sem parâmetros da classe `Coords` inicializa todos os membros de dados como zero, ele pode ser totalmente removido sem alterar a maneira como a classe funciona.</span><span class="sxs-lookup"><span data-stu-id="b1a48-118">Therefore, because the `Coords` class parameterless constructor initializes all data members to zero, it can be removed altogether without changing how the class works.</span></span> <span data-ttu-id="b1a48-119">Um exemplo completo que usa vários construtores é fornecido no Exemplo 1 posteriormente neste tópico e um exemplo de um construtor gerado automaticamente é fornecido no Exemplo 2.</span><span class="sxs-lookup"><span data-stu-id="b1a48-119">A complete example using multiple constructors is provided in Example 1 later in this topic, and an example of an automatically generated constructor is provided in Example 2.</span></span>  
  
 <span data-ttu-id="b1a48-120">Construtores de instância também podem ser usados para chamar os construtores de instância de classes base.</span><span class="sxs-lookup"><span data-stu-id="b1a48-120">Instance constructors can also be used to call the instance constructors of base classes.</span></span> <span data-ttu-id="b1a48-121">O construtor de classe pode invocar o construtor da classe base por meio do inicializador, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b1a48-121">The class constructor can invoke the constructor of the base class through the initializer, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#78](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#78)]  
  
 <span data-ttu-id="b1a48-122">Neste exemplo, a classe `Circle` passa valores que representam o raio e a altura do construtor fornecido pelo `Shape` do qual `Circle` é derivado.</span><span class="sxs-lookup"><span data-stu-id="b1a48-122">In this example, the `Circle` class passes values representing radius and height to the constructor provided by `Shape` from which `Circle` is derived.</span></span> <span data-ttu-id="b1a48-123">Um exemplo completo que usa `Shape` e `Circle` é exibido neste tópico como Exemplo 3.</span><span class="sxs-lookup"><span data-stu-id="b1a48-123">A complete example using `Shape` and `Circle` appears in this topic as Example 3.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="b1a48-124">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="b1a48-124">Example 1</span></span>  
 <span data-ttu-id="b1a48-125">O exemplo a seguir demonstra uma classe com dois construtores de classe, um sem argumentos e outro com dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="b1a48-125">The following example demonstrates a class with two class constructors, one without arguments and one with two arguments.</span></span>  
  
 [!code-csharp[csProgGuideObjects#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#4)]  
  
## <a name="example-2"></a><span data-ttu-id="b1a48-126">Exemplo 2</span><span class="sxs-lookup"><span data-stu-id="b1a48-126">Example 2</span></span>  
 <span data-ttu-id="b1a48-127">Neste exemplo, a classe `Person` não tem nenhum construtor. Nesse caso, um construtor sem parâmetros é fornecido automaticamente e os campos são inicializados com seus valores padrão.</span><span class="sxs-lookup"><span data-stu-id="b1a48-127">In this example, the class `Person` does not have any constructors, in which case, a parameterless constructor is automatically provided and the fields are initialized to their default values.</span></span>  
  
 [!code-csharp[csProgGuideObjects#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#8)]  
  
 <span data-ttu-id="b1a48-128">Observe que o valor padrão de `age` é `0` e o valor padrão de `name` é `null`.</span><span class="sxs-lookup"><span data-stu-id="b1a48-128">Notice that the default value of `age` is `0` and the default value of `name` is `null`.</span></span>
  
## <a name="example-3"></a><span data-ttu-id="b1a48-129">Exemplo 3</span><span class="sxs-lookup"><span data-stu-id="b1a48-129">Example 3</span></span>  
 <span data-ttu-id="b1a48-130">O exemplo a seguir demonstra como usar o inicializador de classe base.</span><span class="sxs-lookup"><span data-stu-id="b1a48-130">The following example demonstrates using the base class initializer.</span></span> <span data-ttu-id="b1a48-131">A classe `Circle` é derivada da classe geral `Shape` e a classe `Cylinder` é derivada da classe `Circle`.</span><span class="sxs-lookup"><span data-stu-id="b1a48-131">The `Circle` class is derived from the general class `Shape`, and the `Cylinder` class is derived from the `Circle` class.</span></span> <span data-ttu-id="b1a48-132">O construtor em cada classe derivada está usando seu inicializador de classe base.</span><span class="sxs-lookup"><span data-stu-id="b1a48-132">The constructor on each derived class is using its base class initializer.</span></span>  
  
 [!code-csharp[csProgGuideObjects#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#9)]  
  
 <span data-ttu-id="b1a48-133">Para obter mais exemplos sobre a invocação de construtores de classe base, consulte [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md) e [base](../../language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="b1a48-133">For more examples on invoking the base class constructors, see [virtual](../../language-reference/keywords/virtual.md), [override](../../language-reference/keywords/override.md), and [base](../../language-reference/keywords/base.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1a48-134">Confira também</span><span class="sxs-lookup"><span data-stu-id="b1a48-134">See also</span></span>

- [<span data-ttu-id="b1a48-135">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="b1a48-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b1a48-136">Classes e structs</span><span class="sxs-lookup"><span data-stu-id="b1a48-136">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="b1a48-137">Construtores</span><span class="sxs-lookup"><span data-stu-id="b1a48-137">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="b1a48-138">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="b1a48-138">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="b1a48-139">Estático</span><span class="sxs-lookup"><span data-stu-id="b1a48-139">static</span></span>](../../language-reference/keywords/static.md)
