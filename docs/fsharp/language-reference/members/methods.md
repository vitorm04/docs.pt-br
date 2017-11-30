---
title: "Métodos (F#)"
description: "Saiba como um método de F # é uma função associada a um tipo que são usadas para expor e implementar a funcionalidade e o comportamento de objetos e tipos."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 1febab3b-c922-49c6-889f-c22db107710c
ms.openlocfilehash: dae31abe6bb0773671b889646c9cceb410a492cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="methods"></a><span data-ttu-id="9f165-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="9f165-104">Methods</span></span>

<span data-ttu-id="9f165-105">Um *método* é uma função que está associada um tipo.</span><span class="sxs-lookup"><span data-stu-id="9f165-105">A *method* is a function that is associated with a type.</span></span> <span data-ttu-id="9f165-106">Em programação orientada a objeto, os métodos são usados para expor e implementar a funcionalidade e o comportamento de objetos e tipos.</span><span class="sxs-lookup"><span data-stu-id="9f165-106">In object-oriented programming, methods are used to expose and implement the functionality and behavior of objects and types.</span></span>


## <a name="syntax"></a><span data-ttu-id="9f165-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f165-107">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="9f165-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="9f165-108">Remarks</span></span>
<span data-ttu-id="9f165-109">Na sintaxe anterior, você pode ver as várias formas de definições e declarações de método.</span><span class="sxs-lookup"><span data-stu-id="9f165-109">In the previous syntax, you can see the various forms of method declarations and definitions.</span></span> <span data-ttu-id="9f165-110">Mais corpos de método, uma quebra de linha segue o sinal de igual (=) e o corpo do método inteiro é recuado.</span><span class="sxs-lookup"><span data-stu-id="9f165-110">In longer method bodies, a line break follows the equal sign (=), and the whole method body is indented.</span></span>

