---
title: '- Operador (Visual Basic) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Negate
- vb.-
dev_langs:
- VB
helpviewer_keywords:
- '- operator [Visual Basic]'
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator
- operators [Visual Basic], arithmetic
- subtraction operator, syntax
- arithmetic operators, subtraction
- difference operator
- math operators
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
caps.latest.revision: 14
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
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: eb9b8e94877cce9aacde69c5f555f4a7f4a9ad7c
ms.contentlocale: pt-br
ms.lasthandoff: 05/23/2017

---
# <a name="--operator-visual-basic"></a><span data-ttu-id="a210e-102">Operador - (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a210e-102">- Operator (Visual Basic)</span></span>
<span data-ttu-id="a210e-103">Retorna a diferença entre duas expressões numéricas ou o valor negativo de uma expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="a210e-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a210e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a210e-104">Syntax</span></span>  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="a210e-105">Partes</span><span class="sxs-lookup"><span data-stu-id="a210e-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="a210e-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="a210e-106">Required.</span></span> <span data-ttu-id="a210e-107">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="a210e-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="a210e-108">Necessário a menos que o `–` operador está calculando um valor negativo.</span><span class="sxs-lookup"><span data-stu-id="a210e-108">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="a210e-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="a210e-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="a210e-110">Resultado</span><span class="sxs-lookup"><span data-stu-id="a210e-110">Result</span></span>  
 <span data-ttu-id="a210e-111">O resultado é a diferença entre `expression1` e `expression2`, ou o valor negado do `expression1`.</span><span class="sxs-lookup"><span data-stu-id="a210e-111">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="a210e-112">O tipo de dados do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`.</span><span class="sxs-lookup"><span data-stu-id="a210e-112">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="a210e-113">Consulte as tabelas de "Aritmética de inteiros" em [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="a210e-113">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="a210e-114">Tipos com suporte</span><span class="sxs-lookup"><span data-stu-id="a210e-114">Supported Types</span></span>  
 <span data-ttu-id="a210e-115">Todos os tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="a210e-115">All numeric types.</span></span> <span data-ttu-id="a210e-116">Isso inclui os tipos de ponto flutuantes e não assinados e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="a210e-116">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a210e-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="a210e-117">Remarks</span></span>  
 <span data-ttu-id="a210e-118">No primeiro uso mostrado a sintaxe mostrada anteriormente, o `–` operador é a *binário* operador de subtração aritmético para a diferença entre duas expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="a210e-118">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="a210e-119">No segundo uso mostrado a sintaxe mostrada anteriormente, o `–` operador é a *unário* operador de negação para o valor negativo de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="a210e-119">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="a210e-120">Nesse sentido, a negação consiste em Reverter o sinal do `expression1` para que o resultado será positivo se `expression1` for negativo.</span><span class="sxs-lookup"><span data-stu-id="a210e-120">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="a210e-121">Se qualquer expressão for avaliada como [nada](../../../visual-basic/language-reference/nothing.md), o `–` operador tratá-la como zero.</span><span class="sxs-lookup"><span data-stu-id="a210e-121">If either expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a210e-122">O `–` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="a210e-122">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="a210e-123">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="a210e-123">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="a210e-124">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="a210e-124">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a210e-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a210e-125">Example</span></span>  
 <span data-ttu-id="a210e-126">O exemplo a seguir usa o `–` operador para calcular e retornar a diferença entre dois números e para negar um número.</span><span class="sxs-lookup"><span data-stu-id="a210e-126">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 <span data-ttu-id="a210e-127">[!code-vb[VbVbalrOperators n º&10;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="a210e-127">[!code-vb[VbVbalrOperators#10](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/subtraction-operator_1.vb)]</span></span>  
  
 <span data-ttu-id="a210e-128">Após a execução dessas instruções `binaryResult` contém 124.45 e `unaryResult` contém –334.90.</span><span class="sxs-lookup"><span data-stu-id="a210e-128">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a210e-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a210e-129">See Also</span></span>  
 <span data-ttu-id="a210e-130">[-= Operador (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
 [operadores aritméticos](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span><span class="sxs-lookup"><span data-stu-id="a210e-130">[-= Operator (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
 [Arithmetic Operators](../../../visual-basic/language-reference/operators/arithmetic-operators.md) </span></span>  
<span data-ttu-id="a210e-131"> [Precedência do operador no Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span><span class="sxs-lookup"><span data-stu-id="a210e-131"> [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md) </span></span>  
<span data-ttu-id="a210e-132"> [Operadores listados por funcionalidade](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span><span class="sxs-lookup"><span data-stu-id="a210e-132"> [Operators Listed by Functionality](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md) </span></span>  
<span data-ttu-id="a210e-133"> [Operadores aritméticos em Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)</span><span class="sxs-lookup"><span data-stu-id="a210e-133"> [Arithmetic Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)</span></span>

