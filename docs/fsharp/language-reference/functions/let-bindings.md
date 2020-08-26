---
title: Associações let
description: "Saiba como usar uma associação de F # ' Let ', que associa um identificador a um valor ou função."
ms.date: 05/16/2016
ms.openlocfilehash: 6f2396f480c5e6c631d0022f4732419ee5b07db6
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812218"
---
# <a name="let-bindings"></a><span data-ttu-id="462c9-103">Associações let</span><span class="sxs-lookup"><span data-stu-id="462c9-103">let Bindings</span></span>

<span data-ttu-id="462c9-104">Uma *Associação* associa um identificador a um valor ou função.</span><span class="sxs-lookup"><span data-stu-id="462c9-104">A *binding* associates an identifier with a value or function.</span></span> <span data-ttu-id="462c9-105">Você usa a `let` palavra-chave para associar um nome a um valor ou função.</span><span class="sxs-lookup"><span data-stu-id="462c9-105">You use the `let` keyword to bind a name to a value or function.</span></span>

## <a name="syntax"></a><span data-ttu-id="462c9-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="462c9-106">Syntax</span></span>

```fsharp
// Binding a value:
let identifier-or-pattern [: type] =expressionbody-expression
// Binding a function value:
let identifier parameter-list [: return-type ] =expressionbody-expression
```

## <a name="remarks"></a><span data-ttu-id="462c9-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="462c9-107">Remarks</span></span>

<span data-ttu-id="462c9-108">A `let` palavra-chave é usada em expressões de associação para definir valores ou valores de função para um ou mais nomes.</span><span class="sxs-lookup"><span data-stu-id="462c9-108">The `let` keyword is used in binding expressions to define values or function values for one or more names.</span></span> <span data-ttu-id="462c9-109">A forma mais simples da `let` expressão associa um nome a um valor simples, como a seguir.</span><span class="sxs-lookup"><span data-stu-id="462c9-109">The simplest form of the `let` expression binds a name to a simple value, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1101.fs)]

<span data-ttu-id="462c9-110">Se você separar a expressão do identificador usando uma nova linha, deverá recuar cada linha da expressão, como no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="462c9-110">If you separate the expression from the identifier by using a new line, you must indent each line of the expression, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1102.fs)]

<span data-ttu-id="462c9-111">Em vez de apenas um nome, um padrão que contém nomes pode ser especificado, por exemplo, uma tupla, como mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="462c9-111">Instead of just a name, a pattern that contains names can be specified, for example, a tuple, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1103.fs)]

<span data-ttu-id="462c9-112">A *expressão Body* é a expressão na qual os nomes são usados.</span><span class="sxs-lookup"><span data-stu-id="462c9-112">The *body-expression* is the expression in which the names are used.</span></span> <span data-ttu-id="462c9-113">A expressão de corpo aparece em sua própria linha, recuada para alinhar exatamente com o primeiro caractere na `let` palavra-chave:</span><span class="sxs-lookup"><span data-stu-id="462c9-113">The body expression appears on its own line, indented to line up exactly with the first character in the `let` keyword:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1104.fs)]

<span data-ttu-id="462c9-114">Uma `let` associação pode aparecer no nível do módulo, na definição de um tipo de classe ou em escopos locais, como em uma definição de função.</span><span class="sxs-lookup"><span data-stu-id="462c9-114">A `let` binding can appear at the module level, in the definition of a class type, or in local scopes, such as in a function definition.</span></span> <span data-ttu-id="462c9-115">Uma `let` associação no nível superior em um módulo ou em um tipo de classe não precisa ter uma expressão Body, mas em outros níveis de escopo, a expressão Body é necessária.</span><span class="sxs-lookup"><span data-stu-id="462c9-115">A `let` binding at the top level in a module or in a class type does not need to have a body expression, but at other scope levels, the body expression is required.</span></span> <span data-ttu-id="462c9-116">Os nomes associados são utilizáveis após o ponto de definição, mas não a qualquer momento antes que a `let` associação seja exibida, como é ilustrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="462c9-116">The bound names are usable after the point of definition, but not at any point before the `let` binding appears, as is illustrated in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1105.fs)]

