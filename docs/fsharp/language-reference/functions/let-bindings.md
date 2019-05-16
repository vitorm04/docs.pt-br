---
title: Associações let
description: Saiba como usar um F# 'let' associação, que associa um identificador com um valor ou uma função.
ms.date: 05/16/2016
ms.openlocfilehash: ac33ee761cd4881f3d82d6680a07f62a1d7e77e5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641882"
---
# <a name="let-bindings"></a><span data-ttu-id="463a2-103">Associações let</span><span class="sxs-lookup"><span data-stu-id="463a2-103">let Bindings</span></span>

<span data-ttu-id="463a2-104">Um *associação* associa um identificador com um valor ou uma função.</span><span class="sxs-lookup"><span data-stu-id="463a2-104">A *binding* associates an identifier with a value or function.</span></span> <span data-ttu-id="463a2-105">Você usa o `let` palavra-chave para associar um nome para a função ou valor.</span><span class="sxs-lookup"><span data-stu-id="463a2-105">You use the `let` keyword to bind a name to a value or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="463a2-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="463a2-106">Syntax</span></span>

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a><span data-ttu-id="463a2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="463a2-107">Remarks</span></span>

<span data-ttu-id="463a2-108">O `let` palavra-chave é usada em expressões para definir valores ou valores de função para um ou mais nomes de associação.</span><span class="sxs-lookup"><span data-stu-id="463a2-108">The `let` keyword is used in binding expressions to define values or function values for one or more names.</span></span> <span data-ttu-id="463a2-109">A forma mais simples de `let` expressão associa um nome a um valor simple, da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="463a2-109">The simplest form of the `let` expression binds a name to a simple value, as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

<span data-ttu-id="463a2-110">Se você separar a expressão do identificador por meio de uma nova linha, você deve recuar cada linha da expressão, como no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="463a2-110">If you separate the expression from the identifier by using a new line, you must indent each line of the expression, as in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

<span data-ttu-id="463a2-111">Em vez de apenas um nome, um padrão que contém os nomes pode ser especificado, por exemplo, uma tupla, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="463a2-111">Instead of just a name, a pattern that contains names can be specified, for example, a tuple, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

<span data-ttu-id="463a2-112">O *corpo da expressão* é a expressão na qual os nomes são usados.</span><span class="sxs-lookup"><span data-stu-id="463a2-112">The *body-expression* is the expression in which the names are used.</span></span> <span data-ttu-id="463a2-113">A expressão do corpo é exibida em sua própria linha, recuada de linha para cima exatamente com o primeiro caractere no `let` palavra-chave:</span><span class="sxs-lookup"><span data-stu-id="463a2-113">The body expression appears on its own line, indented to line up exactly with the first character in the `let` keyword:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

<span data-ttu-id="463a2-114">Um `let` associação pode aparecer no nível de módulo na definição de um tipo de classe ou em escopos locais, como em uma definição de função.</span><span class="sxs-lookup"><span data-stu-id="463a2-114">A `let` binding can appear at the module level, in the definition of a class type, or in local scopes, such as in a function definition.</span></span> <span data-ttu-id="463a2-115">Um `let` vinculação no nível em um módulo ou em um tipo de classe superior não precisa ter um corpo de expressão, mas em outros níveis de escopo, a expressão do corpo é necessário.</span><span class="sxs-lookup"><span data-stu-id="463a2-115">A `let` binding at the top level in a module or in a class type does not need to have a body expression, but at other scope levels, the body expression is required.</span></span> <span data-ttu-id="463a2-116">Os nomes associados serão úteis após o ponto da definição, mas não a qualquer momento antes do `let` associação é exibida, conforme é ilustrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="463a2-116">The bound names are usable after the point of definition, but not at any point before the `let` binding appears, as is illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a><span data-ttu-id="463a2-117">Associações de função</span><span class="sxs-lookup"><span data-stu-id="463a2-117">Function Bindings</span></span>

<span data-ttu-id="463a2-118">Associações de função seguem as regras para associações de valor, exceto que as associações de função incluem o nome da função e os parâmetros, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="463a2-118">Function bindings follow the rules for value bindings, except that function bindings include the function name and the parameters, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

<span data-ttu-id="463a2-119">Em geral, os parâmetros são padrões, como um padrão de tupla:</span><span class="sxs-lookup"><span data-stu-id="463a2-119">In general, parameters are patterns, such as a tuple pattern:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

<span data-ttu-id="463a2-120">Um `let` expressão de associação é avaliada como o valor da última expressão.</span><span class="sxs-lookup"><span data-stu-id="463a2-120">A `let` binding expression evaluates to the value of the last expression.</span></span> <span data-ttu-id="463a2-121">Portanto, no exemplo de código, o valor de `result` é computada a partir `100 * function3 (1, 2)`, que é avaliado como `300`.</span><span class="sxs-lookup"><span data-stu-id="463a2-121">Therefore, in the following code example, the value of `result` is computed from `100 * function3 (1, 2)`, which evaluates to `300`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

