---
title: "Função Statement (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Function
dev_langs:
- VB
helpviewer_keywords:
- procedures, creating
- Function procedures, Function statement syntax
- functions [Visual Basic], function procedures
- ParamArray keyword, Function statements
- Private keyword, Function statements
- declarations, procedures
- procedures, declaration
- Public keyword, in Function statement
- ByVal keyword, Function statements
- procedures, recursive
- Implements keyword, Function statements
- procedures, returning values
- Exit statement, in Function procedures
- recursive procedures
- As keyword, in Function statement
- Optional keyword, Function statements
- Function statement
- Visual Basic code, Function procedures
- procedures, function
- ByRef keyword, Function statements
- Friend keyword, Function statements
- End keyword, Function statements
- Handles keyword, Function statements
ms.assetid: a4497077-0f46-4ede-a27f-9e8670df52b9
caps.latest.revision: 62
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: dc1c456c71efb3cc6e60a8fdc77384e65975f110
ms.openlocfilehash: d875fe6df3ef7ac9390346588b1c2d48497d7116
ms.contentlocale: pt-br
ms.lasthandoff: 05/15/2017

---
# <a name="function-statement-visual-basic"></a><span data-ttu-id="22c0e-102">Instrução Function (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="22c0e-102">Function Statement (Visual Basic)</span></span>
<span data-ttu-id="22c0e-103">Declara o nome, parâmetros e código que definem um `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="22c0e-103">Declares the name, parameters, and code that define a `Function` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22c0e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="22c0e-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async | Iterator ]  
Function name [ (Of typeparamlist) ] [ (parameterlist) ] [ As returntype ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Function ]  
    [ statements ]  
End Function  
```  
  
