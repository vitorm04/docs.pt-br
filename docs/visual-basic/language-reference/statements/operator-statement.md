---
title: Instrução Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.operator
helpviewer_keywords:
- operators [Visual Basic]
- procedures [Visual Basic], operator
- Narrowing keyword [Visual Basic], conversion operators
- Visual Basic code, operators
- Widening keyword [Visual Basic], conversion operators
- syntax [Visual Basic], Operator procedures
- operators [Visual Basic], overloading
- overloaded operators [Visual Basic]
- operator overloading
- operator procedures
- Operator statement [Visual Basic]
- CType function [Visual Basic], Operator statement
ms.assetid: b12ec4af-1ad7-4a17-865b-c5ee96320ae5
ms.openlocfilehash: 184970d33aae4af135153f9d6f6755770bdf84f6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818586"
---
# <a name="operator-statement"></a><span data-ttu-id="e73c4-102">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="e73c4-102">Operator Statement</span></span>
<span data-ttu-id="e73c4-103">Declara o símbolo do operador, operandos e código que definem um procedimento de operador em uma classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="e73c4-103">Declares the operator symbol, operands, and code that define an operator procedure on a class or structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e73c4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e73c4-104">Syntax</span></span>  
  
```  
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]   
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]  
    [ statements ]  
    [ statements ]  
    Return returnvalue  
    [ statements ]  
End Operator  
```  
  