<span data-ttu-id="9f165-111">Atributos podem ser aplicados a qualquer declaração de método.</span><span class="sxs-lookup"><span data-stu-id="9f165-111">Attributes can be applied to any method declaration.</span></span> <span data-ttu-id="9f165-112">Eles precedem a sintaxe para uma definição de método e geralmente são listados em uma linha separada.</span><span class="sxs-lookup"><span data-stu-id="9f165-112">They precede the syntax for a method definition and are usually listed on a separate line.</span></span> <span data-ttu-id="9f165-113">Para obter mais informações, consulte [Atributos](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="9f165-113">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="9f165-114">Métodos podem ser marcados como `inline`.</span><span class="sxs-lookup"><span data-stu-id="9f165-114">Methods can be marked `inline`.</span></span> <span data-ttu-id="9f165-115">Para saber mais sobre `inline`, veja [Funções embutidas](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="9f165-115">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

<span data-ttu-id="9f165-116">Métodos embutido não podem ser usado recursivamente dentro do tipo; não é necessário usar explicitamente o `rec` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="9f165-116">Non-inline methods can be used recursively within the type; there is no need to explicitly use the `rec` keyword.</span></span>


## <a name="instance-methods"></a><span data-ttu-id="9f165-117">Métodos de instância</span><span class="sxs-lookup"><span data-stu-id="9f165-117">Instance Methods</span></span>
<span data-ttu-id="9f165-118">Métodos de instância são declarados com a `member` palavra-chave e uma *identificador Self*, seguido por um ponto (.) e o nome do método e parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9f165-118">Instance methods are declared with the `member` keyword and a *self-identifier*, followed by a period (.) and the method name and parameters.</span></span> <span data-ttu-id="9f165-119">Como é o caso para `let` associações, o *a lista de parâmetros* pode ser um padrão.</span><span class="sxs-lookup"><span data-stu-id="9f165-119">As is the case for `let` bindings, the *parameter-list* can be a pattern.</span></span> <span data-ttu-id="9f165-120">Normalmente, você coloque método parâmetros entre parênteses na forma de tupla, que é os modo como os métodos são exibidos em F # quando elas são criadas em outras linguagens do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f165-120">Typically, you enclose method parameters in parentheses in a tuple form, which is the way methods appear in F# when they are created in other .NET Framework languages.</span></span> <span data-ttu-id="9f165-121">No entanto, o formulário na forma curried (parâmetros separados por espaços) também é comum, e outros padrões têm suporte também.</span><span class="sxs-lookup"><span data-stu-id="9f165-121">However, the curried form (parameters separated by spaces) is also common, and other patterns are supported also.</span></span>

<span data-ttu-id="9f165-122">O exemplo a seguir ilustra a definição e o uso de um método de instância não-abstrato.</span><span class="sxs-lookup"><span data-stu-id="9f165-122">The following example illustrates the definition and use of a non-abstract instance method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

<span data-ttu-id="9f165-123">Dentro de métodos de instância, não use o identificador de autoatendimento para campos de acesso definidos usando associações let.</span><span class="sxs-lookup"><span data-stu-id="9f165-123">Within instance methods, do not use the self identifier to access fields defined by using let bindings.</span></span> <span data-ttu-id="9f165-124">Use o identificador de autoatendimento ao acessar outros membros e propriedades.</span><span class="sxs-lookup"><span data-stu-id="9f165-124">Use the self identifier when accessing other members and properties.</span></span>


## <a name="static-methods"></a><span data-ttu-id="9f165-125">Métodos estáticos</span><span class="sxs-lookup"><span data-stu-id="9f165-125">Static Methods</span></span>
<span data-ttu-id="9f165-126">A palavra-chave `static` é usado para especificar que um método pode ser chamado sem uma instância e não está associado uma instância do objeto.</span><span class="sxs-lookup"><span data-stu-id="9f165-126">The keyword `static` is used to specify that a method can be called without an instance and is not associated with an object instance.</span></span> <span data-ttu-id="9f165-127">Caso contrário, os métodos são métodos de instância.</span><span class="sxs-lookup"><span data-stu-id="9f165-127">Otherwise, methods are instance methods.</span></span>

<span data-ttu-id="9f165-128">O exemplo na próxima seção mostra os campos declarados com o `let` palavra-chave, membros de propriedade declarado com o `member` palavra-chave e um método estático declarado com o `static` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="9f165-128">The example in the next section shows fields declared with the `let` keyword, property members declared with the `member` keyword, and a static method declared with the `static` keyword.</span></span>

<span data-ttu-id="9f165-129">O exemplo a seguir ilustra a definição e o uso de métodos estáticos.</span><span class="sxs-lookup"><span data-stu-id="9f165-129">The following example illustrates the definition and use of static methods.</span></span> <span data-ttu-id="9f165-130">Suponha que essas definições de método em de `SomeType` classe na seção anterior.</span><span class="sxs-lookup"><span data-stu-id="9f165-130">Assume that these method definitions are in the `SomeType` class in the previous section.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a><span data-ttu-id="9f165-131">Métodos abstratos e virtuais</span><span class="sxs-lookup"><span data-stu-id="9f165-131">Abstract and Virtual Methods</span></span>
<span data-ttu-id="9f165-132">A palavra-chave `abstract` indica que um método tem um slot de expedição virtual e pode não ter uma definição de classe.</span><span class="sxs-lookup"><span data-stu-id="9f165-132">The keyword `abstract` indicates that a method has a virtual dispatch slot and might not have a definition in the class.</span></span> <span data-ttu-id="9f165-133">Um *slot de expedição virtual* é uma entrada em uma tabela interna de funções que é usada em tempo de execução para procurar a função virtual chamadas em um tipo orientada a objeto.</span><span class="sxs-lookup"><span data-stu-id="9f165-133">A *virtual dispatch slot* is an entry in an internally maintained table of functions that is used at run time to look up virtual function calls in an object-oriented type.</span></span> <span data-ttu-id="9f165-134">O mecanismo de expedição virtual é o mecanismo que implementa *polimorfismo*, um recurso importante de programação orientada a objeto.</span><span class="sxs-lookup"><span data-stu-id="9f165-134">The virtual dispatch mechanism is the mechanism that implements *polymorphism*, an important feature of object-oriented programming.</span></span> <span data-ttu-id="9f165-135">É uma classe que tem pelo menos um método abstrato sem uma definição de um *classe abstrata*, que significa que nenhuma instância pode ser criada dessa classe.</span><span class="sxs-lookup"><span data-stu-id="9f165-135">A class that has at least one abstract method without a definition is an *abstract class*, which means that no instances can be created of that class.</span></span> <span data-ttu-id="9f165-136">Para obter mais informações sobre classes abstratas, consulte [Classes abstratas](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="9f165-136">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

<span data-ttu-id="9f165-137">Declarações de método abstract não incluir um corpo de método.</span><span class="sxs-lookup"><span data-stu-id="9f165-137">Abstract method declarations do not include a method body.</span></span> <span data-ttu-id="9f165-138">Em vez disso, o nome do método é seguido por dois-pontos (:) e uma assinatura de tipo para o método.</span><span class="sxs-lookup"><span data-stu-id="9f165-138">Instead, the name of the method is followed by a colon (:) and a type signature for the method.</span></span> <span data-ttu-id="9f165-139">A assinatura de tipo de um método é o mesmo que o mostrado pelo IntelliSense quando você pausa o ponteiro do mouse sobre um nome de método no código Editor do Visual Studio, exceto sem nomes de parâmetro.</span><span class="sxs-lookup"><span data-stu-id="9f165-139">The type signature of a method is the same as that shown by IntelliSense when you pause the mouse pointer over a method name in the Visual Studio Code Editor, except without parameter names.</span></span> <span data-ttu-id="9f165-140">Assinaturas de tipo também são exibidas pelo interpretador, fsi.exe, quando você estiver trabalhando interativamente.</span><span class="sxs-lookup"><span data-stu-id="9f165-140">Type signatures are also displayed by the interpreter, fsi.exe, when you are working interactively.</span></span> <span data-ttu-id="9f165-141">A assinatura de tipo de um método é formada por lista os tipos de parâmetros, seguidos pelo tipo de retorno, com símbolos de separador apropriado.</span><span class="sxs-lookup"><span data-stu-id="9f165-141">The type signature of a method is formed by listing out the types of the parameters, followed by the return type, with appropriate separator symbols.</span></span> <span data-ttu-id="9f165-142">Na forma curried parâmetros são separados por `->` e parâmetros de tupla são separados por `*`.</span><span class="sxs-lookup"><span data-stu-id="9f165-142">Curried parameters are separated by `->` and tuple parameters are separated by `*`.</span></span> <span data-ttu-id="9f165-143">O valor de retorno sempre é separado dos argumentos por um `->` símbolo.</span><span class="sxs-lookup"><span data-stu-id="9f165-143">The return value is always separated from the arguments by a `->` symbol.</span></span> <span data-ttu-id="9f165-144">Parênteses podem ser usados para agrupar parâmetros complexos, como quando um tipo de função é um parâmetro, ou para indicar quando uma tupla é tratada como um único parâmetro em vez de dois parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9f165-144">Parentheses can be used to group complex parameters, such as when a function type is a parameter, or to indicate when a tuple is treated as a single parameter rather than as two parameters.</span></span>

<span data-ttu-id="9f165-145">Você também pode fornecer definições padrão de métodos abstratos adicionando a definição para a classe e usando o `default` palavra-chave, conforme mostrado no bloco de sintaxe neste tópico.</span><span class="sxs-lookup"><span data-stu-id="9f165-145">You can also give abstract methods default definitions by adding the definition to the class and using the `default` keyword, as shown in the syntax block in this topic.</span></span> <span data-ttu-id="9f165-146">Um método abstrato que tenha uma definição na mesma classe é equivalente a um método virtual de outras linguagens do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f165-146">An abstract method that has a definition in the same class is equivalent to a virtual method in other .NET Framework languages.</span></span> <span data-ttu-id="9f165-147">Se existe ou não uma definição, o `abstract` palavra-chave cria um novo slot de expedição na tabela de função virtual para a classe.</span><span class="sxs-lookup"><span data-stu-id="9f165-147">Whether or not a definition exists, the `abstract` keyword creates a new dispatch slot in the virtual function table for the class.</span></span>

<span data-ttu-id="9f165-148">Independentemente de se uma classe base implementa seus métodos abstratos, classes derivadas podem fornecer implementações de métodos abstratos.</span><span class="sxs-lookup"><span data-stu-id="9f165-148">Regardless of whether a base class implements its abstract methods, derived classes can provide implementations of abstract methods.</span></span> <span data-ttu-id="9f165-149">Para implementar um método abstrato em uma classe derivada, defina um método que tem o mesmo nome e assinatura na classe derivada, exceto o uso de `override` ou `default` palavra-chave e forneça o corpo do método.</span><span class="sxs-lookup"><span data-stu-id="9f165-149">To implement an abstract method in a derived class, define a method that has the same name and signature in the derived class, except use the `override` or `default` keyword, and provide the method body.</span></span> <span data-ttu-id="9f165-150">As palavras-chave `override` e `default` têm exatamente o mesmo significado.</span><span class="sxs-lookup"><span data-stu-id="9f165-150">The keywords `override` and `default` mean exactly the same thing.</span></span> <span data-ttu-id="9f165-151">Use `override` se o novo método substitui uma implementação da classe base; use `default` quando você cria uma implementação na mesma classe como abstrata declaração original.</span><span class="sxs-lookup"><span data-stu-id="9f165-151">Use `override` if the new method overrides a base class implementation; use `default` when you create an implementation in the same class as the original abstract declaration.</span></span> <span data-ttu-id="9f165-152">Não use o `abstract` palavra-chave no método que implementa o método foi declarado abstrato de classe base.</span><span class="sxs-lookup"><span data-stu-id="9f165-152">Do not use the `abstract` keyword on the method that implements the method that was declared abstract in the base class.</span></span>

<span data-ttu-id="9f165-153">O exemplo a seguir ilustra um método abstrato `Rotate` que tem uma implementação do padrão, o equivalente de um método virtual do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9f165-153">The following example illustrates an abstract method `Rotate` that has a default implementation, the equivalent of a .NET Framework virtual method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

<span data-ttu-id="9f165-154">O exemplo a seguir ilustra uma classe derivada que substitui um método de classe base.</span><span class="sxs-lookup"><span data-stu-id="9f165-154">The following example illustrates a derived class that overrides a base class method.</span></span> <span data-ttu-id="9f165-155">Nesse caso, a substituição altera o comportamento para que o método não fará nada.</span><span class="sxs-lookup"><span data-stu-id="9f165-155">In this case, the override changes the behavior so that the method does nothing.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a><span data-ttu-id="9f165-156">Métodos Sobrecarregados</span><span class="sxs-lookup"><span data-stu-id="9f165-156">Overloaded Methods</span></span>
<span data-ttu-id="9f165-157">Métodos sobrecarregados são métodos que têm nomes idênticos em um determinado tipo, mas com argumentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="9f165-157">Overloaded methods are methods that have identical names in a given type but that have different arguments.</span></span> <span data-ttu-id="9f165-158">Em F #, argumentos opcionais são geralmente usados em vez de métodos sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="9f165-158">In F#, optional arguments are usually used instead of overloaded methods.</span></span> <span data-ttu-id="9f165-159">No entanto, os métodos sobrecarregados são permitidos no idioma, desde que os argumentos na forma de tupla, formulário na forma curried não.</span><span class="sxs-lookup"><span data-stu-id="9f165-159">However, overloaded methods are permitted in the language, provided that the arguments are in tuple form, not curried form.</span></span>

## <a name="optional-arguments"></a><span data-ttu-id="9f165-160">Argumentos opcionais</span><span class="sxs-lookup"><span data-stu-id="9f165-160">Optional Arguments</span></span>

<span data-ttu-id="9f165-161">A partir do F # 4.1, você pode ter argumentos opcionais com um valor de parâmetro padrão também nos métodos.</span><span class="sxs-lookup"><span data-stu-id="9f165-161">Starting with F# 4.1, you can also have optional arguments with a default parameter value in methods.</span></span>  <span data-ttu-id="9f165-162">Isso é para ajudar a facilitar a interoperação com código c#.</span><span class="sxs-lookup"><span data-stu-id="9f165-162">This is to help facilitate interoperation with C# code.</span></span>  <span data-ttu-id="9f165-163">O exemplo a seguir demonstra a sintaxe:</span><span class="sxs-lookup"><span data-stu-id="9f165-163">The following example demonstrates the syntax:</span></span>

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    __.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

<span data-ttu-id="9f165-164">Observe que o valor passado para `DefaultParameterValue` deve corresponder ao tipo de entrada.</span><span class="sxs-lookup"><span data-stu-id="9f165-164">Note that the value passed in for `DefaultParameterValue` must match the input type.</span></span>  <span data-ttu-id="9f165-165">No exemplo acima, é um `int`.</span><span class="sxs-lookup"><span data-stu-id="9f165-165">In the above sample, it is an `int`.</span></span>  <span data-ttu-id="9f165-166">Tentando passar um valor não inteiro em `DefaultParameterValue` resultaria em um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="9f165-166">Attempting to pass a non-integer value into `DefaultParameterValue` would result in a compile error.</span></span>

## <a name="example-properties-and-methods"></a><span data-ttu-id="9f165-167">Exemplo: Propriedades e métodos</span><span class="sxs-lookup"><span data-stu-id="9f165-167">Example: Properties and Methods</span></span>
<span data-ttu-id="9f165-168">O exemplo a seguir contém um tipo que tem exemplos de campos, funções private, propriedades e um método estático.</span><span class="sxs-lookup"><span data-stu-id="9f165-168">The following example contains a type that has examples of fields, private functions, properties, and a static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a><span data-ttu-id="9f165-169">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f165-169">See Also</span></span>
[<span data-ttu-id="9f165-170">Membros</span><span class="sxs-lookup"><span data-stu-id="9f165-170">Members</span></span>](index.md)