## <a name="parts"></a><span data-ttu-id="22c0e-105">Partes</span><span class="sxs-lookup"><span data-stu-id="22c0e-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="22c0e-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="22c0e-106">Optional.</span></span> <span data-ttu-id="22c0e-107">Consulte [lista atributo](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="22c0e-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="22c0e-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="22c0e-108">Optional.</span></span> <span data-ttu-id="22c0e-109">Pode ser uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="22c0e-109">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="22c0e-110">Público</span><span class="sxs-lookup"><span data-stu-id="22c0e-110">Public</span></span>](../../../visual-basic/language-reference/modifiers/public.md)  
  
    -   [<span data-ttu-id="22c0e-111">Protegido</span><span class="sxs-lookup"><span data-stu-id="22c0e-111">Protected</span></span>](../../../visual-basic/language-reference/modifiers/protected.md)  
  
    -   [<span data-ttu-id="22c0e-112">Friend</span><span class="sxs-lookup"><span data-stu-id="22c0e-112">Friend</span></span>](../../../visual-basic/language-reference/modifiers/friend.md)  
  
    -   [<span data-ttu-id="22c0e-113">Privado</span><span class="sxs-lookup"><span data-stu-id="22c0e-113">Private</span></span>](../../../visual-basic/language-reference/modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="22c0e-114">Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="22c0e-114">See [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="22c0e-115">Opcional.</span><span class="sxs-lookup"><span data-stu-id="22c0e-115">Optional.</span></span> <span data-ttu-id="22c0e-116">Pode ser uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="22c0e-116">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="22c0e-117">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="22c0e-117">Overloads</span></span>](../../../visual-basic/language-reference/modifiers/overloads.md)  
  
    -   [<span data-ttu-id="22c0e-118">Substituições</span><span class="sxs-lookup"><span data-stu-id="22c0e-118">Overrides</span></span>](../../../visual-basic/language-reference/modifiers/overrides.md)  
  
    -   [<span data-ttu-id="22c0e-119">Substituível</span><span class="sxs-lookup"><span data-stu-id="22c0e-119">Overridable</span></span>](../../../visual-basic/language-reference/modifiers/overridable.md)  
  
    -   [<span data-ttu-id="22c0e-120">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="22c0e-120">NotOverridable</span></span>](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="22c0e-121">MustOverride</span><span class="sxs-lookup"><span data-stu-id="22c0e-121">MustOverride</span></span>](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="22c0e-122">Opcional.</span><span class="sxs-lookup"><span data-stu-id="22c0e-122">Optional.</span></span> <span data-ttu-id="22c0e-123">Consulte [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="22c0e-123">See [Shared](../../../visual-basic/language-reference/modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="22c0e-124">Opcional.</span><span class="sxs-lookup"><span data-stu-id="22c0e-124">Optional.</span></span> <span data-ttu-id="22c0e-125">Consulte [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="22c0e-125">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="22c0e-126">Opcional.</span><span class="sxs-lookup"><span data-stu-id="22c0e-126">Optional.</span></span> <span data-ttu-id="22c0e-127">Consulte [Async](../../../visual-basic/language-reference/modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="22c0e-127">See [Async](../../../visual-basic/language-reference/modifiers/async.md).</span></span>  
  
-   `Iterator`  
  
     <span data-ttu-id="22c0e-128">Opcional.</span><span class="sxs-lookup"><span data-stu-id="22c0e-128">Optional.</span></span> <span data-ttu-id="22c0e-129">Consulte [iterador](../../../visual-basic/language-reference/modifiers/iterator.md).</span><span class="sxs-lookup"><span data-stu-id="22c0e-129">See [Iterator](../../../visual-basic/language-reference/modifiers/iterator.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="22c0e-130">Necessário.</span><span class="sxs-lookup"><span data-stu-id="22c0e-130">Required.</span></span> <span data-ttu-id="22c0e-131">Nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="22c0e-131">Name of the procedure.</span></span> <span data-ttu-id="22c0e-132">Consulte [nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="22c0e-132">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="22c0e-133">Opcional.</span><span class="sxs-lookup"><span data-stu-id="22c0e-133">Optional.</span></span> <span data-ttu-id="22c0e-134">Lista de parâmetros de tipo para um procedimento genérico.</span><span class="sxs-lookup"><span data-stu-id="22c0e-134">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="22c0e-135">Consulte [digite lista](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="22c0e-135">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="22c0e-136">Opcional.</span><span class="sxs-lookup"><span data-stu-id="22c0e-136">Optional.</span></span> <span data-ttu-id="22c0e-137">Lista de nomes de variáveis locais que representam os parâmetros deste procedimento.</span><span class="sxs-lookup"><span data-stu-id="22c0e-137">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="22c0e-138">Consulte [lista de parâmetros](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="22c0e-138">See [Parameter List](parameter-list.md).</span></span>  
  
-   `returntype`  
  
     <span data-ttu-id="22c0e-139">Necessário se `Option Strict` é `On`.</span><span class="sxs-lookup"><span data-stu-id="22c0e-139">Required if `Option Strict` is `On`.</span></span> <span data-ttu-id="22c0e-140">Tipo de dados do valor retornado por esse procedimento.</span><span class="sxs-lookup"><span data-stu-id="22c0e-140">Data type of the value returned by this procedure.</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="22c0e-141">Opcional.</span><span class="sxs-lookup"><span data-stu-id="22c0e-141">Optional.</span></span> <span data-ttu-id="22c0e-142">Indica que essa propriedade implementa uma ou mais `Function` procedimentos, cada uma delas definida em uma interface implementada pela classe ou estrutura contendo esse procedimento.</span><span class="sxs-lookup"><span data-stu-id="22c0e-142">Indicates that this procedure implements one or more `Function` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="22c0e-143">Consulte [implementa a instrução](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="22c0e-143">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="22c0e-144">Necessário se `Implements` for fornecido.</span><span class="sxs-lookup"><span data-stu-id="22c0e-144">Required if `Implements` is supplied.</span></span> <span data-ttu-id="22c0e-145">Lista de `Function` procedimentos que estão sendo implementados.</span><span class="sxs-lookup"><span data-stu-id="22c0e-145">List of `Function` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="22c0e-146">Cada `implementedprocedure` tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="22c0e-146">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="22c0e-147">Parte</span><span class="sxs-lookup"><span data-stu-id="22c0e-147">Part</span></span>|<span data-ttu-id="22c0e-148">Descrição</span><span class="sxs-lookup"><span data-stu-id="22c0e-148">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="22c0e-149">Necessário.</span><span class="sxs-lookup"><span data-stu-id="22c0e-149">Required.</span></span> <span data-ttu-id="22c0e-150">Nome de uma interface implementada por esse procedimento contendo classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="22c0e-150">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="22c0e-151">Necessário.</span><span class="sxs-lookup"><span data-stu-id="22c0e-151">Required.</span></span> <span data-ttu-id="22c0e-152">Nome pelo qual o procedimento é definido em `interface`.</span><span class="sxs-lookup"><span data-stu-id="22c0e-152">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="22c0e-153">Opcional.</span><span class="sxs-lookup"><span data-stu-id="22c0e-153">Optional.</span></span> <span data-ttu-id="22c0e-154">Indica que esse procedimento pode manipular um ou mais eventos específicos.</span><span class="sxs-lookup"><span data-stu-id="22c0e-154">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="22c0e-155">Consulte [manipula](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="22c0e-155">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="22c0e-156">Necessário se `Handles` for fornecido.</span><span class="sxs-lookup"><span data-stu-id="22c0e-156">Required if `Handles` is supplied.</span></span> <span data-ttu-id="22c0e-157">Lista de eventos que esse procedimento manipula.</span><span class="sxs-lookup"><span data-stu-id="22c0e-157">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="22c0e-158">Cada `eventspecifier` tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="22c0e-158">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="22c0e-159">Parte</span><span class="sxs-lookup"><span data-stu-id="22c0e-159">Part</span></span>|<span data-ttu-id="22c0e-160">Descrição</span><span class="sxs-lookup"><span data-stu-id="22c0e-160">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="22c0e-161">Necessário.</span><span class="sxs-lookup"><span data-stu-id="22c0e-161">Required.</span></span> <span data-ttu-id="22c0e-162">Variável de objeto declarada com o tipo de dados da classe ou estrutura que gera o evento.</span><span class="sxs-lookup"><span data-stu-id="22c0e-162">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="22c0e-163">Necessário.</span><span class="sxs-lookup"><span data-stu-id="22c0e-163">Required.</span></span> <span data-ttu-id="22c0e-164">Nome do evento que esse procedimento manipula.</span><span class="sxs-lookup"><span data-stu-id="22c0e-164">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="22c0e-165">Opcional.</span><span class="sxs-lookup"><span data-stu-id="22c0e-165">Optional.</span></span> <span data-ttu-id="22c0e-166">Bloco de instruções para ser executado dentro deste procedimento.</span><span class="sxs-lookup"><span data-stu-id="22c0e-166">Block of statements to be executed within this procedure.</span></span>  
  
-   `End Function`  
  
     <span data-ttu-id="22c0e-167">Finaliza a definição desse procedimento.</span><span class="sxs-lookup"><span data-stu-id="22c0e-167">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22c0e-168">Comentários</span><span class="sxs-lookup"><span data-stu-id="22c0e-168">Remarks</span></span>  
 <span data-ttu-id="22c0e-169">Todos os códigos executáveis deverão estar dentro de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="22c0e-169">All executable code must be inside a procedure.</span></span> <span data-ttu-id="22c0e-170">Cada procedimento, por sua vez, é declarado dentro de uma classe, uma estrutura ou um módulo que é conhecido como a classe, estrutura ou módulo que contém.</span><span class="sxs-lookup"><span data-stu-id="22c0e-170">Each procedure, in turn, is declared within a class, a structure, or a module that is referred to as the containing class, structure, or module.</span></span>  
  
 <span data-ttu-id="22c0e-171">Para retornar um valor para o código de chamada, use uma `Function` procedimento; caso contrário, use uma `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="22c0e-171">To return a value to the calling code, use a `Function` procedure; otherwise, use a `Sub` procedure.</span></span>  
  
## <a name="defining-a-function"></a><span data-ttu-id="22c0e-172">Definindo uma função</span><span class="sxs-lookup"><span data-stu-id="22c0e-172">Defining a Function</span></span>  
 <span data-ttu-id="22c0e-173">Você pode definir uma `Function` procedimento apenas no nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="22c0e-173">You can define a `Function` procedure only at the module level.</span></span> <span data-ttu-id="22c0e-174">Portanto, o contexto da declaração para uma função deve ser uma classe, uma estrutura, um módulo ou uma interface e não pode ser um arquivo de origem, um namespace, um procedimento ou um bloco.</span><span class="sxs-lookup"><span data-stu-id="22c0e-174">Therefore, the declaration context for a function must be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="22c0e-175">Para obter mais informações, consulte [contextos de declaração e níveis de acesso padrão](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="22c0e-175">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="22c0e-176">`Function`padrão de procedimentos para acesso público.</span><span class="sxs-lookup"><span data-stu-id="22c0e-176">`Function` procedures default to public access.</span></span> <span data-ttu-id="22c0e-177">Você pode ajustar os níveis de acesso com os modificadores de acesso.</span><span class="sxs-lookup"><span data-stu-id="22c0e-177">You can adjust their access levels with the access modifiers.</span></span>  
  
 <span data-ttu-id="22c0e-178">Um `Function` procedimento pode declarar o tipo de dados do valor que o procedimento retorna.</span><span class="sxs-lookup"><span data-stu-id="22c0e-178">A `Function` procedure can declare the data type of the value that the procedure returns.</span></span> <span data-ttu-id="22c0e-179">Você pode especificar qualquer tipo de dados ou o nome de uma enumeração, uma estrutura, uma classe ou uma interface.</span><span class="sxs-lookup"><span data-stu-id="22c0e-179">You can specify any data type or the name of an enumeration, a structure, a class, or an interface.</span></span> <span data-ttu-id="22c0e-180">Se você não especificar o `returntype` , o procedimento retornará `Object`.</span><span class="sxs-lookup"><span data-stu-id="22c0e-180">If you don't specify the `returntype` parameter, the procedure returns `Object`.</span></span>  
  
 <span data-ttu-id="22c0e-181">Se esse procedimento utiliza o `Implements` palavra-chave, a classe ou estrutura continente deve também ter um `Implements` instrução que segue imediatamente o `Class` ou `Structure` instrução.</span><span class="sxs-lookup"><span data-stu-id="22c0e-181">If this procedure uses the `Implements` keyword, the containing class or structure must also have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="22c0e-182">O `Implements` instrução deve incluir cada interface especificada no `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="22c0e-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="22c0e-183">No entanto, o nome pelo qual uma interface define o `Function` (em `definedname`) não precisa corresponder ao nome do procedimento (em `name`).</span><span class="sxs-lookup"><span data-stu-id="22c0e-183">However, the name by which an interface defines the `Function` (in `definedname`) doesn't need to match the name of this procedure (in `name`).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22c0e-184">Você pode usar expressões lambda para definir a função embutida de expressões.</span><span class="sxs-lookup"><span data-stu-id="22c0e-184">You can use lambda expressions to define function expressions inline.</span></span> <span data-ttu-id="22c0e-185">Para obter mais informações, consulte [expressão de função](../../../visual-basic/language-reference/operators/function-expression.md) e [expressões Lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="22c0e-185">For more information, see [Function Expression](../../../visual-basic/language-reference/operators/function-expression.md) and [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).</span></span>  
  
## <a name="returning-from-a-function"></a><span data-ttu-id="22c0e-186">Retornar de uma função</span><span class="sxs-lookup"><span data-stu-id="22c0e-186">Returning from a Function</span></span>  
 <span data-ttu-id="22c0e-187">Quando o `Function` procedimento retorna para o código de chamada, a execução continua com a instrução que segue a declaração que chamou o procedimento.</span><span class="sxs-lookup"><span data-stu-id="22c0e-187">When the `Function` procedure returns to the calling code, execution continues with the statement that follows the statement that called the procedure.</span></span>  
  
 <span data-ttu-id="22c0e-188">Para retornar um valor de uma função, você pode atribuir o valor ao nome da função ou incluí-lo em um `Return` instrução.</span><span class="sxs-lookup"><span data-stu-id="22c0e-188">To return a value from a function, you can either assign the value to the function name or include it in a `Return` statement.</span></span>  
  
 <span data-ttu-id="22c0e-189">O `Return` instrução simultaneamente atribui o valor de retorno e sai da função, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="22c0e-189">The `Return` statement simultaneously assigns the return value and exits the function, as the following example shows.</span></span>  
  
 <span data-ttu-id="22c0e-190">[!code-vb[VbVbalrStatements&#24;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="22c0e-190">[!code-vb[VbVbalrStatements#24](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_1.vb)]</span></span>  
  
 <span data-ttu-id="22c0e-191">O exemplo a seguir atribui o valor de retorno ao nome da função `myFunction` e, em seguida, usa o `Exit Function` instrução para retornar.</span><span class="sxs-lookup"><span data-stu-id="22c0e-191">The following example assigns the return value to the function name `myFunction` and then uses the `Exit Function` statement to return.</span></span>  
  
 <span data-ttu-id="22c0e-192">[!code-vb[VbVbalrStatements&#23;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="22c0e-192">[!code-vb[VbVbalrStatements#23](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_2.vb)]</span></span>  
  
 <span data-ttu-id="22c0e-193">O `Exit Function` e `Return` instruções causam uma saída imediata de uma `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="22c0e-193">The `Exit Function` and `Return` statements cause an immediate exit from a `Function` procedure.</span></span> <span data-ttu-id="22c0e-194">Qualquer número de `Exit Function` e `Return` instruções podem aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Function` e `Return` instruções.</span><span class="sxs-lookup"><span data-stu-id="22c0e-194">Any number of `Exit Function` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Function` and `Return` statements.</span></span>  
  
 <span data-ttu-id="22c0e-195">Se você usar `Exit Function` sem atribuir um valor para `name`, o procedimento retorna o valor padrão para o tipo de dados especificado em `returntype`.</span><span class="sxs-lookup"><span data-stu-id="22c0e-195">If you use `Exit Function` without assigning a value to `name`, the procedure returns the default value for the data type that's specified in `returntype`.</span></span> <span data-ttu-id="22c0e-196">Se `returntype` não for especificado, o procedimento retorna `Nothing`, que é o valor padrão para `Object`.</span><span class="sxs-lookup"><span data-stu-id="22c0e-196">If `returntype` isn't specified, the procedure returns `Nothing`, which is the default value for `Object`.</span></span>  
  
## <a name="calling-a-function"></a><span data-ttu-id="22c0e-197">Chamando uma Função</span><span class="sxs-lookup"><span data-stu-id="22c0e-197">Calling a Function</span></span>  
 <span data-ttu-id="22c0e-198">Chamar uma `Function` procedimento usando o nome do procedimento, seguido de lista de argumentos entre parênteses, em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="22c0e-198">You call a `Function` procedure by using the procedure name, followed by the argument list in parentheses, in an expression.</span></span> <span data-ttu-id="22c0e-199">Você pode omitir os parênteses somente se você não está fornecendo quaisquer argumentos.</span><span class="sxs-lookup"><span data-stu-id="22c0e-199">You can omit the parentheses only if you aren't supplying any arguments.</span></span> <span data-ttu-id="22c0e-200">No entanto, seu código é mais legível se você sempre incluir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="22c0e-200">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="22c0e-201">Você chamar um `Function` procedimento da mesma maneira que você chamar qualquer biblioteca de função como `Sqrt`, `Cos`, ou `ChrW`.</span><span class="sxs-lookup"><span data-stu-id="22c0e-201">You call a `Function` procedure the same way that you call any library function such as `Sqrt`, `Cos`, or `ChrW`.</span></span>  
  
 <span data-ttu-id="22c0e-202">Você também pode chamar uma função usando o `Call` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="22c0e-202">You can also call a function by using the `Call` keyword.</span></span> <span data-ttu-id="22c0e-203">Nesse caso, o valor de retorno será ignorado.</span><span class="sxs-lookup"><span data-stu-id="22c0e-203">In that case, the return value is ignored.</span></span> <span data-ttu-id="22c0e-204">Usar o `Call` palavra-chave não é recomendado na maioria dos casos.</span><span class="sxs-lookup"><span data-stu-id="22c0e-204">Use of the `Call` keyword isn't recommended in most cases.</span></span> <span data-ttu-id="22c0e-205">Para obter mais informações, consulte [instrução Call](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="22c0e-205">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="22c0e-206">Visual Basic, às vezes, reorganiza expressões aritméticas para aumentar a eficiência interna.</span><span class="sxs-lookup"><span data-stu-id="22c0e-206">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="22c0e-207">Por esse motivo, você não deve usar uma `Function` procedimento em uma expressão aritmética quando a função altera o valor de variáveis na mesma expressão.</span><span class="sxs-lookup"><span data-stu-id="22c0e-207">For that reason, you shouldn't use a `Function` procedure in an arithmetic expression when the function changes the value of variables in the same expression.</span></span>  
  
## <a name="async-functions"></a><span data-ttu-id="22c0e-208">Funções assíncronas</span><span class="sxs-lookup"><span data-stu-id="22c0e-208">Async Functions</span></span>  
 <span data-ttu-id="22c0e-209">O *Async* recurso permite que você chame funções assíncronas sem usar retornos de chamada explícitos ou dividir manualmente seu código em várias funções ou expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="22c0e-209">The *Async* feature allows you to invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="22c0e-210">Se você marcar uma função com o [Async](../../../visual-basic/language-reference/modifiers/async.md) modificador, você pode usar o [Await](../../../visual-basic/language-reference/operators/await-operator.md) operador na função.</span><span class="sxs-lookup"><span data-stu-id="22c0e-210">If you mark a function with the [Async](../../../visual-basic/language-reference/modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the function.</span></span> <span data-ttu-id="22c0e-211">Quando o controle atinge um `Await` expressão no `Async` função, o controle retorna ao chamador e progresso na função está suspenso até que a tarefa aguardada seja concluída.</span><span class="sxs-lookup"><span data-stu-id="22c0e-211">When control reaches an `Await` expression in the `Async` function, control returns to the caller, and progress in the function is suspended until the awaited task completes.</span></span> <span data-ttu-id="22c0e-212">Quando a tarefa for concluída, a execução pode retomar na função.</span><span class="sxs-lookup"><span data-stu-id="22c0e-212">When the task is complete, execution can resume in the function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="22c0e-213">Um `Async` procedimento retorna ao chamador quando encontra o primeiro objeto esperado que não ainda foi concluído ou ou chegar ao final do `Async` procedimento, o que ocorrer primeiro.</span><span class="sxs-lookup"><span data-stu-id="22c0e-213">An `Async` procedure returns to the caller when either it encounters the first awaited object that’s not yet complete, or it gets to the end of the `Async` procedure, whichever occurs first.</span></span>  
  
 <span data-ttu-id="22c0e-214">Um `Async` função pode ter um tipo de retorno <xref:System.Threading.Tasks.Task%601>ou <xref:System.Threading.Tasks.Task>.</xref:System.Threading.Tasks.Task> </xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="22c0e-214">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="22c0e-215">Um exemplo de uma `Async` função que tem um tipo de retorno de <xref:System.Threading.Tasks.Task%601>é fornecido abaixo.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="22c0e-215">An example of an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601> is provided below.</span></span>  
  
 <span data-ttu-id="22c0e-216">Um `Async` função não pode declarar qualquer [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parâmetros.</span><span class="sxs-lookup"><span data-stu-id="22c0e-216">An `Async` function cannot declare any [ByRef](../../../visual-basic/language-reference/modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="22c0e-217">A [instrução Sub](sub-statement.md) também podem ser marcados com o `Async` modificador.</span><span class="sxs-lookup"><span data-stu-id="22c0e-217">A [Sub Statement](sub-statement.md) can also be marked with the `Async` modifier.</span></span> <span data-ttu-id="22c0e-218">Isso é usado principalmente para manipuladores de eventos, onde um valor não pode ser retornado.</span><span class="sxs-lookup"><span data-stu-id="22c0e-218">This is primarily used for event handlers, where a value cannot be returned.</span></span> <span data-ttu-id="22c0e-219">Um `Async``Sub` procedimento não pode ser esperado e o chamador de um `Async``Sub` procedimento não pode capturar exceções que são geradas pelo `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="22c0e-219">An `Async``Sub` procedure can't be awaited, and the caller of an `Async``Sub` procedure can't catch exceptions that are thrown by the `Sub` procedure.</span></span>  
  
 <span data-ttu-id="22c0e-220">Para obter mais informações sobre `Async` funções, consulte [programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md), [fluxo de controle em programas assíncronos](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), e [assíncronas retornam tipos](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="22c0e-220">For more information about `Async` functions, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="iterator-functions"></a><span data-ttu-id="22c0e-221">Funções de iterador</span><span class="sxs-lookup"><span data-stu-id="22c0e-221">Iterator Functions</span></span>  
 <span data-ttu-id="22c0e-222">Um *iterador* função realiza a uma iteração personalizada em uma coleção, como uma lista ou matriz.</span><span class="sxs-lookup"><span data-stu-id="22c0e-222">An *iterator* function performs a custom iteration over a collection, such as a list or array.</span></span> <span data-ttu-id="22c0e-223">Usa uma função de iterador de [gerar](yield-statement.md) instrução para retornar cada elemento por vez.</span><span class="sxs-lookup"><span data-stu-id="22c0e-223">An iterator function uses the [Yield](yield-statement.md) statement to return each element one at a time.</span></span> <span data-ttu-id="22c0e-224">Quando um [gerar](yield-statement.md) instrução for atingida, o local atual no código será lembrado.</span><span class="sxs-lookup"><span data-stu-id="22c0e-224">When a [Yield](yield-statement.md) statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="22c0e-225">Execução é reiniciada a partir desse local na próxima vez em que a função de iterador é chamada.</span><span class="sxs-lookup"><span data-stu-id="22c0e-225">Execution is restarted from that location the next time the iterator function is called.</span></span>  
  
 <span data-ttu-id="22c0e-226">Chamar um iterador no código do cliente usando um [para cada uma... Próxima](for-each-next-statement.md) instrução.</span><span class="sxs-lookup"><span data-stu-id="22c0e-226">You call an iterator from client code by using a [For Each…Next](for-each-next-statement.md) statement.</span></span>  
  
 <span data-ttu-id="22c0e-227">O tipo de retorno de uma função do iterador pode ser <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, ou <xref:System.Collections.Generic.IEnumerator%601>.</xref:System.Collections.Generic.IEnumerator%601> </xref:System.Collections.IEnumerator> </xref:System.Collections.Generic.IEnumerable%601> </xref:System.Collections.IEnumerable></span><span class="sxs-lookup"><span data-stu-id="22c0e-227">The return type of an iterator function can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="22c0e-228">Para obter mais informações, consulte [Iteradores](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="22c0e-228">For more information, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="example"></a><span data-ttu-id="22c0e-229">Exemplo</span><span class="sxs-lookup"><span data-stu-id="22c0e-229">Example</span></span>  
 <span data-ttu-id="22c0e-230">O exemplo a seguir usa o `Function` declaração para declarar o nome, parâmetros e código que formam o corpo de uma `Function` procedimento.</span><span class="sxs-lookup"><span data-stu-id="22c0e-230">The following example uses the `Function` statement to declare the name, parameters, and code that form the body of a `Function` procedure.</span></span> <span data-ttu-id="22c0e-231">O `ParamArray` modificador permite que a função aceite um número variável de argumentos.</span><span class="sxs-lookup"><span data-stu-id="22c0e-231">The `ParamArray` modifier enables the function to accept a variable number of arguments.</span></span>  
  
 <span data-ttu-id="22c0e-232">[!code-vb[25 VbVbalrStatements](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="22c0e-232">[!code-vb[VbVbalrStatements#25](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_3.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="22c0e-233">Exemplo</span><span class="sxs-lookup"><span data-stu-id="22c0e-233">Example</span></span>  
 <span data-ttu-id="22c0e-234">O exemplo a seguir chama a função declarada no exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="22c0e-234">The following example invokes the function declared in the preceding example.</span></span>  
  
 <span data-ttu-id="22c0e-235">[!code-vb[VbVbalrStatements&#26;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]</span><span class="sxs-lookup"><span data-stu-id="22c0e-235">[!code-vb[VbVbalrStatements#26](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/function-statement_4.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="22c0e-236">Exemplo</span><span class="sxs-lookup"><span data-stu-id="22c0e-236">Example</span></span>  
 <span data-ttu-id="22c0e-237">No exemplo a seguir, `DelayAsync` é um `Async``Function` que tem um tipo de retorno de <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="22c0e-237">In the following example, `DelayAsync` is an `Async``Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="22c0e-238">`DelayAsync`tem um `Return` instrução que retorna um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="22c0e-238">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="22c0e-239">Portanto, a declaração de função do `DelayAsync` deve ter um tipo de retorno de `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="22c0e-239">Therefore the function declaration of `DelayAsync` needs to have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="22c0e-240">Como o tipo de retorno é `Task(Of Integer)`, a avaliação do `Await` expressão em `DoSomethingAsync` produz um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="22c0e-240">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer.</span></span> <span data-ttu-id="22c0e-241">Isso é demonstrado nesta instrução: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="22c0e-241">This is demonstrated in this statement: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="22c0e-242">O `startButton_Click` procedimento é um exemplo de uma `Async Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="22c0e-242">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="22c0e-243">Porque `DoSomethingAsync` é um `Async` função, a tarefa para a chamada a `DoSomethingAsync` deve ser colocado em espera, como demonstra a seguinte instrução: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="22c0e-243">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement demonstrates: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="22c0e-244">O `startButton_Click``Sub` procedimento deve ser definido com o `Async` modificador porque ele tem um `Await` expressão.</span><span class="sxs-lookup"><span data-stu-id="22c0e-244">The `startButton_Click``Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 <span data-ttu-id="22c0e-245">[!code-vb[csAsyncMethod n º&1;](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]</span><span class="sxs-lookup"><span data-stu-id="22c0e-245">[!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/function-statement_5.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22c0e-246">Consulte também</span><span class="sxs-lookup"><span data-stu-id="22c0e-246">See Also</span></span>  
 <span data-ttu-id="22c0e-247">[Instrução sub](sub-statement.md) </span><span class="sxs-lookup"><span data-stu-id="22c0e-247">[Sub Statement](sub-statement.md) </span></span>  
<span data-ttu-id="22c0e-248"> [Procedimentos de função](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="22c0e-248"> [Function Procedures](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md) </span></span>  
<span data-ttu-id="22c0e-249"> [Lista de parâmetros](parameter-list.md) </span><span class="sxs-lookup"><span data-stu-id="22c0e-249"> [Parameter List](parameter-list.md) </span></span>  
<span data-ttu-id="22c0e-250"> [Instrução Dim](dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="22c0e-250"> [Dim Statement](dim-statement.md) </span></span>  
<span data-ttu-id="22c0e-251"> [Instrução Call](call-statement.md) </span><span class="sxs-lookup"><span data-stu-id="22c0e-251"> [Call Statement](call-statement.md) </span></span>  
<span data-ttu-id="22c0e-252"> [De](of-clause.md) </span><span class="sxs-lookup"><span data-stu-id="22c0e-252"> [Of](of-clause.md) </span></span>  
<span data-ttu-id="22c0e-253"> [Matrizes de parâmetros](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="22c0e-253"> [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md) </span></span>  
<span data-ttu-id="22c0e-254"> [Como: usar uma classe genérica](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md) </span><span class="sxs-lookup"><span data-stu-id="22c0e-254"> [How to: Use a Generic Class](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md) </span></span>  
<span data-ttu-id="22c0e-255"> [Procedimentos de solução de problemas](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="22c0e-255"> [Troubleshooting Procedures](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="22c0e-256"> [Expressões lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="22c0e-256"> [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md) </span></span>  
<span data-ttu-id="22c0e-257"> [Expressão de Função](../../../visual-basic/language-reference/operators/function-expression.md)</span><span class="sxs-lookup"><span data-stu-id="22c0e-257"> [Function Expression](../../../visual-basic/language-reference/operators/function-expression.md)</span></span>

