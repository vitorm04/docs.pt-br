---
title: '- Operador (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.Negate
- vb.-
helpviewer_keywords:
- operator [Visual Basic]
- operators [Visual Basic], subtraction
- operators [Visual Basic], difference
- negation operator [Visual Basic]
- operators [Visual Basic], arithmetic
- subtraction operator [Visual Basic], syntax
- arithmetic operators [Visual Basic], subtraction
- difference operator [Visual Basic]
- math operators [Visual Basic]
- operators [Visual Basic], negation
- minus operator [Visual Basic]
ms.assetid: bff2c368-662d-4c92-ac87-1d9bdfd3426a
ms.openlocfilehash: 1a5c47a2f1bc8a8b9e1b0263b90006a0e58e17bb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58830663"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="5f3d3-102">Operador - (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f3d3-102">- Operator (Visual Basic)</span></span>
<span data-ttu-id="5f3d3-103">Retorna a diferença entre duas expressões numéricas ou o valor negativo de uma expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="5f3d3-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f3d3-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f3d3-104">Syntax</span></span>  
  
```  
      expression1 – expression2  
- or -  
– expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="5f3d3-105">Partes</span><span class="sxs-lookup"><span data-stu-id="5f3d3-105">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="5f3d3-106">Necessário.</span><span class="sxs-lookup"><span data-stu-id="5f3d3-106">Required.</span></span> <span data-ttu-id="5f3d3-107">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="5f3d3-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="5f3d3-108">Necessário a menos que o `–` operador está calculando um valor negativo.</span><span class="sxs-lookup"><span data-stu-id="5f3d3-108">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="5f3d3-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="5f3d3-109">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="5f3d3-110">Resultado</span><span class="sxs-lookup"><span data-stu-id="5f3d3-110">Result</span></span>  
 <span data-ttu-id="5f3d3-111">O resultado é a diferença entre `expression1` e `expression2`, ou o valor negado da `expression1`.</span><span class="sxs-lookup"><span data-stu-id="5f3d3-111">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="5f3d3-112">O tipo de dados do resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`.</span><span class="sxs-lookup"><span data-stu-id="5f3d3-112">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="5f3d3-113">Consulte as tabelas "Aritmética de inteiros" [tipos de dados de resultados de operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="5f3d3-113">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="5f3d3-114">Tipos com suporte</span><span class="sxs-lookup"><span data-stu-id="5f3d3-114">Supported Types</span></span>  
 <span data-ttu-id="5f3d3-115">Todos os tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="5f3d3-115">All numeric types.</span></span> <span data-ttu-id="5f3d3-116">Isso inclui os tipos de ponto flutuantes e não assinados e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="5f3d3-116">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f3d3-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="5f3d3-117">Remarks</span></span>  
 <span data-ttu-id="5f3d3-118">No primeiro uso mostrado na sintaxe mostrada anteriormente, o `–` operador é a *binário* operador de subtração aritmético para a diferença entre duas expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="5f3d3-118">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="5f3d3-119">No segundo uso mostrado a sintaxe mostrada anteriormente, o `–` operador é a *unário* operador de negação para o valor negativo de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="5f3d3-119">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="5f3d3-120">Nesse sentido, a negação consiste em Reverter o sinal do `expression1` para que o resultado será positivo se `expression1` é negativo.</span><span class="sxs-lookup"><span data-stu-id="5f3d3-120">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="5f3d3-121">Se qualquer expressão for avaliada como [nada](../../../visual-basic/language-reference/nothing.md), o `–` operador tratará como zero.</span><span class="sxs-lookup"><span data-stu-id="5f3d3-121">If either expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f3d3-122">O `–` operador pode ser *sobrecarregado*, que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo de classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="5f3d3-122">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="5f3d3-123">Se seu código usa esse operador em uma classe ou estrutura, certifique-se de que você entende seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="5f3d3-123">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="5f3d3-124">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="5f3d3-124">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f3d3-125">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5f3d3-125">Example</span></span>  
 <span data-ttu-id="5f3d3-126">O exemplo a seguir usa o `–` operador para calcular e retornar a diferença entre dois números e, em seguida, para negar a um número.</span><span class="sxs-lookup"><span data-stu-id="5f3d3-126">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 <span data-ttu-id="5f3d3-127">Após a execução dessas instruções `binaryResult` contém 124.45 e `unaryResult` contém –334.90.</span><span class="sxs-lookup"><span data-stu-id="5f3d3-127">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f3d3-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f3d3-128">See also</span></span>

- [<span data-ttu-id="5f3d3-129">-= Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5f3d3-129">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="5f3d3-130">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="5f3d3-130">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="5f3d3-131">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5f3d3-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="5f3d3-132">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="5f3d3-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="5f3d3-133">Operadores aritméticos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5f3d3-133">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
