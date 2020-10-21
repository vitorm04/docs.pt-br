---
title: Métodos
description: 'Saiba como um método F # é uma função associada a um tipo que é usado para expor e implementar a funcionalidade e o comportamento de objetos e tipos.'
ms.date: 11/04/2019
ms.openlocfilehash: 6f5ae76ea450b07763eb58d0c95b18b30f634551
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224107"
---
# <a name="methods"></a><span data-ttu-id="96ca6-103">Métodos</span><span class="sxs-lookup"><span data-stu-id="96ca6-103">Methods</span></span>

<span data-ttu-id="96ca6-104">Um *método* é uma função associada a um tipo.</span><span class="sxs-lookup"><span data-stu-id="96ca6-104">A *method* is a function that is associated with a type.</span></span> <span data-ttu-id="96ca6-105">Na programação orientada a objeto, os métodos são usados para expor e implementar a funcionalidade e o comportamento de objetos e tipos.</span><span class="sxs-lookup"><span data-stu-id="96ca6-105">In object-oriented programming, methods are used to expose and implement the functionality and behavior of objects and types.</span></span>

## <a name="syntax"></a><span data-ttu-id="96ca6-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96ca6-106">Syntax</span></span>

```fsharp
// Instance method definition.
[ attributes ]
member [inline] self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Static method definition.
[ attributes ]
static member [inline] method-name parameter-list [ : return-type ] =
    method-body

// Abstract method declaration or virtual dispatch slot.
[ attributes ]
abstract member method-name : type-signature

// Virtual method declaration and default implementation.
[ attributes ]
abstract member method-name : type-signature
[ attributes ]
default self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Override of inherited virtual method.
[ attributes ]
override self-identifier.method-name parameter-list [ : return-type ] =
    method-body

// Optional and DefaultParameterValue attributes on input parameters
[ attributes ]
[ modifier ] member [inline] self-identifier.method-name ([<Optional; DefaultParameterValue( default-value )>] input) [ : return-type ]
```

## <a name="remarks"></a><span data-ttu-id="96ca6-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="96ca6-107">Remarks</span></span>

<span data-ttu-id="96ca6-108">Na sintaxe anterior, você pode ver as várias formas de declarações e definições de método.</span><span class="sxs-lookup"><span data-stu-id="96ca6-108">In the previous syntax, you can see the various forms of method declarations and definitions.</span></span> <span data-ttu-id="96ca6-109">Em corpos de métodos mais longos, uma quebra de linha segue o sinal de igual (=) e o corpo do método inteiro é recuado.</span><span class="sxs-lookup"><span data-stu-id="96ca6-109">In longer method bodies, a line break follows the equal sign (=), and the whole method body is indented.</span></span>

<span data-ttu-id="96ca6-110">Atributos podem ser aplicados a qualquer declaração de método.</span><span class="sxs-lookup"><span data-stu-id="96ca6-110">Attributes can be applied to any method declaration.</span></span> <span data-ttu-id="96ca6-111">Elas precedem a sintaxe para uma definição de método e geralmente são listadas em uma linha separada.</span><span class="sxs-lookup"><span data-stu-id="96ca6-111">They precede the syntax for a method definition and are usually listed on a separate line.</span></span> <span data-ttu-id="96ca6-112">Para obter mais informações, consulte [Atributos](../attributes.md).</span><span class="sxs-lookup"><span data-stu-id="96ca6-112">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="96ca6-113">Os métodos podem ser marcados `inline` .</span><span class="sxs-lookup"><span data-stu-id="96ca6-113">Methods can be marked `inline`.</span></span> <span data-ttu-id="96ca6-114">Para saber mais sobre `inline`, veja [Funções embutidas](../functions/inline-functions.md).</span><span class="sxs-lookup"><span data-stu-id="96ca6-114">For information about `inline`, see [Inline Functions](../functions/inline-functions.md).</span></span>

<span data-ttu-id="96ca6-115">Métodos não embutidos podem ser usados recursivamente dentro do tipo; Não é necessário usar a `rec` palavra-chave explicitamente.</span><span class="sxs-lookup"><span data-stu-id="96ca6-115">Non-inline methods can be used recursively within the type; there is no need to explicitly use the `rec` keyword.</span></span>

