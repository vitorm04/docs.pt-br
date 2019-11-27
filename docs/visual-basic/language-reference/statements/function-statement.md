---
title: Instrução Function
ms.date: 05/12/2018
f1_keywords:
- vb.Function
helpviewer_keywords:
- procedures [Visual Basic], creating
- Function procedures [Visual Basic], Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword [Visual Basic], Function statements
- Private keyword [Visual Basic], Function statements
- declarations [Visual Basic], procedures
- procedures [Visual Basic], declaration
- Public keyword [Visual Basic], in Function statement
- ByVal keyword [Visual Basic], Function statements
- procedures [Visual Basic], recursive
- Implements keyword [Visual Basic], Function statements
- procedures [Visual Basic], returning values
- Exit statement [Visual Basic], in Function procedures
- recursive procedures
- As keyword [Visual Basic], in Function statement
- Optional keyword [Visual Basic], Function statements
- Function statement [Visual Basic]
- Visual Basic code, Function procedures
- procedures [Visual Basic], function
- ByRef keyword [Visual Basic], Function statements
- Friend keyword [Visual Basic], Function statements
- End keyword [Visual Basic], Function statements
- Handles keyword [Visual Basic], Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
ms.openlocfilehash: 8140c7e6267e66c69c20d413a11d04372400c581
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345927"
---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="d231c-102">Instrução Function (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d231c-102">Function Statement (Visual Basic)</span></span>

<span data-ttu-id="d231c-103">Declara o nome, os parâmetros e o código que definem um procedimento de `Function`.</span><span class="sxs-lookup"><span data-stu-id="d231c-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="d231c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d231c-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a><span data-ttu-id="d231c-105">Partes</span><span class="sxs-lookup"><span data-stu-id="d231c-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="d231c-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d231c-106">Optional.</span></span> <span data-ttu-id="d231c-107">Consulte a [lista de atributos](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="d231c-107">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="d231c-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d231c-108">Optional.</span></span> <span data-ttu-id="d231c-109">Pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="d231c-109">Can be one of the following:</span></span>

  - [<span data-ttu-id="d231c-110">Público</span><span class="sxs-lookup"><span data-stu-id="d231c-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)

  - [<span data-ttu-id="d231c-111">Protegido</span><span class="sxs-lookup"><span data-stu-id="d231c-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)

  - [<span data-ttu-id="d231c-112">Friend</span><span class="sxs-lookup"><span data-stu-id="d231c-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)

  - [<span data-ttu-id="d231c-113">Privado</span><span class="sxs-lookup"><span data-stu-id="d231c-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)

  - [<span data-ttu-id="d231c-114">Amigo Protegido</span><span class="sxs-lookup"><span data-stu-id="d231c-114">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

  - [<span data-ttu-id="d231c-115">Particular Protegido</span><span class="sxs-lookup"><span data-stu-id="d231c-115">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

  <span data-ttu-id="d231c-116">Consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="d231c-116">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="d231c-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d231c-117">Optional.</span></span> <span data-ttu-id="d231c-118">Pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="d231c-118">Can be one of the following:</span></span>

  - [<span data-ttu-id="d231c-119">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="d231c-119">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)

  - [<span data-ttu-id="d231c-120">Substituições</span><span class="sxs-lookup"><span data-stu-id="d231c-120">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)

  - [<span data-ttu-id="d231c-121">Substituível</span><span class="sxs-lookup"><span data-stu-id="d231c-121">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)

  - [<span data-ttu-id="d231c-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="d231c-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)

  - [<span data-ttu-id="d231c-123">MustOverride</span><span class="sxs-lookup"><span data-stu-id="d231c-123">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="d231c-124">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d231c-124">Optional.</span></span> <span data-ttu-id="d231c-125">Consulte [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="d231c-125">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="d231c-126">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d231c-126">Optional.</span></span> <span data-ttu-id="d231c-127">Consulte [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="d231c-127">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="d231c-128">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d231c-128">Optional.</span></span> <span data-ttu-id="d231c-129">Consulte [Async](../../../visual-basic/language-reference/modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="d231c-129">See [Async](../../../visual-basic/language-reference/modifiers/async.md).</span></span>

- `Iterator`

  <span data-ttu-id="d231c-130">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d231c-130">Optional.</span></span> <span data-ttu-id="d231c-131">Consulte [iterador](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="d231c-131">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="d231c-132">Necessária.</span><span class="sxs-lookup"><span data-stu-id="d231c-132">Required.</span></span> <span data-ttu-id="d231c-133">Nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="d231c-133">Name of the procedure.</span></span> <span data-ttu-id="d231c-134">Consulte [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="d231c-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="d231c-135">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d231c-135">Optional.</span></span> <span data-ttu-id="d231c-136">Lista de parâmetros de tipo para um procedimento genérico.</span><span class="sxs-lookup"><span data-stu-id="d231c-136">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="d231c-137">Consulte [lista de tipos](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="d231c-137">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="d231c-138">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d231c-138">Optional.</span></span> <span data-ttu-id="d231c-139">Lista de nomes de variáveis locais que representam os parâmetros deste procedimento.</span><span class="sxs-lookup"><span data-stu-id="d231c-139">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="d231c-140">Consulte a [lista de parâmetros](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="d231c-140">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="d231c-141">Necessário se `Option Strict` for `On`.</span><span class="sxs-lookup"><span data-stu-id="d231c-141">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="d231c-142">Tipo de dados do valor retornado por este procedimento.</span><span class="sxs-lookup"><span data-stu-id="d231c-142">Data type of the value returned by this procedure.</span></span>

- `Implements`

  <span data-ttu-id="d231c-143">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d231c-143">Optional.</span></span> <span data-ttu-id="d231c-144">Indica que este procedimento implementa um ou mais procedimentos de `Function`, cada um definido em uma interface implementada por este procedimento que contém a classe ou a estrutura.</span><span class="sxs-lookup"><span data-stu-id="d231c-144">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="d231c-145">Consulte a [instrução Implements](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d231c-145">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="d231c-146">Necessário se `Implements` for fornecido.</span><span class="sxs-lookup"><span data-stu-id="d231c-146">Required if `Implements` is supplied.</span></span> <span data-ttu-id="d231c-147">Lista de procedimentos de `Function` que estão sendo implementados.</span><span class="sxs-lookup"><span data-stu-id="d231c-147">List of `Function` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="d231c-148">Cada `implementedprocedure` tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="d231c-148">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="d231c-149">Parte</span><span class="sxs-lookup"><span data-stu-id="d231c-149">Part</span></span>|<span data-ttu-id="d231c-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="d231c-150">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="d231c-151">Necessária.</span><span class="sxs-lookup"><span data-stu-id="d231c-151">Required.</span></span> <span data-ttu-id="d231c-152">Nome de uma interface implementada por este procedimento que contém a classe ou a estrutura.</span><span class="sxs-lookup"><span data-stu-id="d231c-152">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="d231c-153">Necessária.</span><span class="sxs-lookup"><span data-stu-id="d231c-153">Required.</span></span> <span data-ttu-id="d231c-154">Nome pelo qual o procedimento é definido em `interface`.</span><span class="sxs-lookup"><span data-stu-id="d231c-154">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="d231c-155">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d231c-155">Optional.</span></span> <span data-ttu-id="d231c-156">Indica que esse procedimento pode manipular um ou mais eventos específicos.</span><span class="sxs-lookup"><span data-stu-id="d231c-156">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="d231c-157">Consulte [identificadores](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d231c-157">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="d231c-158">Necessário se `Handles` for fornecido.</span><span class="sxs-lookup"><span data-stu-id="d231c-158">Required if `Handles` is supplied.</span></span> <span data-ttu-id="d231c-159">Lista de eventos que este procedimento manipula.</span><span class="sxs-lookup"><span data-stu-id="d231c-159">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="d231c-160">Cada `eventspecifier` tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="d231c-160">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="d231c-161">Parte</span><span class="sxs-lookup"><span data-stu-id="d231c-161">Part</span></span>|<span data-ttu-id="d231c-162">Descrição</span><span class="sxs-lookup"><span data-stu-id="d231c-162">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="d231c-163">Necessária.</span><span class="sxs-lookup"><span data-stu-id="d231c-163">Required.</span></span> <span data-ttu-id="d231c-164">Variável de objeto declarada com o tipo de dados da classe ou estrutura que gera o evento.</span><span class="sxs-lookup"><span data-stu-id="d231c-164">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="d231c-165">Necessária.</span><span class="sxs-lookup"><span data-stu-id="d231c-165">Required.</span></span> <span data-ttu-id="d231c-166">Nome do evento que este procedimento manipula.</span><span class="sxs-lookup"><span data-stu-id="d231c-166">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="d231c-167">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d231c-167">Optional.</span></span> <span data-ttu-id="d231c-168">Bloco de instruções a serem executadas neste procedimento.</span><span class="sxs-lookup"><span data-stu-id="d231c-168">Block of statements to be executed within this procedure.</span></span>

- `End Function`

  <span data-ttu-id="d231c-169">Encerra a definição deste procedimento.</span><span class="sxs-lookup"><span data-stu-id="d231c-169">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="d231c-170">Comentários</span><span class="sxs-lookup"><span data-stu-id="d231c-170">Remarks</span></span>

<span data-ttu-id="d231c-171">Todo o código executável deve estar dentro de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="d231c-171">All executable code must be inside a procedure.</span></span> <span data-ttu-id="d231c-172">Cada procedimento, por sua vez, é declarado dentro de uma classe, uma estrutura ou um módulo que é chamado de classe, estrutura ou módulo que o contém.</span><span class="sxs-lookup"><span data-stu-id="d231c-172">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>

<span data-ttu-id="d231c-173">Para retornar um valor para o código de chamada, use um procedimento de `Function`; caso contrário, use um procedimento `Sub`.</span><span class="sxs-lookup"><span data-stu-id="d231c-173">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>

## <a name="defining-a-function"></a><span data-ttu-id="d231c-174">Definindo uma função</span><span class="sxs-lookup"><span data-stu-id="d231c-174">Defining a Function</span></span>

<span data-ttu-id="d231c-175">Você pode definir um procedimento `Function` apenas no nível do módulo.</span><span class="sxs-lookup"><span data-stu-id="d231c-175">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="d231c-176">Portanto, o contexto de declaração para uma função deve ser uma classe, uma estrutura, um módulo ou uma interface e não pode ser um arquivo de origem, um namespace, um procedimento ou um bloco.</span><span class="sxs-lookup"><span data-stu-id="d231c-176">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="d231c-177">Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="d231c-177">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="d231c-178">`Function` procedimentos padrão para acesso público.</span><span class="sxs-lookup"><span data-stu-id="d231c-178">`Function` procedures default to public access.</span></span> <span data-ttu-id="d231c-179">Você pode ajustar seus níveis de acesso com os modificadores de acesso.</span><span class="sxs-lookup"><span data-stu-id="d231c-179">You can adjust their access levels with the access modifiers.</span></span>

<span data-ttu-id="d231c-180">Um procedimento `Function` pode declarar o tipo de dados do valor que o procedimento retorna.</span><span class="sxs-lookup"><span data-stu-id="d231c-180">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="d231c-181">Você pode especificar qualquer tipo de dados ou o nome de uma enumeração, uma estrutura, uma classe ou uma interface.</span><span class="sxs-lookup"><span data-stu-id="d231c-181">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="d231c-182">Se você não especificar o parâmetro `returntype`, o procedimento retornará `Object`.</span><span class="sxs-lookup"><span data-stu-id="d231c-182">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>

<span data-ttu-id="d231c-183">Se esse procedimento usar a palavra-chave `Implements`, a classe ou estrutura que a contém também deverá ter uma instrução `Implements` que siga imediatamente sua instrução `Class` ou `Structure`.</span><span class="sxs-lookup"><span data-stu-id="d231c-183">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="d231c-184">A instrução `Implements` deve incluir cada interface especificada em `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="d231c-184">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="d231c-185">No entanto, o nome pelo qual uma interface define a `Function` (em `definedname`) não precisa corresponder ao nome desse procedimento (em `name`).</span><span class="sxs-lookup"><span data-stu-id="d231c-185">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>

> [!NOTE]
> <span data-ttu-id="d231c-186">Você pode usar expressões lambda para definir expressões de função embutidas.</span><span class="sxs-lookup"><span data-stu-id="d231c-186">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="d231c-187">Para obter mais informações, consulte [expressão de função](../../../visual-basic/language-reference/operators/function-expression.md) e [expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="d231c-187">For more information, see [Function Expression](../../../visual-basic/language-reference/operators/function-expression.md) and [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="returning-from-a-function"></a><span data-ttu-id="d231c-188">Retornando de uma função</span><span class="sxs-lookup"><span data-stu-id="d231c-188">Returning from a Function</span></span>

<span data-ttu-id="d231c-189">Quando o procedimento de `Function` retorna ao código de chamada, a execução continua com a instrução que segue a instrução que chamou o procedimento.</span><span class="sxs-lookup"><span data-stu-id="d231c-189">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>

<span data-ttu-id="d231c-190">Para retornar um valor de uma função, você pode atribuir o valor ao nome da função ou incluí-lo em uma instrução `Return`.</span><span class="sxs-lookup"><span data-stu-id="d231c-190">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>

<span data-ttu-id="d231c-191">A instrução `Return` atribui simultaneamente o valor de retorno e sai da função, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="d231c-191">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

<span data-ttu-id="d231c-192">O exemplo a seguir atribui o valor de retorno ao nome da função `myFunction` e, em seguida, usa a instrução `Exit Function` para retornar.</span><span class="sxs-lookup"><span data-stu-id="d231c-192">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

<span data-ttu-id="d231c-193">As instruções `Exit Function` e `Return` causam uma saída imediata de um procedimento `Function`.</span><span class="sxs-lookup"><span data-stu-id="d231c-193">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="d231c-194">Qualquer número de instruções `Exit Function` e `Return` pode aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Function` e instruções `Return`.</span><span class="sxs-lookup"><span data-stu-id="d231c-194">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>

<span data-ttu-id="d231c-195">Se você usar `Exit Function` sem atribuir um valor a `name`, o procedimento retornará o valor padrão para o tipo de dados especificado em `returntype`.</span><span class="sxs-lookup"><span data-stu-id="d231c-195">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="d231c-196">Se `returntype` não for especificado, o procedimento retornará `Nothing`, que é o valor padrão para `Object`.</span><span class="sxs-lookup"><span data-stu-id="d231c-196">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>

## <a name="calling-a-function"></a><span data-ttu-id="d231c-197">Chamando uma Função</span><span class="sxs-lookup"><span data-stu-id="d231c-197">Calling a Function</span></span>

<span data-ttu-id="d231c-198">Você chama um procedimento de `Function` usando o nome do procedimento, seguido pela lista de argumentos entre parênteses, em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="d231c-198">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="d231c-199">Você pode omitir os parênteses somente se não estiver fornecendo nenhum argumento.</span><span class="sxs-lookup"><span data-stu-id="d231c-199">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="d231c-200">No entanto, seu código será mais legível se você sempre incluir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="d231c-200">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="d231c-201">Você chama um procedimento `Function` da mesma maneira que chama qualquer função de biblioteca, como `Sqrt`, `Cos`ou `ChrW`.</span><span class="sxs-lookup"><span data-stu-id="d231c-201">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>

<span data-ttu-id="d231c-202">Você também pode chamar uma função usando a palavra-chave `Call`.</span><span class="sxs-lookup"><span data-stu-id="d231c-202">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="d231c-203">Nesse caso, o valor de retorno é ignorado.</span><span class="sxs-lookup"><span data-stu-id="d231c-203">In that case, the return value is ignored.</span></span> <span data-ttu-id="d231c-204">O uso da palavra-chave `Call` não é recomendado na maioria dos casos.</span><span class="sxs-lookup"><span data-stu-id="d231c-204">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="d231c-205">Para obter mais informações, consulte [Call Statement](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d231c-205">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="d231c-206">Às vezes, Visual Basic reorganiza as expressões aritméticas para aumentar a eficiência interna.</span><span class="sxs-lookup"><span data-stu-id="d231c-206">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="d231c-207">Por esse motivo, você não deve usar um procedimento `Function` em uma expressão aritmética quando a função altera o valor de variáveis na mesma expressão.</span><span class="sxs-lookup"><span data-stu-id="d231c-207">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>

## <a name="async-functions"></a><span data-ttu-id="d231c-208">Funções assíncronas</span><span class="sxs-lookup"><span data-stu-id="d231c-208">Async Functions</span></span>

<span data-ttu-id="d231c-209">O recurso *Async* permite invocar funções assíncronas sem usar retornos de chamada explícitos ou dividir manualmente seu código em várias funções ou expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="d231c-209">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="d231c-210">Se você marcar uma função com o modificador [Async](../../../visual-basic/language-reference/modifiers/async.md) , poderá usar o operador [Await](../../../visual-basic/language-reference/operators/await-operator.md) na função.</span><span class="sxs-lookup"><span data-stu-id="d231c-210">If you mark a function with the [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="d231c-211">Quando o controle alcança uma expressão de `Await` na função `Async`, o controle retorna ao chamador e o progresso na função é suspenso até que a tarefa esperada seja concluída.</span><span class="sxs-lookup"><span data-stu-id="d231c-211">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="d231c-212">Quando a tarefa for concluída, a execução poderá ser retomada na função.</span><span class="sxs-lookup"><span data-stu-id="d231c-212">When the task is complete, execution can resume in the function.</span></span>

> [!NOTE]
> <span data-ttu-id="d231c-213">Um procedimento `Async` retorna ao chamador quando encontra o primeiro objeto esperado que ainda não está completo, ou chega ao final do procedimento de `Async`, o que ocorrer primeiro.</span><span class="sxs-lookup"><span data-stu-id="d231c-213">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>

<span data-ttu-id="d231c-214">Uma função `Async` pode ter um tipo de retorno de <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="d231c-214">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="d231c-215">Um exemplo de uma função `Async` que tem um tipo de retorno de <xref:System.Threading.Tasks.Task%601> é fornecido abaixo.</span><span class="sxs-lookup"><span data-stu-id="d231c-215">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>

<span data-ttu-id="d231c-216">Uma função `Async` não pode declarar parâmetros [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) .</span><span class="sxs-lookup"><span data-stu-id="d231c-216">An `Async` function cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="d231c-217">Uma [instrução sub](sub-statement.md) também pode ser marcada com o modificador de `Async`.</span><span class="sxs-lookup"><span data-stu-id="d231c-217">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="d231c-218">Isso é usado principalmente para manipuladores de eventos, em que um valor não pode ser retornado.</span><span class="sxs-lookup"><span data-stu-id="d231c-218">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="d231c-219">Um procedimento de `Sub` `Async` não pode ser aguardado e o chamador de um procedimento de `Sub` `Async` não pode capturar exceções que são geradas pelo procedimento `Sub`.</span><span class="sxs-lookup"><span data-stu-id="d231c-219">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>

<span data-ttu-id="d231c-220">Para obter mais informações sobre `Async` funções, consulte [programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md), [fluxo de controle em programas assíncronos](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)e [tipos de retorno assíncronos](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="d231c-220">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="iterator-functions"></a><span data-ttu-id="d231c-221">Funções de iterador</span><span class="sxs-lookup"><span data-stu-id="d231c-221">Iterator Functions</span></span>

<span data-ttu-id="d231c-222">Uma função de *iterador* executa uma iteração personalizada em uma coleção, como uma lista ou matriz.</span><span class="sxs-lookup"><span data-stu-id="d231c-222">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="d231c-223">Uma função de iterador usa a instrução [yield](yield-statement.md) para retornar cada elemento um de cada vez.</span><span class="sxs-lookup"><span data-stu-id="d231c-223">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="d231c-224">Quando uma instrução [yield](yield-statement.md) é atingida, o local atual no código é lembrado.</span><span class="sxs-lookup"><span data-stu-id="d231c-224">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="d231c-225">A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.</span><span class="sxs-lookup"><span data-stu-id="d231c-225">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="d231c-226">Você chama um iterador do código do cliente usando um [para cada... Próxima](for-each-next-statement.md) instrução.</span><span class="sxs-lookup"><span data-stu-id="d231c-226">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>

<span data-ttu-id="d231c-227">O tipo de retorno de uma função de iterador pode ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>ou <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="d231c-227">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="d231c-228">Para obter mais informações, consulte [Iteradores](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="d231c-228">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>

## <a name="example"></a><span data-ttu-id="d231c-229">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d231c-229">Example</span></span>

<span data-ttu-id="d231c-230">O exemplo a seguir usa a instrução `Function` para declarar o nome, os parâmetros e o código que formam o corpo de um procedimento de `Function`.</span><span class="sxs-lookup"><span data-stu-id="d231c-230">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="d231c-231">O modificador `ParamArray` permite que a função aceite um número variável de argumentos.</span><span class="sxs-lookup"><span data-stu-id="d231c-231">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a><span data-ttu-id="d231c-232">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d231c-232">Example</span></span>

<span data-ttu-id="d231c-233">O exemplo a seguir invoca a função declarada no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="d231c-233">The following example invokes the function declared in the preceding example.</span></span>

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a><span data-ttu-id="d231c-234">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d231c-234">Example</span></span>

<span data-ttu-id="d231c-235">No exemplo a seguir, `DelayAsync` é uma `Function` de `Async` que tem um tipo de retorno de <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="d231c-235">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="d231c-236">`DelayAsync` tem uma instrução `Return` que retorna um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="d231c-236">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="d231c-237">Portanto, a declaração de função de `DelayAsync` precisa ter um tipo de retorno de `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="d231c-237">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="d231c-238">Como o tipo de retorno é `Task(Of Integer)`, a avaliação da expressão `Await` no `DoSomethingAsync` produz um inteiro.</span><span class="sxs-lookup"><span data-stu-id="d231c-238">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="d231c-239">Isso é demonstrado nesta instrução: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="d231c-239">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="d231c-240">O procedimento de `startButton_Click` é um exemplo de um procedimento de `Async Sub`.</span><span class="sxs-lookup"><span data-stu-id="d231c-240">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="d231c-241">Como `DoSomethingAsync` é uma função `Async`, a tarefa para a chamada para `DoSomethingAsync` deve ser aguardada, como a instrução a seguir demonstra: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="d231c-241">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="d231c-242">O procedimento de `Sub` de `startButton_Click` deve ser definido com o modificador de `Async` porque ele tem uma expressão de `Await`.</span><span class="sxs-lookup"><span data-stu-id="d231c-242">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="d231c-243">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d231c-243">See also</span></span>

- [<span data-ttu-id="d231c-244">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="d231c-244">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="d231c-245">Procedimentos de Função</span><span class="sxs-lookup"><span data-stu-id="d231c-245">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="d231c-246">Lista de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d231c-246">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="d231c-247">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="d231c-247">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="d231c-248">Instrução Call</span><span class="sxs-lookup"><span data-stu-id="d231c-248">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="d231c-249">Of</span><span class="sxs-lookup"><span data-stu-id="d231c-249">Of</span></span>](of-clause.md)
- [<span data-ttu-id="d231c-250">Matrizes de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d231c-250">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="d231c-251">Como usar uma classe genérica</span><span class="sxs-lookup"><span data-stu-id="d231c-251">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="d231c-252">Solução de problemas de Procedimentos</span><span class="sxs-lookup"><span data-stu-id="d231c-252">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="d231c-253">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="d231c-253">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="d231c-254">Expressão de Função</span><span class="sxs-lookup"><span data-stu-id="d231c-254">Function Expression</span></span>](../../../visual-basic/language-reference/operators/function-expression.md)
