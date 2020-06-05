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
ms.openlocfilehash: 49cf4fead2c5594b7ac6815f82fea0dc995ea436
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404622"
---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="68d97-102">Instrução Function (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="68d97-102">Function Statement (Visual Basic)</span></span>

<span data-ttu-id="68d97-103">Declara o nome, os parâmetros e o código que definem um `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="68d97-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="68d97-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="68d97-104">Syntax</span></span>

```vb
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Function ]
    [ statements ]
End Function
```

## <a name="parts"></a><span data-ttu-id="68d97-105">Partes</span><span class="sxs-lookup"><span data-stu-id="68d97-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="68d97-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="68d97-106">Optional.</span></span> <span data-ttu-id="68d97-107">Consulte a [lista de atributos](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="68d97-107">See [Attribute List](attribute-list.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="68d97-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="68d97-108">Optional.</span></span> <span data-ttu-id="68d97-109">Pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="68d97-109">Can be one of the following:</span></span>

  - [<span data-ttu-id="68d97-110">Pública</span><span class="sxs-lookup"><span data-stu-id="68d97-110">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="68d97-111">Protected</span><span class="sxs-lookup"><span data-stu-id="68d97-111">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="68d97-112">Público</span><span class="sxs-lookup"><span data-stu-id="68d97-112">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="68d97-113">Privada</span><span class="sxs-lookup"><span data-stu-id="68d97-113">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="68d97-114">Amigo Protegido</span><span class="sxs-lookup"><span data-stu-id="68d97-114">Protected Friend</span></span>](../modifiers/protected-friend.md)

  - [<span data-ttu-id="68d97-115">Particular protegido</span><span class="sxs-lookup"><span data-stu-id="68d97-115">Private Protected</span></span>](../modifiers/private-protected.md)

  <span data-ttu-id="68d97-116">Consulte [níveis de acesso em Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="68d97-116">See [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="68d97-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="68d97-117">Optional.</span></span> <span data-ttu-id="68d97-118">Pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="68d97-118">Can be one of the following:</span></span>

  - [<span data-ttu-id="68d97-119">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="68d97-119">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="68d97-120">Substituições</span><span class="sxs-lookup"><span data-stu-id="68d97-120">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="68d97-121">Substituível</span><span class="sxs-lookup"><span data-stu-id="68d97-121">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="68d97-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="68d97-122">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="68d97-123">MustOverride</span><span class="sxs-lookup"><span data-stu-id="68d97-123">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="68d97-124">Opcional.</span><span class="sxs-lookup"><span data-stu-id="68d97-124">Optional.</span></span> <span data-ttu-id="68d97-125">Consulte [compartilhado](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="68d97-125">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="68d97-126">Opcional.</span><span class="sxs-lookup"><span data-stu-id="68d97-126">Optional.</span></span> <span data-ttu-id="68d97-127">Consulte [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="68d97-127">See [Shadows](../modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="68d97-128">Opcional.</span><span class="sxs-lookup"><span data-stu-id="68d97-128">Optional.</span></span> <span data-ttu-id="68d97-129">Consulte [Async](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="68d97-129">See [Async](../modifiers/async.md).</span></span>

- `Iterator`

  <span data-ttu-id="68d97-130">Opcional.</span><span class="sxs-lookup"><span data-stu-id="68d97-130">Optional.</span></span> <span data-ttu-id="68d97-131">Consulte [iterador](../modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="68d97-131">See [Iterator](../modifiers/iterator.md).</span></span>

- `name`

  <span data-ttu-id="68d97-132">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="68d97-132">Required.</span></span> <span data-ttu-id="68d97-133">Nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="68d97-133">Name of the procedure.</span></span> <span data-ttu-id="68d97-134">Consulte [nomes de elementos declarados](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="68d97-134">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="68d97-135">Opcional.</span><span class="sxs-lookup"><span data-stu-id="68d97-135">Optional.</span></span> <span data-ttu-id="68d97-136">Lista de parâmetros de tipo para um procedimento genérico.</span><span class="sxs-lookup"><span data-stu-id="68d97-136">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="68d97-137">Consulte [lista de tipos](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="68d97-137">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="68d97-138">Opcional.</span><span class="sxs-lookup"><span data-stu-id="68d97-138">Optional.</span></span> <span data-ttu-id="68d97-139">Lista de nomes de variáveis locais que representam os parâmetros deste procedimento.</span><span class="sxs-lookup"><span data-stu-id="68d97-139">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="68d97-140">Consulte a [lista de parâmetros](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="68d97-140">See [Parameter List](parameter-list.md).</span></span>

- `returntype`

  <span data-ttu-id="68d97-141">Obrigatório se `Option Strict` for `On` .</span><span class="sxs-lookup"><span data-stu-id="68d97-141">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="68d97-142">Tipo de dados do valor retornado por este procedimento.</span><span class="sxs-lookup"><span data-stu-id="68d97-142">Data type of the value returned by this procedure.</span></span>

- `Implements`

  <span data-ttu-id="68d97-143">Opcional.</span><span class="sxs-lookup"><span data-stu-id="68d97-143">Optional.</span></span> <span data-ttu-id="68d97-144">Indica que este procedimento implementa um ou mais `Function` procedimentos, cada um definido em uma interface implementada por este procedimento que contém a classe ou a estrutura.</span><span class="sxs-lookup"><span data-stu-id="68d97-144">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="68d97-145">Consulte a [instrução Implements](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="68d97-145">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="68d97-146">Necessário se `Implements` for fornecido.</span><span class="sxs-lookup"><span data-stu-id="68d97-146">Required if `Implements` is supplied.</span></span> <span data-ttu-id="68d97-147">Lista de `Function` procedimentos que estão sendo implementados.</span><span class="sxs-lookup"><span data-stu-id="68d97-147">List of `Function` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="68d97-148">Cada `implementedprocedure` uma tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="68d97-148">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="68d97-149">Parte</span><span class="sxs-lookup"><span data-stu-id="68d97-149">Part</span></span>|<span data-ttu-id="68d97-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="68d97-150">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="68d97-151">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="68d97-151">Required.</span></span> <span data-ttu-id="68d97-152">Nome de uma interface implementada por este procedimento que contém a classe ou a estrutura.</span><span class="sxs-lookup"><span data-stu-id="68d97-152">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="68d97-153">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="68d97-153">Required.</span></span> <span data-ttu-id="68d97-154">Nome pelo qual o procedimento é definido `interface` .</span><span class="sxs-lookup"><span data-stu-id="68d97-154">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="68d97-155">Opcional.</span><span class="sxs-lookup"><span data-stu-id="68d97-155">Optional.</span></span> <span data-ttu-id="68d97-156">Indica que esse procedimento pode manipular um ou mais eventos específicos.</span><span class="sxs-lookup"><span data-stu-id="68d97-156">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="68d97-157">Consulte [identificadores](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="68d97-157">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="68d97-158">Necessário se `Handles` for fornecido.</span><span class="sxs-lookup"><span data-stu-id="68d97-158">Required if `Handles` is supplied.</span></span> <span data-ttu-id="68d97-159">Lista de eventos que este procedimento manipula.</span><span class="sxs-lookup"><span data-stu-id="68d97-159">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="68d97-160">Cada `eventspecifier` uma tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="68d97-160">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="68d97-161">Parte</span><span class="sxs-lookup"><span data-stu-id="68d97-161">Part</span></span>|<span data-ttu-id="68d97-162">Descrição</span><span class="sxs-lookup"><span data-stu-id="68d97-162">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="68d97-163">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="68d97-163">Required.</span></span> <span data-ttu-id="68d97-164">Variável de objeto declarada com o tipo de dados da classe ou estrutura que gera o evento.</span><span class="sxs-lookup"><span data-stu-id="68d97-164">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="68d97-165">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="68d97-165">Required.</span></span> <span data-ttu-id="68d97-166">Nome do evento que este procedimento manipula.</span><span class="sxs-lookup"><span data-stu-id="68d97-166">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="68d97-167">Opcional.</span><span class="sxs-lookup"><span data-stu-id="68d97-167">Optional.</span></span> <span data-ttu-id="68d97-168">Bloco de instruções a serem executadas neste procedimento.</span><span class="sxs-lookup"><span data-stu-id="68d97-168">Block of statements to be executed within this procedure.</span></span>

- `End Function`

  <span data-ttu-id="68d97-169">Encerra a definição deste procedimento.</span><span class="sxs-lookup"><span data-stu-id="68d97-169">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="68d97-170">Comentários</span><span class="sxs-lookup"><span data-stu-id="68d97-170">Remarks</span></span>

<span data-ttu-id="68d97-171">Todo o código executável deve estar dentro de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="68d97-171">All executable code must be inside a procedure.</span></span> <span data-ttu-id="68d97-172">Cada procedimento, por sua vez, é declarado dentro de uma classe, uma estrutura ou um módulo que é chamado de classe, estrutura ou módulo que o contém.</span><span class="sxs-lookup"><span data-stu-id="68d97-172">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>

<span data-ttu-id="68d97-173">Para retornar um valor para o código de chamada, use um `Function` procedimento; caso contrário, use um `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="68d97-173">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>

