---
title: "Instrução Function (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Function
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
caps.latest.revision: "62"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 667ab7ceb54e1f339fd645883ca2686c0cbb72b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="4e374-102">Instrução Function (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4e374-102">Function Statement (Visual Basic)</span></span>
<span data-ttu-id="4e374-103">Declara o nome, parâmetros e código que definem um `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="4e374-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e374-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4e374-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]  
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Function ]  
    [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="4e374-105">Partes</span><span class="sxs-lookup"><span data-stu-id="4e374-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="4e374-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4e374-106">Optional.</span></span> <span data-ttu-id="4e374-107">Consulte [lista de atributos](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="4e374-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="4e374-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4e374-108">Optional.</span></span> <span data-ttu-id="4e374-109">Pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="4e374-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="4e374-110">Público</span><span class="sxs-lookup"><span data-stu-id="4e374-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="4e374-111">Protegido</span><span class="sxs-lookup"><span data-stu-id="4e374-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="4e374-112">Friend</span><span class="sxs-lookup"><span data-stu-id="4e374-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="4e374-113">Privado</span><span class="sxs-lookup"><span data-stu-id="4e374-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="4e374-114">Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="4e374-114">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="4e374-115">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4e374-115">Optional.</span></span> <span data-ttu-id="4e374-116">Pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="4e374-116">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="4e374-117">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="4e374-117">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="4e374-118">Substituições</span><span class="sxs-lookup"><span data-stu-id="4e374-118">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="4e374-119">Substituível</span><span class="sxs-lookup"><span data-stu-id="4e374-119">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="4e374-120">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="4e374-120">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="4e374-121">MustOverride</span><span class="sxs-lookup"><span data-stu-id="4e374-121">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="4e374-122">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4e374-122">Optional.</span></span> <span data-ttu-id="4e374-123">Consulte [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="4e374-123">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="4e374-124">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4e374-124">Optional.</span></span> <span data-ttu-id="4e374-125">Consulte [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="4e374-125">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="4e374-126">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4e374-126">Optional.</span></span> <span data-ttu-id="4e374-127">Consulte [Async](../../../visual-basic/language-reference/modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="4e374-127">See [Async](../../../visual-basic/language-reference/modifiers/async.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="4e374-128">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4e374-128">Optional.</span></span> <span data-ttu-id="4e374-129">Consulte [iterador](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="4e374-129">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="4e374-130">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4e374-130">Required.</span></span> <span data-ttu-id="4e374-131">Nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="4e374-131">Name of the procedure.</span></span> <span data-ttu-id="4e374-132">Consulte [declarado nomes de elemento](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="4e374-132">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="4e374-133">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4e374-133">Optional.</span></span> <span data-ttu-id="4e374-134">Lista de parâmetros de tipo para um procedimento genérico.</span><span class="sxs-lookup"><span data-stu-id="4e374-134">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="4e374-135">Consulte [digite lista](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="4e374-135">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="4e374-136">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4e374-136">Optional.</span></span> <span data-ttu-id="4e374-137">Lista de nomes de variáveis locais que representa os parâmetros deste procedimento.</span><span class="sxs-lookup"><span data-stu-id="4e374-137">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="4e374-138">Consulte [lista de parâmetros](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="4e374-138">See [Parameter List](parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="4e374-139">Necessário se `Option Strict` é `On`.</span><span class="sxs-lookup"><span data-stu-id="4e374-139">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="4e374-140">Tipo de dados do valor retornado por esse procedimento.</span><span class="sxs-lookup"><span data-stu-id="4e374-140">Data type of the value returned by this procedure.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="4e374-141">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4e374-141">Optional.</span></span> <span data-ttu-id="4e374-142">Indica que esse procedimento implementa uma ou mais `Function` procedimentos, cada uma delas definida em uma interface implementada pela classe ou estrutura que contém esse procedimento.</span><span class="sxs-lookup"><span data-stu-id="4e374-142">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="4e374-143">Consulte [implementa a instrução](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e374-143">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="4e374-144">Necessário se `Implements` for fornecido.</span><span class="sxs-lookup"><span data-stu-id="4e374-144">Required if `Implements` is supplied.</span></span> <span data-ttu-id="4e374-145">Lista de `Function` procedimentos sendo implementados.</span><span class="sxs-lookup"><span data-stu-id="4e374-145">List of `Function` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="4e374-146">Cada `implementedprocedure` tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="4e374-146">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="4e374-147">Parte</span><span class="sxs-lookup"><span data-stu-id="4e374-147">Part</span></span>|<span data-ttu-id="4e374-148">Descrição</span><span class="sxs-lookup"><span data-stu-id="4e374-148">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="4e374-149">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4e374-149">Required.</span></span> <span data-ttu-id="4e374-150">Nome de uma interface implementada por esse procedimento contendo classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="4e374-150">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="4e374-151">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4e374-151">Required.</span></span> <span data-ttu-id="4e374-152">Nome pelo qual o procedimento é definido em `interface`.</span><span class="sxs-lookup"><span data-stu-id="4e374-152">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="4e374-153">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4e374-153">Optional.</span></span> <span data-ttu-id="4e374-154">Indica que esse procedimento pode manipular um ou mais eventos específicos.</span><span class="sxs-lookup"><span data-stu-id="4e374-154">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="4e374-155">Consulte [manipula](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4e374-155">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="4e374-156">Necessário se `Handles` for fornecido.</span><span class="sxs-lookup"><span data-stu-id="4e374-156">Required if `Handles` is supplied.</span></span> <span data-ttu-id="4e374-157">Lista de eventos que trata este procedimento.</span><span class="sxs-lookup"><span data-stu-id="4e374-157">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="4e374-158">Cada `eventspecifier` tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="4e374-158">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="4e374-159">Parte</span><span class="sxs-lookup"><span data-stu-id="4e374-159">Part</span></span>|<span data-ttu-id="4e374-160">Descrição</span><span class="sxs-lookup"><span data-stu-id="4e374-160">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="4e374-161">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4e374-161">Required.</span></span> <span data-ttu-id="4e374-162">Variável de objeto declarada com o tipo de dados da classe ou estrutura que gera o evento.</span><span class="sxs-lookup"><span data-stu-id="4e374-162">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="4e374-163">Necessário.</span><span class="sxs-lookup"><span data-stu-id="4e374-163">Required.</span></span> <span data-ttu-id="4e374-164">Nome do evento que esse procedimento manipula.</span><span class="sxs-lookup"><span data-stu-id="4e374-164">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="4e374-165">Opcional.</span><span class="sxs-lookup"><span data-stu-id="4e374-165">Optional.</span></span> <span data-ttu-id="4e374-166">Bloco de instruções a ser executado dentro deste procedimento.</span><span class="sxs-lookup"><span data-stu-id="4e374-166">Block of statements to be executed within this procedure.</span></span>  
  
-   `End Function`  
  
     <span data-ttu-id="4e374-167">Finaliza a definição desse procedimento.</span><span class="sxs-lookup"><span data-stu-id="4e374-167">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e374-168">Comentários</span><span class="sxs-lookup"><span data-stu-id="4e374-168">Remarks</span></span>  
 <span data-ttu-id="4e374-169">Todo o código executável deve estar dentro de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="4e374-169">All executable code must be inside a procedure.</span></span> <span data-ttu-id="4e374-170">Cada procedimento, por sua vez, é declarado dentro de uma classe, uma estrutura ou um módulo que é conhecido como a classe, estrutura ou módulo que contém.</span><span class="sxs-lookup"><span data-stu-id="4e374-170">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>  
  
 <span data-ttu-id="4e374-171">Para retornar um valor para o código de chamada, use um `Function` procedimento; caso contrário, use uma `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="4e374-171">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>  
  
## <a name="defining-a-function"></a><span data-ttu-id="4e374-172">Definindo uma função</span><span class="sxs-lookup"><span data-stu-id="4e374-172">Defining a Function</span></span>  
 <span data-ttu-id="4e374-173">Você pode definir um `Function` procedimento apenas no nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="4e374-173">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="4e374-174">Portanto, o contexto da declaração para uma função deve ser uma classe, uma estrutura, um módulo ou uma interface e não pode ser um arquivo de origem, um namespace, um procedimento ou um bloco.</span><span class="sxs-lookup"><span data-stu-id="4e374-174">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="4e374-175">Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="4e374-175">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="4e374-176">`Function`padrão de procedimentos para acesso público.</span><span class="sxs-lookup"><span data-stu-id="4e374-176">`Function` procedures default to public access.</span></span> <span data-ttu-id="4e374-177">Você pode ajustar os níveis de acesso com os modificadores de acesso.</span><span class="sxs-lookup"><span data-stu-id="4e374-177">You can adjust their access levels with the access modifiers.</span></span>  
  
 <span data-ttu-id="4e374-178">Um `Function` procedimento pode declarar o tipo de dados do valor que o procedimento retorna.</span><span class="sxs-lookup"><span data-stu-id="4e374-178">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="4e374-179">Você pode especificar qualquer tipo de dados ou o nome de uma enumeração, uma estrutura, uma classe ou interface.</span><span class="sxs-lookup"><span data-stu-id="4e374-179">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="4e374-180">Se você não especificar o `returntype` , o procedimento retornará `Object`.</span><span class="sxs-lookup"><span data-stu-id="4e374-180">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>  
  
 <span data-ttu-id="4e374-181">Se esse procedimento usa o `Implements` palavra-chave, a classe ou estrutura contendo também deve ter uma `Implements` instrução que segue imediatamente o `Class` ou `Structure` instrução.</span><span class="sxs-lookup"><span data-stu-id="4e374-181">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="4e374-182">O `Implements` instrução deve incluir cada interface que é especificado em `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="4e374-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="4e374-183">No entanto, o nome pelo qual uma interface define o `Function` (em `definedname`) não precisa corresponder ao nome do procedimento (em `name`).</span><span class="sxs-lookup"><span data-stu-id="4e374-183">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e374-184">Você pode usar expressões lambda para definir a função embutida de expressões.</span><span class="sxs-lookup"><span data-stu-id="4e374-184">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="4e374-185">Para obter mais informações, consulte [expressão de função](../../../visual-basic/language-reference/operators/function-expression.md) e [expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="4e374-185">For more information, see [Function Expression](../../../visual-basic/language-reference/operators/function-expression.md) and [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
## <a name="returning-from-a-function"></a><span data-ttu-id="4e374-186">Retornar de uma função</span><span class="sxs-lookup"><span data-stu-id="4e374-186">Returning from a Function</span></span>  
 <span data-ttu-id="4e374-187">Quando o `Function` procedimento retorna para o código de chamada, a execução continua com a instrução que segue a instrução que chamou o procedimento.</span><span class="sxs-lookup"><span data-stu-id="4e374-187">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>  
  
 <span data-ttu-id="4e374-188">Para retornar um valor de uma função, você pode atribuir o valor para o nome da função ou incluí-lo em um `Return` instrução.</span><span class="sxs-lookup"><span data-stu-id="4e374-188">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>  
  
 <span data-ttu-id="4e374-189">O `Return` instrução simultaneamente atribui o valor de retorno e sai da função, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4e374-189">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]  
  
 <span data-ttu-id="4e374-190">O exemplo a seguir atribui o valor de retorno para o nome da função `myFunction` e, em seguida, usa o `Exit Function` instrução para retornar.</span><span class="sxs-lookup"><span data-stu-id="4e374-190">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]  
  
 <span data-ttu-id="4e374-191">O `Exit Function` e `Return` instruções produzem saída imediata de um `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="4e374-191">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="4e374-192">Qualquer número de `Exit Function` e `Return` instruções podem aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Function` e `Return` instruções.</span><span class="sxs-lookup"><span data-stu-id="4e374-192">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>  
  
 <span data-ttu-id="4e374-193">Se você usar `Exit Function` sem atribuir um valor para `name`, o procedimento retorna o valor padrão para o tipo de dados que é especificado em `returntype`.</span><span class="sxs-lookup"><span data-stu-id="4e374-193">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="4e374-194">Se `returntype` não for especificado, o procedimento retorna `Nothing`, que é o valor padrão para `Object`.</span><span class="sxs-lookup"><span data-stu-id="4e374-194">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>  
  
## <a name="calling-a-function"></a><span data-ttu-id="4e374-195">Chamando uma Função</span><span class="sxs-lookup"><span data-stu-id="4e374-195">Calling a Function</span></span>  
 <span data-ttu-id="4e374-196">Você chama um `Function` procedimento usando o nome do procedimento, seguido de lista de argumentos entre parênteses, em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="4e374-196">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="4e374-197">Você pode omitir os parênteses somente se você não fornecer quaisquer argumentos.</span><span class="sxs-lookup"><span data-stu-id="4e374-197">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="4e374-198">No entanto, seu código é mais legível se você sempre incluir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="4e374-198">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="4e374-199">Você chama um `Function` procedimento da mesma maneira que você chamar qualquer biblioteca de função como `Sqrt`, `Cos`, ou `ChrW`.</span><span class="sxs-lookup"><span data-stu-id="4e374-199">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>  
  
 <span data-ttu-id="4e374-200">Você também pode chamar uma função usando o `Call` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="4e374-200">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="4e374-201">Nesse caso, o valor de retorno será ignorado.</span><span class="sxs-lookup"><span data-stu-id="4e374-201">In that case, the return value is ignored.</span></span> <span data-ttu-id="4e374-202">Usar o `Call` palavra-chave não é recomendado na maioria dos casos.</span><span class="sxs-lookup"><span data-stu-id="4e374-202">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="4e374-203">Para obter mais informações, consulte [instrução Call](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4e374-203">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="4e374-204">Visual Basic, às vezes, reorganiza expressões aritméticas para aumentar a eficiência interna.</span><span class="sxs-lookup"><span data-stu-id="4e374-204">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="4e374-205">Por esse motivo, você não deve usar um `Function` procedimento em uma expressão aritmética quando a função altera o valor de variáveis na mesma expressão.</span><span class="sxs-lookup"><span data-stu-id="4e374-205">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>  
  
## <a name="async-functions"></a><span data-ttu-id="4e374-206">Funções assíncronas</span><span class="sxs-lookup"><span data-stu-id="4e374-206">Async Functions</span></span>  
 <span data-ttu-id="4e374-207">O *Async* recurso permite que você chame funções assíncronas sem o uso de retornos de chamada explícitos ou dividir manualmente seu código pelas várias funções ou expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="4e374-207">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="4e374-208">Se você marcar uma função com o [Async](../../../visual-basic/language-reference/modifiers/async.md) modificador, você pode usar o [Await](../../../visual-basic/language-reference/operators/await-operator.md) operador na função.</span><span class="sxs-lookup"><span data-stu-id="4e374-208">If you mark a function with the [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="4e374-209">Controlar quando chega uma `Await` expressão no `Async` função, o controle retorna ao chamador e o progresso na função é suspenso até que a tarefa em espera é concluída.</span><span class="sxs-lookup"><span data-stu-id="4e374-209">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="4e374-210">Quando a tarefa for concluída, pode retomar a execução na função.</span><span class="sxs-lookup"><span data-stu-id="4e374-210">When the task is complete, execution can resume in the function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e374-211">Um `Async` procedimento retorna ao chamador quando ou encontra o primeiro objeto de espera que ainda não foi concluído ou chegar ao final do `Async` procedimento, o que ocorrer primeiro.</span><span class="sxs-lookup"><span data-stu-id="4e374-211">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>  
  
 <span data-ttu-id="4e374-212">Um `Async` função pode ter um tipo de retorno <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="4e374-212">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="4e374-213">Um exemplo de um `Async` função que tem um tipo de retorno de <xref:System.Threading.Tasks.Task%601> é fornecido abaixo.</span><span class="sxs-lookup"><span data-stu-id="4e374-213">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>  
  
 <span data-ttu-id="4e374-214">Um `Async` função não pode declarar qualquer [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parâmetros.</span><span class="sxs-lookup"><span data-stu-id="4e374-214">An `Async` function cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="4e374-215">Um [instrução Sub](sub-statement.md) também pode ser marcado com o `Async` modificador.</span><span class="sxs-lookup"><span data-stu-id="4e374-215">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="4e374-216">Isso é usado principalmente para manipuladores de eventos, onde um valor não pode ser retornado.</span><span class="sxs-lookup"><span data-stu-id="4e374-216">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="4e374-217">Um `Async``Sub` procedimento não pode ser esperado e o chamador de um `Async``Sub` procedimento não pode capturar exceções geradas pelo `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="4e374-217">An `Async``Sub` procedure can't be awaited, and the caller of an `Async``Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>  
  
 <span data-ttu-id="4e374-218">Para obter mais informações sobre `Async` funções, consulte [programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md), [fluxo de controle em programas assíncronos](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), e [Async retornar tipos](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="4e374-218">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="iterator-functions"></a><span data-ttu-id="4e374-219">Funções de iterador</span><span class="sxs-lookup"><span data-stu-id="4e374-219">Iterator Functions</span></span>  
 <span data-ttu-id="4e374-220">Um *iterador* função executa uma iteração personalizada em uma coleção, como uma lista ou matriz.</span><span class="sxs-lookup"><span data-stu-id="4e374-220">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="4e374-221">Uma função iterator usa o [Yield](yield-statement.md) instrução para retornar cada elemento de uma por vez.</span><span class="sxs-lookup"><span data-stu-id="4e374-221">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="4e374-222">Quando um [Yield](yield-statement.md) instrução for atingida, o local atual no código será lembrado.</span><span class="sxs-lookup"><span data-stu-id="4e374-222">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="4e374-223">A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.</span><span class="sxs-lookup"><span data-stu-id="4e374-223">Execution is restarted from that location the next time the iterator function is called.</span></span>  
  
 <span data-ttu-id="4e374-224">Chamar um iterador no código do cliente usando um [para cada um... Próxima](for-each-next-statement.md) instrução.</span><span class="sxs-lookup"><span data-stu-id="4e374-224">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>  
  
 <span data-ttu-id="4e374-225">O tipo de retorno de uma função de iterador pode ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="4e374-225">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="4e374-226">Para obter mais informações, consulte [Iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="4e374-226">For more information, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e374-227">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4e374-227">Example</span></span>  
 <span data-ttu-id="4e374-228">O exemplo a seguir usa o `Function` instrução para declarar o nome, parâmetros e código que formam o corpo de uma `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="4e374-228">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="4e374-229">O `ParamArray` modificador permite que a função aceite um número variável de argumentos.</span><span class="sxs-lookup"><span data-stu-id="4e374-229">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#25](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="4e374-230">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4e374-230">Example</span></span>  
 <span data-ttu-id="4e374-231">O exemplo a seguir chama a função declarada no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="4e374-231">The following example invokes the function declared in the preceding example.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="4e374-232">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4e374-232">Example</span></span>  
 <span data-ttu-id="4e374-233">No exemplo a seguir, `DelayAsync` é um `Async``Function` que tem um tipo de retorno <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="4e374-233">In the following example, `DelayAsync` is an `Async``Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="4e374-234">`DelayAsync` tem uma instrução `Return` que retorna um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="4e374-234">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="4e374-235">Portanto, a declaração da função de `DelayAsync` deve ter um tipo de retorno `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="4e374-235">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="4e374-236">Como o tipo de retorno é `Task(Of Integer)`, a avaliação do `Await` expressão em `DoSomethingAsync` produz um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="4e374-236">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="4e374-237">Isso é demonstrado nesta instrução: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="4e374-237">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="4e374-238">O `startButton_Click` procedimento é um exemplo de uma `Async Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="4e374-238">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="4e374-239">Porque `DoSomethingAsync` é um `Async` função, a tarefa para a chamada `DoSomethingAsync` deve ser aguardada, como mostra a seguinte instrução: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="4e374-239">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="4e374-240">O `startButton_Click``Sub` procedimento deve ser definido com o `Async` modificador porque ele tem um `Await` expressão.</span><span class="sxs-lookup"><span data-stu-id="4e374-240">The `startButton_Click``Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4e374-241">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4e374-241">See Also</span></span>  
 [<span data-ttu-id="4e374-242">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="4e374-242">Sub Statement</span></span>](sub-statement.md)  
 [<span data-ttu-id="4e374-243">Procedimentos de Função</span><span class="sxs-lookup"><span data-stu-id="4e374-243">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [<span data-ttu-id="4e374-244">Lista de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4e374-244">Parameter List</span></span>](parameter-list.md)  
 [<span data-ttu-id="4e374-245">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="4e374-245">Dim Statement</span></span>](dim-statement.md)  
 [<span data-ttu-id="4e374-246">Instrução Call</span><span class="sxs-lookup"><span data-stu-id="4e374-246">Call Statement</span></span>](call-statement.md)  
 [<span data-ttu-id="4e374-247">Of</span><span class="sxs-lookup"><span data-stu-id="4e374-247">Of</span></span>](of-clause.md)  
 [<span data-ttu-id="4e374-248">Matrizes de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4e374-248">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)  
 [<span data-ttu-id="4e374-249">Como usar uma classe genérica</span><span class="sxs-lookup"><span data-stu-id="4e374-249">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [<span data-ttu-id="4e374-250">Solução de problemas de Procedimentos</span><span class="sxs-lookup"><span data-stu-id="4e374-250">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)  
 [<span data-ttu-id="4e374-251">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="4e374-251">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)  
 [<span data-ttu-id="4e374-252">Expressão de Função</span><span class="sxs-lookup"><span data-stu-id="4e374-252">Function Expression</span></span>](../../../visual-basic/language-reference/operators/function-expression.md)