## <a name="function-bindings"></a><span data-ttu-id="462c9-117">Associações de função</span><span class="sxs-lookup"><span data-stu-id="462c9-117">Function Bindings</span></span>

<span data-ttu-id="462c9-118">As associações de função seguem as regras para associações de valor, exceto que as associações de função incluem o nome da função e os parâmetros, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="462c9-118">Function bindings follow the rules for value bindings, except that function bindings include the function name and the parameters, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1106.fs)]

<span data-ttu-id="462c9-119">Em geral, os parâmetros são padrões, como um padrão de tupla:</span><span class="sxs-lookup"><span data-stu-id="462c9-119">In general, parameters are patterns, such as a tuple pattern:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1107.fs)]

<span data-ttu-id="462c9-120">Uma `let` expressão de associação é avaliada como o valor da última expressão.</span><span class="sxs-lookup"><span data-stu-id="462c9-120">A `let` binding expression evaluates to the value of the last expression.</span></span> <span data-ttu-id="462c9-121">Portanto, no exemplo de código a seguir, o valor de `result` é computado de `100 * function3 (1, 2)` , que é avaliado como `300` .</span><span class="sxs-lookup"><span data-stu-id="462c9-121">Therefore, in the following code example, the value of `result` is computed from `100 * function3 (1, 2)`, which evaluates to `300`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1109.fs)]

<span data-ttu-id="462c9-122">Para obter mais informações, consulte [Funções](index.md).</span><span class="sxs-lookup"><span data-stu-id="462c9-122">For more information, see [Functions](index.md).</span></span>

## <a name="type-annotations"></a><span data-ttu-id="462c9-123">Anotações de tipo</span><span class="sxs-lookup"><span data-stu-id="462c9-123">Type Annotations</span></span>

<span data-ttu-id="462c9-124">Você pode especificar tipos de parâmetros, incluindo dois-pontos (:) seguido por um nome de tipo, todos incluídos entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="462c9-124">You can specify types for parameters by including a colon (:) followed by a type name, all enclosed in parentheses.</span></span> <span data-ttu-id="462c9-125">Você também pode especificar o tipo do valor de retorno acrescentando os dois-pontos e o tipo após o último parâmetro.</span><span class="sxs-lookup"><span data-stu-id="462c9-125">You can also specify the type of the return value by appending the colon and type after the last parameter.</span></span> <span data-ttu-id="462c9-126">As anotações de tipo completo para `function1` , com inteiros como os tipos de parâmetro, seriam como a seguir.</span><span class="sxs-lookup"><span data-stu-id="462c9-126">The full type annotations for `function1`, with integers as the parameter types, would be as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1108.fs)]

<span data-ttu-id="462c9-127">Quando não há nenhum parâmetro de tipo explícito, a inferência de tipos é usada para determinar os tipos de parâmetros de funções.</span><span class="sxs-lookup"><span data-stu-id="462c9-127">When there are no explicit type parameters, type inference is used to determine the types of parameters of functions.</span></span> <span data-ttu-id="462c9-128">Isso pode incluir a generalização automática do tipo de um parâmetro como genérico.</span><span class="sxs-lookup"><span data-stu-id="462c9-128">This can include automatically generalizing the type of a parameter to be generic.</span></span>