## <a name="defining-a-function"></a><span data-ttu-id="68d97-174">Definindo uma função</span><span class="sxs-lookup"><span data-stu-id="68d97-174">Defining a Function</span></span>

<span data-ttu-id="68d97-175">Você pode definir um `Function` procedimento somente no nível do módulo.</span><span class="sxs-lookup"><span data-stu-id="68d97-175">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="68d97-176">Portanto, o contexto de declaração para uma função deve ser uma classe, uma estrutura, um módulo ou uma interface e não pode ser um arquivo de origem, um namespace, um procedimento ou um bloco.</span><span class="sxs-lookup"><span data-stu-id="68d97-176">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="68d97-177">Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="68d97-177">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="68d97-178">`Function`os procedimentos assumem como padrão o acesso público.</span><span class="sxs-lookup"><span data-stu-id="68d97-178">`Function` procedures default to public access.</span></span> <span data-ttu-id="68d97-179">Você pode ajustar seus níveis de acesso com os modificadores de acesso.</span><span class="sxs-lookup"><span data-stu-id="68d97-179">You can adjust their access levels with the access modifiers.</span></span>

<span data-ttu-id="68d97-180">Um `Function` procedimento pode declarar o tipo de dados do valor que o procedimento retorna.</span><span class="sxs-lookup"><span data-stu-id="68d97-180">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="68d97-181">Você pode especificar qualquer tipo de dados ou o nome de uma enumeração, uma estrutura, uma classe ou uma interface.</span><span class="sxs-lookup"><span data-stu-id="68d97-181">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="68d97-182">Se você não especificar o `returntype` parâmetro, o procedimento retornará `Object` .</span><span class="sxs-lookup"><span data-stu-id="68d97-182">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>

