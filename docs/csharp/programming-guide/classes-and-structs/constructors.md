---
title: Construtores – Guia de Programação em C#
description: Um construtor em C# é chamado quando uma classe ou struct é criada. Use construtores para definir padrões, limitar a instanciação e escrever código flexível e de fácil leitura.
ms.date: 05/05/2017
helpviewer_keywords:
- constructors [C#]
- classes [C#], constructors
- C# language, constructors
ms.assetid: df2e2e9d-7998-418b-8e7d-890c17ff6c95
ms.openlocfilehash: 4a731e648143f5e0ecf8860625962d8baa29fe26
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474898"
---
# <a name="constructors-c-programming-guide"></a><span data-ttu-id="e5962-104">Construtores (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="e5962-104">Constructors (C# Programming Guide)</span></span>

<span data-ttu-id="e5962-105">Sempre que uma [classe](../../language-reference/keywords/class.md) ou [struct](../../language-reference/builtin-types/struct.md) é criada, o construtor é chamado.</span><span class="sxs-lookup"><span data-stu-id="e5962-105">Whenever a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="e5962-106">Uma classe ou struct pode ter vários construtores que usam argumentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="e5962-106">A class or struct may have multiple constructors that take different arguments.</span></span> <span data-ttu-id="e5962-107">Os construtores permitem que o programador defina valores padrão, limite a instanciação e grave códigos flexíveis e fáceis de ler.</span><span class="sxs-lookup"><span data-stu-id="e5962-107">Constructors enable the programmer to set default values, limit instantiation, and write code that is flexible and easy to read.</span></span> <span data-ttu-id="e5962-108">Para obter mais informações e exemplos, consulte [Usando Construtores](./using-constructors.md) e [Construtores de Instância](./instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="e5962-108">For more information and examples, see [Using Constructors](./using-constructors.md) and [Instance Constructors](./instance-constructors.md).</span></span>  

## <a name="parameterless-constructors"></a><span data-ttu-id="e5962-109">Construtores sem parâmetros</span><span class="sxs-lookup"><span data-stu-id="e5962-109">Parameterless constructors</span></span>
  
<span data-ttu-id="e5962-110">Se você não fornecer um construtor para sua classe, o C# criará um por padrão que instancia o objeto e define as variáveis de membro para os valores padrão, conforme listado no artigo [valores padrão de tipos C#](../../language-reference/builtin-types/default-values.md) .</span><span class="sxs-lookup"><span data-stu-id="e5962-110">If you don't provide a constructor for your class, C# creates one by default that instantiates the object and sets member variables to the default values as listed in the [Default values of C# types](../../language-reference/builtin-types/default-values.md) article.</span></span> <span data-ttu-id="e5962-111">Se você não fornecer um construtor para sua estrutura, o C# se baseará em um *Construtor implícito sem parâmetros* para inicializar automaticamente cada campo com seu valor padrão.</span><span class="sxs-lookup"><span data-stu-id="e5962-111">If you don't provide a constructor for your struct, C# relies on an *implicit parameterless constructor* to automatically initialize each field to its default value.</span></span> <span data-ttu-id="e5962-112">Para obter mais informações e exemplos, consulte [construtores de instância](instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="e5962-112">For more information and examples, see [Instance constructors](instance-constructors.md).</span></span>  

## <a name="constructor-syntax"></a><span data-ttu-id="e5962-113">Sintaxe do construtor</span><span class="sxs-lookup"><span data-stu-id="e5962-113">Constructor syntax</span></span>

<span data-ttu-id="e5962-114">Um construtor é um método cujo nome é igual ao nome de seu tipo.</span><span class="sxs-lookup"><span data-stu-id="e5962-114">A constructor is a method whose name is the same as the name of its type.</span></span> <span data-ttu-id="e5962-115">Sua assinatura do método inclui apenas o nome do método e lista de parâmetros, ele não inclui um tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="e5962-115">Its method signature includes only the method name and its parameter list; it does not include a return type.</span></span> <span data-ttu-id="e5962-116">O exemplo a seguir mostra o construtor para uma classe denominada `Person`.</span><span class="sxs-lookup"><span data-stu-id="e5962-116">The following example shows the constructor for a class named `Person`.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#1)]  

<span data-ttu-id="e5962-117">Se um construtor puder ser implementado como uma única instrução, você poderá usar uma [definição de corpo da expressão](../statements-expressions-operators/expression-bodied-members.md).</span><span class="sxs-lookup"><span data-stu-id="e5962-117">If a constructor can be implemented as a single statement, you can use an [expression body definition](../statements-expressions-operators/expression-bodied-members.md).</span></span> <span data-ttu-id="e5962-118">O exemplo a seguir define uma classe `Location` cujo construtor tem um único parâmetro de cadeia de caracteres chamado *nome*.</span><span class="sxs-lookup"><span data-stu-id="e5962-118">The following example defines a `Location` class whose constructor has a single string parameter named *name*.</span></span> <span data-ttu-id="e5962-119">A definição de corpo da expressão atribui o argumento ao campo `locationName`.</span><span class="sxs-lookup"><span data-stu-id="e5962-119">The expression body definition assigns the argument to the `locationName` field.</span></span>

[!code-csharp[expression-bodied-constructor](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-ctor.cs#1)]  

## <a name="static-constructors"></a><span data-ttu-id="e5962-120">Construtores estáticos</span><span class="sxs-lookup"><span data-stu-id="e5962-120">Static constructors</span></span>

<span data-ttu-id="e5962-121">Os exemplos anteriores têm todos os construtores de instância mostrado, que criam um novo objeto.</span><span class="sxs-lookup"><span data-stu-id="e5962-121">The previous examples have all shown instance constructors, which create a new object.</span></span> <span data-ttu-id="e5962-122">Uma classe ou struct também pode ter um construtor estático, que inicializa membros estáticos do tipo.</span><span class="sxs-lookup"><span data-stu-id="e5962-122">A class or struct can also have a static constructor, which initializes static members of the type.</span></span>  <span data-ttu-id="e5962-123">Construtores estáticos não têm parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e5962-123">Static constructors are parameterless.</span></span> <span data-ttu-id="e5962-124">Se você não fornecer um construtor estático para inicializar campos estáticos, o compilador C# Inicializa campos estáticos para seu valor padrão, conforme listado no artigo [valores padrão de tipos C#](../../language-reference/builtin-types/default-values.md) .</span><span class="sxs-lookup"><span data-stu-id="e5962-124">If you don't provide a static constructor to initialize static fields, the C# compiler initializes static fields to their default value as listed in the [Default values of C# types](../../language-reference/builtin-types/default-values.md) article.</span></span>

<span data-ttu-id="e5962-125">O exemplo a seguir usa um construtor estático para inicializar um campo estático.</span><span class="sxs-lookup"><span data-stu-id="e5962-125">The following example uses a static constructor to initialize a static field.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#2)]  

<span data-ttu-id="e5962-126">Você também pode definir um construtor estático com uma definição de corpo da expressão, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="e5962-126">You can also define a static constructor with an expression body definition, as the following example shows.</span></span>

[!code-csharp[constructors](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/constructors1.cs#3)]  

<span data-ttu-id="e5962-127">Para obter mais informações e exemplos, consulte [Construtores Estáticos](./static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="e5962-127">For more information and examples, see [Static Constructors](./static-constructors.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e5962-128">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e5962-128">In This Section</span></span>  
 [<span data-ttu-id="e5962-129">Usando construtores</span><span class="sxs-lookup"><span data-stu-id="e5962-129">Using Constructors</span></span>](./using-constructors.md)  
  
 [<span data-ttu-id="e5962-130">Construtores de instância</span><span class="sxs-lookup"><span data-stu-id="e5962-130">Instance Constructors</span></span>](./instance-constructors.md)  
  
 [<span data-ttu-id="e5962-131">Construtores particulares</span><span class="sxs-lookup"><span data-stu-id="e5962-131">Private Constructors</span></span>](./private-constructors.md)  
  
 [<span data-ttu-id="e5962-132">Construtores estáticos</span><span class="sxs-lookup"><span data-stu-id="e5962-132">Static Constructors</span></span>](./static-constructors.md)  
  
 [<span data-ttu-id="e5962-133">Como escrever um construtor de cópia</span><span class="sxs-lookup"><span data-stu-id="e5962-133">How to write a copy constructor</span></span>](./how-to-write-a-copy-constructor.md)  
  
## <a name="see-also"></a><span data-ttu-id="e5962-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5962-134">See also</span></span>

- [<span data-ttu-id="e5962-135">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="e5962-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e5962-136">Classes e structs</span><span class="sxs-lookup"><span data-stu-id="e5962-136">Classes and Structs</span></span>](./index.md)
- [<span data-ttu-id="e5962-137">Finalizadores</span><span class="sxs-lookup"><span data-stu-id="e5962-137">Finalizers</span></span>](./destructors.md)
- [<span data-ttu-id="e5962-138">static</span><span class="sxs-lookup"><span data-stu-id="e5962-138">static</span></span>](../../language-reference/keywords/static.md)
- [<span data-ttu-id="e5962-139">Por que inicializadores são executados na ordem oposta como construtores? Parte um</span><span class="sxs-lookup"><span data-stu-id="e5962-139">Why Do Initializers Run In The Opposite Order As Constructors? Part One</span></span>](https://docs.microsoft.com/archive/blogs/ericlippert/why-do-initializers-run-in-the-opposite-order-as-constructors-part-one)