<span data-ttu-id="463a2-122">Para obter mais informações, consulte [Funções](index.md).</span><span class="sxs-lookup"><span data-stu-id="463a2-122">For more information, see [Functions](index.md).</span></span>

## <a name="type-annotations"></a><span data-ttu-id="463a2-123">Anotações de tipo</span><span class="sxs-lookup"><span data-stu-id="463a2-123">Type Annotations</span></span>

<span data-ttu-id="463a2-124">Você pode especificar tipos de parâmetros, incluindo dois-pontos (:) seguido por um nome de tipo, tudo entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="463a2-124">You can specify types for parameters by including a colon (:) followed by a type name, all enclosed in parentheses.</span></span> <span data-ttu-id="463a2-125">Você também pode especificar o tipo do valor de retorno, acrescentando o dois-pontos e o tipo após o último parâmetro.</span><span class="sxs-lookup"><span data-stu-id="463a2-125">You can also specify the type of the return value by appending the colon and type after the last parameter.</span></span> <span data-ttu-id="463a2-126">As anotações de tipo completo da `function1`, com números inteiros como os tipos de parâmetro, seria da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="463a2-126">The full type annotations for `function1`, with integers as the parameter types, would be as follows.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

<span data-ttu-id="463a2-127">Quando não houver nenhum parâmetro de tipo explícito, inferência de tipo é usada para determinar os tipos de parâmetros de funções.</span><span class="sxs-lookup"><span data-stu-id="463a2-127">When there are no explicit type parameters, type inference is used to determine the types of parameters of functions.</span></span> <span data-ttu-id="463a2-128">Isso pode incluir automaticamente generalizar o tipo de um parâmetro para ser genérico.</span><span class="sxs-lookup"><span data-stu-id="463a2-128">This can include automatically generalizing the type of a parameter to be generic.</span></span>