<span data-ttu-id="462c9-129">Para obter mais informações, consulte [generalização automática](../generics/automatic-generalization.md) e [inferência de tipos](../type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="462c9-129">For more information, see [Automatic Generalization](../generics/automatic-generalization.md) and [Type Inference](../type-inference.md).</span></span>

## <a name="let-bindings-in-classes"></a><span data-ttu-id="462c9-130">Associações let em classes</span><span class="sxs-lookup"><span data-stu-id="462c9-130">let Bindings in Classes</span></span>

<span data-ttu-id="462c9-131">Uma `let` associação pode aparecer em um tipo de classe, mas não em um tipo de estrutura ou de registro.</span><span class="sxs-lookup"><span data-stu-id="462c9-131">A `let` binding can appear in a class type but not in a structure or record type.</span></span> <span data-ttu-id="462c9-132">Para usar uma associação let em um tipo de classe, a classe deve ter um construtor principal.</span><span class="sxs-lookup"><span data-stu-id="462c9-132">To use a let binding in a class type, the class must have a primary constructor.</span></span> <span data-ttu-id="462c9-133">Os parâmetros do construtor devem aparecer após o nome do tipo na definição de classe.</span><span class="sxs-lookup"><span data-stu-id="462c9-133">Constructor parameters must appear after the type name in the class definition.</span></span> <span data-ttu-id="462c9-134">Uma `let` associação em um tipo de classe define campos privados e membros para esse tipo de classe e, junto com `do` associações no tipo, forma o código para o construtor primário para o tipo.</span><span class="sxs-lookup"><span data-stu-id="462c9-134">A `let` binding in a class type defines private fields and members for that class type and, together with `do` bindings in the type, forms the code for the primary constructor for the type.</span></span> <span data-ttu-id="462c9-135">Os exemplos de código a seguir mostram uma classe `MyClass` com campos privados `field1` e `field2` .</span><span class="sxs-lookup"><span data-stu-id="462c9-135">The following code examples show a class `MyClass` with private fields `field1` and `field2`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1110.fs)]

<span data-ttu-id="462c9-136">Os escopos de `field1` e `field2` são limitados ao tipo no qual são declarados.</span><span class="sxs-lookup"><span data-stu-id="462c9-136">The scopes of `field1` and `field2` are limited to the type in which they are declared.</span></span> <span data-ttu-id="462c9-137">Para obter mais informações, consulte [ `let` associações em classes](../members/let-bindings-in-classes.md) e [classes](../classes.md).</span><span class="sxs-lookup"><span data-stu-id="462c9-137">For more information, see [`let` Bindings in Classes](../members/let-bindings-in-classes.md) and [Classes](../classes.md).</span></span>

## <a name="type-parameters-in-let-bindings"></a><span data-ttu-id="462c9-138">Parâmetros de tipo em permitir associações</span><span class="sxs-lookup"><span data-stu-id="462c9-138">Type Parameters in let Bindings</span></span>

<span data-ttu-id="462c9-139">Uma `let` associação no nível do módulo, em um tipo ou em uma expressão de computação pode ter parâmetros de tipo explícitos.</span><span class="sxs-lookup"><span data-stu-id="462c9-139">A `let` binding at the module level, in a type, or in a computation expression can have explicit type parameters.</span></span> <span data-ttu-id="462c9-140">Uma associação let em uma expressão, como em uma definição de função, não pode ter parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="462c9-140">A let binding in an expression, such as within a function definition, cannot have type parameters.</span></span> <span data-ttu-id="462c9-141">Para obter mais informações, consulte [Genéricos](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="462c9-141">For more information, see [Generics](../generics/index.md).</span></span>

## <a name="attributes-on-let-bindings"></a><span data-ttu-id="462c9-142">Atributos em permitir associações</span><span class="sxs-lookup"><span data-stu-id="462c9-142">Attributes on let Bindings</span></span>

<span data-ttu-id="462c9-143">Os atributos podem ser aplicados a associações de nível superior `let` em um módulo, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="462c9-143">Attributes can be applied to top-level `let` bindings in a module, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1111.fs)]

## <a name="scope-and-accessibility-of-let-bindings"></a><span data-ttu-id="462c9-144">Escopo e acessibilidade de associações Let</span><span class="sxs-lookup"><span data-stu-id="462c9-144">Scope and Accessibility of Let Bindings</span></span>

