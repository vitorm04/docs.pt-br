---
title: Construtores
description: Saiba como definir e usar construtores no F# para criar e inicializar objetos de classe e estrutura.
ms.date: 05/16/2016
ms.openlocfilehash: ef5dc134ad98179b6a365c4c34a9eca22fe5f7f6
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364364"
---
# <a name="constructors"></a><span data-ttu-id="57a17-103">Construtores</span><span class="sxs-lookup"><span data-stu-id="57a17-103">Constructors</span></span>

<span data-ttu-id="57a17-104">Este tópico descreve como definir e usar construtores para criar e inicializar objetos de classe e estrutura.</span><span class="sxs-lookup"><span data-stu-id="57a17-104">This topic describes how to define and use constructors to create and initialize class and structure objects.</span></span>

## <a name="construction-of-class-objects"></a><span data-ttu-id="57a17-105">Construção de objetos de classe</span><span class="sxs-lookup"><span data-stu-id="57a17-105">Construction of Class Objects</span></span>

<span data-ttu-id="57a17-106">Objetos de tipos de classe têm construtores.</span><span class="sxs-lookup"><span data-stu-id="57a17-106">Objects of class types have constructors.</span></span> <span data-ttu-id="57a17-107">Há dois tipos de construtores.</span><span class="sxs-lookup"><span data-stu-id="57a17-107">There are two kinds of constructors.</span></span> <span data-ttu-id="57a17-108">Um é o Construtor principal, cujos parâmetros aparecem entre parênteses logo após o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="57a17-108">One is the primary constructor, whose parameters appear in parentheses just after the type name.</span></span> <span data-ttu-id="57a17-109">Você especifica outros construtores opcionais adicionais usando a `new` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="57a17-109">You specify other, optional additional constructors by using the `new` keyword.</span></span> <span data-ttu-id="57a17-110">Qualquer Construtor adicional deve chamar o Construtor principal.</span><span class="sxs-lookup"><span data-stu-id="57a17-110">Any such additional constructors must call the primary constructor.</span></span>

