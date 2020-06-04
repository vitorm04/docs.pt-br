---
title: Instrução Operator
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
ms.openlocfilehash: f9e6ffe5a49715592399321ab471d73826e05d8e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404389"
---
# <a name="operator-statement"></a><span data-ttu-id="03b0f-102">Instrução Operator</span><span class="sxs-lookup"><span data-stu-id="03b0f-102">Operator Statement</span></span>

<span data-ttu-id="03b0f-103">Declara o símbolo do operador, os operandos e o código que definem um procedimento de operador em uma classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="03b0f-103">Declares the operator symbol, operands, and code that define an operator procedure on a class or structure.</span></span>

## <a name="syntax"></a><span data-ttu-id="03b0f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="03b0f-104">Syntax</span></span>

```vb
[ <attrlist> ] Public [ Overloads ] Shared [ Shadows ] [ Widening | Narrowing ]
Operator operatorsymbol ( operand1 [, operand2 ]) [ As [ <attrlist> ] type ]
    [ statements ]
    [ statements ]
    Return returnvalue
    [ statements ]
End Operator
```

## <a name="parts"></a><span data-ttu-id="03b0f-105">Partes</span><span class="sxs-lookup"><span data-stu-id="03b0f-105">Parts</span></span>

`attrlist`  
<span data-ttu-id="03b0f-106">Opcional.</span><span class="sxs-lookup"><span data-stu-id="03b0f-106">Optional.</span></span> <span data-ttu-id="03b0f-107">Consulte a [lista de atributos](attribute-list.md).</span><span class="sxs-lookup"><span data-stu-id="03b0f-107">See [Attribute List](attribute-list.md).</span></span>

`Public`  
<span data-ttu-id="03b0f-108">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="03b0f-108">Required.</span></span> <span data-ttu-id="03b0f-109">Indica que este procedimento de operador tem acesso [público](../modifiers/public.md) .</span><span class="sxs-lookup"><span data-stu-id="03b0f-109">Indicates that this operator procedure has [Public](../modifiers/public.md) access.</span></span>

`Overloads`  
<span data-ttu-id="03b0f-110">Opcional.</span><span class="sxs-lookup"><span data-stu-id="03b0f-110">Optional.</span></span> <span data-ttu-id="03b0f-111">Veja [sobrecargas](../modifiers/overloads.md).</span><span class="sxs-lookup"><span data-stu-id="03b0f-111">See [Overloads](../modifiers/overloads.md).</span></span>

`Shared`  
<span data-ttu-id="03b0f-112">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="03b0f-112">Required.</span></span> <span data-ttu-id="03b0f-113">Indica que esse procedimento de operador é um procedimento [compartilhado](../modifiers/shared.md) .</span><span class="sxs-lookup"><span data-stu-id="03b0f-113">Indicates that this operator procedure is a [Shared](../modifiers/shared.md) procedure.</span></span>

`Shadows`  
<span data-ttu-id="03b0f-114">Opcional.</span><span class="sxs-lookup"><span data-stu-id="03b0f-114">Optional.</span></span> <span data-ttu-id="03b0f-115">Consulte [Shadows](../modifiers/shadows.md).</span><span class="sxs-lookup"><span data-stu-id="03b0f-115">See [Shadows](../modifiers/shadows.md).</span></span>

