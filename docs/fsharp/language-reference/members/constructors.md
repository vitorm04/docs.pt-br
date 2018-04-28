---
title: Construtores (F#)
description: 'Saiba como definir e usar os construtores em F # para criar e inicializar objetos de classe e estrutura.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: d9062ae747c37bdc14104658ad0ec7d11f5545f0
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="constructors"></a><span data-ttu-id="b2c2d-103">Construtores</span><span class="sxs-lookup"><span data-stu-id="b2c2d-103">Constructors</span></span>

<span data-ttu-id="b2c2d-104">Este tópico descreve como definir e usar construtores para criar e inicializar objetos de classe e estrutura.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-104">This topic describes how to define and use constructors to create and initialize class and structure objects.</span></span>


## <a name="construction-of-class-objects"></a><span data-ttu-id="b2c2d-105">Construção de objetos de classe</span><span class="sxs-lookup"><span data-stu-id="b2c2d-105">Construction of Class Objects</span></span>
<span data-ttu-id="b2c2d-106">Objetos dos tipos de classe tem construtores.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-106">Objects of class types have constructors.</span></span> <span data-ttu-id="b2c2d-107">Há dois tipos de construtores.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-107">There are two kinds of constructors.</span></span> <span data-ttu-id="b2c2d-108">Um é construtor primário, cujos parâmetros aparecem entre parênteses logo após o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-108">One is the primary constructor, whose parameters appear in parentheses just after the type name.</span></span> <span data-ttu-id="b2c2d-109">Especifique outros, opcionais construtores adicionais usando o `new` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-109">You specify other, optional additional constructors by using the `new` keyword.</span></span> <span data-ttu-id="b2c2d-110">Nenhum construtor tais adicionais deve chamar o construtor primário.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-110">Any such additional constructors must call the primary constructor.</span></span>

<span data-ttu-id="b2c2d-111">O construtor primário contém `let` e `do` associações que aparecem no início da definição de classe.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-111">The primary constructor contains `let` and `do` bindings that appear at the start of the class definition.</span></span> <span data-ttu-id="b2c2d-112">Um `let` associação declara campos particulares e os métodos da classe; um `do` associação executa código.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-112">A `let` binding declares private fields and methods of the class; a `do` binding executes code.</span></span> <span data-ttu-id="b2c2d-113">Para obter mais informações sobre `let` associações em construtores de classe, consulte [ `let` associações em Classes](let-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="b2c2d-113">For more information about `let` bindings in class constructors, see [`let` Bindings in Classes](let-bindings-in-classes.md).</span></span> <span data-ttu-id="b2c2d-114">Para obter mais informações sobre `do` associações em construtores, consulte [ `do` associações em Classes](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="b2c2d-114">For more information about `do` bindings in constructors, see [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

<span data-ttu-id="b2c2d-115">Seja o construtor que você deseja chamar um construtor primário ou um construtor adicional, você pode criar objetos usando um `new` expressão, com ou sem opcional `new` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-115">Regardless of whether the constructor you want to call is a primary constructor or an additional constructor, you can create objects by using a `new` expression, with or without the optional `new` keyword.</span></span> <span data-ttu-id="b2c2d-116">Inicializar seus objetos junto com os argumentos de construtor, seja por meio da lista de argumentos na ordem e separados por vírgulas e colocados entre parênteses, ou usando argumentos nomeados e os valores entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-116">You initialize your objects together with constructor arguments, either by listing the arguments in order and separated by commas and enclosed in parentheses, or by using named arguments and values in parentheses.</span></span> <span data-ttu-id="b2c2d-117">Você também pode definir propriedades em um objeto durante a construção do objeto, usando os nomes de propriedade e atribuir valores, assim como você usa denominado argumentos de construtor.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-117">You can also set properties on an object during the construction of the object by using the property names and assigning values just as you use named constructor arguments.</span></span>

<span data-ttu-id="b2c2d-118">O código a seguir ilustra uma classe que tem um construtor e várias maneiras de criar objetos.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-118">The following code illustrates a class that has a constructor and various ways of creating objects.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

<span data-ttu-id="b2c2d-119">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-119">The output is as follows.</span></span>

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a><span data-ttu-id="b2c2d-120">Construção de estruturas</span><span class="sxs-lookup"><span data-stu-id="b2c2d-120">Construction of Structures</span></span>
<span data-ttu-id="b2c2d-121">Estruturas Siga todas as regras de classes.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-121">Structures follow all the rules of classes.</span></span> <span data-ttu-id="b2c2d-122">Portanto, você pode ter um construtor primário, e você pode fornecer construtores adicionais usando `new`.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-122">Therefore, you can have a primary constructor, and you can provide additional constructors by using `new`.</span></span> <span data-ttu-id="b2c2d-123">No entanto, há uma diferença importante entre as estruturas e classes: estruturas podem ter um construtor padrão (ou seja, aquele sem argumentos), mesmo se nenhum construtor primário é definido.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-123">However, there is one important difference between structures and classes: structures can have a default constructor (that is, one with no arguments) even if no primary constructor is defined.</span></span> <span data-ttu-id="b2c2d-124">O construtor padrão inicializa todos os campos para o valor padrão para esse tipo, geralmente zero ou seu equivalente.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-124">The default constructor initializes all the fields to the default value for that type, usually zero or its equivalent.</span></span> <span data-ttu-id="b2c2d-125">Nenhum construtor definido para estruturas deve ter pelo menos um argumento para que eles não entrem em conflito com o construtor padrão.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-125">Any constructors that you define for structures must have at least one argument so that they do not conflict with the default constructor.</span></span>

<span data-ttu-id="b2c2d-126">Além disso, estruturas geralmente têm campos que são criados usando o `val` palavra-chave; classes também podem ter esses campos.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-126">Also, structures often have fields that are created by using the `val` keyword; classes can also have these fields.</span></span> <span data-ttu-id="b2c2d-127">Estruturas e classes que têm campos definidos usando o `val` palavra-chave também pode ser inicializado em construtores adicionais usando expressões de registro, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-127">Structures and classes that have fields defined by using the `val` keyword can also be initialized in additional constructors by using record expressions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

<span data-ttu-id="b2c2d-128">Para obter mais informações, consulte [campos explícitos: A `val` palavra-chave](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="b2c2d-128">For more information, see [Explicit Fields: The `val` Keyword](explicit-fields-the-val-keyword.md).</span></span>


## <a name="executing-side-effects-in-constructors"></a><span data-ttu-id="b2c2d-129">Efeitos colaterais em execução em construtores</span><span class="sxs-lookup"><span data-stu-id="b2c2d-129">Executing Side Effects in Constructors</span></span>
<span data-ttu-id="b2c2d-130">Um construtor primário em uma classe pode executar código em um `do` associação.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-130">A primary constructor in a class can execute code in a `do` binding.</span></span> <span data-ttu-id="b2c2d-131">No entanto, se você tem que executar código em um construtor adicional, sem um `do` associação?</span><span class="sxs-lookup"><span data-stu-id="b2c2d-131">However, what if you have to execute code in an additional constructor, without a `do` binding?</span></span> <span data-ttu-id="b2c2d-132">Para fazer isso, use o `then` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-132">To do this, you use the `then` keyword.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

<span data-ttu-id="b2c2d-133">Os efeitos colaterais do construtor primário ainda executar.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-133">The side effects of the primary constructor still execute.</span></span> <span data-ttu-id="b2c2d-134">Portanto, a saída é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-134">Therefore, the output is as follows.</span></span>

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a><span data-ttu-id="b2c2d-135">Autoidentificadores em construtores</span><span class="sxs-lookup"><span data-stu-id="b2c2d-135">Self Identifiers in Constructors</span></span>
<span data-ttu-id="b2c2d-136">Em outros membros, você deve fornecer um nome para o objeto atual na definição de cada membro.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-136">In other members, you provide a name for the current object in the definition of each member.</span></span> <span data-ttu-id="b2c2d-137">Você também pode colocar o identificador automático na primeira linha da definição de classe usando o `as` imediatamente após os parâmetros do construtor de palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-137">You can also put the self identifier on the first line of the class definition by using the `as` keyword immediately following the constructor parameters.</span></span> <span data-ttu-id="b2c2d-138">O exemplo a seguir ilustra essa sintaxe.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-138">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

<span data-ttu-id="b2c2d-139">Em construtores adicionais, você também pode definir um identificador de autoatendimento, colocando o `as` cláusula logo após os parâmetros do construtor.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-139">In additional constructors, you can also define a self identifier by putting the `as` clause right after the constructor parameters.</span></span> <span data-ttu-id="b2c2d-140">O exemplo a seguir ilustra essa sintaxe.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-140">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

<span data-ttu-id="b2c2d-141">Podem ocorrer problemas quando você tentar usar um objeto antes que ele esteja totalmente definido.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-141">Problems can occur when you try to use an object before it is fully defined.</span></span> <span data-ttu-id="b2c2d-142">Portanto, usos do identificador de autoatendimento podem causar o compilador emite um aviso e inserir verificações adicionais para garantir que os membros de um objeto não são acessados antes do objeto é inicializado.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-142">Therefore, uses of the self identifier can cause the compiler to emit a warning and insert additional checks to ensure the members of an object are not accessed before the object is initialized.</span></span> <span data-ttu-id="b2c2d-143">Você deve usar apenas o identificador de autoatendimento no `do` associações do construtor primário, ou após o `then` palavra-chave em construtores adicionais.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-143">You should only use the self identifier in the `do` bindings of the primary constructor, or after the `then` keyword in additional constructors.</span></span>

<span data-ttu-id="b2c2d-144">O nome do identificador de autoatendimento não precisa ser `this`.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-144">The name of the self identifier does not have to be `this`.</span></span> <span data-ttu-id="b2c2d-145">Pode ser qualquer identificador válido.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-145">It can be any valid identifier.</span></span>


## <a name="assigning-values-to-properties-at-initialization"></a><span data-ttu-id="b2c2d-146">Atribuindo valores a propriedades de inicialização</span><span class="sxs-lookup"><span data-stu-id="b2c2d-146">Assigning Values to Properties at Initialization</span></span>
<span data-ttu-id="b2c2d-147">Você pode atribuir valores às propriedades de um objeto de classe no código de inicialização adicionando uma lista de atribuições de forma `property = value` à lista de argumentos para um construtor.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-147">You can assign values to the properties of a class object in the initialization code by appending a list of assignments of the form `property = value` to the argument list for a constructor.</span></span> <span data-ttu-id="b2c2d-148">Isso será mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-148">This is shown in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="b2c2d-149">A versão seguinte do código anterior mostra a combinação de argumentos comuns, argumentos opcionais e as configurações de propriedade na chamada de um construtor.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-149">The following version of the previous code illustrates the combination of ordinary arguments, optional arguments, and property settings in one constructor call.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]
    
## <a name="constructors-in-inherited-class"></a><span data-ttu-id="b2c2d-150">Construtores de classe herdada</span><span class="sxs-lookup"><span data-stu-id="b2c2d-150">Constructors in inherited class</span></span>
<span data-ttu-id="b2c2d-151">Ao herdar de uma classe base que tenha um construtor, você deve especificar os argumentos na cláusula herdar.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-151">When inheriting from a base class that has a constructor, you must specify its arguments in the inherit clause.</span></span> <span data-ttu-id="b2c2d-152">Para obter mais informações, consulte [construtores e herança](../inheritance.md#constructors-and-inheritance).</span><span class="sxs-lookup"><span data-stu-id="b2c2d-152">For more information, see [Constructors and inheritance](../inheritance.md#constructors-and-inheritance).</span></span>

## <a name="static-constructors-or-type-constructors"></a><span data-ttu-id="b2c2d-153">Construtores estáticos ou construtores de tipo</span><span class="sxs-lookup"><span data-stu-id="b2c2d-153">Static Constructors or Type Constructors</span></span>
<span data-ttu-id="b2c2d-154">Além de especificar o código para a criação de objetos, estáticos `let` e `do` associações podem ser criadas em tipos de classe que é executada antes do primeiro, o tipo é usado para executar a inicialização em nível de tipo.</span><span class="sxs-lookup"><span data-stu-id="b2c2d-154">In addition to specifying code for creating objects, static `let` and `do` bindings can be authored in class types that execute before the type is first used to perform initialization at the type level.</span></span> <span data-ttu-id="b2c2d-155">Para obter mais informações, consulte [ `let` associações em Classes](let-bindings-in-classes.md) e [ `do` associações em Classes](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="b2c2d-155">For more information, see [`let` Bindings in Classes](let-bindings-in-classes.md) and [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b2c2d-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b2c2d-156">See Also</span></span>
[<span data-ttu-id="b2c2d-157">Membros</span><span class="sxs-lookup"><span data-stu-id="b2c2d-157">Members</span></span>](index.md)
