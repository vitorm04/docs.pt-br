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
ms.openlocfilehash: ab94865f4881b40b38f67eb40d2f9fa2e1982af8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58817221"
---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="94c7a-102">Instrução Sub (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="94c7a-102">Sub Statement (Visual Basic)</span></span>
<span data-ttu-id="94c7a-103">Declara o nome, parâmetros e código que definem um `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="94c7a-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94c7a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="94c7a-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="94c7a-105">Partes</span><span class="sxs-lookup"><span data-stu-id="94c7a-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="94c7a-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94c7a-106">Optional.</span></span> <span data-ttu-id="94c7a-107">Ver [lista de atributos](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="94c7a-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `Partial`  
  
     <span data-ttu-id="94c7a-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94c7a-108">Optional.</span></span> <span data-ttu-id="94c7a-109">Indica a definição de um método parcial.</span><span class="sxs-lookup"><span data-stu-id="94c7a-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="94c7a-110">Ver [métodos parciais](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="94c7a-110">See [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="94c7a-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94c7a-111">Optional.</span></span> <span data-ttu-id="94c7a-112">Pode ser uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="94c7a-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="94c7a-113">Público</span><span class="sxs-lookup"><span data-stu-id="94c7a-113">Public</span></span>](../modifiers/public.md)  
  
    -   [<span data-ttu-id="94c7a-114">Protegido</span><span class="sxs-lookup"><span data-stu-id="94c7a-114">Protected</span></span>](../modifiers/protected.md)  
  
    -   [<span data-ttu-id="94c7a-115">Friend</span><span class="sxs-lookup"><span data-stu-id="94c7a-115">Friend</span></span>](../modifiers/friend.md)  
  
    -   [<span data-ttu-id="94c7a-116">Privado</span><span class="sxs-lookup"><span data-stu-id="94c7a-116">Private</span></span>](../modifiers/private.md)  
  
    - [<span data-ttu-id="94c7a-117">Amigo Protegido</span><span class="sxs-lookup"><span data-stu-id="94c7a-117">Protected Friend</span></span>](../../language-reference/modifiers/protected-friend.md)

    - [<span data-ttu-id="94c7a-118">Particular Protegido</span><span class="sxs-lookup"><span data-stu-id="94c7a-118">Private Protected</span></span>](../../language-reference/modifiers/private-protected.md)
  
     <span data-ttu-id="94c7a-119">Ver [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="94c7a-119">See [Access levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="94c7a-120">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94c7a-120">Optional.</span></span> <span data-ttu-id="94c7a-121">Pode ser uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="94c7a-121">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="94c7a-122">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="94c7a-122">Overloads</span></span>](../modifiers/overloads.md)  
  
    -   [<span data-ttu-id="94c7a-123">Substituições</span><span class="sxs-lookup"><span data-stu-id="94c7a-123">Overrides</span></span>](../modifiers/overrides.md)  
  
    -   [<span data-ttu-id="94c7a-124">Substituível</span><span class="sxs-lookup"><span data-stu-id="94c7a-124">Overridable</span></span>](../modifiers/overridable.md)  
  
    -   [<span data-ttu-id="94c7a-125">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="94c7a-125">NotOverridable</span></span>](../modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="94c7a-126">MustOverride</span><span class="sxs-lookup"><span data-stu-id="94c7a-126">MustOverride</span></span>](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="94c7a-127">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94c7a-127">Optional.</span></span> <span data-ttu-id="94c7a-128">Ver [compartilhado](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="94c7a-128">See [Shared](../modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="94c7a-129">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94c7a-129">Optional.</span></span> <span data-ttu-id="94c7a-130">Ver [sombras](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="94c7a-130">See [Shadows](../modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="94c7a-131">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94c7a-131">Optional.</span></span> <span data-ttu-id="94c7a-132">Ver [Async](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="94c7a-132">See [Async](../modifiers/async.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="94c7a-133">Necessário.</span><span class="sxs-lookup"><span data-stu-id="94c7a-133">Required.</span></span> <span data-ttu-id="94c7a-134">Nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="94c7a-134">Name of the procedure.</span></span> <span data-ttu-id="94c7a-135">Ver [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="94c7a-135">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="94c7a-136">Para criar um procedimento de construtor para uma classe, defina o nome de um `Sub` procedimento para o `New` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="94c7a-136">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="94c7a-137">Para obter mais informações, consulte [tempo de vida do objeto: Como os objetos são criados e destruídos](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="94c7a-137">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="94c7a-138">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94c7a-138">Optional.</span></span> <span data-ttu-id="94c7a-139">Lista de parâmetros de tipo para um procedimento genérico.</span><span class="sxs-lookup"><span data-stu-id="94c7a-139">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="94c7a-140">Ver [lista de tipos](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="94c7a-140">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="94c7a-141">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94c7a-141">Optional.</span></span> <span data-ttu-id="94c7a-142">Lista de nomes de variáveis locais que representam os parâmetros deste procedimento.</span><span class="sxs-lookup"><span data-stu-id="94c7a-142">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="94c7a-143">Ver [lista de parâmetros](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="94c7a-143">See [Parameter List](parameter-list.md).</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="94c7a-144">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94c7a-144">Optional.</span></span> <span data-ttu-id="94c7a-145">Indica que esse procedimento implementa uma ou mais `Sub` procedimentos, cada uma delas definida em uma interface implementada pela classe ou estrutura que contém esse procedimento.</span><span class="sxs-lookup"><span data-stu-id="94c7a-145">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="94c7a-146">Ver [implementa a instrução](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="94c7a-146">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="94c7a-147">Necessário se `Implements` for fornecido.</span><span class="sxs-lookup"><span data-stu-id="94c7a-147">Required if `Implements` is supplied.</span></span> <span data-ttu-id="94c7a-148">Lista de `Sub` procedimentos que está sendo implementados.</span><span class="sxs-lookup"><span data-stu-id="94c7a-148">List of `Sub` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="94c7a-149">Cada `implementedprocedure` tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="94c7a-149">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="94c7a-150">Parte</span><span class="sxs-lookup"><span data-stu-id="94c7a-150">Part</span></span>|<span data-ttu-id="94c7a-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="94c7a-151">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="94c7a-152">Necessário.</span><span class="sxs-lookup"><span data-stu-id="94c7a-152">Required.</span></span> <span data-ttu-id="94c7a-153">Que contém o nome de uma interface implementada por esse procedimento classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="94c7a-153">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="94c7a-154">Necessário.</span><span class="sxs-lookup"><span data-stu-id="94c7a-154">Required.</span></span> <span data-ttu-id="94c7a-155">Nome pelo qual o procedimento é definido em `interface`.</span><span class="sxs-lookup"><span data-stu-id="94c7a-155">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="94c7a-156">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94c7a-156">Optional.</span></span> <span data-ttu-id="94c7a-157">Indica que esse procedimento pode manipular um ou mais eventos específicos.</span><span class="sxs-lookup"><span data-stu-id="94c7a-157">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="94c7a-158">Ver [manipula](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="94c7a-158">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="94c7a-159">Necessário se `Handles` for fornecido.</span><span class="sxs-lookup"><span data-stu-id="94c7a-159">Required if `Handles` is supplied.</span></span> <span data-ttu-id="94c7a-160">Lista de eventos que manipula esse procedimento.</span><span class="sxs-lookup"><span data-stu-id="94c7a-160">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="94c7a-161">Cada `eventspecifier` tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="94c7a-161">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="94c7a-162">Parte</span><span class="sxs-lookup"><span data-stu-id="94c7a-162">Part</span></span>|<span data-ttu-id="94c7a-163">Descrição</span><span class="sxs-lookup"><span data-stu-id="94c7a-163">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="94c7a-164">Necessário.</span><span class="sxs-lookup"><span data-stu-id="94c7a-164">Required.</span></span> <span data-ttu-id="94c7a-165">Variável de objeto declarado com o tipo de dados da classe ou estrutura que gera o evento.</span><span class="sxs-lookup"><span data-stu-id="94c7a-165">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="94c7a-166">Necessário.</span><span class="sxs-lookup"><span data-stu-id="94c7a-166">Required.</span></span> <span data-ttu-id="94c7a-167">Nome do evento que lida com esse procedimento.</span><span class="sxs-lookup"><span data-stu-id="94c7a-167">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="94c7a-168">Opcional.</span><span class="sxs-lookup"><span data-stu-id="94c7a-168">Optional.</span></span> <span data-ttu-id="94c7a-169">Bloco de instruções para executar dentro deste procedimento.</span><span class="sxs-lookup"><span data-stu-id="94c7a-169">Block of statements to run within this procedure.</span></span>  
  
-   `End Sub`  
  
     <span data-ttu-id="94c7a-170">Finaliza a definição desse procedimento.</span><span class="sxs-lookup"><span data-stu-id="94c7a-170">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="94c7a-171">Comentários</span><span class="sxs-lookup"><span data-stu-id="94c7a-171">Remarks</span></span>  
 <span data-ttu-id="94c7a-172">Todo o código executável deve ser dentro de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="94c7a-172">All executable code must be inside a procedure.</span></span> <span data-ttu-id="94c7a-173">Use um `Sub` quando você não quiser retornar um valor para o código de chamada de procedimento.</span><span class="sxs-lookup"><span data-stu-id="94c7a-173">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="94c7a-174">Use um `Function` procedimento quando desejar retornar um valor.</span><span class="sxs-lookup"><span data-stu-id="94c7a-174">Use a `Function` procedure when you want to return a value.</span></span>  
  
## <a name="defining-a-sub-procedure"></a><span data-ttu-id="94c7a-175">Definindo um procedimento Sub</span><span class="sxs-lookup"><span data-stu-id="94c7a-175">Defining a Sub Procedure</span></span>  
 <span data-ttu-id="94c7a-176">Você pode definir um `Sub` procedimento apenas no nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="94c7a-176">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="94c7a-177">O contexto da declaração para um procedimento sub deve, portanto, ser uma classe, uma estrutura, um módulo ou uma interface e não pode ser um arquivo de origem, um namespace, um procedimento ou um bloco.</span><span class="sxs-lookup"><span data-stu-id="94c7a-177">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="94c7a-178">Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="94c7a-178">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="94c7a-179">`Sub` padrão de procedimentos para acesso público.</span><span class="sxs-lookup"><span data-stu-id="94c7a-179">`Sub` procedures default to public access.</span></span> <span data-ttu-id="94c7a-180">Você pode ajustar os níveis de acesso usando os modificadores de acesso.</span><span class="sxs-lookup"><span data-stu-id="94c7a-180">You can adjust their access levels by using the access modifiers.</span></span>  
  
 <span data-ttu-id="94c7a-181">Se o procedimento usa o `Implements` deve ter a palavra-chave, a classe ou estrutura contendo um `Implements` instrução que segue imediatamente seus `Class` ou `Structure` instrução.</span><span class="sxs-lookup"><span data-stu-id="94c7a-181">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="94c7a-182">O `Implements` instrução deve incluir cada interface que é especificado no `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="94c7a-182">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="94c7a-183">No entanto, o nome pelo qual uma interface define os `Sub` (no `definedname`) não precisa corresponder ao nome do procedimento (no `name`).</span><span class="sxs-lookup"><span data-stu-id="94c7a-183">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>  
  
## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="94c7a-184">Retornando de um procedimento Sub</span><span class="sxs-lookup"><span data-stu-id="94c7a-184">Returning from a Sub Procedure</span></span>  
 <span data-ttu-id="94c7a-185">Quando um `Sub` procedimento retorna para o código de chamada, a execução continua com a instrução após a instrução que o chamou.</span><span class="sxs-lookup"><span data-stu-id="94c7a-185">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>  
  
 <span data-ttu-id="94c7a-186">O exemplo a seguir mostra um retorno de um `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="94c7a-186">The following example shows a return from a `Sub` procedure.</span></span>  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 <span data-ttu-id="94c7a-187">O `Exit Sub` e `Return` instruções fazem com que uma saída imediata de uma `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="94c7a-187">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="94c7a-188">Qualquer número de `Exit Sub` e `Return` instruções podem aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Sub` e `Return` instruções.</span><span class="sxs-lookup"><span data-stu-id="94c7a-188">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>  
  
## <a name="calling-a-sub-procedure"></a><span data-ttu-id="94c7a-189">Chamar um procedimento Sub</span><span class="sxs-lookup"><span data-stu-id="94c7a-189">Calling a Sub Procedure</span></span>  
 <span data-ttu-id="94c7a-190">Você chama um `Sub` procedimento usando o nome do procedimento em uma instrução e, em seguida, seguindo esse nome com sua lista de argumentos entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="94c7a-190">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="94c7a-191">Você pode omitir os parênteses somente se você não fornecer nenhum argumento.</span><span class="sxs-lookup"><span data-stu-id="94c7a-191">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="94c7a-192">No entanto, seu código é mais legível, se você sempre incluir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="94c7a-192">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="94c7a-193">Um `Sub` procedimento e um `Function` procedimento pode ter parâmetros e executar uma série de instruções.</span><span class="sxs-lookup"><span data-stu-id="94c7a-193">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="94c7a-194">No entanto, uma `Function` procedimento retorna um valor e um `Sub` não de procedimento.</span><span class="sxs-lookup"><span data-stu-id="94c7a-194">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="94c7a-195">Portanto, é possível usar um `Sub` procedimento em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="94c7a-195">Therefore, you can't use a `Sub` procedure in an expression.</span></span>  
  
 <span data-ttu-id="94c7a-196">Você pode usar o `Call` palavra-chave quando você chama um `Sub` procedimento, mas essa palavra-chave não é recomendado para a maioria dos usos.</span><span class="sxs-lookup"><span data-stu-id="94c7a-196">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="94c7a-197">Para obter mais informações, consulte [instrução Call](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="94c7a-197">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="94c7a-198">Visual Basic, às vezes, reorganiza expressões aritméticas para aumentar a eficiência interna.</span><span class="sxs-lookup"><span data-stu-id="94c7a-198">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="94c7a-199">Por esse motivo, se a lista de argumento inclui expressões que chamam outros procedimentos, você não deve presumir que as expressões serão chamadas em uma ordem específica.</span><span class="sxs-lookup"><span data-stu-id="94c7a-199">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>  
  
## <a name="async-sub-procedures"></a><span data-ttu-id="94c7a-200">Procedimentos Sub Async</span><span class="sxs-lookup"><span data-stu-id="94c7a-200">Async Sub Procedures</span></span>  
 <span data-ttu-id="94c7a-201">Ao usar o recurso Async, você pode chamar funções assíncronas sem usar retornos de chamada explícitos ou dividir manualmente seu código em várias funções ou expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="94c7a-201">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="94c7a-202">Se você marcar um procedimento com o [Async](../modifiers/async.md) modificador, você pode usar o [Await](../../../visual-basic/language-reference/operators/await-operator.md) operador no procedimento.</span><span class="sxs-lookup"><span data-stu-id="94c7a-202">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="94c7a-203">Quando o controle atinge uma `Await` expressão no `Async` procedimento, o controle retorna ao chamador e o progresso no procedimento é suspenso até que a tarefa aguardada seja concluída.</span><span class="sxs-lookup"><span data-stu-id="94c7a-203">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="94c7a-204">Quando a tarefa for concluída, a execução pode retomar no procedimento.</span><span class="sxs-lookup"><span data-stu-id="94c7a-204">When the task is complete, execution can resume in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="94c7a-205">Uma `Async` procedimento retorna ao chamador quando ambos o primeiro objeto esperado que ainda não está completo é encontrado ou o final do `Async` procedimento for atingido, o que ocorrer primeiro.</span><span class="sxs-lookup"><span data-stu-id="94c7a-205">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>  
  
 <span data-ttu-id="94c7a-206">Você também pode marcar um [instrução Function](function-statement.md) com o `Async` modificador.</span><span class="sxs-lookup"><span data-stu-id="94c7a-206">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="94c7a-207">Uma `Async` função pode ter um tipo de retorno <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.Task>.</span><span class="sxs-lookup"><span data-stu-id="94c7a-207">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="94c7a-208">Um exemplo mais adiante neste tópico mostra uma `Async` que tem um tipo de retorno da função <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="94c7a-208">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="94c7a-209">`Async` `Sub` procedimentos são usados principalmente para manipuladores de eventos, onde um valor não pode ser retornado.</span><span class="sxs-lookup"><span data-stu-id="94c7a-209">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="94c7a-210">Uma `Async` `Sub` procedimento não pode ser esperado e o chamador de um `Async` `Sub` procedimento não pode capturar exceções que o `Sub` procedimento gera.</span><span class="sxs-lookup"><span data-stu-id="94c7a-210">An `Async` `Sub` procedure can't be awaited, and the caller of an `Async` `Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>  
  
 <span data-ttu-id="94c7a-211">Uma `Async` procedimento não pode declarar qualquer [ByRef](../modifiers/byref.md) parâmetros.</span><span class="sxs-lookup"><span data-stu-id="94c7a-211">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="94c7a-212">Para obter mais informações sobre `Async` procedimentos, consulte [programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md), [fluxo de controle em programas assíncronos](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), e [tipos de retorno assíncronos](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="94c7a-212">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="94c7a-213">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94c7a-213">Example</span></span>  
 <span data-ttu-id="94c7a-214">O exemplo a seguir usa o `Sub` instrução para definir o nome, parâmetros e código que formam o corpo de uma `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="94c7a-214">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#58](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#58)]  
  
## <a name="example"></a><span data-ttu-id="94c7a-215">Exemplo</span><span class="sxs-lookup"><span data-stu-id="94c7a-215">Example</span></span>  
 <span data-ttu-id="94c7a-216">No exemplo a seguir `DelayAsync` é um `Async` `Function` que tem um tipo de retorno <xref:System.Threading.Tasks.Task%601>.</span><span class="sxs-lookup"><span data-stu-id="94c7a-216">In the following example, `DelayAsync` is an `Async` `Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="94c7a-217">`DelayAsync` tem uma instrução `Return` que retorna um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="94c7a-217">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="94c7a-218">Portanto, a declaração da função de `DelayAsync` deve ter um tipo de retorno `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="94c7a-218">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="94c7a-219">Porque é o tipo de retorno `Task(Of Integer)`, a avaliação do `Await` expressão na `DoSomethingAsync` produz um inteiro, como mostra a seguinte instrução: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="94c7a-219">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="94c7a-220">O `startButton_Click` procedimento é um exemplo de um `Async Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="94c7a-220">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="94c7a-221">Porque `DoSomethingAsync` é um `Async` função, a tarefa para a chamada a `DoSomethingAsync` deve ser colocada em espera, como mostra a seguinte instrução: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="94c7a-221">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="94c7a-222">O `startButton_Click` `Sub` procedimento deve ser definido com o `Async` modificador porque ele tem um `Await` expressão.</span><span class="sxs-lookup"><span data-stu-id="94c7a-222">The `startButton_Click` `Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 [!code-vb[csAsyncMethod#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/csasyncmethod/vb/mainwindow.xaml.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="94c7a-223">Consulte também</span><span class="sxs-lookup"><span data-stu-id="94c7a-223">See also</span></span>

- [<span data-ttu-id="94c7a-224">Instrução Implements</span><span class="sxs-lookup"><span data-stu-id="94c7a-224">Implements Statement</span></span>](implements-statement.md)
- [<span data-ttu-id="94c7a-225">Instrução Function</span><span class="sxs-lookup"><span data-stu-id="94c7a-225">Function Statement</span></span>](function-statement.md)
- [<span data-ttu-id="94c7a-226">Lista de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="94c7a-226">Parameter List</span></span>](parameter-list.md)
- [<span data-ttu-id="94c7a-227">Instrução Dim</span><span class="sxs-lookup"><span data-stu-id="94c7a-227">Dim Statement</span></span>](dim-statement.md)
- [<span data-ttu-id="94c7a-228">Instrução Call</span><span class="sxs-lookup"><span data-stu-id="94c7a-228">Call Statement</span></span>](call-statement.md)
- [<span data-ttu-id="94c7a-229">Of</span><span class="sxs-lookup"><span data-stu-id="94c7a-229">Of</span></span>](of-clause.md)
- [<span data-ttu-id="94c7a-230">Matrizes de Parâmetros</span><span class="sxs-lookup"><span data-stu-id="94c7a-230">Parameter Arrays</span></span>](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md)
- [<span data-ttu-id="94c7a-231">Como: usar uma classe genérica</span><span class="sxs-lookup"><span data-stu-id="94c7a-231">How to: Use a Generic Class</span></span>](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [<span data-ttu-id="94c7a-232">Solução de problemas de Procedimentos</span><span class="sxs-lookup"><span data-stu-id="94c7a-232">Troubleshooting Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
- [<span data-ttu-id="94c7a-233">Métodos Parciais</span><span class="sxs-lookup"><span data-stu-id="94c7a-233">Partial Methods</span></span>](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)
