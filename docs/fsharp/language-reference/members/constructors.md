---
title: Construtores
description: Saiba como definir e usar construtores em F# para criar e inicializar objetos de classe e estrutura.
ms.date: 05/16/2016
ms.openlocfilehash: 34989e2877b29f6f9fe1f6cc05e3fd7c90a1306a
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612069"
---
# <a name="constructors"></a><span data-ttu-id="e6736-103">Construtores</span><span class="sxs-lookup"><span data-stu-id="e6736-103">Constructors</span></span>

<span data-ttu-id="e6736-104">Este tópico descreve como definir e usar construtores para criar e inicializar objetos de classe e estrutura.</span><span class="sxs-lookup"><span data-stu-id="e6736-104">This topic describes how to define and use constructors to create and initialize class and structure objects.</span></span>

## <a name="construction-of-class-objects"></a><span data-ttu-id="e6736-105">Construção de objetos de classe</span><span class="sxs-lookup"><span data-stu-id="e6736-105">Construction of Class Objects</span></span>

<span data-ttu-id="e6736-106">Os objetos dos tipos de classe tiverem construtores.</span><span class="sxs-lookup"><span data-stu-id="e6736-106">Objects of class types have constructors.</span></span> <span data-ttu-id="e6736-107">Há dois tipos de construtores.</span><span class="sxs-lookup"><span data-stu-id="e6736-107">There are two kinds of constructors.</span></span> <span data-ttu-id="e6736-108">Um é o construtor primário, cujos parâmetros são exibidos entre parênteses, logo após o nome do tipo.</span><span class="sxs-lookup"><span data-stu-id="e6736-108">One is the primary constructor, whose parameters appear in parentheses just after the type name.</span></span> <span data-ttu-id="e6736-109">Especificar construtores adicionais opcionais, outros, usando o `new` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="e6736-109">You specify other, optional additional constructors by using the `new` keyword.</span></span> <span data-ttu-id="e6736-110">Todos esses construtores adicionais devem chamar o construtor primário.</span><span class="sxs-lookup"><span data-stu-id="e6736-110">Any such additional constructors must call the primary constructor.</span></span>

