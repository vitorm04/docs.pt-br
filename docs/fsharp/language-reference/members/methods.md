---
title: Métodos (F#)
description: 'Saiba como um método de F # é uma função associada a um tipo que são usadas para expor e implementar a funcionalidade e o comportamento de objetos e tipos.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: e73e4f8ea6979de3b0d5403fcb31275e99e9fa5f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="methods"></a><span data-ttu-id="06132-103">Métodos</span><span class="sxs-lookup"><span data-stu-id="06132-103">Methods</span></span>

<span data-ttu-id="06132-104">Um *método* é uma função que está associada um tipo.</span><span class="sxs-lookup"><span data-stu-id="06132-104">A *method* is a function that is associated with a type.</span></span> <span data-ttu-id="06132-105">Em programação orientada a objeto, os métodos são usados para expor e implementar a funcionalidade e o comportamento de objetos e tipos.</span><span class="sxs-lookup"><span data-stu-id="06132-105">In object-oriented programming, methods are used to expose and implement the functionality and behavior of objects and types.</span></span>


## <a name="syntax"></a><span data-ttu-id="06132-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06132-106">Syntax</span></span>

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-nameparameter-list [ : return-type ]=
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member self-identifier.method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member [inline] self-identifier.method-name : type-signature
[ attributes ]
default member [inline] self-identifier.method-nameparameter-list[ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override member [inline] self-identifier.method-nameparameter-list [ : return-type ]=
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue([ default-value ])>] input) [ : return-type ]
```

## <a name="remarks"></a><span data-ttu-id="06132-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="06132-107">Remarks</span></span>
<span data-ttu-id="06132-108">Na sintaxe anterior, você pode ver as várias formas de definições e declarações de método.</span><span class="sxs-lookup"><span data-stu-id="06132-108">In the previous syntax, you can see the various forms of method declarations and definitions.</span></span> <span data-ttu-id="06132-109">Mais corpos de método, uma quebra de linha segue o sinal de igual (=) e o corpo do método inteiro é recuado.</span><span class="sxs-lookup"><span data-stu-id="06132-109">In longer method bodies, a line break follows the equal sign (=), and the whole method body is indented.</span></span>

<span data-ttu-id="06132-110">Atributos podem ser aplicados a qualquer declaração de método.</span><span class="sxs-lookup"><span data-stu-id="06132-110">Attributes can be applied to any method declaration.</span></span> <span data-ttu-id="06132-111">Eles precedem a sintaxe para uma definição de método e geralmente são listados em uma linha separada.</span><span class="sxs-lookup"><span data-stu-id="06132-111">They precede the syntax for a method definition and are usually listed on a separate line.</span></span> <span data-ttu-id="06132-112">Para obter mais informações, consulte [Atributos](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="06132-112">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="06132-113">Métodos podem ser marcados como `inline`.</span><span class="sxs-lookup"><span data-stu-id="06132-113">Methods can be marked `inline`.</span></span> <span data-ttu-id="06132-114">Para saber mais sobre `inline`, veja [Funções embutidas](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="06132-114">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

<span data-ttu-id="06132-115">Métodos embutido não podem ser usado recursivamente dentro do tipo; não é necessário usar explicitamente o `rec` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="06132-115">Non-inline methods can be used recursively within the type; there is no need to explicitly use the `rec` keyword.</span></span>


## <a name="instance-methods"></a><span data-ttu-id="06132-116">Métodos de instância</span><span class="sxs-lookup"><span data-stu-id="06132-116">Instance Methods</span></span>
<span data-ttu-id="06132-117">Métodos de instância são declarados com a `member` palavra-chave e uma *identificador Self*, seguido por um ponto (.) e o nome do método e parâmetros.</span><span class="sxs-lookup"><span data-stu-id="06132-117">Instance methods are declared with the `member` keyword and a *self-identifier*, followed by a period (.) and the method name and parameters.</span></span> <span data-ttu-id="06132-118">Como é o caso para `let` associações, o *a lista de parâmetros* pode ser um padrão.</span><span class="sxs-lookup"><span data-stu-id="06132-118">As is the case for `let` bindings, the *parameter-list* can be a pattern.</span></span> <span data-ttu-id="06132-119">Normalmente, você coloque método parâmetros entre parênteses na forma de tupla, que é os modo como os métodos são exibidos em F # quando elas são criadas em outras linguagens do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="06132-119">Typically, you enclose method parameters in parentheses in a tuple form, which is the way methods appear in F# when they are created in other .NET Framework languages.</span></span> <span data-ttu-id="06132-120">No entanto, o formulário na forma curried (parâmetros separados por espaços) também é comum, e outros padrões têm suporte também.</span><span class="sxs-lookup"><span data-stu-id="06132-120">However, the curried form (parameters separated by spaces) is also common, and other patterns are supported also.</span></span>

<span data-ttu-id="06132-121">O exemplo a seguir ilustra a definição e o uso de um método de instância não-abstrato.</span><span class="sxs-lookup"><span data-stu-id="06132-121">The following example illustrates the definition and use of a non-abstract instance method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

<span data-ttu-id="06132-122">Dentro de métodos de instância, não use o identificador de autoatendimento para campos de acesso definidos usando associações let.</span><span class="sxs-lookup"><span data-stu-id="06132-122">Within instance methods, do not use the self identifier to access fields defined by using let bindings.</span></span> <span data-ttu-id="06132-123">Use o identificador de autoatendimento ao acessar outros membros e propriedades.</span><span class="sxs-lookup"><span data-stu-id="06132-123">Use the self identifier when accessing other members and properties.</span></span>


## <a name="static-methods"></a><span data-ttu-id="06132-124">Métodos estáticos</span><span class="sxs-lookup"><span data-stu-id="06132-124">Static Methods</span></span>
<span data-ttu-id="06132-125">A palavra-chave `static` é usado para especificar que um método pode ser chamado sem uma instância e não está associado uma instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="06132-125">The keyword `static` is used to specify that a method can be called without an instance and is not associated with an object instance.</span></span> <span data-ttu-id="06132-126">Caso contrário, os métodos são métodos de instância.</span><span class="sxs-lookup"><span data-stu-id="06132-126">Otherwise, methods are instance methods.</span></span>

<span data-ttu-id="06132-127">O exemplo na próxima seção mostra os campos declarados com o `let` palavra-chave, membros de propriedade declarado com o `member` palavra-chave e um método estático declarado com o `static` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="06132-127">The example in the next section shows fields declared with the `let` keyword, property members declared with the `member` keyword, and a static method declared with the `static` keyword.</span></span>

<span data-ttu-id="06132-128">O exemplo a seguir ilustra a definição e o uso de métodos estáticos.</span><span class="sxs-lookup"><span data-stu-id="06132-128">The following example illustrates the definition and use of static methods.</span></span> <span data-ttu-id="06132-129">Suponha que essas definições de método em de `SomeType` classe na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="06132-129">Assume that these method definitions are in the `SomeType` class in the previous section.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a><span data-ttu-id="06132-130">Métodos abstratos e virtuais</span><span class="sxs-lookup"><span data-stu-id="06132-130">Abstract and Virtual Methods</span></span>
<span data-ttu-id="06132-131">A palavra-chave `abstract` indica que um método tem um slot de expedição virtual e pode não ter uma definição de classe.</span><span class="sxs-lookup"><span data-stu-id="06132-131">The keyword `abstract` indicates that a method has a virtual dispatch slot and might not have a definition in the class.</span></span> <span data-ttu-id="06132-132">Um *slot de expedição virtual* é uma entrada em uma tabela interna de funções que é usada em tempo de execução para procurar a função virtual chamadas em um tipo orientada a objeto.</span><span class="sxs-lookup"><span data-stu-id="06132-132">A *virtual dispatch slot* is an entry in an internally maintained table of functions that is used at run time to look up virtual function calls in an object-oriented type.</span></span> <span data-ttu-id="06132-133">O mecanismo de expedição virtual é o mecanismo que implementa *polimorfismo*, um recurso importante de programação orientada a objeto.</span><span class="sxs-lookup"><span data-stu-id="06132-133">The virtual dispatch mechanism is the mechanism that implements *polymorphism*, an important feature of object-oriented programming.</span></span> <span data-ttu-id="06132-134">É uma classe que tem pelo menos um método abstrato sem uma definição de um *classe abstrata*, que significa que nenhuma instância pode ser criada dessa classe.</span><span class="sxs-lookup"><span data-stu-id="06132-134">A class that has at least one abstract method without a definition is an *abstract class*, which means that no instances can be created of that class.</span></span> <span data-ttu-id="06132-135">Para obter mais informações sobre classes abstratas, consulte [Classes abstratas](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="06132-135">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

<span data-ttu-id="06132-136">Declarações de método abstract não incluir um corpo de método.</span><span class="sxs-lookup"><span data-stu-id="06132-136">Abstract method declarations do not include a method body.</span></span> <span data-ttu-id="06132-137">Em vez disso, o nome do método é seguido por dois-pontos (:) e uma assinatura de tipo para o método.</span><span class="sxs-lookup"><span data-stu-id="06132-137">Instead, the name of the method is followed by a colon (:) and a type signature for the method.</span></span> <span data-ttu-id="06132-138">A assinatura de tipo de um método é o mesmo que o mostrado pelo IntelliSense quando você pausa o ponteiro do mouse sobre um nome de método no código Editor do Visual Studio, exceto sem nomes de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="06132-138">The type signature of a method is the same as that shown by IntelliSense when you pause the mouse pointer over a method name in the Visual Studio Code Editor, except without parameter names.</span></span> <span data-ttu-id="06132-139">Assinaturas de tipo também são exibidas pelo interpretador, fsi.exe, quando você estiver trabalhando interativamente.</span><span class="sxs-lookup"><span data-stu-id="06132-139">Type signatures are also displayed by the interpreter, fsi.exe, when you are working interactively.</span></span> <span data-ttu-id="06132-140">A assinatura de tipo de um método é formada por lista os tipos de parâmetros, seguidos pelo tipo de retorno, com símbolos de separador apropriado.</span><span class="sxs-lookup"><span data-stu-id="06132-140">The type signature of a method is formed by listing out the types of the parameters, followed by the return type, with appropriate separator symbols.</span></span> <span data-ttu-id="06132-141">Na forma curried parâmetros são separados por `->` e parâmetros de tupla são separados por `*`.</span><span class="sxs-lookup"><span data-stu-id="06132-141">Curried parameters are separated by `->` and tuple parameters are separated by `*`.</span></span> <span data-ttu-id="06132-142">O valor de retorno sempre é separado dos argumentos por um `->` símbolo.</span><span class="sxs-lookup"><span data-stu-id="06132-142">The return value is always separated from the arguments by a `->` symbol.</span></span> <span data-ttu-id="06132-143">Parênteses podem ser usados para agrupar parâmetros complexos, como quando um tipo de função é um parâmetro, ou para indicar quando uma tupla é tratada como um único parâmetro em vez de dois parâmetros.</span><span class="sxs-lookup"><span data-stu-id="06132-143">Parentheses can be used to group complex parameters, such as when a function type is a parameter, or to indicate when a tuple is treated as a single parameter rather than as two parameters.</span></span>

<span data-ttu-id="06132-144">Você também pode fornecer definições padrão de métodos abstratos adicionando a definição para a classe e usando o `default` palavra-chave, conforme mostrado no bloco de sintaxe neste tópico.</span><span class="sxs-lookup"><span data-stu-id="06132-144">You can also give abstract methods default definitions by adding the definition to the class and using the `default` keyword, as shown in the syntax block in this topic.</span></span> <span data-ttu-id="06132-145">Um método abstrato que tenha uma definição na mesma classe é equivalente a um método virtual de outras linguagens do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="06132-145">An abstract method that has a definition in the same class is equivalent to a virtual method in other .NET Framework languages.</span></span> <span data-ttu-id="06132-146">Se existe ou não uma definição, o `abstract` palavra-chave cria um novo slot de expedição na tabela de função virtual para a classe.</span><span class="sxs-lookup"><span data-stu-id="06132-146">Whether or not a definition exists, the `abstract` keyword creates a new dispatch slot in the virtual function table for the class.</span></span>

<span data-ttu-id="06132-147">Independentemente de se uma classe base implementa seus métodos abstratos, classes derivadas podem fornecer implementações de métodos abstratos.</span><span class="sxs-lookup"><span data-stu-id="06132-147">Regardless of whether a base class implements its abstract methods, derived classes can provide implementations of abstract methods.</span></span> <span data-ttu-id="06132-148">Para implementar um método abstrato em uma classe derivada, defina um método que tem o mesmo nome e assinatura na classe derivada, exceto o uso de `override` ou `default` palavra-chave e forneça o corpo do método.</span><span class="sxs-lookup"><span data-stu-id="06132-148">To implement an abstract method in a derived class, define a method that has the same name and signature in the derived class, except use the `override` or `default` keyword, and provide the method body.</span></span> <span data-ttu-id="06132-149">As palavras-chave `override` e `default` têm exatamente o mesmo significado.</span><span class="sxs-lookup"><span data-stu-id="06132-149">The keywords `override` and `default` mean exactly the same thing.</span></span> <span data-ttu-id="06132-150">Use `override` se o novo método substitui uma implementação da classe base; use `default` quando você cria uma implementação na mesma classe como abstrata declaração original.</span><span class="sxs-lookup"><span data-stu-id="06132-150">Use `override` if the new method overrides a base class implementation; use `default` when you create an implementation in the same class as the original abstract declaration.</span></span> <span data-ttu-id="06132-151">Não use o `abstract` palavra-chave no método que implementa o método foi declarado abstrato de classe base.</span><span class="sxs-lookup"><span data-stu-id="06132-151">Do not use the `abstract` keyword on the method that implements the method that was declared abstract in the base class.</span></span>

<span data-ttu-id="06132-152">O exemplo a seguir ilustra um método abstrato `Rotate` que tem uma implementação do padrão, o equivalente de um método virtual do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="06132-152">The following example illustrates an abstract method `Rotate` that has a default implementation, the equivalent of a .NET Framework virtual method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

<span data-ttu-id="06132-153">O exemplo a seguir ilustra uma classe derivada que substitui um método de classe base.</span><span class="sxs-lookup"><span data-stu-id="06132-153">The following example illustrates a derived class that overrides a base class method.</span></span> <span data-ttu-id="06132-154">Nesse caso, a substituição altera o comportamento para que o método não fará nada.</span><span class="sxs-lookup"><span data-stu-id="06132-154">In this case, the override changes the behavior so that the method does nothing.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a><span data-ttu-id="06132-155">Métodos Sobrecarregados</span><span class="sxs-lookup"><span data-stu-id="06132-155">Overloaded Methods</span></span>
<span data-ttu-id="06132-156">Métodos sobrecarregados são métodos que têm nomes idênticos em um determinado tipo, mas com argumentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="06132-156">Overloaded methods are methods that have identical names in a given type but that have different arguments.</span></span> <span data-ttu-id="06132-157">Em F #, argumentos opcionais são geralmente usados em vez de métodos sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="06132-157">In F#, optional arguments are usually used instead of overloaded methods.</span></span> <span data-ttu-id="06132-158">No entanto, os métodos sobrecarregados são permitidos no idioma, desde que os argumentos na forma de tupla, formulário na forma curried não.</span><span class="sxs-lookup"><span data-stu-id="06132-158">However, overloaded methods are permitted in the language, provided that the arguments are in tuple form, not curried form.</span></span>

## <a name="optional-arguments"></a><span data-ttu-id="06132-159">Argumentos opcionais</span><span class="sxs-lookup"><span data-stu-id="06132-159">Optional Arguments</span></span>

<span data-ttu-id="06132-160">A partir do F # 4.1, você pode ter argumentos opcionais com um valor de parâmetro padrão também nos métodos.</span><span class="sxs-lookup"><span data-stu-id="06132-160">Starting with F# 4.1, you can also have optional arguments with a default parameter value in methods.</span></span>  <span data-ttu-id="06132-161">Isso é para ajudar a facilitar a interoperação com código c#.</span><span class="sxs-lookup"><span data-stu-id="06132-161">This is to help facilitate interoperation with C# code.</span></span>  <span data-ttu-id="06132-162">O exemplo a seguir demonstra a sintaxe:</span><span class="sxs-lookup"><span data-stu-id="06132-162">The following example demonstrates the syntax:</span></span>

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

<span data-ttu-id="06132-163">Observe que o valor passado para `DefaultParameterValue` deve corresponder ao tipo de entrada.</span><span class="sxs-lookup"><span data-stu-id="06132-163">Note that the value passed in for `DefaultParameterValue` must match the input type.</span></span>  <span data-ttu-id="06132-164">No exemplo acima, é um `int`.</span><span class="sxs-lookup"><span data-stu-id="06132-164">In the above sample, it is an `int`.</span></span>  <span data-ttu-id="06132-165">Tentando passar um valor não inteiro em `DefaultParameterValue` resultaria em um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="06132-165">Attempting to pass a non-integer value into `DefaultParameterValue` would result in a compile error.</span></span>

## <a name="example-properties-and-methods"></a><span data-ttu-id="06132-166">Exemplo: Propriedades e métodos</span><span class="sxs-lookup"><span data-stu-id="06132-166">Example: Properties and Methods</span></span>
<span data-ttu-id="06132-167">O exemplo a seguir contém um tipo que tem exemplos de campos, funções private, propriedades e um método estático.</span><span class="sxs-lookup"><span data-stu-id="06132-167">The following example contains a type that has examples of fields, private functions, properties, and a static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a><span data-ttu-id="06132-168">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06132-168">See Also</span></span>
[<span data-ttu-id="06132-169">Membros</span><span class="sxs-lookup"><span data-stu-id="06132-169">Members</span></span>](index.md)