<span data-ttu-id="57a17-111">O Construtor principal contém `let` e `do` associações que aparecem no início da definição de classe.</span><span class="sxs-lookup"><span data-stu-id="57a17-111">The primary constructor contains `let` and `do` bindings that appear at the start of the class definition.</span></span> <span data-ttu-id="57a17-112">Uma `let` Associação declara campos privados e métodos da classe; uma associação executa `do` o código.</span><span class="sxs-lookup"><span data-stu-id="57a17-112">A `let` binding declares private fields and methods of the class; a `do` binding executes code.</span></span> <span data-ttu-id="57a17-113">Para obter mais informações `let` sobre associações em construtores de classe, consulte [ `let` associações em classes](let-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="57a17-113">For more information about `let` bindings in class constructors, see [`let` Bindings in Classes](let-bindings-in-classes.md).</span></span> <span data-ttu-id="57a17-114">Para obter mais informações `do` sobre associações em construtores, consulte [ `do` associações em classes](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="57a17-114">For more information about `do` bindings in constructors, see [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

<span data-ttu-id="57a17-115">Independentemente de o construtor que você deseja chamar ser um construtor primário ou um Construtor adicional, você pode criar objetos usando uma `new` expressão, com ou sem a palavra-chave opcional. `new`</span><span class="sxs-lookup"><span data-stu-id="57a17-115">Regardless of whether the constructor you want to call is a primary constructor or an additional constructor, you can create objects by using a `new` expression, with or without the optional `new` keyword.</span></span> <span data-ttu-id="57a17-116">Você inicializa os objetos junto com argumentos de construtor, seja listando os argumentos em ordem e separados por vírgulas e entre parênteses, ou usando argumentos nomeados e valores entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="57a17-116">You initialize your objects together with constructor arguments, either by listing the arguments in order and separated by commas and enclosed in parentheses, or by using named arguments and values in parentheses.</span></span> <span data-ttu-id="57a17-117">Você também pode definir propriedades em um objeto durante a construção do objeto usando os nomes de propriedade e atribuindo valores da mesma forma que usa argumentos de Construtor nomeados.</span><span class="sxs-lookup"><span data-stu-id="57a17-117">You can also set properties on an object during the construction of the object by using the property names and assigning values just as you use named constructor arguments.</span></span>

<span data-ttu-id="57a17-118">O código a seguir ilustra uma classe que tem um construtor e várias maneiras de criar objetos.</span><span class="sxs-lookup"><span data-stu-id="57a17-118">The following code illustrates a class that has a constructor and various ways of creating objects.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

<span data-ttu-id="57a17-119">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="57a17-119">The output is as follows.</span></span>

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a><span data-ttu-id="57a17-120">Construção de estruturas</span><span class="sxs-lookup"><span data-stu-id="57a17-120">Construction of Structures</span></span>

<span data-ttu-id="57a17-121">As estruturas seguem todas as regras de classes.</span><span class="sxs-lookup"><span data-stu-id="57a17-121">Structures follow all the rules of classes.</span></span> <span data-ttu-id="57a17-122">Portanto, você pode ter um construtor principal e pode fornecer construtores adicionais usando `new`o.</span><span class="sxs-lookup"><span data-stu-id="57a17-122">Therefore, you can have a primary constructor, and you can provide additional constructors by using `new`.</span></span> <span data-ttu-id="57a17-123">No entanto, há uma diferença importante entre estruturas e classes: estruturas podem ter um construtor sem parâmetros (ou seja, um sem argumentos) mesmo que nenhum construtor principal seja definido.</span><span class="sxs-lookup"><span data-stu-id="57a17-123">However, there is one important difference between structures and classes: structures can have a parameterless constructor (that is, one with no arguments) even if no primary constructor is defined.</span></span> <span data-ttu-id="57a17-124">O construtor sem parâmetros inicializa todos os campos para o valor padrão desse tipo, geralmente zero ou seu equivalente.</span><span class="sxs-lookup"><span data-stu-id="57a17-124">The parameterless constructor initializes all the fields to the default value for that type, usually zero or its equivalent.</span></span> <span data-ttu-id="57a17-125">Todos os construtores que você definir para estruturas devem ter pelo menos um argumento para que não entrem em conflito com o construtor padrão.</span><span class="sxs-lookup"><span data-stu-id="57a17-125">Any constructors that you define for structures must have at least one argument so that they do not conflict with the default constructor.</span></span>

<span data-ttu-id="57a17-126">Além disso, as estruturas geralmente têm campos que são criados usando `val` a palavra-chave; as classes também podem ter esses campos.</span><span class="sxs-lookup"><span data-stu-id="57a17-126">Also, structures often have fields that are created by using the `val` keyword; classes can also have these fields.</span></span> <span data-ttu-id="57a17-127">Estruturas e classes que têm campos definidos usando a `val` palavra-chave também podem ser inicializadas em construtores adicionais usando expressões de registro, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="57a17-127">Structures and classes that have fields defined by using the `val` keyword can also be initialized in additional constructors by using record expressions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

<span data-ttu-id="57a17-128">Para obter mais informações, [consulte campos explícitos: A `val` palavra](explicit-fields-the-val-keyword.md)-chave.</span><span class="sxs-lookup"><span data-stu-id="57a17-128">For more information, see [Explicit Fields: The `val` Keyword](explicit-fields-the-val-keyword.md).</span></span>

## <a name="executing-side-effects-in-constructors"></a><span data-ttu-id="57a17-129">Executando efeitos colaterais em construtores</span><span class="sxs-lookup"><span data-stu-id="57a17-129">Executing Side Effects in Constructors</span></span>

<span data-ttu-id="57a17-130">Um construtor principal em uma classe pode executar código em uma `do` associação.</span><span class="sxs-lookup"><span data-stu-id="57a17-130">A primary constructor in a class can execute code in a `do` binding.</span></span> <span data-ttu-id="57a17-131">No entanto, e se você tiver que executar o código em um Construtor adicional `do` , sem uma associação?</span><span class="sxs-lookup"><span data-stu-id="57a17-131">However, what if you have to execute code in an additional constructor, without a `do` binding?</span></span> <span data-ttu-id="57a17-132">Para fazer isso, use a `then` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="57a17-132">To do this, you use the `then` keyword.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

<span data-ttu-id="57a17-133">Os efeitos colaterais do construtor primário ainda são executados.</span><span class="sxs-lookup"><span data-stu-id="57a17-133">The side effects of the primary constructor still execute.</span></span> <span data-ttu-id="57a17-134">Portanto, a saída é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="57a17-134">Therefore, the output is as follows.</span></span>

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a><span data-ttu-id="57a17-135">Identificadores automáticos em construtores</span><span class="sxs-lookup"><span data-stu-id="57a17-135">Self Identifiers in Constructors</span></span>

<span data-ttu-id="57a17-136">Em outros membros, você fornece um nome para o objeto atual na definição de cada membro.</span><span class="sxs-lookup"><span data-stu-id="57a17-136">In other members, you provide a name for the current object in the definition of each member.</span></span> <span data-ttu-id="57a17-137">Você também pode colocar o identificador automático na primeira linha da definição de classe usando a `as` palavra-chave imediatamente após os parâmetros do construtor.</span><span class="sxs-lookup"><span data-stu-id="57a17-137">You can also put the self identifier on the first line of the class definition by using the `as` keyword immediately following the constructor parameters.</span></span> <span data-ttu-id="57a17-138">O exemplo a seguir ilustra essa sintaxe.</span><span class="sxs-lookup"><span data-stu-id="57a17-138">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

<span data-ttu-id="57a17-139">Em construtores adicionais, você também pode definir um autoidentifier colocando a `as` cláusula logo após os parâmetros do construtor.</span><span class="sxs-lookup"><span data-stu-id="57a17-139">In additional constructors, you can also define a self identifier by putting the `as` clause right after the constructor parameters.</span></span> <span data-ttu-id="57a17-140">O exemplo a seguir ilustra essa sintaxe.</span><span class="sxs-lookup"><span data-stu-id="57a17-140">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

<span data-ttu-id="57a17-141">Podem ocorrer problemas quando você tenta usar um objeto antes que ele seja totalmente definido.</span><span class="sxs-lookup"><span data-stu-id="57a17-141">Problems can occur when you try to use an object before it is fully defined.</span></span> <span data-ttu-id="57a17-142">Portanto, os usos do autoidentifier podem fazer com que o compilador emita um aviso e insira verificações adicionais para garantir que os membros de um objeto não sejam acessados antes de o objeto ser inicializado.</span><span class="sxs-lookup"><span data-stu-id="57a17-142">Therefore, uses of the self identifier can cause the compiler to emit a warning and insert additional checks to ensure the members of an object are not accessed before the object is initialized.</span></span> <span data-ttu-id="57a17-143">Você só deve usar o autoidentifier nas `do` associações do Construtor principal ou depois da `then` palavra-chave em construtores adicionais.</span><span class="sxs-lookup"><span data-stu-id="57a17-143">You should only use the self identifier in the `do` bindings of the primary constructor, or after the `then` keyword in additional constructors.</span></span>

<span data-ttu-id="57a17-144">O nome do autoidentifier não precisa ser `this`.</span><span class="sxs-lookup"><span data-stu-id="57a17-144">The name of the self identifier does not have to be `this`.</span></span> <span data-ttu-id="57a17-145">Pode ser qualquer identificador válido.</span><span class="sxs-lookup"><span data-stu-id="57a17-145">It can be any valid identifier.</span></span>

## <a name="assigning-values-to-properties-at-initialization"></a><span data-ttu-id="57a17-146">Atribuindo valores a propriedades na inicialização</span><span class="sxs-lookup"><span data-stu-id="57a17-146">Assigning Values to Properties at Initialization</span></span>

<span data-ttu-id="57a17-147">Você pode atribuir valores às propriedades de um objeto de classe no código de inicialização acrescentando uma lista de atribuições do formulário `property = value` à lista de argumentos para um construtor.</span><span class="sxs-lookup"><span data-stu-id="57a17-147">You can assign values to the properties of a class object in the initialization code by appending a list of assignments of the form `property = value` to the argument list for a constructor.</span></span> <span data-ttu-id="57a17-148">Isso será mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="57a17-148">This is shown in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="57a17-149">A seguinte versão do código anterior ilustra a combinação de argumentos comuns, argumentos opcionais e configurações de propriedade em uma chamada de construtor.</span><span class="sxs-lookup"><span data-stu-id="57a17-149">The following version of the previous code illustrates the combination of ordinary arguments, optional arguments, and property settings in one constructor call.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a><span data-ttu-id="57a17-150">Construtores na classe herdada</span><span class="sxs-lookup"><span data-stu-id="57a17-150">Constructors in inherited class</span></span>

<span data-ttu-id="57a17-151">Ao herdar de uma classe base que tem um construtor, você deve especificar seus argumentos na cláusula Inherit.</span><span class="sxs-lookup"><span data-stu-id="57a17-151">When inheriting from a base class that has a constructor, you must specify its arguments in the inherit clause.</span></span> <span data-ttu-id="57a17-152">Para obter mais informações, consulte [construtores e herança](../inheritance.md#constructors-and-inheritance).</span><span class="sxs-lookup"><span data-stu-id="57a17-152">For more information, see [Constructors and inheritance](../inheritance.md#constructors-and-inheritance).</span></span>

## <a name="static-constructors-or-type-constructors"></a><span data-ttu-id="57a17-153">Construtores estáticos ou construtores de tipo</span><span class="sxs-lookup"><span data-stu-id="57a17-153">Static Constructors or Type Constructors</span></span>

<span data-ttu-id="57a17-154">Além de especificar o código para criar objetos, static `let` e `do` bindings podem ser criados em tipos de classe que são executados antes de o tipo ser usado pela primeira vez para executar a inicialização no nível de tipo.</span><span class="sxs-lookup"><span data-stu-id="57a17-154">In addition to specifying code for creating objects, static `let` and `do` bindings can be authored in class types that execute before the type is first used to perform initialization at the type level.</span></span> <span data-ttu-id="57a17-155">Para obter mais informações, consulte [ `let` associações em classes](let-bindings-in-classes.md) e [ `do` associações em classes](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="57a17-155">For more information, see [`let` Bindings in Classes](let-bindings-in-classes.md) and [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="57a17-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="57a17-156">See also</span></span>

- [<span data-ttu-id="57a17-157">Membros</span><span class="sxs-lookup"><span data-stu-id="57a17-157">Members</span></span>](index.md)