## <a name="instance-methods"></a><span data-ttu-id="96ca6-116">Métodos de instância</span><span class="sxs-lookup"><span data-stu-id="96ca6-116">Instance Methods</span></span>

<span data-ttu-id="96ca6-117">Os métodos de instância são declarados com a `member` palavra-chave e um *autoidentificador*, seguidos por um ponto (.) e o nome do método e os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="96ca6-117">Instance methods are declared with the `member` keyword and a *self-identifier*, followed by a period (.) and the method name and parameters.</span></span> <span data-ttu-id="96ca6-118">Como é o caso de `let` associações, a *lista de parâmetros* pode ser um padrão.</span><span class="sxs-lookup"><span data-stu-id="96ca6-118">As is the case for `let` bindings, the *parameter-list* can be a pattern.</span></span> <span data-ttu-id="96ca6-119">Normalmente, você coloca parâmetros de método entre parênteses em um formulário de tupla, que é a maneira como os métodos aparecem em F # quando eles são criados em outros idiomas de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="96ca6-119">Typically, you enclose method parameters in parentheses in a tuple form, which is the way methods appear in F# when they are created in other .NET Framework languages.</span></span> <span data-ttu-id="96ca6-120">No entanto, o formulário na forma curried (parâmetros separados por espaços) também é comum e também há suporte para outros padrões.</span><span class="sxs-lookup"><span data-stu-id="96ca6-120">However, the curried form (parameters separated by spaces) is also common, and other patterns are supported also.</span></span>

<span data-ttu-id="96ca6-121">O exemplo a seguir ilustra a definição e o uso de um método de instância não abstrata.</span><span class="sxs-lookup"><span data-stu-id="96ca6-121">The following example illustrates the definition and use of a non-abstract instance method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3401.fs)]

<span data-ttu-id="96ca6-122">Em métodos de instância, não use o autoidentifier para acessar os campos definidos usando Let bindings.</span><span class="sxs-lookup"><span data-stu-id="96ca6-122">Within instance methods, do not use the self identifier to access fields defined by using let bindings.</span></span> <span data-ttu-id="96ca6-123">Use o autoidentifier ao acessar outros membros e propriedades.</span><span class="sxs-lookup"><span data-stu-id="96ca6-123">Use the self identifier when accessing other members and properties.</span></span>

## <a name="static-methods"></a><span data-ttu-id="96ca6-124">Métodos estáticos</span><span class="sxs-lookup"><span data-stu-id="96ca6-124">Static Methods</span></span>

<span data-ttu-id="96ca6-125">A palavra-chave `static` é usada para especificar que um método pode ser chamado sem uma instância e não está associado a uma instância de objeto.</span><span class="sxs-lookup"><span data-stu-id="96ca6-125">The keyword `static` is used to specify that a method can be called without an instance and is not associated with an object instance.</span></span> <span data-ttu-id="96ca6-126">Caso contrário, os métodos são métodos de instância.</span><span class="sxs-lookup"><span data-stu-id="96ca6-126">Otherwise, methods are instance methods.</span></span>

<span data-ttu-id="96ca6-127">O exemplo na próxima seção mostra os campos declarados com a `let` palavra-chave, os membros da propriedade declarados com a `member` palavra-chave e um método estático declarado com a `static` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="96ca6-127">The example in the next section shows fields declared with the `let` keyword, property members declared with the `member` keyword, and a static method declared with the `static` keyword.</span></span>

<span data-ttu-id="96ca6-128">O exemplo a seguir ilustra a definição e o uso de métodos estáticos.</span><span class="sxs-lookup"><span data-stu-id="96ca6-128">The following example illustrates the definition and use of static methods.</span></span> <span data-ttu-id="96ca6-129">Suponha que essas definições de método estejam na `SomeType` classe da seção anterior.</span><span class="sxs-lookup"><span data-stu-id="96ca6-129">Assume that these method definitions are in the `SomeType` class in the previous section.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3402.fs)]