`Widening`  
<span data-ttu-id="03b0f-116">Necessário para um operador de conversão, a menos que você especifique `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="03b0f-116">Required for a conversion operator unless you specify `Narrowing`.</span></span> <span data-ttu-id="03b0f-117">Indica que este procedimento de operador define uma conversão de [ampliação](../modifiers/widening.md) .</span><span class="sxs-lookup"><span data-stu-id="03b0f-117">Indicates that this operator procedure defines a [Widening](../modifiers/widening.md) conversion.</span></span> <span data-ttu-id="03b0f-118">Consulte "conversões de alargamento e estreitamento" nesta página de ajuda.</span><span class="sxs-lookup"><span data-stu-id="03b0f-118">See "Widening and Narrowing Conversions" on this Help page.</span></span>

`Narrowing`  
<span data-ttu-id="03b0f-119">Necessário para um operador de conversão, a menos que você especifique `Widening` .</span><span class="sxs-lookup"><span data-stu-id="03b0f-119">Required for a conversion operator unless you specify `Widening`.</span></span> <span data-ttu-id="03b0f-120">Indica que este procedimento de operador define uma conversão de [restrição](../modifiers/narrowing.md) .</span><span class="sxs-lookup"><span data-stu-id="03b0f-120">Indicates that this operator procedure defines a [Narrowing](../modifiers/narrowing.md) conversion.</span></span> <span data-ttu-id="03b0f-121">Consulte "conversões de alargamento e estreitamento" nesta página de ajuda.</span><span class="sxs-lookup"><span data-stu-id="03b0f-121">See "Widening and Narrowing Conversions" on this Help page.</span></span>

`operatorsymbol`  
<span data-ttu-id="03b0f-122">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="03b0f-122">Required.</span></span> <span data-ttu-id="03b0f-123">O símbolo ou identificador do operador que este procedimento de operador define.</span><span class="sxs-lookup"><span data-stu-id="03b0f-123">The symbol or identifier of the operator that this operator procedure defines.</span></span>

`operand1`  
<span data-ttu-id="03b0f-124">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="03b0f-124">Required.</span></span> <span data-ttu-id="03b0f-125">O nome e o tipo do operando único de um operador unário (incluindo um operador de conversão) ou o operando esquerdo de um operador binário.</span><span class="sxs-lookup"><span data-stu-id="03b0f-125">The name and type of the single operand of a unary operator (including a conversion operator) or the left operand of a binary operator.</span></span>

`operand2`  
<span data-ttu-id="03b0f-126">Necessário para operadores binários.</span><span class="sxs-lookup"><span data-stu-id="03b0f-126">Required for binary operators.</span></span> <span data-ttu-id="03b0f-127">O nome e o tipo do operando direito de um operador binário.</span><span class="sxs-lookup"><span data-stu-id="03b0f-127">The name and type of the right operand of a binary operator.</span></span>

<span data-ttu-id="03b0f-128">`operand1`e `operand2` têm a seguinte sintaxe e partes:</span><span class="sxs-lookup"><span data-stu-id="03b0f-128">`operand1` and `operand2` have the following syntax and parts:</span></span>

`[ ByVal ] operandname [ As operandtype ]`

|<span data-ttu-id="03b0f-129">Parte</span><span class="sxs-lookup"><span data-stu-id="03b0f-129">Part</span></span>|<span data-ttu-id="03b0f-130">Descrição</span><span class="sxs-lookup"><span data-stu-id="03b0f-130">Description</span></span>|
|----------|-----------------|
|`ByVal`|<span data-ttu-id="03b0f-131">Opcional, mas o mecanismo de passagem deve ser [ByVal](../modifiers/byval.md).</span><span class="sxs-lookup"><span data-stu-id="03b0f-131">Optional, but the passing mechanism must be [ByVal](../modifiers/byval.md).</span></span>|
|`operandname`|<span data-ttu-id="03b0f-132">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="03b0f-132">Required.</span></span> <span data-ttu-id="03b0f-133">Nome da variável que representa esse operando.</span><span class="sxs-lookup"><span data-stu-id="03b0f-133">Name of the variable representing this operand.</span></span> <span data-ttu-id="03b0f-134">Consulte [nomes de elementos declarados](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="03b0f-134">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`operandtype`|<span data-ttu-id="03b0f-135">Opcional, a menos que `Option Strict` seja `On` .</span><span class="sxs-lookup"><span data-stu-id="03b0f-135">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="03b0f-136">Tipo de dados deste operando.</span><span class="sxs-lookup"><span data-stu-id="03b0f-136">Data type of this operand.</span></span>|

`type`  
<span data-ttu-id="03b0f-137">Opcional, a menos que `Option Strict` seja `On` .</span><span class="sxs-lookup"><span data-stu-id="03b0f-137">Optional unless `Option Strict` is `On`.</span></span> <span data-ttu-id="03b0f-138">Tipo de dados do valor que o procedimento do operador retorna.</span><span class="sxs-lookup"><span data-stu-id="03b0f-138">Data type of the value the operator procedure returns.</span></span>

`statements`  
<span data-ttu-id="03b0f-139">Opcional.</span><span class="sxs-lookup"><span data-stu-id="03b0f-139">Optional.</span></span> <span data-ttu-id="03b0f-140">Bloco de instruções que o procedimento de operador executa.</span><span class="sxs-lookup"><span data-stu-id="03b0f-140">Block of statements that the operator procedure runs.</span></span>

`returnvalue`  
<span data-ttu-id="03b0f-141">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="03b0f-141">Required.</span></span> <span data-ttu-id="03b0f-142">O valor que o procedimento do operador retorna para o código de chamada.</span><span class="sxs-lookup"><span data-stu-id="03b0f-142">The value that the operator procedure returns to the calling code.</span></span>

<span data-ttu-id="03b0f-143">`End` `Operator`</span><span class="sxs-lookup"><span data-stu-id="03b0f-143">`End` `Operator`</span></span>  
<span data-ttu-id="03b0f-144">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="03b0f-144">Required.</span></span> <span data-ttu-id="03b0f-145">Encerra a definição deste procedimento de operador.</span><span class="sxs-lookup"><span data-stu-id="03b0f-145">Terminates the definition of this operator procedure.</span></span>

## <a name="remarks"></a><span data-ttu-id="03b0f-146">Comentários</span><span class="sxs-lookup"><span data-stu-id="03b0f-146">Remarks</span></span>

<span data-ttu-id="03b0f-147">Você pode usar `Operator` somente em uma classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="03b0f-147">You can use `Operator` only in a class or structure.</span></span> <span data-ttu-id="03b0f-148">Isso significa que o *contexto de declaração* para um operador não pode ser um arquivo de origem, namespace, módulo, interface, procedimento ou bloco.</span><span class="sxs-lookup"><span data-stu-id="03b0f-148">This means the *declaration context* for an operator cannot be a source file, namespace, module, interface, procedure, or block.</span></span> <span data-ttu-id="03b0f-149">Para obter mais informações, consulte [Contextos de declaração e níveis de acesso padrão](declaration-contexts-and-default-access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="03b0f-149">For more information, see [Declaration Contexts and Default Access Levels](declaration-contexts-and-default-access-levels.md).</span></span>

<span data-ttu-id="03b0f-150">Todos os operadores devem ser `Public Shared` .</span><span class="sxs-lookup"><span data-stu-id="03b0f-150">All operators must be `Public Shared`.</span></span> <span data-ttu-id="03b0f-151">Você não pode especificar `ByRef` , `Optional` ou `ParamArray` para qualquer operando.</span><span class="sxs-lookup"><span data-stu-id="03b0f-151">You cannot specify `ByRef`, `Optional`, or `ParamArray` for either operand.</span></span>

<span data-ttu-id="03b0f-152">Você não pode usar o identificador ou símbolo do operador para manter um valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="03b0f-152">You cannot use the operator symbol or identifier to hold a return value.</span></span> <span data-ttu-id="03b0f-153">Você deve usar a `Return` instrução e deve especificar um valor.</span><span class="sxs-lookup"><span data-stu-id="03b0f-153">You must use the `Return` statement, and it must specify a value.</span></span> <span data-ttu-id="03b0f-154">Qualquer número de `Return` instruções pode aparecer em qualquer lugar no procedimento.</span><span class="sxs-lookup"><span data-stu-id="03b0f-154">Any number of `Return` statements can appear anywhere in the procedure.</span></span>

<span data-ttu-id="03b0f-155">A definição de um operador dessa maneira é chamada de *sobrecarga de operador*, independentemente de você usar ou não a `Overloads` palavra-chave.</span><span class="sxs-lookup"><span data-stu-id="03b0f-155">Defining an operator in this way is called *operator overloading*, whether or not you use the `Overloads` keyword.</span></span> <span data-ttu-id="03b0f-156">A tabela a seguir lista os operadores que você pode definir.</span><span class="sxs-lookup"><span data-stu-id="03b0f-156">The following table lists the operators you can define.</span></span>

|<span data-ttu-id="03b0f-157">Tipo</span><span class="sxs-lookup"><span data-stu-id="03b0f-157">Type</span></span>|<span data-ttu-id="03b0f-158">Operadores</span><span class="sxs-lookup"><span data-stu-id="03b0f-158">Operators</span></span>|
|----------|---------------|
|<span data-ttu-id="03b0f-159">Unário</span><span class="sxs-lookup"><span data-stu-id="03b0f-159">Unary</span></span>|<span data-ttu-id="03b0f-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="03b0f-160">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|
|<span data-ttu-id="03b0f-161">Binário</span><span class="sxs-lookup"><span data-stu-id="03b0f-161">Binary</span></span>|<span data-ttu-id="03b0f-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="03b0f-162">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|
|<span data-ttu-id="03b0f-163">Conversão (unário)</span><span class="sxs-lookup"><span data-stu-id="03b0f-163">Conversion (unary)</span></span>|`CType`|

<span data-ttu-id="03b0f-164">Observe que o operador `=` na lista binária é o operador de comparação, não o operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="03b0f-164">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>

<span data-ttu-id="03b0f-165">Ao definir `CType` o, você deve especificar `Widening` ou `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="03b0f-165">When you define `CType`, you must specify either `Widening` or `Narrowing`.</span></span>

