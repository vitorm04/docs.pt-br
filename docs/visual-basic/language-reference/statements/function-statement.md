---
title: Instrução Function (Visual Basic)
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
ms.openlocfilehash: 5018aebb0401ce5a1c46ecf04a7c65ca676271e7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565898"
---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="94cc6-102">Instrução Function (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94cc6-102">Function Statement (Visual Basic)</span></span>
<span data-ttu-id="94cc6-103">Declara o nome, parâmetros e código que definem um `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="94cc6-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94cc6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94cc6-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]  
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Function ]  
    [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="94cc6-105">Partes</span><span class="sxs-lookup"><span data-stu-id="94cc6-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="94cc6-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94cc6-106">Optional.</span></span> <span data-ttu-id="94cc6-107">Ver [lista de atributos](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="94cc6-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="94cc6-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94cc6-108">Optional.</span></span> <span data-ttu-id="94cc6-109">Pode ser uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="94cc6-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="94cc6-110">Público</span><span class="sxs-lookup"><span data-stu-id="94cc6-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="94cc6-111">Protegido</span><span class="sxs-lookup"><span data-stu-id="94cc6-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="94cc6-112">Friend</span><span class="sxs-lookup"><span data-stu-id="94cc6-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="94cc6-113">Privado</span><span class="sxs-lookup"><span data-stu-id="94cc6-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   [<span data-ttu-id="94cc6-114">Amigo Protegido</span><span class="sxs-lookup"><span data-stu-id="94cc6-114">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

    - [<span data-ttu-id="94cc6-115">Particular Protegido</span><span class="sxs-lookup"><span data-stu-id="94cc6-115">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)  
  
     <span data-ttu-id="94cc6-116">Ver [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="94cc6-116">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="94cc6-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94cc6-117">Optional.</span></span> <span data-ttu-id="94cc6-118">Pode ser uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="94cc6-118">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="94cc6-119">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="94cc6-119">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="94cc6-120">Substituições</span><span class="sxs-lookup"><span data-stu-id="94cc6-120">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="94cc6-121">Substituível</span><span class="sxs-lookup"><span data-stu-id="94cc6-121">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="94cc6-122">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="94cc6-122">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="94cc6-123">MustOverride</span><span class="sxs-lookup"><span data-stu-id="94cc6-123">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="94cc6-124">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94cc6-124">Optional.</span></span> <span data-ttu-id="94cc6-125">Ver [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="94cc6-125">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="94cc6-126">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94cc6-126">Optional.</span></span> <span data-ttu-id="94cc6-127">Ver [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="94cc6-127">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="94cc6-128">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94cc6-128">Optional.</span></span> <span data-ttu-id="94cc6-129">Ver [Async](../../../visual-basic/language-reference/modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="94cc6-129">See [Async](../../../visual-basic/language-reference/modifiers/async.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="94cc6-130">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94cc6-130">Optional.</span></span> <span data-ttu-id="94cc6-131">Ver [iterador](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="94cc6-131">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="94cc6-132">Necessário.</span><span class="sxs-lookup"><span data-stu-id="94cc6-132">Required.</span></span> <span data-ttu-id="94cc6-133">Nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="94cc6-133">Name of the procedure.</span></span> <span data-ttu-id="94cc6-134">Ver [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="94cc6-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="94cc6-135">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94cc6-135">Optional.</span></span> <span data-ttu-id="94cc6-136">Lista de parâmetros de tipo para um procedimento genérico.</span><span class="sxs-lookup"><span data-stu-id="94cc6-136">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="94cc6-137">Ver [lista de tipos](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="94cc6-137">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="94cc6-138">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94cc6-138">Optional.</span></span> <span data-ttu-id="94cc6-139">Lista de nomes de variáveis locais que representam os parâmetros deste procedimento.</span><span class="sxs-lookup"><span data-stu-id="94cc6-139">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="94cc6-140">Ver [lista de parâmetros](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="94cc6-140">See [Parameter List](parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="94cc6-141">Necessário se `Option Strict` é `On`.</span><span class="sxs-lookup"><span data-stu-id="94cc6-141">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="94cc6-142">Tipo de dados do valor retornado por esse procedimento.</span><span class="sxs-lookup"><span data-stu-id="94cc6-142">Data type of the value returned by this procedure.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="94cc6-143">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94cc6-143">Optional.</span></span> <span data-ttu-id="94cc6-144">Indica que esse procedimento implementa uma ou mais `Function` procedimentos, cada uma delas definida em uma interface implementada pela classe ou estrutura que contém esse procedimento.</span><span class="sxs-lookup"><span data-stu-id="94cc6-144">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="94cc6-145">Ver [implementa a instrução](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="94cc6-145">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="94cc6-146">Necessário se `Implements` for fornecido.</span><span class="sxs-lookup"><span data-stu-id="94cc6-146">Required if `Implements` is supplied.</span></span> <span data-ttu-id="94cc6-147">Lista de `Function` procedimentos que está sendo implementados.</span><span class="sxs-lookup"><span data-stu-id="94cc6-147">List of `Function` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="94cc6-148">Cada `implementedprocedure` tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="94cc6-148">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="94cc6-149">Parte</span><span class="sxs-lookup"><span data-stu-id="94cc6-149">Part</span></span>|<span data-ttu-id="94cc6-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="94cc6-150">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="94cc6-151">Necessário.</span><span class="sxs-lookup"><span data-stu-id="94cc6-151">Required.</span></span> <span data-ttu-id="94cc6-152">Que contém o nome de uma interface implementada por esse procedimento classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="94cc6-152">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="94cc6-153">Necessário.</span><span class="sxs-lookup"><span data-stu-id="94cc6-153">Required.</span></span> <span data-ttu-id="94cc6-154">Nome pelo qual o procedimento é definido em `interface`.</span><span class="sxs-lookup"><span data-stu-id="94cc6-154">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="94cc6-155">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94cc6-155">Optional.</span></span> <span data-ttu-id="94cc6-156">Indica que esse procedimento pode manipular um ou mais eventos específicos.</span><span class="sxs-lookup"><span data-stu-id="94cc6-156">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="94cc6-157">Ver [manipula](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="94cc6-157">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="94cc6-158">Necessário se `Handles` for fornecido.</span><span class="sxs-lookup"><span data-stu-id="94cc6-158">Required if `Handles` is supplied.</span></span> <span data-ttu-id="94cc6-159">Lista de eventos que manipula esse procedimento.</span><span class="sxs-lookup"><span data-stu-id="94cc6-159">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="94cc6-160">Cada `eventspecifier` tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="94cc6-160">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="94cc6-161">Parte</span><span class="sxs-lookup"><span data-stu-id="94cc6-161">Part</span></span>|<span data-ttu-id="94cc6-162">Descrição</span><span class="sxs-lookup"><span data-stu-id="94cc6-162">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="94cc6-163">Necessário.</span><span class="sxs-lookup"><span data-stu-id="94cc6-163">Required.</span></span> <span data-ttu-id="94cc6-164">Variável de objeto declarado com o tipo de dados da classe ou estrutura que gera o evento.</span><span class="sxs-lookup"><span data-stu-id="94cc6-164">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="94cc6-165">Necessário.</span><span class="sxs-lookup"><span data-stu-id="94cc6-165">Required.</span></span> <span data-ttu-id="94cc6-166">Nome do evento que lida com esse procedimento.</span><span class="sxs-lookup"><span data-stu-id="94cc6-166">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="94cc6-167">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94cc6-167">Optional.</span></span> <span data-ttu-id="94cc6-168">Bloco de instruções a serem executadas dentro deste procedimento.</span><span class="sxs-lookup"><span data-stu-id="94cc6-168">Block of statements to be executed within this procedure.</span></span>  
  
-   `End Function`  
  
     <span data-ttu-id="94cc6-169">Finaliza a definição desse procedimento.</span><span class="sxs-lookup"><span data-stu-id="94cc6-169">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94cc6-170">Comentários</span><span class="sxs-lookup"><span data-stu-id="94cc6-170">Remarks</span></span>  
 <span data-ttu-id="94cc6-171">Todo o código executável deve ser dentro de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="94cc6-171">All executable code must be inside a procedure.</span></span> <span data-ttu-id="94cc6-172">Cada procedimento, por sua vez, é declarado dentro de uma classe, uma estrutura ou um módulo que é conhecido como a classe, estrutura ou módulo recipiente.</span><span class="sxs-lookup"><span data-stu-id="94cc6-172">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>  
  
 <span data-ttu-id="94cc6-173">Para retornar um valor para o código de chamada, use uma `Function` procedimento; caso contrário, use um `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="94cc6-173">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>  
  
## <a name="defining-a-function"></a><span data-ttu-id="94cc6-174">Definição de uma função</span><span class="sxs-lookup"><span data-stu-id="94cc6-174">Defining a Function</span></span>  
 <span data-ttu-id="94cc6-175">Você pode definir um `Function` procedimento apenas no nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="94cc6-175">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="94cc6-176">Portanto, o contexto da declaração para uma função deve ser uma classe, uma estrutura, um módulo ou uma interface e não pode ser um arquivo de origem, um namespace, um procedimento ou um bloco.</span><span class="sxs-lookup"><span data-stu-id="94cc6-176">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="94cc6-177">Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="94cc6-177">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="94cc6-178">`Function` padrão de procedimentos para acesso público.</span><span class="sxs-lookup"><span data-stu-id="94cc6-178">`Function` procedures default to public access.</span></span> <span data-ttu-id="94cc6-179">Você pode ajustar os níveis de acesso com os modificadores de acesso.</span><span class="sxs-lookup"><span data-stu-id="94cc6-179">You can adjust their access levels with the access modifiers.</span></span>  
  
 <span data-ttu-id="94cc6-180">Um `Function` procedimento pode declarar o tipo de dados do valor que o procedimento retorna.</span><span class="sxs-lookup"><span data-stu-id="94cc6-180">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="94cc6-181">Você pode especificar qualquer tipo de dados ou o nome de uma enumeração, uma estrutura, uma classe ou uma interface.</span><span class="sxs-lookup"><span data-stu-id="94cc6-181">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="94cc6-182">Se você não especificar o `returntype` parâmetro, o procedimento retornará `Object`.</span><span class="sxs-lookup"><span data-stu-id="94cc6-182">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>  
  
 <span data-ttu-id="94cc6-183">Se esse procedimento usa o `Implements` palavra-chave, a classe ou estrutura contendo também deve ter um `Implements` instrução que segue imediatamente seus `Class` ou `Structure` instrução.</span><span class="sxs-lookup"><span data-stu-id="94cc6-183">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="94cc6-184">O `Implements` instrução deve incluir cada interface que é especificado no `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="94cc6-184">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="94cc6-185">No entanto, o nome pelo qual uma interface define os `Function` (no `definedname`) não precisa corresponder ao nome do procedimento (no `name`).</span><span class="sxs-lookup"><span data-stu-id="94cc6-185">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94cc6-186">Você pode usar expressões lambda para definir expressões de função embutida.</span><span class="sxs-lookup"><span data-stu-id="94cc6-186">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="94cc6-187">Para obter mais informações, consulte [expressão de função](../../../visual-basic/language-reference/operators/function-expression.md) e [expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="94cc6-187">For more information, see [Function Expression](../../../visual-basic/language-reference/operators/function-expression.md) and [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
## <a name="returning-from-a-function"></a><span data-ttu-id="94cc6-188">Retornar de uma função</span><span class="sxs-lookup"><span data-stu-id="94cc6-188">Returning from a Function</span></span>  
 <span data-ttu-id="94cc6-189">Quando o `Function` procedimento retorna para o código de chamada, a execução continua com a instrução que segue a instrução que chamou o procedimento.</span><span class="sxs-lookup"><span data-stu-id="94cc6-189">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>  
  
 <span data-ttu-id="94cc6-190">Para retornar um valor de uma função, você pode atribuir o valor para o nome da função ou incluí-lo em um `Return` instrução.</span><span class="sxs-lookup"><span data-stu-id="94cc6-190">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>  
  
 <span data-ttu-id="94cc6-191">O `Return` instrução simultaneamente atribui o valor de retorno e sai da função, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="94cc6-191">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>  
  
 [!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]  
  
 <span data-ttu-id="94cc6-192">O exemplo a seguir atribui o valor de retorno para o nome da função `myFunction` e, em seguida, usa o `Exit Function` instrução para retornar.</span><span class="sxs-lookup"><span data-stu-id="94cc6-192">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>  
  
 [!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]  
  
 <span data-ttu-id="94cc6-193">O `Exit Function` e `Return` instruções fazem com que uma saída imediata de uma `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="94cc6-193">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="94cc6-194">Qualquer número de `Exit Function` e `Return` instruções podem aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Function` e `Return` instruções.</span><span class="sxs-lookup"><span data-stu-id="94cc6-194">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>  
  
 <span data-ttu-id="94cc6-195">Se você usar `Exit Function` sem atribuir um valor para `name`, o procedimento retorna o valor padrão para o tipo de dados que é especificado no `returntype`.</span><span class="sxs-lookup"><span data-stu-id="94cc6-195">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="94cc6-196">Se `returntype` não for especificado, o procedimento retorna `Nothing`, que é o valor padrão para `Object`.</span><span class="sxs-lookup"><span data-stu-id="94cc6-196">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>  
  
## <a name="calling-a-function"></a><span data-ttu-id="94cc6-197">Chamando uma Função</span><span class="sxs-lookup"><span data-stu-id="94cc6-197">Calling a Function</span></span>  
 <span data-ttu-id="94cc6-198">Você chama um `Function` procedimento usando o nome do procedimento, seguido de lista de argumentos entre parênteses, em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="94cc6-198">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="94cc6-199">Você pode omitir os parênteses somente se você não estiver fornecendo quaisquer argumentos.</span><span class="sxs-lookup"><span data-stu-id="94cc6-199">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="94cc6-200">No entanto, seu código é mais legível, se você sempre incluir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="94cc6-200">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="94cc6-201">Você chama um `Function` procedimento da mesma maneira que você chame qualquer biblioteca de função como `Sqrt`, `Cos`, ou `ChrW`.</span><span class="sxs-lookup"><span data-stu-id="94cc6-201">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>  
  
 <span data-ttu-id="94cc6-202">Você também pode chamar uma função usando o `Call` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="94cc6-202">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="94cc6-203">Nesse caso, o valor retornado é ignorado.</span><span class="sxs-lookup"><span data-stu-id="94cc6-203">In that case, the return value is ignored.</span></span> <span data-ttu-id="94cc6-204">Usar o `Call` palavra-chave não é recomendado na maioria dos casos.</span><span class="sxs-lookup"><span data-stu-id="94cc6-204">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="94cc6-205">Para obter mais informações, consulte [instrução Call](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="94cc6-205">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="94cc6-206">Visual Basic, às vezes, reorganiza expressões aritméticas para aumentar a eficiência interna.</span><span class="sxs-lookup"><span data-stu-id="94cc6-206">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="94cc6-207">Por esse motivo, você não deve usar um `Function` procedimento em uma expressão aritmética quando a função altera o valor de variáveis na mesma expressão.</span><span class="sxs-lookup"><span data-stu-id="94cc6-207">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>  
  
## <a name="async-functions"></a><span data-ttu-id="94cc6-208">Funções assíncronas</span><span class="sxs-lookup"><span data-stu-id="94cc6-208">Async Functions</span></span>  
 <span data-ttu-id="94cc6-209">O *Async* recurso permite que você invocar funções assíncronas sem usar retornos de chamada explícitos ou dividir manualmente seu código em várias funções ou expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="94cc6-209">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="94cc6-210">Se você marcar uma função com o [Async](../../../visual-basic/language-reference/modifiers/async.md) modificador, você pode usar o [Await](../../../visual-basic/language-reference/operators/await-operator.md) operador na função.</span><span class="sxs-lookup"><span data-stu-id="94cc6-210">If you mark a function with the [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="94cc6-211">Quando o controle atinge uma `Await` expressão no `Async` função, o controle retorna ao chamador e o progresso na função é suspenso até que a tarefa aguardada seja concluída.</span><span class="sxs-lookup"><span data-stu-id="94cc6-211">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="94cc6-212">Quando a tarefa for concluída, pode retomar a execução na função.</span><span class="sxs-lookup"><span data-stu-id="94cc6-212">When the task is complete, execution can resume in the function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94cc6-213">Uma `Async` procedimento retorna ao chamador quando encontra o primeiro objeto esperado que não ainda foi concluído ou ou chega ao final do `Async` procedimento, o que ocorrer primeiro.</span><span class="sxs-lookup"><span data-stu-id="94cc6-213">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>  
  
 <span data-ttu-id="94cc6-214">Uma `Async` função pode ter um tipo de retorno <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="94cc6-214">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="94cc6-215">Um exemplo de um `Async` que tem um tipo de retorno da função <xref:System.Threading.Tasks.Task%601> é fornecido abaixo.</span><span class="sxs-lookup"><span data-stu-id="94cc6-215">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>  
  
 <span data-ttu-id="94cc6-216">Uma `Async` função não pode declarar qualquer [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parâmetros.</span><span class="sxs-lookup"><span data-stu-id="94cc6-216">An `Async` function cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="94cc6-217">Um [instrução Sub](sub-statement.md) também pode ser marcado com o `Async` modificador.</span><span class="sxs-lookup"><span data-stu-id="94cc6-217">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="94cc6-218">Isso é usado principalmente para manipuladores de eventos, onde um valor não pode ser retornado.</span><span class="sxs-lookup"><span data-stu-id="94cc6-218">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="94cc6-219">Uma `Async` `Sub` procedimento não pode ser esperado e o chamador de um `Async` `Sub` procedimento não pode capturar exceções geradas pelo `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="94cc6-219">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>  
  
 <span data-ttu-id="94cc6-220">Para obter mais informações sobre `Async` funções, consulte [programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md), [fluxo de controle em programas assíncronos](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), e [tipos de retorno assíncronos](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="94cc6-220">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="iterator-functions"></a><span data-ttu-id="94cc6-221">Funções de iterador</span><span class="sxs-lookup"><span data-stu-id="94cc6-221">Iterator Functions</span></span>  
 <span data-ttu-id="94cc6-222">Uma *iterador* função realiza uma iteração personalizada em uma coleção, como uma lista ou matriz.</span><span class="sxs-lookup"><span data-stu-id="94cc6-222">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="94cc6-223">Uma função de iterador usa a [Yield](yield-statement.md) instrução para retornar um elemento de cada vez.</span><span class="sxs-lookup"><span data-stu-id="94cc6-223">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="94cc6-224">Quando um [Yield](yield-statement.md) instrução for atingida, o local atual no código será lembrado.</span><span class="sxs-lookup"><span data-stu-id="94cc6-224">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="94cc6-225">A execução será reiniciada desse local na próxima vez que a função iteradora for chamada.</span><span class="sxs-lookup"><span data-stu-id="94cc6-225">Execution is restarted from that location the next time the iterator function is called.</span></span>  
  
 <span data-ttu-id="94cc6-226">Você chama um iterador no código do cliente usando um [para cada um... Próxima](for-each-next-statement.md) instrução.</span><span class="sxs-lookup"><span data-stu-id="94cc6-226">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>  
  
 <span data-ttu-id="94cc6-227">O tipo de retorno de uma função de iterador pode ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="94cc6-227">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="94cc6-228">Para obter mais informações, consulte [Iteradores](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="94cc6-228">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="94cc6-229">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94cc6-229">Example</span></span>  
 <span data-ttu-id="94cc6-230">O exemplo a seguir usa o `Function` instrução para declarar o nome, parâmetros e código que formam o corpo de uma `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="94cc6-230">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="94cc6-231">O `ParamArray` modificador permite que a função aceite um número variável de argumentos.</span><span class="sxs-lookup"><span data-stu-id="94cc6-231">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>  
  
 [!code-vb[VbVbalrStatements#25](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]  
  
## <a name="example"></a><span data-ttu-id="94cc6-232">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94cc6-232">Example</span></span>  
 <span data-ttu-id="94cc6-233">O exemplo a seguir chama a função declarada no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="94cc6-233">The following example invokes the function declared in the preceding example.</span></span>  
  
 [!code-vb[VbVbalrStatements#26](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="94cc6-234">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94cc6-234">Example</span></span>  
 <span data-ttu-id="94cc6-235">No exemplo a seguir `DelayAsync` é um `Async` `Function` que tem um tipo de retorno <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="94cc6-235">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="94cc6-236">`DelayAsync` tem uma instrução `Return` que retorna um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="94cc6-236">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="94cc6-237">Portanto, a declaração da função de `DelayAsync` precisa ter um tipo de retorno `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="94cc6-237">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="94cc6-238">Como é o tipo de retorno `Task(Of Integer)`, a avaliação do `Await` expressão em `DoSomethingAsync` produz um inteiro.</span><span class="sxs-lookup"><span data-stu-id="94cc6-238">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="94cc6-239">Isso é demonstrado nesta instrução: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="94cc6-239">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="94cc6-240">O `startButton_Click` procedimento é um exemplo de um `Async Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="94cc6-240">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="94cc6-241">Porque `DoSomethingAsync` é um `Async` função, a tarefa para a chamada a `DoSomethingAsync` deve ser colocada em espera, como a instrução a seguir demonstra: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="94cc6-241">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="94cc6-242">O `startButton_Click` `Sub` procedimento deve ser definido com o `Async` modificador porque ele tem um `Await` expressão.</span><span class="sxs-lookup"><span data-stu-id="94cc6-242">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 [!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="94cc6-243">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94cc6-243">See also</span></span>
- [<span data-ttu-id="94cc6-244">Instrução Sub</span><span class="sxs-lookup"><span data-stu-id="94cc6-244">Sub Statement</span></span>](sub-statement.md)
- [<span data-ttu-id="94cc6-245">Procedimentos de Função</span><span class="sxs-lookup"><span data-stu-id="94cc6-245">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="94cc6-246">Lista de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="94cc6-246">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="94cc6-247">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="94cc6-247">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="94cc6-248">Instrução Call</span><span class="sxs-lookup"><span data-stu-id="94cc6-248">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="94cc6-249">Of</span><span class="sxs-lookup"><span data-stu-id="94cc6-249">Of</span></span>](of-clause.md)
- [<span data-ttu-id="94cc6-250">Matrizes de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="94cc6-250">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="94cc6-251">Como: usar uma classe genérica</span><span class="sxs-lookup"><span data-stu-id="94cc6-251">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="94cc6-252">Solução de problemas de Procedimentos</span><span class="sxs-lookup"><span data-stu-id="94cc6-252">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="94cc6-253">Expressões Lambda</span><span class="sxs-lookup"><span data-stu-id="94cc6-253">Lambda Expressions</span></span>](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
- [<span data-ttu-id="94cc6-254">Expressão de Função</span><span class="sxs-lookup"><span data-stu-id="94cc6-254">Function Expression</span></span>](../../../visual-basic/language-reference/operators/function-expression.md)
