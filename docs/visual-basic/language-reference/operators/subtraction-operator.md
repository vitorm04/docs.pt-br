---
title: '- Operador'
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
ms.openlocfilehash: 9687c366c5b23693c05ab5c6b34f50c04131dfda
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348218"
---
# <a name="--operator-visual-basic"></a><span data-ttu-id="80ec4-102">Operador - (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80ec4-102">- Operator (Visual Basic)</span></span>
<span data-ttu-id="80ec4-103">Retorna a diferença entre duas expressões numéricas ou o valor negativo de uma expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="80ec4-103">Returns the difference between two numeric expressions or the negative value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80ec4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="80ec4-104">Syntax</span></span>  
  
```vb  
expression1 – expression2
```
  
<span data-ttu-id="80ec4-105">ou</span><span class="sxs-lookup"><span data-stu-id="80ec4-105">or</span></span>

```vb  
–expression1  
```  
  
## <a name="parts"></a><span data-ttu-id="80ec4-106">Partes</span><span class="sxs-lookup"><span data-stu-id="80ec4-106">Parts</span></span>  
 `expression1`  
 <span data-ttu-id="80ec4-107">Necessário.</span><span class="sxs-lookup"><span data-stu-id="80ec4-107">Required.</span></span> <span data-ttu-id="80ec4-108">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="80ec4-108">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="80ec4-109">Necessário, a menos que o operador de `–` esteja calculando um valor negativo.</span><span class="sxs-lookup"><span data-stu-id="80ec4-109">Required unless the `–` operator is calculating a negative value.</span></span> <span data-ttu-id="80ec4-110">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="80ec4-110">Any numeric expression.</span></span>  
  
## <a name="result"></a><span data-ttu-id="80ec4-111">Resultado</span><span class="sxs-lookup"><span data-stu-id="80ec4-111">Result</span></span>  
 <span data-ttu-id="80ec4-112">O resultado é a diferença entre `expression1` e `expression2`ou o valor negado de `expression1`.</span><span class="sxs-lookup"><span data-stu-id="80ec4-112">The result is the difference between `expression1` and `expression2`, or the negated value of `expression1`.</span></span>  
  
 <span data-ttu-id="80ec4-113">O tipo de dados de resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2`.</span><span class="sxs-lookup"><span data-stu-id="80ec4-113">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="80ec4-114">Consulte as tabelas "aritmética de inteiros" em [tipos de dados de resultados do operador](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="80ec4-114">See the "Integer Arithmetic" tables in [Data Types of Operator Results](../../../visual-basic/language-reference/operators/data-types-of-operator-results.md).</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="80ec4-115">Tipos com suporte</span><span class="sxs-lookup"><span data-stu-id="80ec4-115">Supported Types</span></span>  
 <span data-ttu-id="80ec4-116">Todos os tipos numéricos.</span><span class="sxs-lookup"><span data-stu-id="80ec4-116">All numeric types.</span></span> <span data-ttu-id="80ec4-117">Isso inclui os tipos de ponto flutuante e não assinados e `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="80ec4-117">This includes the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80ec4-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="80ec4-118">Remarks</span></span>  
 <span data-ttu-id="80ec4-119">No primeiro uso mostrado na sintaxe mostrada anteriormente, o operador de `–` é o operador de subtração de aritmética *binária* para a diferença entre duas expressões numéricas.</span><span class="sxs-lookup"><span data-stu-id="80ec4-119">In the first usage shown in the syntax shown previously, the `–` operator is the *binary* arithmetic subtraction operator for the difference between two numeric expressions.</span></span>  
  
 <span data-ttu-id="80ec4-120">No segundo uso mostrado na sintaxe mostrada anteriormente, o operador de `–` é o operador de negação *unário* para o valor negativo de uma expressão.</span><span class="sxs-lookup"><span data-stu-id="80ec4-120">In the second usage shown in the syntax shown previously, the `–` operator is the *unary* negation operator for the negative value of an expression.</span></span> <span data-ttu-id="80ec4-121">Nesse sentido, a negação consiste em reverter o sinal de `expression1` para que o resultado seja positivo se `expression1` for negativo.</span><span class="sxs-lookup"><span data-stu-id="80ec4-121">In this sense, the negation consists of reversing the sign of `expression1` so that the result is positive if `expression1` is negative.</span></span>  
  
 <span data-ttu-id="80ec4-122">Se qualquer expressão for avaliada como [Nothing](../../../visual-basic/language-reference/nothing.md), o operador de `–` a tratará como zero.</span><span class="sxs-lookup"><span data-stu-id="80ec4-122">If either expression evaluates to [Nothing](../../../visual-basic/language-reference/nothing.md), the `–` operator treats it as zero.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80ec4-123">O operador `–` pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="80ec4-123">The `–` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="80ec4-124">Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de que você entendeu seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="80ec4-124">If your code uses this operator on such a class or structure, make sure that you understand its redefined behavior.</span></span> <span data-ttu-id="80ec4-125">Para obter mais informações, consulte [procedimentos de operador](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="80ec4-125">For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="80ec4-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="80ec4-126">Example</span></span>  
 <span data-ttu-id="80ec4-127">O exemplo a seguir usa o operador `–` para calcular e retornar a diferença entre dois números e, em seguida, para negar um número.</span><span class="sxs-lookup"><span data-stu-id="80ec4-127">The following example uses the `–` operator to calculate and return the difference between two numbers, and then to negate a number.</span></span>  
  
 [!code-vb[VbVbalrOperators#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#10)]  
  
 <span data-ttu-id="80ec4-128">Após a execução dessas instruções, `binaryResult` contém 124,45 e `unaryResult` contém – 334,90.</span><span class="sxs-lookup"><span data-stu-id="80ec4-128">Following the execution of these statements, `binaryResult` contains 124.45 and `unaryResult` contains –334.90.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80ec4-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="80ec4-129">See also</span></span>

- [<span data-ttu-id="80ec4-130">-= Operador (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="80ec4-130">-= Operator (Visual Basic)</span></span>](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [<span data-ttu-id="80ec4-131">Operadores Aritméticos</span><span class="sxs-lookup"><span data-stu-id="80ec4-131">Arithmetic Operators</span></span>](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [<span data-ttu-id="80ec4-132">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="80ec4-132">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="80ec4-133">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="80ec4-133">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="80ec4-134">Operadores aritméticos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="80ec4-134">Arithmetic Operators in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