## <a name="matched-pairs"></a><span data-ttu-id="03b0f-166">Pares correspondentes</span><span class="sxs-lookup"><span data-stu-id="03b0f-166">Matched Pairs</span></span>

<span data-ttu-id="03b0f-167">Você deve definir certos operadores como pares correspondentes.</span><span class="sxs-lookup"><span data-stu-id="03b0f-167">You must define certain operators as matched pairs.</span></span> <span data-ttu-id="03b0f-168">Se você definir qualquer um dos dois operadores, também deverá definir o outro.</span><span class="sxs-lookup"><span data-stu-id="03b0f-168">If you define either operator of such a pair, you must define the other as well.</span></span> <span data-ttu-id="03b0f-169">Os pares correspondentes são os seguintes:</span><span class="sxs-lookup"><span data-stu-id="03b0f-169">The matched pairs are the following:</span></span>

- <span data-ttu-id="03b0f-170">`=` e `<>`</span><span class="sxs-lookup"><span data-stu-id="03b0f-170">`=` and `<>`</span></span>

- <span data-ttu-id="03b0f-171">`>` e `<`</span><span class="sxs-lookup"><span data-stu-id="03b0f-171">`>` and `<`</span></span>

- <span data-ttu-id="03b0f-172">`>=` e `<=`</span><span class="sxs-lookup"><span data-stu-id="03b0f-172">`>=` and `<=`</span></span>

