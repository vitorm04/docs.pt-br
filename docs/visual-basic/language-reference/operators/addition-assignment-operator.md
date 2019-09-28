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
ms.openlocfilehash: 249a19abfb08677c01ac4cc484d049a7ed1a983c
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591642"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="2075b-102">Operador += (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2075b-102">+= Operator (Visual Basic)</span></span>
<span data-ttu-id="2075b-103">Adiciona o valor de uma expressão numérica ao valor de uma variável numérica ou propriedade e atribui o resultado à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="2075b-103">Adds the value of a numeric expression to the value of a numeric variable or property and assigns the result to the variable or property.</span></span> <span data-ttu-id="2075b-104">Também pode ser usado para concatenar uma expressão `String` a uma variável ou Propriedade `String` e atribuir o resultado à variável ou à propriedade.</span><span class="sxs-lookup"><span data-stu-id="2075b-104">Can also be used to concatenate a `String` expression to a `String` variable or property and assign the result to the variable or property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2075b-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2075b-105">Syntax</span></span>  
  
```vb  
variableorproperty += expression  
```  
  
## <a name="parts"></a><span data-ttu-id="2075b-106">Partes</span><span class="sxs-lookup"><span data-stu-id="2075b-106">Parts</span></span>  
 `variableorproperty`  
 <span data-ttu-id="2075b-107">Necessário.</span><span class="sxs-lookup"><span data-stu-id="2075b-107">Required.</span></span> <span data-ttu-id="2075b-108">Qualquer variável ou propriedade numérica ou `String`.</span><span class="sxs-lookup"><span data-stu-id="2075b-108">Any numeric or `String` variable or property.</span></span>  
  
 `expression`  
 <span data-ttu-id="2075b-109">Necessário.</span><span class="sxs-lookup"><span data-stu-id="2075b-109">Required.</span></span> <span data-ttu-id="2075b-110">Qualquer expressão numérica ou `String`.</span><span class="sxs-lookup"><span data-stu-id="2075b-110">Any numeric or `String` expression.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2075b-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="2075b-111">Remarks</span></span>  
 <span data-ttu-id="2075b-112">O elemento no lado esquerdo do operador `+=` pode ser uma variável escalar simples, uma propriedade ou um elemento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="2075b-112">The element on the left side of the `+=` operator can be a simple scalar variable, a property, or an element of an array.</span></span> <span data-ttu-id="2075b-113">A variável ou a propriedade não pode ser [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span><span class="sxs-lookup"><span data-stu-id="2075b-113">The variable or property cannot be [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md).</span></span>  
  
 <span data-ttu-id="2075b-114">O operador `+=` adiciona o valor à sua direita à variável ou à propriedade à esquerda e atribui o resultado à variável ou à propriedade à esquerda.</span><span class="sxs-lookup"><span data-stu-id="2075b-114">The `+=` operator adds the value on its right to the variable or property on its left, and assigns the result to the variable or property on its left.</span></span> <span data-ttu-id="2075b-115">O operador `+=` também pode ser usado para concatenar a expressão `String` à direita para a variável ou a propriedade `String` à esquerda e atribuir o resultado à variável ou à propriedade à esquerda.</span><span class="sxs-lookup"><span data-stu-id="2075b-115">The `+=` operator can also be used to concatenate the `String` expression on its right to the `String` variable or property on its left, and assign the result to the variable or property on its left.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2075b-116">Ao usar o operador `+=` , talvez você não consiga determinar se a adição ou a concatenação de cadeia de caracteres ocorrerá.</span><span class="sxs-lookup"><span data-stu-id="2075b-116">When you use the `+=` operator, you might not be able to determine whether addition or string concatenation will occur.</span></span> <span data-ttu-id="2075b-117">Use o `&=` operador para concatenação para eliminar ambigüidade e fornecer código de autodocumentação.</span><span class="sxs-lookup"><span data-stu-id="2075b-117">Use the `&=` operator for concatenation to eliminate ambiguity and to provide self-documenting code.</span></span>  
  
 <span data-ttu-id="2075b-118">Esse operador de atribuição executa implicitamente as conversões de alargamento, mas não de estreitamento se o ambiente de compilação impõe semântica estrita.</span><span class="sxs-lookup"><span data-stu-id="2075b-118">This assignment operator implicitly performs widening but not narrowing conversions if the compilation environment enforces strict semantics.</span></span> <span data-ttu-id="2075b-119">Para obter mais informações sobre essas conversões, consulte [conversões de alargamento e estreitamento](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span><span class="sxs-lookup"><span data-stu-id="2075b-119">For more information on these conversions, see [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md).</span></span> <span data-ttu-id="2075b-120">Para obter mais informações sobre semântica estrita e permissiva, consulte [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2075b-120">For more information on strict and permissive semantics, see [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md).</span></span>  
  
 <span data-ttu-id="2075b-121">Se forem permitidas semânticas permissivas, o operador `+=` implicitamente executará uma variedade de conversões numéricas e de cadeia de caracteres idênticas àquelas executadas pelo operador `+`.</span><span class="sxs-lookup"><span data-stu-id="2075b-121">If permissive semantics are allowed, the `+=` operator implicitly performs a variety of string and numeric conversions identical to those performed by the `+` operator.</span></span> <span data-ttu-id="2075b-122">Para obter detalhes sobre essas conversões, consulte [operador +](../../../visual-basic/language-reference/operators/addition-operator.md).</span><span class="sxs-lookup"><span data-stu-id="2075b-122">For details on these conversions, see [+ Operator](../../../visual-basic/language-reference/operators/addition-operator.md).</span></span>  
  
## <a name="overloading"></a><span data-ttu-id="2075b-123">Sobrecarga</span><span class="sxs-lookup"><span data-stu-id="2075b-123">Overloading</span></span>  
 <span data-ttu-id="2075b-124">O operador `+` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="2075b-124">The `+` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="2075b-125">Sobrecarregar o operador `+` afeta o comportamento do operador `+=`.</span><span class="sxs-lookup"><span data-stu-id="2075b-125">Overloading the `+` operator affects the behavior of the `+=` operator.</span></span> <span data-ttu-id="2075b-126">Se seu código usar `+=` em uma classe ou estrutura que sobrecarrega `+`, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="2075b-126">If your code uses `+=` on a class or structure that overloads `+`, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="2075b-127">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="2075b-127">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2075b-128">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2075b-128">Example</span></span>  
 <span data-ttu-id="2075b-129">O exemplo a seguir usa o operador `+=` para combinar o valor de uma variável com outra.</span><span class="sxs-lookup"><span data-stu-id="2075b-129">The following example uses the `+=` operator to combine the value of one variable with another.</span></span> <span data-ttu-id="2075b-130">A primeira parte usa `+=` com variáveis numéricas para adicionar um valor a outro.</span><span class="sxs-lookup"><span data-stu-id="2075b-130">The first part uses `+=` with numeric variables to add one value to another.</span></span> <span data-ttu-id="2075b-131">A segunda parte usa `+=` com variáveis `String` para concatenar um valor com outro.</span><span class="sxs-lookup"><span data-stu-id="2075b-131">The second part uses `+=` with `String` variables to concatenate one value with another.</span></span> <span data-ttu-id="2075b-132">Em ambos os casos, o resultado é atribuído à primeira variável.</span><span class="sxs-lookup"><span data-stu-id="2075b-132">In both cases, the result is assigned to the first variable.</span></span>  
  
 [!code-vb[VbVbalrOperators#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#7)]  
  
 [!code-vb[VbVbalrOperators#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#8)]  
  
 <span data-ttu-id="2075b-133">O valor de `num1` agora é 13 e o valor de `str1` agora é "103".</span><span class="sxs-lookup"><span data-stu-id="2075b-133">The value of `num1` is now 13, and the value of `str1` is now "103".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2075b-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2075b-134">See also</span></span>

- [<span data-ttu-id="2075b-135">Operador +</span><span class="sxs-lookup"><span data-stu-id="2075b-135">+ Operator</span></span>](../../../visual-basic/language-reference/operators/addition-operator.md)
- [<span data-ttu-id="2075b-136">Operadores de Atribuição</span><span class="sxs-lookup"><span data-stu-id="2075b-136">Assignment Operators</span></span>](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [<span data-ttu-id="2075b-137">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="2075b-137">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="2075b-138">Operadores de Concatenação</span><span class="sxs-lookup"><span data-stu-id="2075b-138">Concatenation Operators</span></span>](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [<span data-ttu-id="2075b-139">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2075b-139">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="2075b-140">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="2075b-140">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="2075b-141">Instruções</span><span class="sxs-lookup"><span data-stu-id="2075b-141">Statements</span></span>](../../../visual-basic/programming-guide/language-features/statements.md)
