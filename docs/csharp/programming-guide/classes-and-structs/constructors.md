---
title: Construtores – Guia de Programação em C#
ms.custom: seodec18
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 8c5d34e5350f3ca64753f1d07cabb40712c66b88
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/26/2019
ms.locfileid: "67398534"
---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="ce546-102">Construtores (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="ce546-102">Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="ce546-103">Sempre que uma [classe](../../../csharp/language-reference/keywords/class.md) ou [struct](../../../csharp/language-reference/keywords/struct.md) é criada, o construtor é chamado.</span><span class="sxs-lookup"><span data-stu-id="ce546-103">Whenever a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="ce546-104">Uma classe ou struct pode ter vários construtores que usam argumentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="ce546-104">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="ce546-105">Os construtores permitem que o programador defina valores padrão, limite a instanciação e grave códigos flexíveis e fáceis de ler.</span><span class="sxs-lookup"><span data-stu-id="ce546-105">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="ce546-106">Para obter mais informações e exemplos, consulte [Usando Construtores](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) e [Construtores de Instância](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="ce546-106">For more information and examples, see [Using Constructors](../../../csharp/programming-guide/classes-and-structs/using-constructors.md) and [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  

## <a name="parameterless-constructors"></a><span data-ttu-id="ce546-107">Construtores sem parâmetros</span><span class="sxs-lookup"><span data-stu-id="ce546-107">Parameterless constructors</span></span>
  
<span data-ttu-id="ce546-108">Se um construtor não for fornecido para a classe, o C# criará por padrão um construtor que instancia o objeto e define variáveis de membro para os valores padrão, conforme listado na [Tabela de Valores Padrão](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="ce546-108">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="ce546-109">Se você não fornecer um construtor para o struct, o C# dependerá de um *construtor sem parâmetro implícito* para inicializar automaticamente a cada campo de um tipo de valor para o valor padrão conforme listado na [Tabela de Valores Padrão](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="ce546-109">If you don't provide a constructor for your struct, C# relies on an *implicit parameterless constructor* to automatically initialize each field of a value type to its default value as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="ce546-110">Para obter mais informações e exemplos, consulte [Construtores de Instância](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="ce546-110">For more information and examples, see [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="ce546-111">Sintaxe do construtor</span><span class="sxs-lookup"><span data-stu-id="ce546-111">Constructor syntax</span></span>

<span data-ttu-id="ce546-112">Um construtor é um método cujo nome é igual ao nome de seu tipo.</span><span class="sxs-lookup"><span data-stu-id="ce546-112">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="ce546-113">Sua assinatura do método inclui apenas o nome do método e lista de parâmetros, ele não inclui um tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="ce546-113">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="ce546-114">O exemplo a seguir mostra o construtor para uma classe denominada `Person`.</span><span class="sxs-lookup"><span data-stu-id="ce546-114">The following example shows the constructor for a class named `Person`.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

<span data-ttu-id="ce546-115">Se um construtor puder ser implementado como uma única instrução, você poderá usar uma [definição de corpo da expressão](../statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="ce546-115">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="ce546-116">O exemplo a seguir define uma classe `Location` cujo construtor tem um único parâmetro de cadeia de caracteres chamado *nome*.</span><span class="sxs-lookup"><span data-stu-id="ce546-116">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="ce546-117">A definição de corpo da expressão atribui o argumento ao campo `locationName`.</span><span class="sxs-lookup"><span data-stu-id="ce546-117">The expression body definition assigns the argument to the `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a><span data-ttu-id="ce546-118">Construtores estáticos</span><span class="sxs-lookup"><span data-stu-id="ce546-118">Static constructors</span></span>

<span data-ttu-id="ce546-119">Os exemplos anteriores têm todos os construtores de instância mostrado, que criam um novo objeto.</span><span class="sxs-lookup"><span data-stu-id="ce546-119">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="ce546-120">Uma classe ou struct também pode ter um construtor estático, que inicializa membros estáticos do tipo.</span><span class="sxs-lookup"><span data-stu-id="ce546-120">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="ce546-121">Construtores estáticos não têm parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ce546-121">Static constructors are parameterless.</span></span> <span data-ttu-id="ce546-122">Se você não fornecer um construtor estático para inicializar campos estáticos, o compilador C# inicializará campos estáticos com seu valor padrão, conforme listado na [Tabela de Valores Padrão](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="ce546-122">If you don't provide a static constructor to initialize static fields, the C# compiler initializes static fields to their default value as listed in the [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span>

<span data-ttu-id="ce546-123">O exemplo a seguir usa um construtor estático para inicializar um campo estático.</span><span class="sxs-lookup"><span data-stu-id="ce546-123">The following example uses a static constructor to initialize a static field.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

<span data-ttu-id="ce546-124">Você também pode definir um construtor estático com uma definição de corpo da expressão, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ce546-124">You can also define a static constructor with an expression body definition, as the following example shows.</span></span> 

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

<span data-ttu-id="ce546-125">Para obter mais informações e exemplos, consulte [Construtores Estáticos](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="ce546-125">For more information and examples, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ce546-126">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ce546-126">In This Section</span></span>  
 [<span data-ttu-id="ce546-127">Usando construtores</span><span class="sxs-lookup"><span data-stu-id="ce546-127">Using Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/using-constructors.md)  
  
 [<span data-ttu-id="ce546-128">Construtores de instância</span><span class="sxs-lookup"><span data-stu-id="ce546-128">Instance Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md)  
  
 [<span data-ttu-id="ce546-129">Construtores particulares</span><span class="sxs-lookup"><span data-stu-id="ce546-129">Private Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/private-constructors.md)  
  
 [<span data-ttu-id="ce546-130">Construtores estáticos</span><span class="sxs-lookup"><span data-stu-id="ce546-130">Static Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/static-constructors.md)  
  
 [<span data-ttu-id="ce546-131">Como: escrever um construtor de cópia</span><span class="sxs-lookup"><span data-stu-id="ce546-131">How to: Write a Copy Constructor</span></span>](../../../csharp/programming-guide/classes-and-structs/how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="ce546-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce546-132">See also</span></span>

- [<span data-ttu-id="ce546-133">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="ce546-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ce546-134">Classes e Structs</span><span class="sxs-lookup"><span data-stu-id="ce546-134">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
- [<span data-ttu-id="ce546-135">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="ce546-135">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
- [<span data-ttu-id="ce546-136">static</span><span class="sxs-lookup"><span data-stu-id="ce546-136">static</span></span>](../../../csharp/language-reference/keywords/static.md)
- [<span data-ttu-id="ce546-137">Por que os inicializadores são executados na ordem oposta, como construtores? Parte 1</span><span class="sxs-lookup"><span data-stu-id="ce546-137">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](https://blogs.msdn.microsoft.com/ericlippert/2008/02/15/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