<span data-ttu-id="68d97-183">Se esse procedimento usar a `Implements` palavra-chave, a classe ou estrutura que a contém também deverá ter uma `Implements` instrução que imediatamente segue sua `Class` `Structure` instrução or.</span><span class="sxs-lookup"><span data-stu-id="68d97-183">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="68d97-184">A `Implements` instrução deve incluir cada interface especificada em `implementslist` .</span><span class="sxs-lookup"><span data-stu-id="68d97-184">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="68d97-185">No entanto, o nome pelo qual uma interface define o `Function` (in `definedname` ) não precisa corresponder ao nome desse procedimento (em `name` ).</span><span class="sxs-lookup"><span data-stu-id="68d97-185">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>

> [!NOTE]
> <span data-ttu-id="68d97-186">Você pode usar expressões lambda para definir expressões de função embutidas.</span><span class="sxs-lookup"><span data-stu-id="68d97-186">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="68d97-187">Para obter mais informações, consulte [expressão de função](../operators/function-expression.md) e [expressões lambda](../../programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="68d97-187">For more information, see [Function Expression](../operators/function-expression.md) and [Lambda Expressions](../../programming-guide/language-features/procedures/lambda-expressions.md).</span></span>

## <a name="returning-from-a-function"></a><span data-ttu-id="68d97-188">Retornando de uma função</span><span class="sxs-lookup"><span data-stu-id="68d97-188">Returning from a Function</span></span>

<span data-ttu-id="68d97-189">Quando o `Function` procedimento retorna ao código de chamada, a execução continua com a instrução que segue a instrução que chamou o procedimento.</span><span class="sxs-lookup"><span data-stu-id="68d97-189">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>

<span data-ttu-id="68d97-190">Para retornar um valor de uma função, você pode atribuir o valor ao nome da função ou incluí-lo em uma `Return` instrução.</span><span class="sxs-lookup"><span data-stu-id="68d97-190">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>

<span data-ttu-id="68d97-191">A `Return` instrução atribui simultaneamente o valor de retorno e sai da função, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="68d97-191">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>

[!code-vb[VbVbalrStatements#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#24)]

<span data-ttu-id="68d97-192">O exemplo a seguir atribui o valor de retorno ao nome da função `myFunction` e, em seguida, usa a `Exit Function` instrução a ser retornada.</span><span class="sxs-lookup"><span data-stu-id="68d97-192">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>

[!code-vb[VbVbalrStatements#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#23)]

<span data-ttu-id="68d97-193">As `Exit Function` `Return` instruções e causam uma saída imediata de um `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="68d97-193">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="68d97-194">Qualquer número de `Exit Function` `Return` instruções and pode aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Function` e `Return` demonstrativos.</span><span class="sxs-lookup"><span data-stu-id="68d97-194">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>

<span data-ttu-id="68d97-195">Se você usar `Exit Function` sem atribuir um valor ao `name` , o procedimento retornará o valor padrão para o tipo de dados especificado em `returntype` .</span><span class="sxs-lookup"><span data-stu-id="68d97-195">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="68d97-196">Se `returntype` não for especificado, o procedimento retornará `Nothing` , que é o valor padrão para `Object` .</span><span class="sxs-lookup"><span data-stu-id="68d97-196">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>

## <a name="calling-a-function"></a><span data-ttu-id="68d97-197">Chamando uma Função</span><span class="sxs-lookup"><span data-stu-id="68d97-197">Calling a Function</span></span>

<span data-ttu-id="68d97-198">Você chama um `Function` procedimento usando o nome do procedimento, seguido pela lista de argumentos entre parênteses, em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="68d97-198">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="68d97-199">Você pode omitir os parênteses somente se não estiver fornecendo nenhum argumento.</span><span class="sxs-lookup"><span data-stu-id="68d97-199">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="68d97-200">No entanto, seu código será mais legível se você sempre incluir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="68d97-200">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="68d97-201">Você chama um `Function` procedimento da mesma maneira que chama qualquer função de biblioteca, como `Sqrt` , `Cos` ou `ChrW` .</span><span class="sxs-lookup"><span data-stu-id="68d97-201">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>

<span data-ttu-id="68d97-202">Você também pode chamar uma função usando a `Call` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="68d97-202">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="68d97-203">Nesse caso, o valor de retorno é ignorado.</span><span class="sxs-lookup"><span data-stu-id="68d97-203">In that case, the return value is ignored.</span></span> <span data-ttu-id="68d97-204">O uso da `Call` palavra-chave não é recomendado na maioria dos casos.</span><span class="sxs-lookup"><span data-stu-id="68d97-204">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="68d97-205">Para obter mais informações, consulte [Call Statement](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="68d97-205">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="68d97-206">Às vezes, Visual Basic reorganiza as expressões aritméticas para aumentar a eficiência interna.</span><span class="sxs-lookup"><span data-stu-id="68d97-206">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="68d97-207">Por esse motivo, você não deve usar um `Function` procedimento em uma expressão aritmética quando a função altera o valor de variáveis na mesma expressão.</span><span class="sxs-lookup"><span data-stu-id="68d97-207">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>

## <a name="async-functions"></a><span data-ttu-id="68d97-208">Funções assíncronas</span><span class="sxs-lookup"><span data-stu-id="68d97-208">Async Functions</span></span>

<span data-ttu-id="68d97-209">O recurso *Async* permite invocar funções assíncronas sem usar retornos de chamada explícitos ou dividir manualmente seu código em várias funções ou expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="68d97-209">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="68d97-210">Se você marcar uma função com o modificador [Async](../modifiers/async.md) , poderá usar o operador [Await](../operators/await-operator.md) na função.</span><span class="sxs-lookup"><span data-stu-id="68d97-210">If you mark a function with the [Async](../modifiers/async.md) modifier, you can use the [Await](../operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="68d97-211">Quando o controle alcança uma `Await` expressão na `Async` função, o controle retorna ao chamador e o progresso na função é suspenso até que a tarefa esperada seja concluída.</span><span class="sxs-lookup"><span data-stu-id="68d97-211">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="68d97-212">Quando a tarefa for concluída, a execução poderá ser retomada na função.</span><span class="sxs-lookup"><span data-stu-id="68d97-212">When the task is complete, execution can resume in the function.</span></span>

> [!NOTE]
> <span data-ttu-id="68d97-213">Um `Async` procedimento retorna ao chamador quando ele encontra o primeiro objeto esperado que ainda não está completo, ou chega ao final do `Async` procedimento, o que ocorrer primeiro.</span><span class="sxs-lookup"><span data-stu-id="68d97-213">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>

<span data-ttu-id="68d97-214">Uma `Async` função pode ter um tipo de retorno de <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.Task> .</span><span class="sxs-lookup"><span data-stu-id="68d97-214">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="68d97-215">Um exemplo de uma `Async` função que tem um tipo de retorno <xref:System.Threading.Tasks.Task%601> é fornecido abaixo.</span><span class="sxs-lookup"><span data-stu-id="68d97-215">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>

<span data-ttu-id="68d97-216">Uma `Async` função não pode declarar parâmetros [ByRef](../modifiers/byref.md) .</span><span class="sxs-lookup"><span data-stu-id="68d97-216">An `Async` function cannot declare any [ByRef](../modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="68d97-217">Uma [instrução sub](sub-statement.md) também pode ser marcada com o `Async` modificador.</span><span class="sxs-lookup"><span data-stu-id="68d97-217">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="68d97-218">Isso é usado principalmente para manipuladores de eventos, em que um valor não pode ser retornado.</span><span class="sxs-lookup"><span data-stu-id="68d97-218">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="68d97-219">Um `Async` `Sub` procedimento não pode ser aguardado e o chamador de um `Async` `Sub` procedimento não pode capturar exceções que são geradas pelo `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="68d97-219">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>

<span data-ttu-id="68d97-220">Para obter mais informações sobre as `Async` funções, consulte [programação assíncrona com Async e Await](../../programming-guide/concepts/async/index.md), [fluxo de controle em programas assíncronos](../../programming-guide/concepts/async/control-flow-in-async-programs.md)e [tipos de retorno assíncronos](../../programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="68d97-220">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="iterator-functions"></a><span data-ttu-id="68d97-221">Funções de iterador</span><span class="sxs-lookup"><span data-stu-id="68d97-221">Iterator Functions</span></span>

<span data-ttu-id="68d97-222">Uma função de *iterador* executa uma iteração personalizada em uma coleção, como uma lista ou matriz.</span><span class="sxs-lookup"><span data-stu-id="68d97-222">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="68d97-223">Uma função de iterador usa a instrução [yield](yield-statement.md) para retornar cada elemento um de cada vez.</span><span class="sxs-lookup"><span data-stu-id="68d97-223">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="68d97-224">Quando uma instrução [yield](yield-statement.md) é atingida, o local atual no código é lembrado.</span><span class="sxs-lookup"><span data-stu-id="68d97-224">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="68d97-225">A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.</span><span class="sxs-lookup"><span data-stu-id="68d97-225">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="68d97-226">Você chama um iterador do código do cliente usando um [para cada... Próxima](for-each-next-statement.md) instrução.</span><span class="sxs-lookup"><span data-stu-id="68d97-226">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>

<span data-ttu-id="68d97-227">O tipo de retorno de uma função de iterador pode ser <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.IEnumerator> ou <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="68d97-227">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="68d97-228">Para obter mais informações, consulte [Iteradores](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="68d97-228">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>

## <a name="example"></a><span data-ttu-id="68d97-229">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68d97-229">Example</span></span>

<span data-ttu-id="68d97-230">O exemplo a seguir usa a `Function` instrução para declarar o nome, os parâmetros e o código que formam o corpo de um `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="68d97-230">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="68d97-231">O `ParamArray` modificador permite que a função aceite um número variável de argumentos.</span><span class="sxs-lookup"><span data-stu-id="68d97-231">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>

[!code-vb[VbVbalrStatements#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#25)]

## <a name="example"></a><span data-ttu-id="68d97-232">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68d97-232">Example</span></span>

<span data-ttu-id="68d97-233">O exemplo a seguir invoca a função declarada no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="68d97-233">The following example invokes the function declared in the preceding example.</span></span>

[!code-vb[VbVbalrStatements#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#26)]

## <a name="example"></a><span data-ttu-id="68d97-234">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68d97-234">Example</span></span>

<span data-ttu-id="68d97-235">No exemplo a seguir, `DelayAsync` é um `Async` `Function` que tem um tipo de retorno de <xref:System.Threading.Tasks.Task%601> .</span><span class="sxs-lookup"><span data-stu-id="68d97-235">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="68d97-236">`DelayAsync` tem uma instrução `Return` que retorna um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="68d97-236">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="68d97-237">Portanto, a declaração de função de `DelayAsync` precisa ter um tipo de retorno de `Task(Of Integer)` .</span><span class="sxs-lookup"><span data-stu-id="68d97-237">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="68d97-238">Como o tipo de retorno é `Task(Of Integer)` , a avaliação da `Await` expressão em `DoSomethingAsync` produz um inteiro.</span><span class="sxs-lookup"><span data-stu-id="68d97-238">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="68d97-239">Isso é demonstrado nesta instrução: `Dim result As Integer = Await delayTask` .</span><span class="sxs-lookup"><span data-stu-id="68d97-239">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="68d97-240">O `startButton_Click` procedimento é um exemplo de um `Async Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="68d97-240">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="68d97-241">Como `DoSomethingAsync` é uma `Async` função, a tarefa para a chamada `DoSomethingAsync` deve ser esperada, como demonstra a seguinte instrução: `Await DoSomethingAsync()` .</span><span class="sxs-lookup"><span data-stu-id="68d97-241">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="68d97-242">O `startButton_Click` `Sub` procedimento deve ser definido com o `Async` modificador porque ele tem uma `Await` expressão.</span><span class="sxs-lookup"><span data-stu-id="68d97-242">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="68d97-243">Confira também</span><span class="sxs-lookup"><span data-stu-id="68d97-243">See also</span></span>

- [<span data-ttu-id="68d97-244">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="68d97-244">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="68d97-245">Procedimentos de função</span><span class="sxs-lookup"><span data-stu-id="68d97-245">Function Procedures</span></span>](../../programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="68d97-246">Lista de parâmetros</span><span class="sxs-lookup"><span data-stu-id="68d97-246">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="68d97-247">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="68d97-247">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="68d97-248">Instrução Call</span><span class="sxs-lookup"><span data-stu-id="68d97-248">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="68d97-249">Desse</span><span class="sxs-lookup"><span data-stu-id="68d97-249">Of</span></span>](of-clause.md)
- [<span data-ttu-id="68d97-250">Matrizes de parâmetros</span><span class="sxs-lookup"><span data-stu-id="68d97-250">Parameter Arrays</span></span>](../../programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="68d97-251">Como: Usar uma classe genérica</span><span class="sxs-lookup"><span data-stu-id="68d97-251">How to: Use a Generic Class</span></span>](../../programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="68d97-252">Solucionando problemas de procedimentos</span><span class="sxs-lookup"><span data-stu-id="68d97-252">Troubleshooting Procedures</span></span>](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="68d97-253">Expressões lambda</span><span class="sxs-lookup"><span data-stu-id="68d97-253">Lambda Expressions</span></span>](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="68d97-254">Expressão de função</span><span class="sxs-lookup"><span data-stu-id="68d97-254">Function Expression</span></span>](../operators/function-expression.md)
