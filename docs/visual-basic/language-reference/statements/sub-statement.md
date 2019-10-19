---
title: Instrução Sub (Visual Basic)
ms.date: 05/12/2018
f1_keywords:
- vb.Sub
helpviewer_keywords:
- Public keyword [Visual Basic], Sub statements
- procedures [Visual Basic], creating
- declaring procedures [Visual Basic], Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword [Visual Basic], Sub statements
- Optional keyword [Visual Basic], Sub statements
- declarations [Visual Basic], procedures
- Sub keyword [Visual Basic]
- Handles keyword [Visual Basic], Sub statements
- Protected Friend keyword [Visual Basic]
- ParamArray keyword [Visual Basic], Sub statements
- Implements keyword [Visual Basic], Sub statements
- Sub statement [Visual Basic]
- subroutines
- ByRef keyword [Visual Basic], Sub statements
- Sub procedures [Visual Basic], Sub statement
- recursive procedures
- Private keyword [Visual Basic], Sub statements
- Friend keyword [Visual Basic], Sub statements
- Exit statement [Visual Basic], Sub statements
- procedures [Visual Basic], Sub
- End keyword [Visual Basic], Sub statements
- ByVal keyword [Visual Basic], Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
ms.openlocfilehash: 7dc0ea1f1b30f5ffb0db8917538adf440c5ef891
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583195"
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="67b4d-102">Instrução Sub (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67b4d-102">Sub Statement (Visual Basic)</span></span>

<span data-ttu-id="67b4d-103">Declara o nome, os parâmetros e o código que definem um procedimento de `Sub`.</span><span class="sxs-lookup"><span data-stu-id="67b4d-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>

## <a name="syntax"></a><span data-ttu-id="67b4d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="67b4d-104">Syntax</span></span>

```vb
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]
    [ statements ]
    [ Exit Sub ]
    [ statements ]
End Sub
```

## <a name="parts"></a><span data-ttu-id="67b4d-105">Partes</span><span class="sxs-lookup"><span data-stu-id="67b4d-105">Parts</span></span>

- `attributelist`

  <span data-ttu-id="67b4d-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="67b4d-106">Optional.</span></span> <span data-ttu-id="67b4d-107">Consulte a [lista de atributos](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="67b4d-107">See [Attribute List](attribute-list.md).</span></span>

- `Partial`

  <span data-ttu-id="67b4d-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="67b4d-108">Optional.</span></span> <span data-ttu-id="67b4d-109">Indica a definição de um método parcial.</span><span class="sxs-lookup"><span data-stu-id="67b4d-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="67b4d-110">Consulte [métodos parciais](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="67b4d-110">See [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span></span>

- `accessmodifier`

  <span data-ttu-id="67b4d-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="67b4d-111">Optional.</span></span> <span data-ttu-id="67b4d-112">Pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="67b4d-112">Can be one of the following:</span></span>

  - [<span data-ttu-id="67b4d-113">Público</span><span class="sxs-lookup"><span data-stu-id="67b4d-113">Public</span></span>](../modifiers/public.md)

  - [<span data-ttu-id="67b4d-114">Protegido</span><span class="sxs-lookup"><span data-stu-id="67b4d-114">Protected</span></span>](../modifiers/protected.md)

  - [<span data-ttu-id="67b4d-115">Friend</span><span class="sxs-lookup"><span data-stu-id="67b4d-115">Friend</span></span>](../modifiers/friend.md)

  - [<span data-ttu-id="67b4d-116">Privado</span><span class="sxs-lookup"><span data-stu-id="67b4d-116">Private</span></span>](../modifiers/private.md)

  - [<span data-ttu-id="67b4d-117">Amigo Protegido</span><span class="sxs-lookup"><span data-stu-id="67b4d-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

  - [<span data-ttu-id="67b4d-118">Particular Protegido</span><span class="sxs-lookup"><span data-stu-id="67b4d-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)

  <span data-ttu-id="67b4d-119">Consulte [níveis de acesso em Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="67b4d-119">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>

- `proceduremodifiers`

  <span data-ttu-id="67b4d-120">Opcional.</span><span class="sxs-lookup"><span data-stu-id="67b4d-120">Optional.</span></span> <span data-ttu-id="67b4d-121">Pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="67b4d-121">Can be one of the following:</span></span>

  - [<span data-ttu-id="67b4d-122">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="67b4d-122">Overloads</span></span>](../modifiers/overloads.md)

  - [<span data-ttu-id="67b4d-123">Substituições</span><span class="sxs-lookup"><span data-stu-id="67b4d-123">Overrides</span></span>](../modifiers/overrides.md)

  - [<span data-ttu-id="67b4d-124">Substituível</span><span class="sxs-lookup"><span data-stu-id="67b4d-124">Overridable</span></span>](../modifiers/overridable.md)

  - [<span data-ttu-id="67b4d-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="67b4d-125">NotOverridable</span></span>](../modifiers/notoverridable.md)

  - [<span data-ttu-id="67b4d-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="67b4d-126">MustOverride</span></span>](../modifiers/mustoverride.md)

  - `MustOverride Overrides`

  - `NotOverridable Overrides`

- `Shared`

  <span data-ttu-id="67b4d-127">Opcional.</span><span class="sxs-lookup"><span data-stu-id="67b4d-127">Optional.</span></span> <span data-ttu-id="67b4d-128">Consulte [compartilhado](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="67b4d-128">See [Shared](../modifiers/shared.md).</span></span>

- `Shadows`

  <span data-ttu-id="67b4d-129">Opcional.</span><span class="sxs-lookup"><span data-stu-id="67b4d-129">Optional.</span></span> <span data-ttu-id="67b4d-130">Consulte [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="67b4d-130">See [Shadows](../modifiers/shadows.md).</span></span>

- `Async`

  <span data-ttu-id="67b4d-131">Opcional.</span><span class="sxs-lookup"><span data-stu-id="67b4d-131">Optional.</span></span> <span data-ttu-id="67b4d-132">Consulte [Async](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="67b4d-132">See [Async](../modifiers/async.md).</span></span>

- `name`

  <span data-ttu-id="67b4d-133">Necessário.</span><span class="sxs-lookup"><span data-stu-id="67b4d-133">Required.</span></span> <span data-ttu-id="67b4d-134">Nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="67b4d-134">Name of the procedure.</span></span> <span data-ttu-id="67b4d-135">Consulte [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="67b4d-135">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="67b4d-136">Para criar um procedimento de construtor para uma classe, defina o nome de um procedimento `Sub` para a palavra-chave `New`.</span><span class="sxs-lookup"><span data-stu-id="67b4d-136">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="67b4d-137">Para obter mais informações, consulte [tempo de vida do objeto: como os objetos são criados e destruídos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="67b4d-137">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>

- `typeparamlist`

  <span data-ttu-id="67b4d-138">Opcional.</span><span class="sxs-lookup"><span data-stu-id="67b4d-138">Optional.</span></span> <span data-ttu-id="67b4d-139">Lista de parâmetros de tipo para um procedimento genérico.</span><span class="sxs-lookup"><span data-stu-id="67b4d-139">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="67b4d-140">Consulte [lista de tipos](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="67b4d-140">See [Type List](type-list.md).</span></span>

- `parameterlist`

  <span data-ttu-id="67b4d-141">Opcional.</span><span class="sxs-lookup"><span data-stu-id="67b4d-141">Optional.</span></span> <span data-ttu-id="67b4d-142">Lista de nomes de variáveis locais que representam os parâmetros deste procedimento.</span><span class="sxs-lookup"><span data-stu-id="67b4d-142">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="67b4d-143">Consulte a [lista de parâmetros](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="67b4d-143">See [Parameter List](parameter-list.md).</span></span>

- `Implements`

  <span data-ttu-id="67b4d-144">Opcional.</span><span class="sxs-lookup"><span data-stu-id="67b4d-144">Optional.</span></span> <span data-ttu-id="67b4d-145">Indica que este procedimento implementa um ou mais procedimentos de `Sub`, cada um definido em uma interface implementada por este procedimento que contém a classe ou a estrutura.</span><span class="sxs-lookup"><span data-stu-id="67b4d-145">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="67b4d-146">Consulte a [instrução Implements](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="67b4d-146">See [Implements Statement](implements-statement.md).</span></span>

- `implementslist`

  <span data-ttu-id="67b4d-147">Necessário se `Implements` for fornecido.</span><span class="sxs-lookup"><span data-stu-id="67b4d-147">Required if `Implements` is supplied.</span></span> <span data-ttu-id="67b4d-148">Lista de procedimentos de `Sub` que estão sendo implementados.</span><span class="sxs-lookup"><span data-stu-id="67b4d-148">List of `Sub` procedures being implemented.</span></span>

  `implementedprocedure [ , implementedprocedure ... ]`

  <span data-ttu-id="67b4d-149">Cada `implementedprocedure` tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="67b4d-149">Each `implementedprocedure` has the following syntax and parts:</span></span>

  `interface.definedname`

  |<span data-ttu-id="67b4d-150">Parte</span><span class="sxs-lookup"><span data-stu-id="67b4d-150">Part</span></span>|<span data-ttu-id="67b4d-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="67b4d-151">Description</span></span>|
  |---|---|
  |`interface`|<span data-ttu-id="67b4d-152">Necessário.</span><span class="sxs-lookup"><span data-stu-id="67b4d-152">Required.</span></span> <span data-ttu-id="67b4d-153">Nome de uma interface implementada por este procedimento que contém a classe ou a estrutura.</span><span class="sxs-lookup"><span data-stu-id="67b4d-153">Name of an interface implemented by this procedure's containing class or structure.</span></span>|
  |`definedname`|<span data-ttu-id="67b4d-154">Necessário.</span><span class="sxs-lookup"><span data-stu-id="67b4d-154">Required.</span></span> <span data-ttu-id="67b4d-155">Nome pelo qual o procedimento é definido em `interface`.</span><span class="sxs-lookup"><span data-stu-id="67b4d-155">Name by which the procedure is defined in `interface`.</span></span>|

- `Handles`

  <span data-ttu-id="67b4d-156">Opcional.</span><span class="sxs-lookup"><span data-stu-id="67b4d-156">Optional.</span></span> <span data-ttu-id="67b4d-157">Indica que esse procedimento pode manipular um ou mais eventos específicos.</span><span class="sxs-lookup"><span data-stu-id="67b4d-157">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="67b4d-158">Consulte [identificadores](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="67b4d-158">See [Handles](handles-clause.md).</span></span>

- `eventlist`

  <span data-ttu-id="67b4d-159">Necessário se `Handles` for fornecido.</span><span class="sxs-lookup"><span data-stu-id="67b4d-159">Required if `Handles` is supplied.</span></span> <span data-ttu-id="67b4d-160">Lista de eventos que este procedimento manipula.</span><span class="sxs-lookup"><span data-stu-id="67b4d-160">List of events this procedure handles.</span></span>

  `eventspecifier [ , eventspecifier ... ]`

  <span data-ttu-id="67b4d-161">Cada `eventspecifier` tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="67b4d-161">Each `eventspecifier` has the following syntax and parts:</span></span>

  `eventvariable.event`

  |<span data-ttu-id="67b4d-162">Parte</span><span class="sxs-lookup"><span data-stu-id="67b4d-162">Part</span></span>|<span data-ttu-id="67b4d-163">Descrição</span><span class="sxs-lookup"><span data-stu-id="67b4d-163">Description</span></span>|
  |---|---|
  |`eventvariable`|<span data-ttu-id="67b4d-164">Necessário.</span><span class="sxs-lookup"><span data-stu-id="67b4d-164">Required.</span></span> <span data-ttu-id="67b4d-165">Variável de objeto declarada com o tipo de dados da classe ou estrutura que gera o evento.</span><span class="sxs-lookup"><span data-stu-id="67b4d-165">Object variable declared with the data type of the class or structure that raises the event.</span></span>|
  |`event`|<span data-ttu-id="67b4d-166">Necessário.</span><span class="sxs-lookup"><span data-stu-id="67b4d-166">Required.</span></span> <span data-ttu-id="67b4d-167">Nome do evento que este procedimento manipula.</span><span class="sxs-lookup"><span data-stu-id="67b4d-167">Name of the event this procedure handles.</span></span>|

- `statements`

  <span data-ttu-id="67b4d-168">Opcional.</span><span class="sxs-lookup"><span data-stu-id="67b4d-168">Optional.</span></span> <span data-ttu-id="67b4d-169">Bloco de instruções a serem executadas neste procedimento.</span><span class="sxs-lookup"><span data-stu-id="67b4d-169">Block of statements to run within this procedure.</span></span>

- `End Sub`

  <span data-ttu-id="67b4d-170">Encerra a definição deste procedimento.</span><span class="sxs-lookup"><span data-stu-id="67b4d-170">Terminates the definition of this procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="67b4d-171">Comentários</span><span class="sxs-lookup"><span data-stu-id="67b4d-171">Remarks</span></span>

<span data-ttu-id="67b4d-172">Todo o código executável deve estar dentro de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="67b4d-172">All executable code must be inside a procedure.</span></span> <span data-ttu-id="67b4d-173">Use um procedimento `Sub` quando não quiser retornar um valor para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="67b4d-173">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="67b4d-174">Use um procedimento `Function` quando desejar retornar um valor.</span><span class="sxs-lookup"><span data-stu-id="67b4d-174">Use a `Function` procedure when you want to return a value.</span></span>

## <a name="defining-a-sub-procedure"></a><span data-ttu-id="67b4d-175">Definindo um procedimento Sub</span><span class="sxs-lookup"><span data-stu-id="67b4d-175">Defining a Sub Procedure</span></span>

<span data-ttu-id="67b4d-176">Você pode definir um procedimento `Sub` apenas no nível do módulo.</span><span class="sxs-lookup"><span data-stu-id="67b4d-176">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="67b4d-177">O contexto de declaração para um procedimento Sub deve, portanto, ser uma classe, uma estrutura, um módulo ou uma interface e não pode ser um arquivo de origem, um namespace, um procedimento ou um bloco.</span><span class="sxs-lookup"><span data-stu-id="67b4d-177">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="67b4d-178">Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="67b4d-178">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="67b4d-179">`Sub` procedimentos padrão para acesso público.</span><span class="sxs-lookup"><span data-stu-id="67b4d-179">`Sub` procedures default to public access.</span></span> <span data-ttu-id="67b4d-180">Você pode ajustar seus níveis de acesso usando os modificadores de acesso.</span><span class="sxs-lookup"><span data-stu-id="67b4d-180">You can adjust their access levels by using the access modifiers.</span></span>

<span data-ttu-id="67b4d-181">Se o procedimento usa a palavra-chave `Implements`, a classe ou estrutura que a contém deve ter uma instrução `Implements` que segue imediatamente sua instrução `Class` ou `Structure`.</span><span class="sxs-lookup"><span data-stu-id="67b4d-181">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="67b4d-182">A instrução `Implements` deve incluir cada interface especificada em `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="67b4d-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="67b4d-183">No entanto, o nome pelo qual uma interface define a `Sub` (em `definedname`) não precisa corresponder ao nome desse procedimento (em `name`).</span><span class="sxs-lookup"><span data-stu-id="67b4d-183">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>

## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="67b4d-184">Retornando de um procedimento Sub</span><span class="sxs-lookup"><span data-stu-id="67b4d-184">Returning from a Sub Procedure</span></span>

<span data-ttu-id="67b4d-185">Quando um procedimento de `Sub` retorna ao código de chamada, a execução continua com a instrução após a instrução que a chamou.</span><span class="sxs-lookup"><span data-stu-id="67b4d-185">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>

<span data-ttu-id="67b4d-186">O exemplo a seguir mostra um retorno de um procedimento de `Sub`.</span><span class="sxs-lookup"><span data-stu-id="67b4d-186">The following example shows a return from a `Sub` procedure.</span></span>

```vb
Sub mySub(ByVal q As String)
    Return
End Sub
```

<span data-ttu-id="67b4d-187">As instruções `Exit Sub` e `Return` causam uma saída imediata de um procedimento `Sub`.</span><span class="sxs-lookup"><span data-stu-id="67b4d-187">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="67b4d-188">Qualquer número de instruções `Exit Sub` e `Return` pode aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Sub` e instruções `Return`.</span><span class="sxs-lookup"><span data-stu-id="67b4d-188">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>

## <a name="calling-a-sub-procedure"></a><span data-ttu-id="67b4d-189">Chamando um procedimento Sub</span><span class="sxs-lookup"><span data-stu-id="67b4d-189">Calling a Sub Procedure</span></span>

<span data-ttu-id="67b4d-190">Você chama um procedimento de `Sub` usando o nome do procedimento em uma instrução e, em seguida, seguindo esse nome com sua lista de argumentos entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="67b4d-190">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="67b4d-191">Você pode omitir os parênteses somente se não fornecer argumentos.</span><span class="sxs-lookup"><span data-stu-id="67b4d-191">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="67b4d-192">No entanto, seu código será mais legível se você sempre incluir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="67b4d-192">However, your code is more readable if you always include the parentheses.</span></span>

<span data-ttu-id="67b4d-193">Um procedimento `Sub` e um procedimento de `Function` podem ter parâmetros e executar uma série de instruções.</span><span class="sxs-lookup"><span data-stu-id="67b4d-193">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="67b4d-194">No entanto, um procedimento de `Function` retorna um valor e um procedimento de `Sub` não.</span><span class="sxs-lookup"><span data-stu-id="67b4d-194">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="67b4d-195">Portanto, você não pode usar um procedimento `Sub` em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="67b4d-195">Therefore, you can't use a `Sub` procedure in an expression.</span></span>

<span data-ttu-id="67b4d-196">Você pode usar a palavra-chave `Call` ao chamar um procedimento de `Sub`, mas essa palavra-chave não é recomendada para a maioria dos usos.</span><span class="sxs-lookup"><span data-stu-id="67b4d-196">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="67b4d-197">Para obter mais informações, consulte [Call Statement](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="67b4d-197">For more information, see [Call Statement](call-statement.md).</span></span>

<span data-ttu-id="67b4d-198">Às vezes, Visual Basic reorganiza as expressões aritméticas para aumentar a eficiência interna.</span><span class="sxs-lookup"><span data-stu-id="67b4d-198">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="67b4d-199">Por esse motivo, se a lista de argumentos incluir expressões que chamam outros procedimentos, você não deve presumir que essas expressões serão chamadas em uma ordem específica.</span><span class="sxs-lookup"><span data-stu-id="67b4d-199">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>

## <a name="async-sub-procedures"></a><span data-ttu-id="67b4d-200">Procedimentos Async sub</span><span class="sxs-lookup"><span data-stu-id="67b4d-200">Async Sub Procedures</span></span>

<span data-ttu-id="67b4d-201">Usando o recurso assíncrono, você pode invocar funções assíncronas sem usar retornos de chamada explícitos ou dividir manualmente seu código em várias funções ou expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="67b4d-201">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>

<span data-ttu-id="67b4d-202">Se você marcar um procedimento com o modificador [Async](../modifiers/async.md) , poderá usar o operador [Await](../../../visual-basic/language-reference/operators/await-operator.md) no procedimento.</span><span class="sxs-lookup"><span data-stu-id="67b4d-202">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="67b4d-203">Quando o controle alcança uma expressão de `Await` no procedimento de `Async`, o controle retorna ao chamador e o progresso no procedimento é suspenso até que a tarefa esperada seja concluída.</span><span class="sxs-lookup"><span data-stu-id="67b4d-203">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="67b4d-204">Quando a tarefa for concluída, a execução poderá ser retomada no procedimento.</span><span class="sxs-lookup"><span data-stu-id="67b4d-204">When the task is complete, execution can resume in the procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="67b4d-205">Um procedimento `Async` retorna ao chamador quando o primeiro objeto esperado que ainda não está concluído é encontrado ou o final do procedimento `Async` é atingido, o que ocorrer primeiro.</span><span class="sxs-lookup"><span data-stu-id="67b4d-205">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>

<span data-ttu-id="67b4d-206">Você também pode marcar uma [instrução de função](function-statement.md) com o modificador de `Async`.</span><span class="sxs-lookup"><span data-stu-id="67b4d-206">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="67b4d-207">Uma função `Async` pode ter um tipo de retorno de <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="67b4d-207">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="67b4d-208">Um exemplo mais adiante neste tópico mostra uma função `Async` que tem um tipo de retorno de <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="67b4d-208">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>

<span data-ttu-id="67b4d-209">os procedimentos de `Sub` `Async` são usados principalmente para manipuladores de eventos, em que um valor não pode ser retornado.</span><span class="sxs-lookup"><span data-stu-id="67b4d-209">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="67b4d-210">Um procedimento de `Sub` `Async` não pode ser aguardado e o chamador de um procedimento de `Sub` `Async` não pode capturar exceções que o procedimento de `Sub` gera.</span><span class="sxs-lookup"><span data-stu-id="67b4d-210">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>

<span data-ttu-id="67b4d-211">Um procedimento de `Async` não pode declarar parâmetros [ByRef](../modifiers/byref.md) .</span><span class="sxs-lookup"><span data-stu-id="67b4d-211">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>

<span data-ttu-id="67b4d-212">Para obter mais informações sobre procedimentos `Async`, consulte [programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md), [fluxo de controle em programas assíncronos](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)e [tipos de retorno assíncronos](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="67b4d-212">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="example"></a><span data-ttu-id="67b4d-213">Exemplo</span><span class="sxs-lookup"><span data-stu-id="67b4d-213">Example</span></span>

<span data-ttu-id="67b4d-214">O exemplo a seguir usa a instrução `Sub` para definir o nome, os parâmetros e o código que formam o corpo de um procedimento de `Sub`.</span><span class="sxs-lookup"><span data-stu-id="67b4d-214">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>

[!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]

## <a name="example"></a><span data-ttu-id="67b4d-215">Exemplo</span><span class="sxs-lookup"><span data-stu-id="67b4d-215">Example</span></span>

<span data-ttu-id="67b4d-216">No exemplo a seguir, `DelayAsync` é uma `Function` de `Async` que tem um tipo de retorno de <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="67b4d-216">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="67b4d-217">`DelayAsync` tem uma instrução `Return` que retorna um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="67b4d-217">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="67b4d-218">Portanto, a declaração de função de `DelayAsync` deve ter um tipo de retorno de `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="67b4d-218">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="67b4d-219">Como o tipo de retorno é `Task(Of Integer)`, a avaliação da expressão `Await` no `DoSomethingAsync` produz um inteiro, como mostra a instrução a seguir: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="67b4d-219">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>

<span data-ttu-id="67b4d-220">O procedimento de `startButton_Click` é um exemplo de um procedimento de `Async Sub`.</span><span class="sxs-lookup"><span data-stu-id="67b4d-220">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="67b4d-221">Como `DoSomethingAsync` é uma função `Async`, a tarefa para a chamada para `DoSomethingAsync` deve ser aguardada, como mostra a instrução a seguir: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="67b4d-221">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="67b4d-222">O procedimento de `Sub` de `startButton_Click` deve ser definido com o modificador de `Async` porque ele tem uma expressão de `Await`.</span><span class="sxs-lookup"><span data-stu-id="67b4d-222">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>

[!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]

## <a name="see-also"></a><span data-ttu-id="67b4d-223">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67b4d-223">See also</span></span>

- [<span data-ttu-id="67b4d-224">Instrução Implements</span><span class="sxs-lookup"><span data-stu-id="67b4d-224">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="67b4d-225">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="67b4d-225">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="67b4d-226">Lista de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="67b4d-226">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="67b4d-227">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="67b4d-227">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="67b4d-228">Instrução Call</span><span class="sxs-lookup"><span data-stu-id="67b4d-228">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="67b4d-229">Of</span><span class="sxs-lookup"><span data-stu-id="67b4d-229">Of</span></span>](of-clause.md)
- [<span data-ttu-id="67b4d-230">Matrizes de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="67b4d-230">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="67b4d-231">Como usar uma classe genérica</span><span class="sxs-lookup"><span data-stu-id="67b4d-231">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="67b4d-232">Solução de problemas de Procedimentos</span><span class="sxs-lookup"><span data-stu-id="67b4d-232">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="67b4d-233">Métodos Parciais</span><span class="sxs-lookup"><span data-stu-id="67b4d-233">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