<span data-ttu-id="462c9-145">O escopo de uma entidade declarada com uma associação let é limitado à parte do escopo de contenção (como uma função, módulo, arquivo ou classe) depois que a associação é exibida.</span><span class="sxs-lookup"><span data-stu-id="462c9-145">The scope of an entity declared with a let binding is limited to the portion of the containing scope (such as a function, module, file or class) after the binding appears.</span></span> <span data-ttu-id="462c9-146">Portanto, pode ser dito que uma associação let introduz um nome em um escopo.</span><span class="sxs-lookup"><span data-stu-id="462c9-146">Therefore, it can be said that a let binding introduces a name into a scope.</span></span> <span data-ttu-id="462c9-147">Em um módulo, uma função ou valor de Let é acessível aos clientes de um módulo, desde que o módulo esteja acessível, pois as associações Let em um módulo são compiladas em funções públicas do módulo.</span><span class="sxs-lookup"><span data-stu-id="462c9-147">In a module, a let-bound value or function is accessible to clients of a module as long as the module is accessible, since the let bindings in a module are compiled into public functions of the module.</span></span> <span data-ttu-id="462c9-148">Por outro lado, permite que as associações em uma classe sejam privadas para a classe.</span><span class="sxs-lookup"><span data-stu-id="462c9-148">By contrast, let bindings in a class are private to the class.</span></span>

<span data-ttu-id="462c9-149">Normalmente, as funções em módulos devem ser qualificadas pelo nome do módulo quando usadas pelo código do cliente.</span><span class="sxs-lookup"><span data-stu-id="462c9-149">Normally, functions in modules must be qualified by the name of the module when used by client code.</span></span> <span data-ttu-id="462c9-150">Por exemplo, se um módulo `Module1` tiver uma função `function1` , os usuários especificarão a `Module1.function1` referência à função.</span><span class="sxs-lookup"><span data-stu-id="462c9-150">For example, if a module `Module1` has a function `function1`, users would specify `Module1.function1` to refer to the function.</span></span>

<span data-ttu-id="462c9-151">Os usuários de um módulo podem usar uma declaração de importação para tornar as funções dentro desse módulo disponíveis para uso sem serem qualificadas pelo nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="462c9-151">Users of a module may use an import declaration to make the functions within that module available for use without being qualified by the module name.</span></span> <span data-ttu-id="462c9-152">No exemplo que acabamos de mencionar, os usuários do módulo podem, nesse caso, abrir o módulo usando a declaração de importação aberta `Module1` e depois se referirem `function1` diretamente.</span><span class="sxs-lookup"><span data-stu-id="462c9-152">In the example just mentioned, users of the module can in that case open the module by using the import declaration open `Module1` and thereafter refer to `function1` directly.</span></span>

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

<span data-ttu-id="462c9-153">Alguns módulos têm o atributo [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html), o que significa que as funções que eles expões devem ser qualificadas com o nome do módulo.</span><span class="sxs-lookup"><span data-stu-id="462c9-153">Some modules have the attribute [RequireQualifiedAccess](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-requirequalifiedaccessattribute.html), which means that the functions that they expose must be qualified with the name of the module.</span></span> <span data-ttu-id="462c9-154">Por exemplo, o módulo da lista F # tem esse atributo.</span><span class="sxs-lookup"><span data-stu-id="462c9-154">For example, the F# List module has this attribute.</span></span>

<span data-ttu-id="462c9-155">Para obter mais informações sobre módulos e controle de acesso, consulte [módulos](../modules.md) e [controle de acesso](../access-control.md).</span><span class="sxs-lookup"><span data-stu-id="462c9-155">For more information on modules and access control, see [Modules](../modules.md) and [Access Control](../access-control.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="462c9-156">Confira também</span><span class="sxs-lookup"><span data-stu-id="462c9-156">See also</span></span>

- [<span data-ttu-id="462c9-157">Funções</span><span class="sxs-lookup"><span data-stu-id="462c9-157">Functions</span></span>](index.md)
- [<span data-ttu-id="462c9-158">`let` Associações em classes</span><span class="sxs-lookup"><span data-stu-id="462c9-158">`let` Bindings in Classes</span></span>](../members/let-bindings-in-classes.md)