- <span data-ttu-id="03b0f-173">`IsTrue` e `IsFalse`</span><span class="sxs-lookup"><span data-stu-id="03b0f-173">`IsTrue` and `IsFalse`</span></span>

## <a name="data-type-restrictions"></a><span data-ttu-id="03b0f-174">Restrições de tipo de dados</span><span class="sxs-lookup"><span data-stu-id="03b0f-174">Data Type Restrictions</span></span>

<span data-ttu-id="03b0f-175">Cada operador que você define deve envolver a classe ou estrutura na qual você o define.</span><span class="sxs-lookup"><span data-stu-id="03b0f-175">Every operator you define must involve the class or structure on which you define it.</span></span> <span data-ttu-id="03b0f-176">Isso significa que a classe ou estrutura deve aparecer como o tipo de dados do seguinte:</span><span class="sxs-lookup"><span data-stu-id="03b0f-176">This means that the class or structure must appear as the data type of the following:</span></span>

- <span data-ttu-id="03b0f-177">O operando de um operador unário.</span><span class="sxs-lookup"><span data-stu-id="03b0f-177">The operand of a unary operator.</span></span>

- <span data-ttu-id="03b0f-178">Pelo menos um dos operandos de um operador binário.</span><span class="sxs-lookup"><span data-stu-id="03b0f-178">At least one of the operands of a binary operator.</span></span>

- <span data-ttu-id="03b0f-179">O operando ou o tipo de retorno de um operador de conversão.</span><span class="sxs-lookup"><span data-stu-id="03b0f-179">Either the operand or the return type of a conversion operator.</span></span>

 <span data-ttu-id="03b0f-180">Determinados operadores têm restrições de tipo de dados adicionais, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="03b0f-180">Certain operators have additional data type restrictions, as follows:</span></span>

- <span data-ttu-id="03b0f-181">Se você definir os `IsTrue` `IsFalse` operadores e, eles deverão retornar o `Boolean` tipo.</span><span class="sxs-lookup"><span data-stu-id="03b0f-181">If you define the `IsTrue` and `IsFalse` operators, they must both return the `Boolean` type.</span></span>

- <span data-ttu-id="03b0f-182">Se você definir os `<<` `>>` operadores e, eles deverão especificar o `Integer` tipo para o `operandtype` de `operand2` .</span><span class="sxs-lookup"><span data-stu-id="03b0f-182">If you define the `<<` and `>>` operators, they must both specify the `Integer` type for the `operandtype` of `operand2`.</span></span>