## <a name="parts"></a><span data-ttu-id="e73c4-105">Partes</span><span class="sxs-lookup"><span data-stu-id="e73c4-105">Parts</span></span>  
 `attrlist`  
 <span data-ttu-id="e73c4-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e73c4-106">Optional.</span></span> <span data-ttu-id="e73c4-107">Ver [lista de atributos](../../../visual-basic/language-reference/statements/attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="e73c4-107">See [Attribute List](../../../visual-basic/language-reference/statements/attribute-list.md).</span></span>  
  
 `Public`  
 <span data-ttu-id="e73c4-108">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e73c4-108">Required.</span></span> <span data-ttu-id="e73c4-109">Indica que esse procedimento de operador tem [pública](../../../visual-basic/language-reference/modifiers/public.md) acesso.</span><span class="sxs-lookup"><span data-stu-id="e73c4-109">Indicates that this operator procedure has [Public](../../../visual-basic/language-reference/modifiers/public.md) access.</span></span>  
  
 `Overloads`  
 <span data-ttu-id="e73c4-110">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e73c4-110">Optional.</span></span> <span data-ttu-id="e73c4-111">Ver [sobrecarrega](../../../visual-basic/language-reference/modifiers/overloads.md).</span><span class="sxs-lookup"><span data-stu-id="e73c4-111">See [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md).</span></span>  
  
 `Shared`  
 <span data-ttu-id="e73c4-112">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e73c4-112">Required.</span></span> <span data-ttu-id="e73c4-113">Indica que esse procedimento de operador é um [compartilhado](../../../visual-basic/language-reference/modifiers/shared.md) procedimento.</span><span class="sxs-lookup"><span data-stu-id="e73c4-113">Indicates that this operator procedure is a [Shared](../../../visual-basic/language-reference/modifiers/shared.md) procedure.</span></span>  
  
 `Shadows`  
 <span data-ttu-id="e73c4-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e73c4-114">Optional.</span></span> <span data-ttu-id="e73c4-115">Ver [sombras](../../../visual-basic/language-reference/modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="e73c4-115">See [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md).</span></span>  
  
 `Widening`  
 <span data-ttu-id="e73c4-116">Necessário para um operador de conversão, a menos que você especifique `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="e73c4-116">Required for a conversion operator unless you specify `Narrowing`.</span></span> <span data-ttu-id="e73c4-117">Indica que esse procedimento de operador define uma [Widening](../../../visual-basic/language-reference/modifiers/widening.md) conversão.</span><span class="sxs-lookup"><span data-stu-id="e73c4-117">Indicates that this operator procedure defines a [Widening](../../../visual-basic/language-reference/modifiers/widening.md) conversion.</span></span> <span data-ttu-id="e73c4-118">Consulte "De ampliação e redução conversões" nesta página de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="e73c4-118">See "Widening and Narrowing Conversions" on this Help page.</span></span>  
  
 `Narrowing`  
 <span data-ttu-id="e73c4-119">Necessário para um operador de conversão, a menos que você especifique `Widening`.</span><span class="sxs-lookup"><span data-stu-id="e73c4-119">Required for a conversion operator unless you specify `Widening`.</span></span> <span data-ttu-id="e73c4-120">Indica que esse procedimento de operador define uma [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) conversão.</span><span class="sxs-lookup"><span data-stu-id="e73c4-120">Indicates that this operator procedure defines a [Narrowing](../../../visual-basic/language-reference/modifiers/narrowing.md) conversion.</span></span> <span data-ttu-id="e73c4-121">Consulte "De ampliação e redução conversões" nesta página de Ajuda.</span><span class="sxs-lookup"><span data-stu-id="e73c4-121">See "Widening and Narrowing Conversions" on this Help page.</span></span>  
  
 `operatorsymbol`  
 <span data-ttu-id="e73c4-122">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e73c4-122">Required.</span></span> <span data-ttu-id="e73c4-123">O símbolo ou o identificador do operador que define este procedimento de operador.</span><span class="sxs-lookup"><span data-stu-id="e73c4-123">The symbol or identifier of the operator that this operator procedure defines.</span></span>  
  
 `operand1`  
 <span data-ttu-id="e73c4-124">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e73c4-124">Required.</span></span> <span data-ttu-id="e73c4-125">O nome e tipo de operando único de um operador unário (incluindo um operador de conversão) ou o operando esquerdo de um operador binário.</span><span class="sxs-lookup"><span data-stu-id="e73c4-125">The name and type of the single operand of a unary operator (including a conversion operator) or the left operand of a binary operator.</span></span>  
  
 `operand2`  
 <span data-ttu-id="e73c4-126">Necessário para os operadores binários.</span><span class="sxs-lookup"><span data-stu-id="e73c4-126">Required for binary operators.</span></span> <span data-ttu-id="e73c4-127">O nome e o tipo do operando à direita de um operador binário.</span><span class="sxs-lookup"><span data-stu-id="e73c4-127">The name and type of the right operand of a binary operator.</span></span>  
  
 <span data-ttu-id="e73c4-128">`operand1` e `operand2` tem a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="e73c4-128">`operand1` and `operand2` have the following syntax and parts:</span></span>  
  
 `[ ByVal ] operandname [ As operandtype ]`  
  
|<span data-ttu-id="e73c4-129">Parte</span><span class="sxs-lookup"><span data-stu-id="e73c4-129">Part</span></span>|<span data-ttu-id="e73c4-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="e73c4-130">Description</span></span>|  
|----------|-----------------|  
|`ByVal`|<span data-ttu-id="e73c4-131">Opcional, mas o mecanismo de passagem deve ser [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="e73c4-131">Optional, but the passing mechanism must be [ByVal](../../../visual-basic/language-reference/modifiers/byval.md).</span></span>|  
|`operandname`|<span data-ttu-id="e73c4-132">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e73c4-132">Required.</span></span> <span data-ttu-id="e73c4-133">Nome da variável que representa esse operando.</span><span class="sxs-lookup"><span data-stu-id="e73c4-133">Name of the variable representing this operand.</span></span> <span data-ttu-id="e73c4-134">Ver [nomes de elementos declarados](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="e73c4-134">See [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|  
|`operandtype`|<span data-ttu-id="e73c4-135">Opcional, a menos que `Option Strict` é `On`.</span><span class="sxs-lookup"><span data-stu-id="e73c4-135">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="e73c4-136">Tipo de dados desse operando.</span><span class="sxs-lookup"><span data-stu-id="e73c4-136">Data type of this operand.</span></span>|  
  
 `type`  
 <span data-ttu-id="e73c4-137">Opcional, a menos que `Option Strict` é `On`.</span><span class="sxs-lookup"><span data-stu-id="e73c4-137">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="e73c4-138">Retorna o tipo de dados do valor do qual o procedimento de operador.</span><span class="sxs-lookup"><span data-stu-id="e73c4-138">Data type of the value the operator procedure returns.</span></span>  
  
 `statements`  
 <span data-ttu-id="e73c4-139">Opcional.</span><span class="sxs-lookup"><span data-stu-id="e73c4-139">Optional.</span></span> <span data-ttu-id="e73c4-140">Bloco de instruções que executa o procedimento de operador.</span><span class="sxs-lookup"><span data-stu-id="e73c4-140">Block of statements that the operator procedure runs.</span></span>  
  
 `returnvalue`  
 <span data-ttu-id="e73c4-141">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e73c4-141">Required.</span></span> <span data-ttu-id="e73c4-142">O valor que o procedimento de operador retorna para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="e73c4-142">The value that the operator procedure returns to the calling code.</span></span>  
  
 <span data-ttu-id="e73c4-143">`End` `Operator`</span><span class="sxs-lookup"><span data-stu-id="e73c4-143">`End` `Operator`</span></span>  
 <span data-ttu-id="e73c4-144">Necessário.</span><span class="sxs-lookup"><span data-stu-id="e73c4-144">Required.</span></span> <span data-ttu-id="e73c4-145">Finaliza a definição desse procedimento de operador.</span><span class="sxs-lookup"><span data-stu-id="e73c4-145">Terminates the definition of this operator procedure.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e73c4-146">Comentários</span><span class="sxs-lookup"><span data-stu-id="e73c4-146">Remarks</span></span>  
 <span data-ttu-id="e73c4-147">Você pode usar `Operator` somente em uma classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="e73c4-147">You can use `Operator` only in a class or structure.</span></span> <span data-ttu-id="e73c4-148">Isso significa que o *contexto de declaração* para um operador não pode ser um arquivo de origem, namespace, módulo, interface, procedimento ou bloco.</span><span class="sxs-lookup"><span data-stu-id="e73c4-148">This means the *declaration context* for an operator cannot be a source file, namespace, module, interface, procedure, or block.</span></span> <span data-ttu-id="e73c4-149">Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="e73c4-149">For more information, see [Declaration Contexts and Default Access Levels](../../../visual-basic/language-reference/statements/declaration-contexts-and-default-access-levels.md).</span></span>  
  
 <span data-ttu-id="e73c4-150">Todos os operadores devem ser `Public Shared`.</span><span class="sxs-lookup"><span data-stu-id="e73c4-150">All operators must be `Public Shared`.</span></span> <span data-ttu-id="e73c4-151">Não é possível especificar `ByRef`, `Optional`, ou `ParamArray` para qualquer um dos operandos.</span><span class="sxs-lookup"><span data-stu-id="e73c4-151">You cannot specify `ByRef`, `Optional`, or `ParamArray` for either operand.</span></span>  
  
 <span data-ttu-id="e73c4-152">Você não pode usar o símbolo do operador ou o identificador para manter um valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="e73c4-152">You cannot use the operator symbol or identifier to hold a return value.</span></span> <span data-ttu-id="e73c4-153">Você deve usar o `Return` instrução e ele devem especificar um valor.</span><span class="sxs-lookup"><span data-stu-id="e73c4-153">You must use the `Return` statement, and it must specify a value.</span></span> <span data-ttu-id="e73c4-154">Qualquer número de `Return` instruções podem aparecer em qualquer lugar no procedimento.</span><span class="sxs-lookup"><span data-stu-id="e73c4-154">Any number of `Return` statements can appear anywhere in the procedure.</span></span>  
  
 <span data-ttu-id="e73c4-155">Definindo um operador dessa maneira é chamado *sobrecarregamento*, se você usar o `Overloads` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="e73c4-155">Defining an operator in this way is called *operator overloading*, whether or not you use the `Overloads` keyword.</span></span> <span data-ttu-id="e73c4-156">A tabela a seguir lista os operadores que você pode definir.</span><span class="sxs-lookup"><span data-stu-id="e73c4-156">The following table lists the operators you can define.</span></span>  
  
|<span data-ttu-id="e73c4-157">Tipo</span><span class="sxs-lookup"><span data-stu-id="e73c4-157">Type</span></span>|<span data-ttu-id="e73c4-158">Operadores</span><span class="sxs-lookup"><span data-stu-id="e73c4-158">Operators</span></span>|  
|----------|---------------|  
|<span data-ttu-id="e73c4-159">Unário</span><span class="sxs-lookup"><span data-stu-id="e73c4-159">Unary</span></span>|<span data-ttu-id="e73c4-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="e73c4-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|  
|<span data-ttu-id="e73c4-161">Binário</span><span class="sxs-lookup"><span data-stu-id="e73c4-161">Binary</span></span>|<span data-ttu-id="e73c4-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="e73c4-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|  
|<span data-ttu-id="e73c4-163">Conversão (unário)</span><span class="sxs-lookup"><span data-stu-id="e73c4-163">Conversion (unary)</span></span>|`CType`|  
  
 <span data-ttu-id="e73c4-164">Observe que o `=` operador na lista binária é o operador de comparação, não o operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="e73c4-164">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>  
  
 <span data-ttu-id="e73c4-165">Quando você define `CType`, você deve especificar `Widening` ou `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="e73c4-165">When you define `CType`, you must specify either `Widening` or `Narrowing`.</span></span>  
  
## <a name="matched-pairs"></a><span data-ttu-id="e73c4-166">Pares correspondentes</span><span class="sxs-lookup"><span data-stu-id="e73c4-166">Matched Pairs</span></span>  
 <span data-ttu-id="e73c4-167">Você deve definir determinados operadores como pares correspondentes.</span><span class="sxs-lookup"><span data-stu-id="e73c4-167">You must define certain operators as matched pairs.</span></span> <span data-ttu-id="e73c4-168">Se você definir um operador de tal par, você deve definir o outro também.</span><span class="sxs-lookup"><span data-stu-id="e73c4-168">If you define either operator of such a pair, you must define the other as well.</span></span> <span data-ttu-id="e73c4-169">Os pares correspondentes são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="e73c4-169">The matched pairs are the following:</span></span>  
  
-   <span data-ttu-id="e73c4-170">`=` e `<>`</span><span class="sxs-lookup"><span data-stu-id="e73c4-170">`=` and `<>`</span></span>  
  
-   <span data-ttu-id="e73c4-171">`>` e `<`</span><span class="sxs-lookup"><span data-stu-id="e73c4-171">`>` and `<`</span></span>  
  
-   <span data-ttu-id="e73c4-172">`>=` e `<=`</span><span class="sxs-lookup"><span data-stu-id="e73c4-172">`>=` and `<=`</span></span>  
  
-   <span data-ttu-id="e73c4-173">`IsTrue` e `IsFalse`</span><span class="sxs-lookup"><span data-stu-id="e73c4-173">`IsTrue` and `IsFalse`</span></span>  
  
## <a name="data-type-restrictions"></a><span data-ttu-id="e73c4-174">Restrições de tipo de dados</span><span class="sxs-lookup"><span data-stu-id="e73c4-174">Data Type Restrictions</span></span>  
 <span data-ttu-id="e73c4-175">Cada operador que você definir deve envolver a classe ou estrutura na qual você defini-lo.</span><span class="sxs-lookup"><span data-stu-id="e73c4-175">Every operator you define must involve the class or structure on which you define it.</span></span> <span data-ttu-id="e73c4-176">Isso significa que a classe ou estrutura deve aparecer como o tipo de dados das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="e73c4-176">This means that the class or structure must appear as the data type of the following:</span></span>  
  
-   <span data-ttu-id="e73c4-177">O operando de um operador unário.</span><span class="sxs-lookup"><span data-stu-id="e73c4-177">The operand of a unary operator.</span></span>  
  
-   <span data-ttu-id="e73c4-178">Pelo menos um dos operandos de um operador binário.</span><span class="sxs-lookup"><span data-stu-id="e73c4-178">At least one of the operands of a binary operator.</span></span>  
  
-   <span data-ttu-id="e73c4-179">O operando ou tipo de retorno de um operador de conversão.</span><span class="sxs-lookup"><span data-stu-id="e73c4-179">Either the operand or the return type of a conversion operator.</span></span>  
  
 <span data-ttu-id="e73c4-180">Determinados operadores têm dados adicionais que digite as restrições, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="e73c4-180">Certain operators have additional data type restrictions, as follows:</span></span>  
  
-   <span data-ttu-id="e73c4-181">Se você definir a `IsTrue` e `IsFalse` operadores, eles devem retornar o `Boolean` tipo.</span><span class="sxs-lookup"><span data-stu-id="e73c4-181">If you define the `IsTrue` and `IsFalse` operators, they must both return the `Boolean` type.</span></span>  
  
-   <span data-ttu-id="e73c4-182">Se você definir a `<<` e `>>` operadores, eles devem ambos especificam o `Integer` de tipo para o `operandtype` de `operand2`.</span><span class="sxs-lookup"><span data-stu-id="e73c4-182">If you define the `<<` and `>>` operators, they must both specify the `Integer` type for the `operandtype` of `operand2`.</span></span>  
  
 <span data-ttu-id="e73c4-183">O tipo de retorno não precisa corresponder ao tipo de qualquer um dos operandos.</span><span class="sxs-lookup"><span data-stu-id="e73c4-183">The return type does not have to correspond to the type of either operand.</span></span> <span data-ttu-id="e73c4-184">Por exemplo, um operador de comparação, como `=` ou `<>` pode retornar `Boolean` mesmo se nenhum dos operandos é `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="e73c4-184">For example, a comparison operator such as `=` or `<>` can return `Boolean` even if neither operand is `Boolean`.</span></span>  
  
## <a name="logical-and-bitwise-operators"></a><span data-ttu-id="e73c4-185">Operadores lógicos e bit a bit</span><span class="sxs-lookup"><span data-stu-id="e73c4-185">Logical and Bitwise Operators</span></span>  
 <span data-ttu-id="e73c4-186">O `And`, `Or`, `Not`, e `Xor` operadores podem executar operações de lógicas ou bit a bit no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e73c4-186">The `And`, `Or`, `Not`, and `Xor` operators can perform either logical or bitwise operations in Visual Basic.</span></span> <span data-ttu-id="e73c4-187">No entanto, se você definir um destes operadores em uma classe ou estrutura, você pode definir apenas sua operação bit a bit.</span><span class="sxs-lookup"><span data-stu-id="e73c4-187">However, if you define one of these operators on a class or structure, you can define only its bitwise operation.</span></span>  
  
 <span data-ttu-id="e73c4-188">Não é possível definir a `AndAlso` operador diretamente com um `Operator` instrução.</span><span class="sxs-lookup"><span data-stu-id="e73c4-188">You cannot define the `AndAlso` operator directly with an `Operator` statement.</span></span> <span data-ttu-id="e73c4-189">No entanto, você pode usar `AndAlso` se você cumpriu as seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="e73c4-189">However, you can use `AndAlso` if you have fulfilled the following conditions:</span></span>  
  
-   <span data-ttu-id="e73c4-190">Você definiu `And` nos mesmos tipos de operando que você deseja usar para `AndAlso`.</span><span class="sxs-lookup"><span data-stu-id="e73c4-190">You have defined `And` on the same operand types you want to use for `AndAlso`.</span></span>  
  
-   <span data-ttu-id="e73c4-191">Sua definição de `And` retorna o mesmo tipo que a classe ou estrutura na qual você o define.</span><span class="sxs-lookup"><span data-stu-id="e73c4-191">Your definition of `And` returns the same type as the class or structure on which you have defined it.</span></span>  
  
-   <span data-ttu-id="e73c4-192">Você definiu o `IsFalse` operador na classe ou estrutura na qual você definiu `And`.</span><span class="sxs-lookup"><span data-stu-id="e73c4-192">You have defined the `IsFalse` operator on the class or structure on which you have defined `And`.</span></span>  
  
 <span data-ttu-id="e73c4-193">Da mesma forma, você pode usar `OrElse` se você tiver definido `Or` nos operandos mesmos, com o tipo de retorno da classe ou estrutura e você tiver definido `IsTrue` na classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="e73c4-193">Similarly, you can use `OrElse` if you have defined `Or` on the same operands, with the return type of the class or structure, and you have defined `IsTrue` on the class or structure.</span></span>  
  
## <a name="widening-and-narrowing-conversions"></a><span data-ttu-id="e73c4-194">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="e73c4-194">Widening and Narrowing Conversions</span></span>  
 <span data-ttu-id="e73c4-195">Um *conversão de ampliação* sempre terá êxito em tempo de execução, enquanto um *conversão de estreitamento* pode falhar em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e73c4-195">A *widening conversion* always succeeds at run time, while a *narrowing conversion* can fail at run time.</span></span> <span data-ttu-id="e73c4-196">Para obter mais informações, consulte [Ampliando e restringindo conversões](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="e73c4-196">For more information, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>  
  
 <span data-ttu-id="e73c4-197">Se você declarar um procedimento de conversão para ser `Widening`, seu código de procedimento não deve gerar falhas.</span><span class="sxs-lookup"><span data-stu-id="e73c4-197">If you declare a conversion procedure to be `Widening`, your procedure code must not generate any failures.</span></span> <span data-ttu-id="e73c4-198">Isso significa que o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e73c4-198">This means the following:</span></span>  
  
-   <span data-ttu-id="e73c4-199">Ele deve sempre retornar um valor válido do tipo `type`.</span><span class="sxs-lookup"><span data-stu-id="e73c4-199">It must always return a valid value of type `type`.</span></span>  
  
-   <span data-ttu-id="e73c4-200">Ele deve tratar todas as possíveis exceções e outras condições de erro.</span><span class="sxs-lookup"><span data-stu-id="e73c4-200">It must handle all possible exceptions and other error conditions.</span></span>  
  
-   <span data-ttu-id="e73c4-201">Ele deve tratar retorna qualquer erro de qualquer procedimento que ele chama.</span><span class="sxs-lookup"><span data-stu-id="e73c4-201">It must handle any error returns from any procedures it calls.</span></span>  
  
 <span data-ttu-id="e73c4-202">Se houver a possibilidade que um procedimento de conversão talvez não seja bem-sucedida, ou que ele pode causar uma exceção sem tratamento, você deve declará-la para ser `Narrowing`.</span><span class="sxs-lookup"><span data-stu-id="e73c4-202">If there is any possibility that a conversion procedure might not succeed, or that it might cause an unhandled exception, you must declare it to be `Narrowing`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e73c4-203">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e73c4-203">Example</span></span>  
 <span data-ttu-id="e73c4-204">O seguinte exemplo de código usa o `Operator` instrução para definir o contorno de uma estrutura que inclui procedimentos de operador para o `And`, `Or`, `IsFalse`, e `IsTrue` operadores.</span><span class="sxs-lookup"><span data-stu-id="e73c4-204">The following code example uses the `Operator` statement to define the outline of a structure that includes operator procedures for the `And`, `Or`, `IsFalse`, and `IsTrue` operators.</span></span> <span data-ttu-id="e73c4-205">`And` e `Or` cada usam dois operandos do tipo `abc` e o tipo de retorno `abc`.</span><span class="sxs-lookup"><span data-stu-id="e73c4-205">`And` and `Or` each take two operands of type `abc` and return type `abc`.</span></span> <span data-ttu-id="e73c4-206">`IsFalse` e `IsTrue` utilizar um único operando do tipo de cada `abc` e retornar `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="e73c4-206">`IsFalse` and `IsTrue` each take a single operand of type `abc` and return `Boolean`.</span></span> <span data-ttu-id="e73c4-207">Essas definições permitem que o código de chamada usar `And`, `AndAlso`, `Or`, e `OrElse` com operandos do tipo `abc`.</span><span class="sxs-lookup"><span data-stu-id="e73c4-207">These definitions allow the calling code to use `And`, `AndAlso`, `Or`, and `OrElse` with operands of type `abc`.</span></span>  
  
 [!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]  
  
## <a name="see-also"></a><span data-ttu-id="e73c4-208">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e73c4-208">See also</span></span>

- [<span data-ttu-id="e73c4-209">Operador IsFalse</span><span class="sxs-lookup"><span data-stu-id="e73c4-209">IsFalse Operator</span></span>](../../../visual-basic/language-reference/operators/isfalse-operator.md)
- [<span data-ttu-id="e73c4-210">Operador IsTrue</span><span class="sxs-lookup"><span data-stu-id="e73c4-210">IsTrue Operator</span></span>](../../../visual-basic/language-reference/operators/istrue-operator.md)
- [<span data-ttu-id="e73c4-211">Ampliação</span><span class="sxs-lookup"><span data-stu-id="e73c4-211">Widening</span></span>](../../../visual-basic/language-reference/modifiers/widening.md)
- [<span data-ttu-id="e73c4-212">Narrowing</span><span class="sxs-lookup"><span data-stu-id="e73c4-212">Narrowing</span></span>](../../../visual-basic/language-reference/modifiers/narrowing.md)
- [<span data-ttu-id="e73c4-213">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="e73c4-213">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="e73c4-214">Procedimentos de Operador</span><span class="sxs-lookup"><span data-stu-id="e73c4-214">Operator Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="e73c4-215">Como: Definir um operador</span><span class="sxs-lookup"><span data-stu-id="e73c4-215">How to: Define an Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="e73c4-216">Como: Definir um operador de conversão</span><span class="sxs-lookup"><span data-stu-id="e73c4-216">How to: Define a Conversion Operator</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="e73c4-217">Como: Chamar um procedimento de operador</span><span class="sxs-lookup"><span data-stu-id="e73c4-217">How to: Call an Operator Procedure</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="e73c4-218">Como: Usar uma classe que define operadores</span><span class="sxs-lookup"><span data-stu-id="e73c4-218">How to: Use a Class that Defines Operators</span></span>](../../../visual-basic/programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