## <a name="abstract-and-virtual-methods"></a><span data-ttu-id="96ca6-130">Métodos abstratos e virtuais</span><span class="sxs-lookup"><span data-stu-id="96ca6-130">Abstract and Virtual Methods</span></span>

<span data-ttu-id="96ca6-131">A palavra-chave `abstract` indica que um método tem um slot de expedição virtual e pode não ter uma definição na classe.</span><span class="sxs-lookup"><span data-stu-id="96ca6-131">The keyword `abstract` indicates that a method has a virtual dispatch slot and might not have a definition in the class.</span></span> <span data-ttu-id="96ca6-132">Um *slot de expedição virtual* é uma entrada em uma tabela mantida internamente de funções que é usada em tempo de execução para pesquisar chamadas de função virtual em um tipo orientado a objeto.</span><span class="sxs-lookup"><span data-stu-id="96ca6-132">A *virtual dispatch slot* is an entry in an internally maintained table of functions that is used at run time to look up virtual function calls in an object-oriented type.</span></span> <span data-ttu-id="96ca6-133">O mecanismo de expedição virtual é o mecanismo que implementa o *polimorfismo*, um recurso importante da programação orientada a objeto.</span><span class="sxs-lookup"><span data-stu-id="96ca6-133">The virtual dispatch mechanism is the mechanism that implements *polymorphism*, an important feature of object-oriented programming.</span></span> <span data-ttu-id="96ca6-134">Uma classe que tem pelo menos um método abstrato sem uma definição é uma *classe abstrata*, o que significa que nenhuma instância pode ser criada dessa classe.</span><span class="sxs-lookup"><span data-stu-id="96ca6-134">A class that has at least one abstract method without a definition is an *abstract class*, which means that no instances can be created of that class.</span></span> <span data-ttu-id="96ca6-135">Para obter mais informações sobre classes abstratas, consulte [classes abstratas](../abstract-classes.md).</span><span class="sxs-lookup"><span data-stu-id="96ca6-135">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

<span data-ttu-id="96ca6-136">Declarações de método abstract não incluem um corpo de método.</span><span class="sxs-lookup"><span data-stu-id="96ca6-136">Abstract method declarations do not include a method body.</span></span> <span data-ttu-id="96ca6-137">Em vez disso, o nome do método é seguido por dois-pontos (:) e uma assinatura de tipo para o método.</span><span class="sxs-lookup"><span data-stu-id="96ca6-137">Instead, the name of the method is followed by a colon (:) and a type signature for the method.</span></span> <span data-ttu-id="96ca6-138">A assinatura de tipo de um método é igual à mostrada pelo IntelliSense quando você pausa o ponteiro do mouse sobre um nome de método no editor de Visual Studio Code, exceto sem nomes de parâmetros.</span><span class="sxs-lookup"><span data-stu-id="96ca6-138">The type signature of a method is the same as that shown by IntelliSense when you pause the mouse pointer over a method name in the Visual Studio Code Editor, except without parameter names.</span></span> <span data-ttu-id="96ca6-139">As assinaturas de tipo também são exibidas pelo intérprete, fsi.exe, quando você estiver trabalhando interativamente.</span><span class="sxs-lookup"><span data-stu-id="96ca6-139">Type signatures are also displayed by the interpreter, fsi.exe, when you are working interactively.</span></span> <span data-ttu-id="96ca6-140">A assinatura de tipo de um método é formada pela listagem dos tipos dos parâmetros, seguidos pelo tipo de retorno, com os símbolos de separadores apropriados.</span><span class="sxs-lookup"><span data-stu-id="96ca6-140">The type signature of a method is formed by listing out the types of the parameters, followed by the return type, with appropriate separator symbols.</span></span> <span data-ttu-id="96ca6-141">Os parâmetros na forma curried são separados por `->` e os parâmetros de tupla são separados por `*` .</span><span class="sxs-lookup"><span data-stu-id="96ca6-141">Curried parameters are separated by `->` and tuple parameters are separated by `*`.</span></span> <span data-ttu-id="96ca6-142">O valor de retorno é sempre separado dos argumentos por um `->` símbolo.</span><span class="sxs-lookup"><span data-stu-id="96ca6-142">The return value is always separated from the arguments by a `->` symbol.</span></span> <span data-ttu-id="96ca6-143">Os parênteses podem ser usados para agrupar parâmetros complexos, como quando um tipo de função é um parâmetro ou para indicar quando uma tupla é tratada como um único parâmetro, e não como dois parâmetros.</span><span class="sxs-lookup"><span data-stu-id="96ca6-143">Parentheses can be used to group complex parameters, such as when a function type is a parameter, or to indicate when a tuple is treated as a single parameter rather than as two parameters.</span></span>