<span data-ttu-id="03b0f-183">O tipo de retorno não precisa corresponder ao tipo de um dos operandos.</span><span class="sxs-lookup"><span data-stu-id="03b0f-183">The return type does not have to correspond to the type of either operand.</span></span> <span data-ttu-id="03b0f-184">Por exemplo, um operador de comparação como `=` ou `<>` pode retornar `Boolean` mesmo se nenhum operando for `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="03b0f-184">For example, a comparison operator such as `=` or `<>` can return `Boolean` even if neither operand is `Boolean`.</span></span>

## <a name="logical-and-bitwise-operators"></a><span data-ttu-id="03b0f-185">Operadores lógicos e bit a bit</span><span class="sxs-lookup"><span data-stu-id="03b0f-185">Logical and Bitwise Operators</span></span>

<span data-ttu-id="03b0f-186">Os `And` `Or` operadores,, `Not` , e `Xor` podem executar operações lógicas ou bit-a-em Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="03b0f-186">The `And`, `Or`, `Not`, and `Xor` operators can perform either logical or bitwise operations in Visual Basic.</span></span> <span data-ttu-id="03b0f-187">No entanto, se você definir um desses operadores em uma classe ou estrutura, você poderá definir apenas sua operação bit-up.</span><span class="sxs-lookup"><span data-stu-id="03b0f-187">However, if you define one of these operators on a class or structure, you can define only its bitwise operation.</span></span>

<span data-ttu-id="03b0f-188">Você não pode definir o `AndAlso` operador diretamente com uma `Operator` instrução.</span><span class="sxs-lookup"><span data-stu-id="03b0f-188">You cannot define the `AndAlso` operator directly with an `Operator` statement.</span></span> <span data-ttu-id="03b0f-189">No entanto, você pode usar `AndAlso` se tiver atendido às seguintes condições:</span><span class="sxs-lookup"><span data-stu-id="03b0f-189">However, you can use `AndAlso` if you have fulfilled the following conditions:</span></span>

- <span data-ttu-id="03b0f-190">Você definiu `And` os mesmos tipos de operando para os quais deseja usar `AndAlso` .</span><span class="sxs-lookup"><span data-stu-id="03b0f-190">You have defined `And` on the same operand types you want to use for `AndAlso`.</span></span>

- <span data-ttu-id="03b0f-191">Sua definição de `And` retorna o mesmo tipo da classe ou estrutura na qual você o definiu.</span><span class="sxs-lookup"><span data-stu-id="03b0f-191">Your definition of `And` returns the same type as the class or structure on which you have defined it.</span></span>

- <span data-ttu-id="03b0f-192">Você definiu o `IsFalse` operador na classe ou estrutura na qual você definiu `And` .</span><span class="sxs-lookup"><span data-stu-id="03b0f-192">You have defined the `IsFalse` operator on the class or structure on which you have defined `And`.</span></span>

<span data-ttu-id="03b0f-193">Da mesma forma, você pode usar `OrElse` se tiver definido `Or` nos mesmos operandos, com o tipo de retorno da classe ou estrutura, e você tiver definido `IsTrue` na classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="03b0f-193">Similarly, you can use `OrElse` if you have defined `Or` on the same operands, with the return type of the class or structure, and you have defined `IsTrue` on the class or structure.</span></span>

## <a name="widening-and-narrowing-conversions"></a><span data-ttu-id="03b0f-194">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="03b0f-194">Widening and Narrowing Conversions</span></span>

<span data-ttu-id="03b0f-195">Uma *conversão de ampliação* sempre é bem-sucedida em tempo de execução, enquanto uma *conversão de restrição* pode falhar em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="03b0f-195">A *widening conversion* always succeeds at run time, while a *narrowing conversion* can fail at run time.</span></span> <span data-ttu-id="03b0f-196">Para obter mais informações, consulte [Ampliando e restringindo conversões](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="03b0f-196">For more information, see [Widening and Narrowing Conversions](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span>

<span data-ttu-id="03b0f-197">Se você declarar um procedimento de conversão para ser `Widening` , o código do procedimento não deverá gerar nenhuma falha.</span><span class="sxs-lookup"><span data-stu-id="03b0f-197">If you declare a conversion procedure to be `Widening`, your procedure code must not generate any failures.</span></span> <span data-ttu-id="03b0f-198">Isso significa o seguinte:</span><span class="sxs-lookup"><span data-stu-id="03b0f-198">This means the following:</span></span>

- <span data-ttu-id="03b0f-199">Ele sempre deve retornar um valor válido do tipo `type` .</span><span class="sxs-lookup"><span data-stu-id="03b0f-199">It must always return a valid value of type `type`.</span></span>

- <span data-ttu-id="03b0f-200">Ele deve lidar com todas as possíveis exceções e outras condições de erro.</span><span class="sxs-lookup"><span data-stu-id="03b0f-200">It must handle all possible exceptions and other error conditions.</span></span>

- <span data-ttu-id="03b0f-201">Ele deve lidar com qualquer erro retornado de qualquer procedimento chamado por ele.</span><span class="sxs-lookup"><span data-stu-id="03b0f-201">It must handle any error returns from any procedures it calls.</span></span>

<span data-ttu-id="03b0f-202">Se houver alguma possibilidade de que um procedimento de conversão não tenha sucesso ou que possa causar uma exceção sem tratamento, você deverá declará-lo como sendo `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="03b0f-202">If there is any possibility that a conversion procedure might not succeed, or that it might cause an unhandled exception, you must declare it to be `Narrowing`.</span></span>