<span data-ttu-id="e6736-111">O construtor primário contém `let` e `do` associações que aparecem no início da definição de classe.</span><span class="sxs-lookup"><span data-stu-id="e6736-111">The primary constructor contains `let` and `do` bindings that appear at the start of the class definition.</span></span> <span data-ttu-id="e6736-112">Um `let` associação declara campos particulares e métodos da classe; um `do` associação executa o código.</span><span class="sxs-lookup"><span data-stu-id="e6736-112">A `let` binding declares private fields and methods of the class; a `do` binding executes code.</span></span> <span data-ttu-id="e6736-113">Para obter mais informações sobre `let` associações em construtores de classe, consulte [ `let` associações em Classes](let-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="e6736-113">For more information about `let` bindings in class constructors, see [`let` Bindings in Classes](let-bindings-in-classes.md).</span></span> <span data-ttu-id="e6736-114">Para obter mais informações sobre `do` associações em construtores, consulte [ `do` associações em Classes](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="e6736-114">For more information about `do` bindings in constructors, see [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

<span data-ttu-id="e6736-115">Independentemente se o construtor que você deseja chamar é um construtor primário ou um construtor adicional, você pode criar objetos usando um `new` expressão, com ou sem opcional `new` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="e6736-115">Regardless of whether the constructor you want to call is a primary constructor or an additional constructor, you can create objects by using a `new` expression, with or without the optional `new` keyword.</span></span> <span data-ttu-id="e6736-116">Inicializar seus objetos junto com os argumentos de construtor, qualquer um, listando os argumentos na ordem e separados por vírgulas e colocados entre parênteses, ou usando argumentos nomeados e os valores entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="e6736-116">You initialize your objects together with constructor arguments, either by listing the arguments in order and separated by commas and enclosed in parentheses, or by using named arguments and values in parentheses.</span></span> <span data-ttu-id="e6736-117">Você também pode definir propriedades em um objeto durante a construção do objeto usando os nomes de propriedade e atribuir valores, assim como você usa chamado argumentos de construtor.</span><span class="sxs-lookup"><span data-stu-id="e6736-117">You can also set properties on an object during the construction of the object by using the property names and assigning values just as you use named constructor arguments.</span></span>

<span data-ttu-id="e6736-118">O código a seguir ilustra uma classe que tem um construtor e várias maneiras de criar objetos.</span><span class="sxs-lookup"><span data-stu-id="e6736-118">The following code illustrates a class that has a constructor and various ways of creating objects.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3501.fs)]

<span data-ttu-id="e6736-119">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="e6736-119">The output is as follows.</span></span>

```console
Initialized object that has coordinates (1, 2, 3)
Initialized object that has coordinates (4, 5, 6)
Initialized object that has coordinates (7, 8, 9)
Initialized object that has coordinates (0, 0, 0)
```

## <a name="construction-of-structures"></a><span data-ttu-id="e6736-120">Construção de estruturas</span><span class="sxs-lookup"><span data-stu-id="e6736-120">Construction of Structures</span></span>

<span data-ttu-id="e6736-121">As estruturas seguem todas as regras de classes.</span><span class="sxs-lookup"><span data-stu-id="e6736-121">Structures follow all the rules of classes.</span></span> <span data-ttu-id="e6736-122">Portanto, você pode ter um construtor primário, e você pode fornecer construtores adicionais usando `new`.</span><span class="sxs-lookup"><span data-stu-id="e6736-122">Therefore, you can have a primary constructor, and you can provide additional constructors by using `new`.</span></span> <span data-ttu-id="e6736-123">No entanto, há uma diferença importante entre classes e estruturas: estruturas podem ter um construtor padrão (ou seja, um sem argumentos), mesmo se nenhum construtor primário é definido.</span><span class="sxs-lookup"><span data-stu-id="e6736-123">However, there is one important difference between structures and classes: structures can have a default constructor (that is, one with no arguments) even if no primary constructor is defined.</span></span> <span data-ttu-id="e6736-124">O construtor padrão inicializa todos os campos para o valor padrão para esse tipo, geralmente zero ou seu equivalente.</span><span class="sxs-lookup"><span data-stu-id="e6736-124">The default constructor initializes all the fields to the default value for that type, usually zero or its equivalent.</span></span> <span data-ttu-id="e6736-125">Os construtores que você define para estruturas devem ter pelo menos um argumento para que eles não entrem em conflito com o construtor padrão.</span><span class="sxs-lookup"><span data-stu-id="e6736-125">Any constructors that you define for structures must have at least one argument so that they do not conflict with the default constructor.</span></span>

<span data-ttu-id="e6736-126">Além disso, a estruturas geralmente têm campos que são criados usando o `val` palavra-chave; as classes também podem ter esses campos.</span><span class="sxs-lookup"><span data-stu-id="e6736-126">Also, structures often have fields that are created by using the `val` keyword; classes can also have these fields.</span></span> <span data-ttu-id="e6736-127">Estruturas e classes que têm campos definidos usando o `val` palavra-chave também pode ser inicializado em construtores adicionais usando expressões de registro, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e6736-127">Structures and classes that have fields defined by using the `val` keyword can also be initialized in additional constructors by using record expressions, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3502.fs)]

<span data-ttu-id="e6736-128">Para obter mais informações, consulte [campos explícitos: O `val` palavra-chave](explicit-fields-the-val-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="e6736-128">For more information, see [Explicit Fields: The `val` Keyword](explicit-fields-the-val-keyword.md).</span></span>

## <a name="executing-side-effects-in-constructors"></a><span data-ttu-id="e6736-129">Execução de efeitos colaterais em construtores</span><span class="sxs-lookup"><span data-stu-id="e6736-129">Executing Side Effects in Constructors</span></span>

<span data-ttu-id="e6736-130">Um construtor primário em uma classe pode executar código em um `do` associação.</span><span class="sxs-lookup"><span data-stu-id="e6736-130">A primary constructor in a class can execute code in a `do` binding.</span></span> <span data-ttu-id="e6736-131">No entanto, e se você tiver que executar código em um construtor adicional, sem um `do` associação?</span><span class="sxs-lookup"><span data-stu-id="e6736-131">However, what if you have to execute code in an additional constructor, without a `do` binding?</span></span> <span data-ttu-id="e6736-132">Para fazer isso, você deve usar o `then` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="e6736-132">To do this, you use the `then` keyword.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3503.fs)]

<span data-ttu-id="e6736-133">Os efeitos colaterais do construtor primário ainda executar.</span><span class="sxs-lookup"><span data-stu-id="e6736-133">The side effects of the primary constructor still execute.</span></span> <span data-ttu-id="e6736-134">Portanto, a saída é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="e6736-134">Therefore, the output is as follows.</span></span>

```console
Created a person object.
Created a person object.
Created an invalid person object.
```

## <a name="self-identifiers-in-constructors"></a><span data-ttu-id="e6736-135">Autoidentificadores em construtores</span><span class="sxs-lookup"><span data-stu-id="e6736-135">Self Identifiers in Constructors</span></span>

<span data-ttu-id="e6736-136">Em outros membros, você deve fornecer um nome para o objeto atual na definição de cada membro.</span><span class="sxs-lookup"><span data-stu-id="e6736-136">In other members, you provide a name for the current object in the definition of each member.</span></span> <span data-ttu-id="e6736-137">Você também pode colocar o identificador de auto na primeira linha da definição da classe usando o `as` imediatamente após os parâmetros do construtor de palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="e6736-137">You can also put the self identifier on the first line of the class definition by using the `as` keyword immediately following the constructor parameters.</span></span> <span data-ttu-id="e6736-138">O exemplo a seguir ilustra essa sintaxe.</span><span class="sxs-lookup"><span data-stu-id="e6736-138">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3504.fs)]

<span data-ttu-id="e6736-139">Em construtores adicionais, você também pode definir um identificador de self, colocando o `as` cláusula logo após os parâmetros do construtor.</span><span class="sxs-lookup"><span data-stu-id="e6736-139">In additional constructors, you can also define a self identifier by putting the `as` clause right after the constructor parameters.</span></span> <span data-ttu-id="e6736-140">O exemplo a seguir ilustra essa sintaxe.</span><span class="sxs-lookup"><span data-stu-id="e6736-140">The following example illustrates this syntax.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3505.fs)]