<span data-ttu-id="463a2-129">Para obter mais informações, consulte [generalização automática](../generics/automatic-generalization.md) e [inferência de tipo](../type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="463a2-129">For more information, see [Automatic Generalization](../generics/automatic-generalization.md) and [Type Inference](../type-inference.md).</span></span>

## <a name="let-bindings-in-classes"></a><span data-ttu-id="463a2-130">Associações let em classes</span><span class="sxs-lookup"><span data-stu-id="463a2-130">let Bindings in Classes</span></span>

<span data-ttu-id="463a2-131">Um `let` associação pode aparecer em um tipo de classe, mas não em uma estrutura ou o tipo de registro.</span><span class="sxs-lookup"><span data-stu-id="463a2-131">A `let` binding can appear in a class type but not in a structure or record type.</span></span> <span data-ttu-id="463a2-132">Para usar um let de associação em um tipo de classe, a classe deve ter um construtor primário.</span><span class="sxs-lookup"><span data-stu-id="463a2-132">To use a let binding in a class type, the class must have a primary constructor.</span></span> <span data-ttu-id="463a2-133">Parâmetros do construtor devem aparecer após o nome do tipo na definição de classe.</span><span class="sxs-lookup"><span data-stu-id="463a2-133">Constructor parameters must appear after the type name in the class definition.</span></span> <span data-ttu-id="463a2-134">Um `let` associação em um tipo de classe define os campos particulares e membros para esse tipo de classe e, em conjunto com `do` associações de tipo, o código para o construtor primário para o tipo de formulários.</span><span class="sxs-lookup"><span data-stu-id="463a2-134">A `let` binding in a class type defines private fields and members for that class type and, together with `do` bindings in the type, forms the code for the primary constructor for the type.</span></span> <span data-ttu-id="463a2-135">Os exemplos de código a seguir mostram uma classe `MyClass` com campos privados `field1` e `field2`.</span><span class="sxs-lookup"><span data-stu-id="463a2-135">The following code examples show a class `MyClass` with private fields `field1` and `field2`.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

<span data-ttu-id="463a2-136">Os escopos de `field1` e `field2` são limitados ao tipo no qual eles são declarados.</span><span class="sxs-lookup"><span data-stu-id="463a2-136">The scopes of `field1` and `field2` are limited to the type in which they are declared.</span></span> <span data-ttu-id="463a2-137">Para obter mais informações, consulte [ `let` associações em Classes](../members/let-bindings-in-classes.md) e [Classes](../classes.md).</span><span class="sxs-lookup"><span data-stu-id="463a2-137">For more information, see [`let` Bindings in Classes](../members/let-bindings-in-classes.md) and [Classes](../classes.md).</span></span>

## <a name="type-parameters-in-let-bindings"></a><span data-ttu-id="463a2-138">Associações let de parâmetros de tipo em</span><span class="sxs-lookup"><span data-stu-id="463a2-138">Type Parameters in let Bindings</span></span>

<span data-ttu-id="463a2-139">Um `let` vinculação no nível de módulo em um tipo ou em uma expressão de computação pode ter parâmetros de tipo explícito.</span><span class="sxs-lookup"><span data-stu-id="463a2-139">A `let` binding at the module level, in a type, or in a computation expression can have explicit type parameters.</span></span> <span data-ttu-id="463a2-140">Um let de associação em uma expressão, como em uma definição de função não pode ter parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="463a2-140">A let binding in an expression, such as within a function definition, cannot have type parameters.</span></span> <span data-ttu-id="463a2-141">Para obter mais informações, consulte [Genéricos](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="463a2-141">For more information, see [Generics](../generics/index.md).</span></span>

## <a name="attributes-on-let-bindings"></a><span data-ttu-id="463a2-142">Associações let de atributos em</span><span class="sxs-lookup"><span data-stu-id="463a2-142">Attributes on let Bindings</span></span>

<span data-ttu-id="463a2-143">Atributos podem ser aplicados ao nível superior `let` associações em um módulo, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="463a2-143">Attributes can be applied to top-level `let` bindings in a module, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a><span data-ttu-id="463a2-144">Escopo e a acessibilidade das associações Let</span><span class="sxs-lookup"><span data-stu-id="463a2-144">Scope and Accessibility of Let Bindings</span></span>

<span data-ttu-id="463a2-145">O escopo de uma entidade declarada com uma associação let é limitado à parte do recipiente de escopo (por exemplo, uma função, módulo, arquivo ou classe) depois que a associação é exibida.</span><span class="sxs-lookup"><span data-stu-id="463a2-145">The scope of an entity declared with a let binding is limited to the portion of the containing scope (such as a function, module, file or class) after the binding appears.</span></span> <span data-ttu-id="463a2-146">Portanto, pode-se dizer que uma associação let introduz um nome em um escopo.</span><span class="sxs-lookup"><span data-stu-id="463a2-146">Therefore, it can be said that a let binding introduces a name into a scope.</span></span> <span data-ttu-id="463a2-147">Em um módulo, um valor de associação let ou uma função é acessível para clientes de um módulo desde que o módulo está acessível, já que as associações let em um módulo são compiladas em funções públicas do módulo.</span><span class="sxs-lookup"><span data-stu-id="463a2-147">In a module, a let-bound value or function is accessible to clients of a module as long as the module is accessible, since the let bindings in a module are compiled into public functions of the module.</span></span> <span data-ttu-id="463a2-148">Por outro lado, as associações let em uma classe são privadas à classe.</span><span class="sxs-lookup"><span data-stu-id="463a2-148">By contrast, let bindings in a class are private to the class.</span></span>

<span data-ttu-id="463a2-149">Normalmente, as funções em módulos devem ser qualificadas pelo nome do módulo quando usado pelo código do cliente.</span><span class="sxs-lookup"><span data-stu-id="463a2-149">Normally, functions in modules must be qualified by the name of the module when used by client code.</span></span> <span data-ttu-id="463a2-150">Por exemplo, se um módulo `Module1` tem uma função `function1`, especificam os usuários `Module1.function1` para referir-se a função.</span><span class="sxs-lookup"><span data-stu-id="463a2-150">For example, if a module `Module1` has a function `function1`, users would specify `Module1.function1` to refer to the function.</span></span>

<span data-ttu-id="463a2-151">Os usuários de um módulo podem usar uma declaração de importação para tornar as funções dentro daquele módulo disponíveis para uso sem serem qualificados pelo nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="463a2-151">Users of a module may use an import declaration to make the functions within that module available for use without being qualified by the module name.</span></span> <span data-ttu-id="463a2-152">No exemplo que acabei de mencionar, os usuários do módulo podem nesse caso, abra o módulo usando a abertura da declaração de importação `Module1` e depois disso, se referir a `function1` diretamente.</span><span class="sxs-lookup"><span data-stu-id="463a2-152">In the example just mentioned, users of the module can in that case open the module by using the import declaration open `Module1` and thereafter refer to `function1` directly.</span></span>

```fsharp
module Module1 =
    let function1 x = x + 1.0

module Module2 =
    let function2 x =
        Module1.function1 x

open Module1

let function3 x =
    function1 x
```

<span data-ttu-id="463a2-153">Alguns módulos têm o atributo [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), o que significa que as funções que eles expõem devem ser qualificadas com o nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="463a2-153">Some modules have the attribute [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15), which means that the functions that they expose must be qualified with the name of the module.</span></span> <span data-ttu-id="463a2-154">Por exemplo, o F# módulo de lista tem esse atributo.</span><span class="sxs-lookup"><span data-stu-id="463a2-154">For example, the F# List module has this attribute.</span></span>

<span data-ttu-id="463a2-155">Para obter mais informações sobre módulos e controle de acesso, consulte [módulos](../modules.md) e [controle de acesso](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="463a2-155">For more information on modules and access control, see [Modules](../modules.md) and [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="463a2-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="463a2-156">See also</span></span>

- [<span data-ttu-id="463a2-157">Funções</span><span class="sxs-lookup"><span data-stu-id="463a2-157">Functions</span></span>](index.md)
- [<span data-ttu-id="463a2-158">`let`Associações em Classes</span><span class="sxs-lookup"><span data-stu-id="463a2-158">`let` Bindings in Classes</span></span>](../members/let-bindings-in-classes.md)