## <a name="example"></a><span data-ttu-id="03b0f-203">Exemplo</span><span class="sxs-lookup"><span data-stu-id="03b0f-203">Example</span></span>

<span data-ttu-id="03b0f-204">O exemplo de código a seguir usa a `Operator` instrução para definir o contorno de uma estrutura que inclui procedimentos de operador para os `And` `Or` operadores,, `IsFalse` e `IsTrue` .</span><span class="sxs-lookup"><span data-stu-id="03b0f-204">The following code example uses the `Operator` statement to define the outline of a structure that includes operator procedures for the `And`, `Or`, `IsFalse`, and `IsTrue` operators.</span></span> <span data-ttu-id="03b0f-205">`And`e `Or` cada um tem dois operandos do tipo `abc` e do tipo de retorno `abc` .</span><span class="sxs-lookup"><span data-stu-id="03b0f-205">`And` and `Or` each take two operands of type `abc` and return type `abc`.</span></span> <span data-ttu-id="03b0f-206">`IsFalse`e `IsTrue` cada um tem um único operando do tipo `abc` e do retorno `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="03b0f-206">`IsFalse` and `IsTrue` each take a single operand of type `abc` and return `Boolean`.</span></span> <span data-ttu-id="03b0f-207">Essas definições permitem que o código de chamada use `And` ,, `AndAlso` `Or` e `OrElse` com operandos do tipo `abc` .</span><span class="sxs-lookup"><span data-stu-id="03b0f-207">These definitions allow the calling code to use `And`, `AndAlso`, `Or`, and `OrElse` with operands of type `abc`.</span></span>

[!code-vb[VbVbalrStatements#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#44)]

## <a name="see-also"></a><span data-ttu-id="03b0f-208">Confira também</span><span class="sxs-lookup"><span data-stu-id="03b0f-208">See also</span></span>

- [<span data-ttu-id="03b0f-209">Operador IsFalse</span><span class="sxs-lookup"><span data-stu-id="03b0f-209">IsFalse Operator</span></span>](../operators/isfalse-operator.md)
- [<span data-ttu-id="03b0f-210">Operador IsTrue</span><span class="sxs-lookup"><span data-stu-id="03b0f-210">IsTrue Operator</span></span>](../operators/istrue-operator.md)
- [<span data-ttu-id="03b0f-211">Widening</span><span class="sxs-lookup"><span data-stu-id="03b0f-211">Widening</span></span>](../modifiers/widening.md)
- [<span data-ttu-id="03b0f-212">Narrowing</span><span class="sxs-lookup"><span data-stu-id="03b0f-212">Narrowing</span></span>](../modifiers/narrowing.md)
- [<span data-ttu-id="03b0f-213">Conversões de Widening e Narrowing</span><span class="sxs-lookup"><span data-stu-id="03b0f-213">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="03b0f-214">Procedimentos do operador</span><span class="sxs-lookup"><span data-stu-id="03b0f-214">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="03b0f-215">Como definir um operador</span><span class="sxs-lookup"><span data-stu-id="03b0f-215">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="03b0f-216">Como definir um operador de conversão</span><span class="sxs-lookup"><span data-stu-id="03b0f-216">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="03b0f-217">Como chamar um procedimento de operador</span><span class="sxs-lookup"><span data-stu-id="03b0f-217">How to: Call an Operator Procedure</span></span>](../../programming-guide/language-features/procedures/how-to-call-an-operator-procedure.md)
- [<span data-ttu-id="03b0f-218">Como usar uma classe que define operadores</span><span class="sxs-lookup"><span data-stu-id="03b0f-218">How to: Use a Class that Defines Operators</span></span>](../../programming-guide/language-features/procedures/how-to-use-a-class-that-defines-operators.md)