<span data-ttu-id="e6736-141">Problemas podem ocorrer quando você tentar usar um objeto antes que ele está totalmente definido.</span><span class="sxs-lookup"><span data-stu-id="e6736-141">Problems can occur when you try to use an object before it is fully defined.</span></span> <span data-ttu-id="e6736-142">Portanto, os usos do identificador de self podem causar o compilador emite um aviso e insira verificações adicionais para garantir que os membros de um objeto não são acessados antes que o objeto é inicializado.</span><span class="sxs-lookup"><span data-stu-id="e6736-142">Therefore, uses of the self identifier can cause the compiler to emit a warning and insert additional checks to ensure the members of an object are not accessed before the object is initialized.</span></span> <span data-ttu-id="e6736-143">Você deve usar apenas o identificador de autoatendimento na `do` associações do construtor primário, ou após o `then` palavra-chave em construtores adicionais.</span><span class="sxs-lookup"><span data-stu-id="e6736-143">You should only use the self identifier in the `do` bindings of the primary constructor, or after the `then` keyword in additional constructors.</span></span>

<span data-ttu-id="e6736-144">O nome do identificador self não precisa ser `this`.</span><span class="sxs-lookup"><span data-stu-id="e6736-144">The name of the self identifier does not have to be `this`.</span></span> <span data-ttu-id="e6736-145">Ele pode ser qualquer identificador válido.</span><span class="sxs-lookup"><span data-stu-id="e6736-145">It can be any valid identifier.</span></span>

## <a name="assigning-values-to-properties-at-initialization"></a><span data-ttu-id="e6736-146">Atribuir valores às propriedades de inicialização</span><span class="sxs-lookup"><span data-stu-id="e6736-146">Assigning Values to Properties at Initialization</span></span>

<span data-ttu-id="e6736-147">Você pode atribuir valores às propriedades de um objeto de classe no código de inicialização, acrescentando uma lista de atribuições do formulário `property = value` à lista de argumentos para um construtor.</span><span class="sxs-lookup"><span data-stu-id="e6736-147">You can assign values to the properties of a class object in the initialization code by appending a list of assignments of the form `property = value` to the argument list for a constructor.</span></span> <span data-ttu-id="e6736-148">Isso será mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="e6736-148">This is shown in the following code example.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3506.fs)]

<span data-ttu-id="e6736-149">A versão seguinte do código anterior ilustra a combinação de argumentos comuns, argumentos opcionais e as configurações de propriedade na chamada de um construtor.</span><span class="sxs-lookup"><span data-stu-id="e6736-149">The following version of the previous code illustrates the combination of ordinary arguments, optional arguments, and property settings in one constructor call.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-2/snippet3507.fs)]

## <a name="constructors-in-inherited-class"></a><span data-ttu-id="e6736-150">Construtores de classe herdada</span><span class="sxs-lookup"><span data-stu-id="e6736-150">Constructors in inherited class</span></span>

<span data-ttu-id="e6736-151">Ao herdar de uma classe base que tem um construtor, você deve especificar seus argumentos na cláusula herdar.</span><span class="sxs-lookup"><span data-stu-id="e6736-151">When inheriting from a base class that has a constructor, you must specify its arguments in the inherit clause.</span></span> <span data-ttu-id="e6736-152">Para obter mais informações, consulte [construtores e herança](../inheritance.md#constructors-and-inheritance).</span><span class="sxs-lookup"><span data-stu-id="e6736-152">For more information, see [Constructors and inheritance](../inheritance.md#constructors-and-inheritance).</span></span>

## <a name="static-constructors-or-type-constructors"></a><span data-ttu-id="e6736-153">Construtores estáticos ou construtores de tipo</span><span class="sxs-lookup"><span data-stu-id="e6736-153">Static Constructors or Type Constructors</span></span>

<span data-ttu-id="e6736-154">Além de especificar o código para a criação de objetos, estáticos `let` e `do` associações podem ser criadas de tipos de classe que é executado antes que o tipo é usado pela primeira vez para executar a inicialização no nível do tipo.</span><span class="sxs-lookup"><span data-stu-id="e6736-154">In addition to specifying code for creating objects, static `let` and `do` bindings can be authored in class types that execute before the type is first used to perform initialization at the type level.</span></span> <span data-ttu-id="e6736-155">Para obter mais informações, consulte [ `let` associações em Classes](let-bindings-in-classes.md) e [ `do` associações em Classes](do-bindings-in-classes.md).</span><span class="sxs-lookup"><span data-stu-id="e6736-155">For more information, see [`let` Bindings in Classes](let-bindings-in-classes.md) and [`do` Bindings in Classes](do-bindings-in-classes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e6736-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6736-156">See also</span></span>

- [<span data-ttu-id="e6736-157">Membros</span><span class="sxs-lookup"><span data-stu-id="e6736-157">Members</span></span>](index.md)