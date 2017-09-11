---
title: Sub Statement (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Sub
dev_langs:
- VB
helpviewer_keywords:
- Public keyword, Sub statements
- procedures, creating
- declaring procedures, Sub statement
- arguments [Visual Basic], Sub procedures
- As keyword, Sub statements
- Optional keyword, Sub statements
- declarations, procedures
- Sub keyword
- Handles keyword, Sub statements
- Protected Friend keyword
- ParamArray keyword, Sub statements
- Implements keyword, Sub statements
- Sub statement
- subroutines
- ByRef keyword, Sub statements
- Sub procedures, Sub statement
- recursive procedures
- Private keyword, Sub statements
- Friend keyword, Sub statements
- Exit statement, Sub statements
- procedures, Sub
- End keyword, Sub statements
- ByVal keyword, Sub statements
- Visual Basic code, Sub procedures
ms.assetid: e347d700-d06c-405b-b302-e9b1edb57dfc
caps.latest.revision: 52
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
ms.openlocfilehash: 61853a4f2321837683997b8e4241b688bc9f622c
ms.contentlocale: pt-br
ms.lasthandoff: 05/15/2017

---
# <a name="sub-statement-visual-basic"></a><span data-ttu-id="259e2-102">Instrução Sub (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="259e2-102">Sub Statement (Visual Basic)</span></span>
<span data-ttu-id="259e2-103">Declara o nome, parâmetros e código que definem um `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="259e2-103">Declares the name, parameters, and code that define a `Sub` procedure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="259e2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="259e2-104">Syntax</span></span>  
  
```  
[ <attributelist> ] [ Partial ] [ accessmodifier ] [ proceduremodifiers ] [ Shared ] [ Shadows ] [ Async ]  
Sub name [ (Of typeparamlist) ] [ (parameterlist) ] [ Implements implementslist | Handles eventlist ]  
    [ statements ]  
    [ Exit Sub ]  
    [ statements ]  
End Sub  
```  
  
## <a name="parts"></a><span data-ttu-id="259e2-105">Partes</span><span class="sxs-lookup"><span data-stu-id="259e2-105">Parts</span></span>  
  
-   `attributelist`  
  
     <span data-ttu-id="259e2-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="259e2-106">Optional.</span></span> <span data-ttu-id="259e2-107">Consulte [lista atributo](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="259e2-107">See [Attribute List](attribute-list.md).</span></span>  
  
-   `Partial`  
  
     <span data-ttu-id="259e2-108">Opcional.</span><span class="sxs-lookup"><span data-stu-id="259e2-108">Optional.</span></span> <span data-ttu-id="259e2-109">Indica a definição de um método parcial.</span><span class="sxs-lookup"><span data-stu-id="259e2-109">Indicates definition of a partial method.</span></span> <span data-ttu-id="259e2-110">Consulte [métodos parciais](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span><span class="sxs-lookup"><span data-stu-id="259e2-110">See [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md).</span></span>  
  
-   `accessmodifier`  
  
     <span data-ttu-id="259e2-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="259e2-111">Optional.</span></span> <span data-ttu-id="259e2-112">Pode ser uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="259e2-112">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="259e2-113">Público</span><span class="sxs-lookup"><span data-stu-id="259e2-113">Public</span></span>](../modifiers/public.md)  
  
    -   [<span data-ttu-id="259e2-114">Protegido</span><span class="sxs-lookup"><span data-stu-id="259e2-114">Protected</span></span>](../modifiers/protected.md)  
  
    -   [<span data-ttu-id="259e2-115">Friend</span><span class="sxs-lookup"><span data-stu-id="259e2-115">Friend</span></span>](../modifiers/friend.md)  
  
    -   [<span data-ttu-id="259e2-116">Privado</span><span class="sxs-lookup"><span data-stu-id="259e2-116">Private</span></span>](../modifiers/private.md)  
  
    -   `Protected Friend`  
  
     <span data-ttu-id="259e2-117">Consulte [acessar níveis no Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="259e2-117">See [Access Levels in Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).</span></span>  
  
-   `proceduremodifiers`  
  
     <span data-ttu-id="259e2-118">Opcional.</span><span class="sxs-lookup"><span data-stu-id="259e2-118">Optional.</span></span> <span data-ttu-id="259e2-119">Pode ser uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="259e2-119">Can be one of the following:</span></span>  
  
    -   [<span data-ttu-id="259e2-120">Sobrecargas</span><span class="sxs-lookup"><span data-stu-id="259e2-120">Overloads</span></span>](../modifiers/overloads.md)  
  
    -   [<span data-ttu-id="259e2-121">Substituições</span><span class="sxs-lookup"><span data-stu-id="259e2-121">Overrides</span></span>](../modifiers/overrides.md)  
  
    -   [<span data-ttu-id="259e2-122">Substituível</span><span class="sxs-lookup"><span data-stu-id="259e2-122">Overridable</span></span>](../modifiers/overridable.md)  
  
    -   [<span data-ttu-id="259e2-123">NotOverridable</span><span class="sxs-lookup"><span data-stu-id="259e2-123">NotOverridable</span></span>](../modifiers/notoverridable.md)  
  
    -   [<span data-ttu-id="259e2-124">MustOverride</span><span class="sxs-lookup"><span data-stu-id="259e2-124">MustOverride</span></span>](../modifiers/mustoverride.md)  
  
    -   `MustOverride Overrides`  
  
    -   `NotOverridable Overrides`  
  
-   `Shared`  
  
     <span data-ttu-id="259e2-125">Opcional.</span><span class="sxs-lookup"><span data-stu-id="259e2-125">Optional.</span></span> <span data-ttu-id="259e2-126">Consulte [compartilhado](../modifiers/shared.md).</span><span class="sxs-lookup"><span data-stu-id="259e2-126">See [Shared](../modifiers/shared.md).</span></span>  
  
-   `Shadows`  
  
     <span data-ttu-id="259e2-127">Opcional.</span><span class="sxs-lookup"><span data-stu-id="259e2-127">Optional.</span></span> <span data-ttu-id="259e2-128">Consulte [sombras](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="259e2-128">See [Shadows](../modifiers/shadows.md).</span></span>  
  
-   `Async`  
  
     <span data-ttu-id="259e2-129">Opcional.</span><span class="sxs-lookup"><span data-stu-id="259e2-129">Optional.</span></span> <span data-ttu-id="259e2-130">Consulte [Async](../modifiers/async.md).</span><span class="sxs-lookup"><span data-stu-id="259e2-130">See [Async](../modifiers/async.md).</span></span>  
  
-   `name`  
  
     <span data-ttu-id="259e2-131">Necessário.</span><span class="sxs-lookup"><span data-stu-id="259e2-131">Required.</span></span> <span data-ttu-id="259e2-132">Nome do procedimento.</span><span class="sxs-lookup"><span data-stu-id="259e2-132">Name of the procedure.</span></span> <span data-ttu-id="259e2-133">Consulte [nomes de elemento declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="259e2-133">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span> <span data-ttu-id="259e2-134">Para criar um procedimento de construtor para uma classe, defina o nome de uma `Sub` procedimento para o `New` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="259e2-134">To create a constructor procedure for a class, set the name of a `Sub` procedure to the `New` keyword.</span></span> <span data-ttu-id="259e2-135">Para obter mais informações, consulte [tempo de vida do objeto: como os objetos são criados e Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span><span class="sxs-lookup"><span data-stu-id="259e2-135">For more information, see [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).</span></span>  
  
-   `typeparamlist`  
  
     <span data-ttu-id="259e2-136">Opcional.</span><span class="sxs-lookup"><span data-stu-id="259e2-136">Optional.</span></span> <span data-ttu-id="259e2-137">Lista de parâmetros de tipo para um procedimento genérico.</span><span class="sxs-lookup"><span data-stu-id="259e2-137">List of type parameters for a generic procedure.</span></span> <span data-ttu-id="259e2-138">Consulte [digite lista](type-list.md).</span><span class="sxs-lookup"><span data-stu-id="259e2-138">See [Type List](type-list.md).</span></span>  
  
-   `parameterlist`  
  
     <span data-ttu-id="259e2-139">Opcional.</span><span class="sxs-lookup"><span data-stu-id="259e2-139">Optional.</span></span> <span data-ttu-id="259e2-140">Lista de nomes de variáveis locais que representam os parâmetros deste procedimento.</span><span class="sxs-lookup"><span data-stu-id="259e2-140">List of local variable names representing the parameters of this procedure.</span></span> <span data-ttu-id="259e2-141">Consulte [lista de parâmetros](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="259e2-141">See [Parameter List](parameter-list.md).</span></span>  
  
-   `Implements`  
  
     <span data-ttu-id="259e2-142">Opcional.</span><span class="sxs-lookup"><span data-stu-id="259e2-142">Optional.</span></span> <span data-ttu-id="259e2-143">Indica que essa propriedade implementa uma ou mais `Sub` procedimentos, cada uma delas definida em uma interface implementada pela classe ou estrutura contendo esse procedimento.</span><span class="sxs-lookup"><span data-stu-id="259e2-143">Indicates that this procedure implements one or more `Sub` procedures, each one defined in an interface implemented by this procedure's containing class or structure.</span></span> <span data-ttu-id="259e2-144">Consulte [implementa a instrução](implements-statement.md).</span><span class="sxs-lookup"><span data-stu-id="259e2-144">See [Implements Statement](implements-statement.md).</span></span>  
  
-   `implementslist`  
  
     <span data-ttu-id="259e2-145">Necessário se `Implements` for fornecido.</span><span class="sxs-lookup"><span data-stu-id="259e2-145">Required if `Implements` is supplied.</span></span> <span data-ttu-id="259e2-146">Lista de `Sub` procedimentos que estão sendo implementados.</span><span class="sxs-lookup"><span data-stu-id="259e2-146">List of `Sub` procedures being implemented.</span></span>  
  
     `implementedprocedure [ , implementedprocedure ... ]`  
  
     <span data-ttu-id="259e2-147">Cada `implementedprocedure` tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="259e2-147">Each `implementedprocedure` has the following syntax and parts:</span></span>  
  
     `interface.definedname`  
  
    |<span data-ttu-id="259e2-148">Parte</span><span class="sxs-lookup"><span data-stu-id="259e2-148">Part</span></span>|<span data-ttu-id="259e2-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="259e2-149">Description</span></span>|  
    |---|---|  
    |`interface`|<span data-ttu-id="259e2-150">Necessário.</span><span class="sxs-lookup"><span data-stu-id="259e2-150">Required.</span></span> <span data-ttu-id="259e2-151">Nome de uma interface implementada por esse procedimento contendo classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="259e2-151">Name of an interface implemented by this procedure's containing class or structure.</span></span>|  
    |`definedname`|<span data-ttu-id="259e2-152">Necessário.</span><span class="sxs-lookup"><span data-stu-id="259e2-152">Required.</span></span> <span data-ttu-id="259e2-153">Nome pelo qual o procedimento é definido em `interface`.</span><span class="sxs-lookup"><span data-stu-id="259e2-153">Name by which the procedure is defined in `interface`.</span></span>|  
  
-   `Handles`  
  
     <span data-ttu-id="259e2-154">Opcional.</span><span class="sxs-lookup"><span data-stu-id="259e2-154">Optional.</span></span> <span data-ttu-id="259e2-155">Indica que esse procedimento pode manipular um ou mais eventos específicos.</span><span class="sxs-lookup"><span data-stu-id="259e2-155">Indicates that this procedure can handle one or more specific events.</span></span> <span data-ttu-id="259e2-156">Consulte [manipula](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="259e2-156">See [Handles](handles-clause.md).</span></span>  
  
-   `eventlist`  
  
     <span data-ttu-id="259e2-157">Necessário se `Handles` for fornecido.</span><span class="sxs-lookup"><span data-stu-id="259e2-157">Required if `Handles` is supplied.</span></span> <span data-ttu-id="259e2-158">Lista de eventos que esse procedimento manipula.</span><span class="sxs-lookup"><span data-stu-id="259e2-158">List of events this procedure handles.</span></span>  
  
     `eventspecifier [ , eventspecifier ... ]`  
  
     <span data-ttu-id="259e2-159">Cada `eventspecifier` tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="259e2-159">Each `eventspecifier` has the following syntax and parts:</span></span>  
  
     `eventvariable.event`  
  
    |<span data-ttu-id="259e2-160">Parte</span><span class="sxs-lookup"><span data-stu-id="259e2-160">Part</span></span>|<span data-ttu-id="259e2-161">Descrição</span><span class="sxs-lookup"><span data-stu-id="259e2-161">Description</span></span>|  
    |---|---|  
    |`eventvariable`|<span data-ttu-id="259e2-162">Necessário.</span><span class="sxs-lookup"><span data-stu-id="259e2-162">Required.</span></span> <span data-ttu-id="259e2-163">Variável de objeto declarada com o tipo de dados da classe ou estrutura que gera o evento.</span><span class="sxs-lookup"><span data-stu-id="259e2-163">Object variable declared with the data type of the class or structure that raises the event.</span></span>|  
    |`event`|<span data-ttu-id="259e2-164">Necessário.</span><span class="sxs-lookup"><span data-stu-id="259e2-164">Required.</span></span> <span data-ttu-id="259e2-165">Nome do evento que esse procedimento manipula.</span><span class="sxs-lookup"><span data-stu-id="259e2-165">Name of the event this procedure handles.</span></span>|  
  
-   `statements`  
  
     <span data-ttu-id="259e2-166">Opcional.</span><span class="sxs-lookup"><span data-stu-id="259e2-166">Optional.</span></span> <span data-ttu-id="259e2-167">Bloco de instruções para execução deste procedimento.</span><span class="sxs-lookup"><span data-stu-id="259e2-167">Block of statements to run within this procedure.</span></span>  
  
-   `End Sub`  
  
     <span data-ttu-id="259e2-168">Finaliza a definição desse procedimento.</span><span class="sxs-lookup"><span data-stu-id="259e2-168">Terminates the definition of this procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="259e2-169">Comentários</span><span class="sxs-lookup"><span data-stu-id="259e2-169">Remarks</span></span>  
 <span data-ttu-id="259e2-170">Todos os códigos executáveis deverão estar dentro de um procedimento.</span><span class="sxs-lookup"><span data-stu-id="259e2-170">All executable code must be inside a procedure.</span></span> <span data-ttu-id="259e2-171">Use um `Sub` quando você não desejar retornar um valor para o código de chamada de procedimento.</span><span class="sxs-lookup"><span data-stu-id="259e2-171">Use a `Sub` procedure when you don't want to return a value to the calling code.</span></span> <span data-ttu-id="259e2-172">Use uma `Function` procedimento quando desejar retornar um valor.</span><span class="sxs-lookup"><span data-stu-id="259e2-172">Use a `Function` procedure when you want to return a value.</span></span>  
  
## <a name="defining-a-sub-procedure"></a><span data-ttu-id="259e2-173">Definindo um procedimento Sub</span><span class="sxs-lookup"><span data-stu-id="259e2-173">Defining a Sub Procedure</span></span>  
 <span data-ttu-id="259e2-174">Você pode definir uma `Sub` procedimento apenas no nível de módulo.</span><span class="sxs-lookup"><span data-stu-id="259e2-174">You can define a `Sub` procedure only at the module level.</span></span> <span data-ttu-id="259e2-175">O contexto da declaração para um procedimento sub deve, portanto, ser uma classe, uma estrutura, um módulo ou uma interface e não pode ser um arquivo de origem, um namespace, um procedimento ou um bloco.</span><span class="sxs-lookup"><span data-stu-id="259e2-175">The declaration context for a sub procedure must, therefore, be a class, a structure, a module, or an interface and can't be a source file, a namespace, a procedure, or a block.</span></span> <span data-ttu-id="259e2-176">Para obter mais informações, consulte [contextos de declaração e níveis de acesso padrão](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="259e2-176">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="259e2-177">`Sub`padrão de procedimentos para acesso público.</span><span class="sxs-lookup"><span data-stu-id="259e2-177">`Sub` procedures default to public access.</span></span> <span data-ttu-id="259e2-178">Você pode ajustar os níveis de acesso usando os modificadores de acesso.</span><span class="sxs-lookup"><span data-stu-id="259e2-178">You can adjust their access levels by using the access modifiers.</span></span>  
  
 <span data-ttu-id="259e2-179">Se o procedimento usa o `Implements` palavra-chave, a classe ou estrutura continente deve ter uma `Implements` instrução que segue imediatamente seus `Class` ou `Structure` instrução.</span><span class="sxs-lookup"><span data-stu-id="259e2-179">If the procedure uses the `Implements` keyword, the containing class or structure must have an `Implements` statement that immediately follows its `Class` or `Structure` statement.</span></span> <span data-ttu-id="259e2-180">O `Implements` instrução deve incluir cada interface especificada no `implementslist`.</span><span class="sxs-lookup"><span data-stu-id="259e2-180">The `Implements` statement must include each interface that's specified in `implementslist`.</span></span> <span data-ttu-id="259e2-181">No entanto, o nome pelo qual uma interface define o `Sub` (em `definedname`) não precisa corresponder ao nome do procedimento (em `name`).</span><span class="sxs-lookup"><span data-stu-id="259e2-181">However, the name by which an interface defines the `Sub` (in `definedname`) doesn't have to match the name of this procedure (in `name`).</span></span>  
  
## <a name="returning-from-a-sub-procedure"></a><span data-ttu-id="259e2-182">Retornando a partir de um procedimento Sub</span><span class="sxs-lookup"><span data-stu-id="259e2-182">Returning from a Sub Procedure</span></span>  
 <span data-ttu-id="259e2-183">Quando uma `Sub` procedimento retorna para o código de chamada, a execução continua com a instrução após a instrução que o chamou.</span><span class="sxs-lookup"><span data-stu-id="259e2-183">When a `Sub` procedure returns to the calling code, execution continues with the statement after the statement that called it.</span></span>  
  
 <span data-ttu-id="259e2-184">O exemplo a seguir mostra um retorno de uma `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="259e2-184">The following example shows a return from a `Sub` procedure.</span></span>  
  
```vb  
Sub mySub(ByVal q As String)  
    Return  
End Sub   
```  
  
 <span data-ttu-id="259e2-185">O `Exit Sub` e `Return` instruções causam uma saída imediata de uma `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="259e2-185">The `Exit Sub` and `Return` statements cause an immediate exit from a `Sub` procedure.</span></span> <span data-ttu-id="259e2-186">Qualquer número de `Exit Sub` e `Return` instruções podem aparecer em qualquer lugar no procedimento, e você pode misturar `Exit Sub` e `Return` instruções.</span><span class="sxs-lookup"><span data-stu-id="259e2-186">Any number of `Exit Sub` and `Return` statements can appear anywhere in the procedure, and you can mix `Exit Sub` and `Return` statements.</span></span>  
  
## <a name="calling-a-sub-procedure"></a><span data-ttu-id="259e2-187">Chamar um procedimento Sub</span><span class="sxs-lookup"><span data-stu-id="259e2-187">Calling a Sub Procedure</span></span>  
 <span data-ttu-id="259e2-188">Chamar uma `Sub` procedimento usando o nome do procedimento em uma instrução e seguindo esse nome com sua lista de argumentos entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="259e2-188">You call a `Sub` procedure by using the procedure name in a statement and then following that name with its argument list in parentheses.</span></span> <span data-ttu-id="259e2-189">Você pode omitir os parênteses somente se você não fornecer nenhum argumento.</span><span class="sxs-lookup"><span data-stu-id="259e2-189">You can omit the parentheses only if you don't supply any arguments.</span></span> <span data-ttu-id="259e2-190">No entanto, seu código é mais legível se você sempre incluir os parênteses.</span><span class="sxs-lookup"><span data-stu-id="259e2-190">However, your code is more readable if you always include the parentheses.</span></span>  
  
 <span data-ttu-id="259e2-191">A `Sub` procedimento e uma `Function` procedimento pode ter parâmetros e executar uma série de instruções.</span><span class="sxs-lookup"><span data-stu-id="259e2-191">A `Sub` procedure and a `Function` procedure  can have parameters and perform a series of statements.</span></span> <span data-ttu-id="259e2-192">No entanto, uma `Function` procedimento retorna um valor e um `Sub` procedimento não.</span><span class="sxs-lookup"><span data-stu-id="259e2-192">However, a `Function` procedure returns a value, and a `Sub` procedure doesn't.</span></span> <span data-ttu-id="259e2-193">Portanto, você não pode usar uma `Sub` procedimento em uma expressão.</span><span class="sxs-lookup"><span data-stu-id="259e2-193">Therefore, you can't use a `Sub` procedure in an expression.</span></span>  
  
 <span data-ttu-id="259e2-194">Você pode usar o `Call` palavra-chave quando você chama um `Sub` procedimento, mas essa palavra-chave não é recomendado para a maioria dos usos.</span><span class="sxs-lookup"><span data-stu-id="259e2-194">You can use the `Call` keyword when you call a `Sub` procedure, but that keyword isn't recommended for most uses.</span></span> <span data-ttu-id="259e2-195">Para obter mais informações, consulte [instrução Call](call-statement.md).</span><span class="sxs-lookup"><span data-stu-id="259e2-195">For more information, see [Call Statement](call-statement.md).</span></span>  
  
 <span data-ttu-id="259e2-196">Visual Basic, às vezes, reorganiza expressões aritméticas para aumentar a eficiência interna.</span><span class="sxs-lookup"><span data-stu-id="259e2-196">Visual Basic sometimes rearranges arithmetic expressions to increase internal efficiency.</span></span> <span data-ttu-id="259e2-197">Por esse motivo, se a lista de argumentos contém expressões que chamam outros procedimentos, você não deve supor que as expressões serão chamadas em uma ordem específica.</span><span class="sxs-lookup"><span data-stu-id="259e2-197">For that reason, if your argument list includes expressions that call other procedures, you shouldn't assume that those expressions will be called in a particular order.</span></span>  
  
## <a name="async-sub-procedures"></a><span data-ttu-id="259e2-198">Procedimentos Sub Async</span><span class="sxs-lookup"><span data-stu-id="259e2-198">Async Sub Procedures</span></span>  
 <span data-ttu-id="259e2-199">Usando o recurso Async, você pode chamar funções assíncronas sem usar retornos de chamada explícitos ou dividir manualmente seu código em várias funções ou expressões lambda.</span><span class="sxs-lookup"><span data-stu-id="259e2-199">By using the Async feature, you can invoke asynchronous functions without using explicit callbacks or manually splitting your code across multiple functions or lambda expressions.</span></span>  
  
 <span data-ttu-id="259e2-200">Se você marcar um procedimento com o [Async](../modifiers/async.md) modificador, você pode usar o [Await](../../../visual-basic/language-reference/operators/await-operator.md) operador no procedimento.</span><span class="sxs-lookup"><span data-stu-id="259e2-200">If you mark a procedure with the [Async](../modifiers/async.md) modifier, you can use the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator in the procedure.</span></span> <span data-ttu-id="259e2-201">Quando o controle atinge um `Await` expressão no `Async` procedimento, o controle retorna ao chamador e progresso no procedimento está suspenso até que a tarefa aguardada seja concluída.</span><span class="sxs-lookup"><span data-stu-id="259e2-201">When control reaches an `Await` expression in the `Async` procedure, control returns to the caller, and progress in the procedure is suspended until the awaited task completes.</span></span> <span data-ttu-id="259e2-202">Quando a tarefa for concluída, a execução pode retomar o procedimento.</span><span class="sxs-lookup"><span data-stu-id="259e2-202">When the task is complete, execution can resume in the procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="259e2-203">Um `Async` procedimento retorna ao chamador quando ambos o primeiro objeto esperado que ainda não está completo é encontrado ou o final do `Async` procedimento for atingido, o que ocorrer primeiro.</span><span class="sxs-lookup"><span data-stu-id="259e2-203">An `Async` procedure returns to the caller when either the first awaited object that’s not yet complete is encountered or the end of the `Async` procedure is reached, whichever occurs first.</span></span>  
  
 <span data-ttu-id="259e2-204">Você também pode marcar um [instrução Function](function-statement.md) com o `Async` modificador.</span><span class="sxs-lookup"><span data-stu-id="259e2-204">You can also mark a [Function Statement](function-statement.md) with the `Async` modifier.</span></span> <span data-ttu-id="259e2-205">Um `Async` função pode ter um tipo de retorno <xref:System.Threading.Tasks.Task%601>ou <xref:System.Threading.Tasks.Task>.</xref:System.Threading.Tasks.Task> </xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="259e2-205">An `Async` function can have a return type of <xref:System.Threading.Tasks.Task%601> or <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="259e2-206">Um exemplo mais adiante neste tópico mostra um `Async` função que tem um tipo de retorno de <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="259e2-206">An example later in this topic shows an `Async` function that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
 <span data-ttu-id="259e2-207">`Async``Sub` procedimentos são usados principalmente para manipuladores de eventos, onde um valor não pode ser retornado.</span><span class="sxs-lookup"><span data-stu-id="259e2-207">`Async` `Sub` procedures are primarily used for event handlers, where a value can't be returned.</span></span> <span data-ttu-id="259e2-208">Um `Async``Sub` procedimento não pode ser esperado e o chamador de um `Async``Sub` procedimento não pode capturar exceções que o `Sub` procedimento lança.</span><span class="sxs-lookup"><span data-stu-id="259e2-208">An `Async``Sub` procedure can't be awaited, and the caller of an `Async``Sub` procedure can't catch exceptions that the `Sub` procedure throws.</span></span>  
  
 <span data-ttu-id="259e2-209">Um `Async` procedimento não pode declarar qualquer [ByRef](../modifiers/byref.md) parâmetros.</span><span class="sxs-lookup"><span data-stu-id="259e2-209">An `Async` procedure can't declare any [ByRef](../modifiers/byref.md) parameters.</span></span>  
  
 <span data-ttu-id="259e2-210">Para obter mais informações sobre `Async` procedimentos, consulte [programação assíncrona com Async e Await](../../../visual-basic/programming-guide/concepts/async/index.md), [fluxo de controle em programas assíncronos](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), e [assíncronas retornam tipos](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="259e2-210">For more information about `Async` procedures, see [Asynchronous Programming with Async and Await](../../../visual-basic/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md), and [Async Return Types](../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="259e2-211">Exemplo</span><span class="sxs-lookup"><span data-stu-id="259e2-211">Example</span></span>  
 <span data-ttu-id="259e2-212">O exemplo a seguir usa o `Sub` instrução para definir o nome, parâmetros e código que formam o corpo de uma `Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="259e2-212">The following example uses the `Sub` statement to define the name, parameters, and code that form the body of a `Sub` procedure.</span></span>  
  
 <span data-ttu-id="259e2-213">[!code-vb[VbVbalrStatements&#58;](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="259e2-213">[!code-vb[VbVbalrStatements#58](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/sub-statement_1.vb)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="259e2-214">Exemplo</span><span class="sxs-lookup"><span data-stu-id="259e2-214">Example</span></span>  
 <span data-ttu-id="259e2-215">No exemplo a seguir, `DelayAsync` é um uma `Async``Function` que tem um tipo de retorno de <xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="259e2-215">In the following example, `DelayAsync` is an an `Async``Function` that has a return type of <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="259e2-216">`DelayAsync`tem um `Return` instrução que retorna um número inteiro.</span><span class="sxs-lookup"><span data-stu-id="259e2-216">`DelayAsync` has a `Return` statement that returns an integer.</span></span> <span data-ttu-id="259e2-217">Portanto, a declaração de função do `DelayAsync` deve ter um tipo de retorno de `Task(Of Integer)`.</span><span class="sxs-lookup"><span data-stu-id="259e2-217">Therefore, the function declaration of `DelayAsync` must have a return type of `Task(Of Integer)`.</span></span> <span data-ttu-id="259e2-218">Como o tipo de retorno é `Task(Of Integer)`, a avaliação do `Await` expressão em `DoSomethingAsync` produz um número inteiro, como mostra a seguinte instrução: `Dim result As Integer = Await delayTask`.</span><span class="sxs-lookup"><span data-stu-id="259e2-218">Because the return type is `Task(Of Integer)`, the evaluation of the `Await` expression in `DoSomethingAsync` produces an integer, as the following statement shows: `Dim result As Integer = Await delayTask`.</span></span>  
  
 <span data-ttu-id="259e2-219">O `startButton_Click` procedimento é um exemplo de uma `Async Sub` procedimento.</span><span class="sxs-lookup"><span data-stu-id="259e2-219">The `startButton_Click` procedure is an example of an `Async Sub` procedure.</span></span> <span data-ttu-id="259e2-220">Porque `DoSomethingAsync` é um `Async` função, a tarefa para a chamada a `DoSomethingAsync` deve ser colocado em espera, como mostra a seguinte instrução: `Await DoSomethingAsync()`.</span><span class="sxs-lookup"><span data-stu-id="259e2-220">Because `DoSomethingAsync` is an `Async` function, the task for the call to `DoSomethingAsync` must be awaited, as the following statement shows: `Await DoSomethingAsync()`.</span></span> <span data-ttu-id="259e2-221">O `startButton_Click``Sub` procedimento deve ser definido com o `Async` modificador porque ele tem um `Await` expressão.</span><span class="sxs-lookup"><span data-stu-id="259e2-221">The `startButton_Click``Sub` procedure must be defined with the `Async` modifier because it has an `Await` expression.</span></span>  
  
 <span data-ttu-id="259e2-222">[!code-vb[csAsyncMethod n º&1;](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="259e2-222">[!code-vb[csAsyncMethod#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/VisualBasic/sub-statement_2.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="259e2-223">Consulte também</span><span class="sxs-lookup"><span data-stu-id="259e2-223">See Also</span></span>  
 <span data-ttu-id="259e2-224">[Instrução Implements](implements-statement.md) </span><span class="sxs-lookup"><span data-stu-id="259e2-224">[Implements Statement](implements-statement.md) </span></span>  
<span data-ttu-id="259e2-225"> [Instrução Function](function-statement.md) </span><span class="sxs-lookup"><span data-stu-id="259e2-225"> [Function Statement](function-statement.md) </span></span>  
<span data-ttu-id="259e2-226"> [Lista de parâmetros](parameter-list.md) </span><span class="sxs-lookup"><span data-stu-id="259e2-226"> [Parameter List](parameter-list.md) </span></span>  
<span data-ttu-id="259e2-227"> [Instrução Dim](dim-statement.md) </span><span class="sxs-lookup"><span data-stu-id="259e2-227"> [Dim Statement](dim-statement.md) </span></span>  
<span data-ttu-id="259e2-228"> [Instrução Call](call-statement.md) </span><span class="sxs-lookup"><span data-stu-id="259e2-228"> [Call Statement](call-statement.md) </span></span>  
<span data-ttu-id="259e2-229"> [De](of-clause.md) </span><span class="sxs-lookup"><span data-stu-id="259e2-229"> [Of](of-clause.md) </span></span>  
<span data-ttu-id="259e2-230"> [Matrizes de parâmetros](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md) </span><span class="sxs-lookup"><span data-stu-id="259e2-230"> [Parameter Arrays](../../../visual-basic/programming-guide/language-features/procedures/parameter-arrays.md) </span></span>  
<span data-ttu-id="259e2-231"> [Como: usar uma classe genérica](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md) </span><span class="sxs-lookup"><span data-stu-id="259e2-231"> [How to: Use a Generic Class](../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md) </span></span>  
<span data-ttu-id="259e2-232"> [Procedimentos de solução de problemas](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="259e2-232"> [Troubleshooting Procedures](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md) </span></span>  
<span data-ttu-id="259e2-233"> [Métodos Parciais](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)</span><span class="sxs-lookup"><span data-stu-id="259e2-233"> [Partial Methods](../../../visual-basic/programming-guide/language-features/procedures/partial-methods.md)</span></span>