<span data-ttu-id="96ca6-144">Você também pode fornecer definições padrão de métodos abstratos adicionando a definição à classe e usando a `default` palavra-chave, conforme mostrado no bloco de sintaxe neste tópico.</span><span class="sxs-lookup"><span data-stu-id="96ca6-144">You can also give abstract methods default definitions by adding the definition to the class and using the `default` keyword, as shown in the syntax block in this topic.</span></span> <span data-ttu-id="96ca6-145">Um método abstrato que tem uma definição na mesma classe é equivalente a um método virtual em outras linguagens de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="96ca6-145">An abstract method that has a definition in the same class is equivalent to a virtual method in other .NET Framework languages.</span></span> <span data-ttu-id="96ca6-146">Se houver ou não uma definição, a `abstract` palavra-chave criará um novo slot de expedição na tabela de funções virtuais para a classe.</span><span class="sxs-lookup"><span data-stu-id="96ca6-146">Whether or not a definition exists, the `abstract` keyword creates a new dispatch slot in the virtual function table for the class.</span></span>

<span data-ttu-id="96ca6-147">Independentemente de uma classe base implementar seus métodos abstratos, as classes derivadas podem fornecer implementações de métodos abstratos.</span><span class="sxs-lookup"><span data-stu-id="96ca6-147">Regardless of whether a base class implements its abstract methods, derived classes can provide implementations of abstract methods.</span></span> <span data-ttu-id="96ca6-148">Para implementar um método abstract em uma classe derivada, defina um método que tenha o mesmo nome e assinatura na classe derivada, exceto use a `override` `default` palavra-chave ou e forneça o corpo do método.</span><span class="sxs-lookup"><span data-stu-id="96ca6-148">To implement an abstract method in a derived class, define a method that has the same name and signature in the derived class, except use the `override` or `default` keyword, and provide the method body.</span></span> <span data-ttu-id="96ca6-149">As palavras-chave `override` e `default` significam exatamente a mesma coisa.</span><span class="sxs-lookup"><span data-stu-id="96ca6-149">The keywords `override` and `default` mean exactly the same thing.</span></span> <span data-ttu-id="96ca6-150">Use `override` se o novo método substituir uma implementação de classe base; use `default` quando você criar uma implementação na mesma classe que a declaração abstrata original.</span><span class="sxs-lookup"><span data-stu-id="96ca6-150">Use `override` if the new method overrides a base class implementation; use `default` when you create an implementation in the same class as the original abstract declaration.</span></span> <span data-ttu-id="96ca6-151">Não use a `abstract` palavra-chave no método que implementa o método que foi declarado abstrato na classe base.</span><span class="sxs-lookup"><span data-stu-id="96ca6-151">Do not use the `abstract` keyword on the method that implements the method that was declared abstract in the base class.</span></span>

<span data-ttu-id="96ca6-152">O exemplo a seguir ilustra um método abstrato `Rotate` que tem uma implementação padrão, o equivalente a um método virtual .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="96ca6-152">The following example illustrates an abstract method `Rotate` that has a default implementation, the equivalent of a .NET Framework virtual method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3403.fs)]

<span data-ttu-id="96ca6-153">O exemplo a seguir ilustra uma classe derivada que substitui um método de classe base.</span><span class="sxs-lookup"><span data-stu-id="96ca6-153">The following example illustrates a derived class that overrides a base class method.</span></span> <span data-ttu-id="96ca6-154">Nesse caso, a substituição altera o comportamento para que o método não faça nada.</span><span class="sxs-lookup"><span data-stu-id="96ca6-154">In this case, the override changes the behavior so that the method does nothing.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3404.fs)]

