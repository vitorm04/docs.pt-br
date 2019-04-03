---
title: Operador += (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.+=
helpviewer_keywords:
- += operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- += operator [Visual Basic], appending strings
- compound assignment statements [Visual Basic]
ms.assetid: d3e959f4-85d4-4e47-87c4-77b62335a5b3
ms.openlocfilehash: 4b8f36397d0f52866ebe9fa188d6b163364aeffc
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58838988"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="42c7e-102">Operador += (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="42c7e-102">+= Operator (Visual Basic)</span></span>
<span data-ttu-id="42c7e-103">Adiciona o valor de uma expressão numérica para o valor de uma variável numérica ou propriedade e atribui o resultado à variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="42c7e-103">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="42c7e-104">Também pode ser usado para concatenar um `String` expressão para um `String` variável ou propriedade e atribui o resultado à variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="42c7e-104">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42c7e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="42c7e-105">Syntax</span></span>  
  
```  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="42c7e-106">Partes</span><span class="sxs-lookup"><span data-stu-id="42c7e-106">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="42c7e-107">Necessário.</span><span class="sxs-lookup"><span data-stu-id="42c7e-107">Required.</span></span> <span data-ttu-id="42c7e-108">Qualquer numérico ou `String` variável ou propriedade.</span><span class="sxs-lookup"><span data-stu-id="42c7e-108">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="42c7e-109">Necessário.</span><span class="sxs-lookup"><span data-stu-id="42c7e-109">Required.</span></span> <span data-ttu-id="42c7e-110">Qualquer numérico ou `String` expressão.</span><span class="sxs-lookup"><span data-stu-id="42c7e-110">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42c7e-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="42c7e-111">Remarks</span></span>  
 <span data-ttu-id="42c7e-112">O elemento no lado esquerdo do `+=` operador pode ser uma variável escalar simple, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="42c7e-112">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="42c7e-113">A variável ou propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="42c7e-113">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="42c7e-114">O `+=` operador adiciona o valor à sua direita à variável ou propriedade à sua esquerda e atribui o resultado à variável ou propriedade à sua esquerda.</span><span class="sxs-lookup"><span data-stu-id="42c7e-114">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="42c7e-115">O `+=` operador também pode ser usado para concatenar os `String` expressão à sua direita o `String` variável ou propriedade à sua esquerda e atribui o resultado à variável ou propriedade à sua esquerda.</span><span class="sxs-lookup"><span data-stu-id="42c7e-115">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="42c7e-116">Quando você usa o `+=` operador, você não pode ser capaz de determinar se a adição ou a cadeia de caracteres de concatenação ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="42c7e-116">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="42c7e-117">Use o `&=` operador de concatenação para eliminar a ambiguidade e fornecer o código autodocumentado.</span><span class="sxs-lookup"><span data-stu-id="42c7e-117">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="42c7e-118">Esse operador de atribuição implicitamente executa, mas não conversões de estreitamento se o ambiente de compilação impõe semântica estrita de ampliação.</span><span class="sxs-lookup"><span data-stu-id="42c7e-118">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="42c7e-119">Para obter mais informações sobre essas conversões, consulte [ampliando e restringindo conversões](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="42c7e-119">For more information on these conversions, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="42c7e-120">Para obter mais informações sobre a semântica estrita e permissiva, consulte [instrução Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="42c7e-120">For more information on strict and permissive semantics, see [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="42c7e-121">Se semântica permissiva é permitida, o `+=` operador executa implicitamente uma variedade de conversões de cadeia de caracteres e numéricos idênticas àqueles executados pelo `+` operador.</span><span class="sxs-lookup"><span data-stu-id="42c7e-121">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="42c7e-122">Para obter detalhes sobre essas conversões, consulte [operador +](../../../visual-basic/language-reference/operators/addition-operator.md).</span><span class="sxs-lookup"><span data-stu-id="42c7e-122">For details on these conversions, see [+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="42c7e-123">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="42c7e-123">Overloading</span></span>  
 <span data-ttu-id="42c7e-124">O `+` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="42c7e-124">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="42c7e-125">Sobrecarregando o `+` operador afeta o comportamento do `+=` operador.</span><span class="sxs-lookup"><span data-stu-id="42c7e-125">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="42c7e-126">Se seu código usa `+=` em uma classe ou estrutura que sobrecarrega `+`, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="42c7e-126">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="42c7e-127">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="42c7e-127">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="42c7e-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="42c7e-128">Example</span></span>  
 <span data-ttu-id="42c7e-129">O exemplo a seguir usa o `+=` operador para combinar o valor de uma variável com outra.</span><span class="sxs-lookup"><span data-stu-id="42c7e-129">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="42c7e-130">A primeira parte usa `+=` com variáveis numéricas para adicionar um valor para outro.</span><span class="sxs-lookup"><span data-stu-id="42c7e-130">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="42c7e-131">A segunda usa `+=` com `String` variáveis para concatenar um valor com outro.</span><span class="sxs-lookup"><span data-stu-id="42c7e-131">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="42c7e-132">Em ambos os casos, o resultado é atribuído à primeira variável.</span><span class="sxs-lookup"><span data-stu-id="42c7e-132">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 <span data-ttu-id="42c7e-133">O valor de `num1` agora é 13 e o valor de `str1` agora é "103".</span><span class="sxs-lookup"><span data-stu-id="42c7e-133">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42c7e-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42c7e-134">See also</span></span>

- [<span data-ttu-id="42c7e-135">Operador +</span><span class="sxs-lookup"><span data-stu-id="42c7e-135">+ Operator</span></span>](../../../visual-basic/language-reference/operators/addition-operator.md)
- [<span data-ttu-id="42c7e-136">Operadores de Atribuição</span><span class="sxs-lookup"><span data-stu-id="42c7e-136">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="42c7e-137">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="42c7e-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="42c7e-138">Operadores de Concatenação</span><span class="sxs-lookup"><span data-stu-id="42c7e-138">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="42c7e-139">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="42c7e-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="42c7e-140">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="42c7e-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="42c7e-141">Instruções</span><span class="sxs-lookup"><span data-stu-id="42c7e-141">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