## <a name="overloaded-methods"></a><span data-ttu-id="96ca6-155">Métodos sobrecarregados</span><span class="sxs-lookup"><span data-stu-id="96ca6-155">Overloaded Methods</span></span>

<span data-ttu-id="96ca6-156">Métodos sobrecarregados são métodos que têm nomes idênticos em um determinado tipo, mas que têm argumentos diferentes.</span><span class="sxs-lookup"><span data-stu-id="96ca6-156">Overloaded methods are methods that have identical names in a given type but that have different arguments.</span></span> <span data-ttu-id="96ca6-157">Em F #, os argumentos opcionais geralmente são usados em vez de métodos sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="96ca6-157">In F#, optional arguments are usually used instead of overloaded methods.</span></span> <span data-ttu-id="96ca6-158">No entanto, os métodos sobrecarregados são permitidos na linguagem, desde que os argumentos estejam no formato de tupla, não no formulário na forma curried.</span><span class="sxs-lookup"><span data-stu-id="96ca6-158">However, overloaded methods are permitted in the language, provided that the arguments are in tuple form, not curried form.</span></span>

## <a name="optional-arguments"></a><span data-ttu-id="96ca6-159">Argumentos opcionais</span><span class="sxs-lookup"><span data-stu-id="96ca6-159">Optional Arguments</span></span>

<span data-ttu-id="96ca6-160">A partir do F # 4,1, você também pode ter argumentos opcionais com um valor de parâmetro padrão em métodos.</span><span class="sxs-lookup"><span data-stu-id="96ca6-160">Starting with F# 4.1, you can also have optional arguments with a default parameter value in methods.</span></span>  <span data-ttu-id="96ca6-161">Isso é para ajudar a facilitar a interoperação com o código C#.</span><span class="sxs-lookup"><span data-stu-id="96ca6-161">This is to help facilitate interoperation with C# code.</span></span>  <span data-ttu-id="96ca6-162">O exemplo a seguir demonstra a sintaxe:</span><span class="sxs-lookup"><span data-stu-id="96ca6-162">The following example demonstrates the syntax:</span></span>

```fsharp
// A class with a method M, which takes in an optional integer argument.
type C() =
    _.M([<Optional; DefaultParameterValue(12)>] i) = i + 1
```

<span data-ttu-id="96ca6-163">Observe que o valor passado para `DefaultParameterValue` deve corresponder ao tipo de entrada.</span><span class="sxs-lookup"><span data-stu-id="96ca6-163">Note that the value passed in for `DefaultParameterValue` must match the input type.</span></span>  <span data-ttu-id="96ca6-164">No exemplo acima, é um `int` .</span><span class="sxs-lookup"><span data-stu-id="96ca6-164">In the above sample, it is an `int`.</span></span>  <span data-ttu-id="96ca6-165">A tentativa de passar um valor não inteiro em `DefaultParameterValue` resultaria em um erro de compilação.</span><span class="sxs-lookup"><span data-stu-id="96ca6-165">Attempting to pass a non-integer value into `DefaultParameterValue` would result in a compile error.</span></span>

## <a name="example-properties-and-methods"></a><span data-ttu-id="96ca6-166">Exemplo: propriedades e métodos</span><span class="sxs-lookup"><span data-stu-id="96ca6-166">Example: Properties and Methods</span></span>

<span data-ttu-id="96ca6-167">O exemplo a seguir contém um tipo que tem exemplos de campos, funções particulares, propriedades e um método estático.</span><span class="sxs-lookup"><span data-stu-id="96ca6-167">The following example contains a type that has examples of fields, private functions, properties, and a static method.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3406.fs)]

## <a name="see-also"></a><span data-ttu-id="96ca6-168">Confira também</span><span class="sxs-lookup"><span data-stu-id="96ca6-168">See also</span></span>

- [<span data-ttu-id="96ca6-169">Membros</span><span class="sxs-lookup"><span data-stu-id="96ca6-169">Members</span></span>](index.md)
