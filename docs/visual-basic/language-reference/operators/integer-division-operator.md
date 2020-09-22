---
title: Operador \
ms.date: 07/20/2015
f1_keywords:
- vb.\
- '\'
helpviewer_keywords:
- division operator [Visual Basic], integer
- integer division operator [Visual Basic]
- zero, division by zero
- arithmetic operators [Visual Basic], division
- division [Visual Basic], by zero
- backslash (\) [Visual Basic]
- '\ operator [Visual Basic]'
- integer quotient
- math operators [Visual Basic]
- quotients, integer
- truncation [Visual Basic], integer division
ms.assetid: 4b0ee347-950c-45c9-8e23-54bc85df208e
ms.openlocfilehash: cf2dc66532925d56cea6fd141f44a245bc2dd8dd
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873391"
---
# <a name="-operator-visual-basic"></a><span data-ttu-id="cfab5-102">Operador \ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cfab5-102">\ Operator (Visual Basic)</span></span>

<span data-ttu-id="cfab5-103">Divide dois números e retorna um resultado de número inteiro.</span><span class="sxs-lookup"><span data-stu-id="cfab5-103">Divides two numbers and returns an integer result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfab5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cfab5-104">Syntax</span></span>  
  
```vb  
expression1 \ expression2  
```  
  
## <a name="parts"></a><span data-ttu-id="cfab5-105">Partes</span><span class="sxs-lookup"><span data-stu-id="cfab5-105">Parts</span></span>  

 `expression1`  
 <span data-ttu-id="cfab5-106">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="cfab5-106">Required.</span></span> <span data-ttu-id="cfab5-107">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="cfab5-107">Any numeric expression.</span></span>  
  
 `expression2`  
 <span data-ttu-id="cfab5-108">Obrigatórios.</span><span class="sxs-lookup"><span data-stu-id="cfab5-108">Required.</span></span> <span data-ttu-id="cfab5-109">Qualquer expressão numérica.</span><span class="sxs-lookup"><span data-stu-id="cfab5-109">Any numeric expression.</span></span>  
  
## <a name="supported-types"></a><span data-ttu-id="cfab5-110">Tipos com suporte</span><span class="sxs-lookup"><span data-stu-id="cfab5-110">Supported Types</span></span>  

 <span data-ttu-id="cfab5-111">Todos os tipos numéricos, incluindo os tipos de ponto flutuante e não assinados e `Decimal` .</span><span class="sxs-lookup"><span data-stu-id="cfab5-111">All numeric types, including the unsigned and floating-point types and `Decimal`.</span></span>  
  
## <a name="result"></a><span data-ttu-id="cfab5-112">Resultado</span><span class="sxs-lookup"><span data-stu-id="cfab5-112">Result</span></span>  

 <span data-ttu-id="cfab5-113">O resultado é o quociente inteiro de `expression1` dividido por `expression2` , que descarta qualquer restante e retém apenas a parte inteira.</span><span class="sxs-lookup"><span data-stu-id="cfab5-113">The result is the integer quotient of `expression1` divided by `expression2`, which discards any remainder and retains only the integer portion.</span></span> <span data-ttu-id="cfab5-114">Isso é conhecido como *truncamento*.</span><span class="sxs-lookup"><span data-stu-id="cfab5-114">This is known as *truncation*.</span></span>  
  
 <span data-ttu-id="cfab5-115">O tipo de dados de resultado é um tipo numérico apropriado para os tipos de dados de `expression1` e `expression2` .</span><span class="sxs-lookup"><span data-stu-id="cfab5-115">The result data type is a numeric type appropriate for the data types of `expression1` and `expression2`.</span></span> <span data-ttu-id="cfab5-116">Consulte as tabelas "aritmética de inteiros" em [tipos de dados de resultados do operador](data-types-of-operator-results.md).</span><span class="sxs-lookup"><span data-stu-id="cfab5-116">See the "Integer Arithmetic" tables in [Data Types of Operator Results](data-types-of-operator-results.md).</span></span>  
  
 <span data-ttu-id="cfab5-117">O [operador/(Visual Basic)](floating-point-division-operator.md) retorna o quociente completo, que retém o restante na parte fracionária.</span><span class="sxs-lookup"><span data-stu-id="cfab5-117">The [/ Operator (Visual Basic)](floating-point-division-operator.md) returns the full quotient, which retains the remainder in the fractional portion.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfab5-118">Comentários</span><span class="sxs-lookup"><span data-stu-id="cfab5-118">Remarks</span></span>  

 <span data-ttu-id="cfab5-119">Antes de executar a divisão, Visual Basic tenta converter qualquer expressão numérica de ponto flutuante para `Long` .</span><span class="sxs-lookup"><span data-stu-id="cfab5-119">Before performing the division, Visual Basic attempts to convert any floating-point numeric expression to `Long`.</span></span> <span data-ttu-id="cfab5-120">Se `Option Strict` for `On` , ocorrerá um erro do compilador.</span><span class="sxs-lookup"><span data-stu-id="cfab5-120">If `Option Strict` is `On`, a compiler error occurs.</span></span> <span data-ttu-id="cfab5-121">Se `Option Strict` for `Off` , um <xref:System.OverflowException> será possível se o valor estiver fora do intervalo do [tipo de dados Long](../data-types/long-data-type.md).</span><span class="sxs-lookup"><span data-stu-id="cfab5-121">If `Option Strict` is `Off`, an <xref:System.OverflowException> is possible if the value is outside the range of the [Long Data Type](../data-types/long-data-type.md).</span></span> <span data-ttu-id="cfab5-122">A conversão em `Long` também está sujeita ao *arredondamento do banco*.</span><span class="sxs-lookup"><span data-stu-id="cfab5-122">The conversion to `Long` is also subject to *banker's rounding*.</span></span> <span data-ttu-id="cfab5-123">Para obter mais informações, consulte "partes fracionárias" em [funções de conversão de tipo](../functions/type-conversion-functions.md).</span><span class="sxs-lookup"><span data-stu-id="cfab5-123">For more information, see "Fractional Parts" in [Type Conversion Functions](../functions/type-conversion-functions.md).</span></span>  
  
 <span data-ttu-id="cfab5-124">Se `expression1` ou `expression2` for avaliado como [Nothing](../nothing.md), ele será tratado como zero.</span><span class="sxs-lookup"><span data-stu-id="cfab5-124">If `expression1` or `expression2` evaluates to [Nothing](../nothing.md), it is treated as zero.</span></span>  
  
## <a name="attempted-division-by-zero"></a><span data-ttu-id="cfab5-125">Tentativa de divisão por zero</span><span class="sxs-lookup"><span data-stu-id="cfab5-125">Attempted Division by Zero</span></span>  

 <span data-ttu-id="cfab5-126">Se `expression2` for avaliada como zero, o `\` operador lançará uma <xref:System.DivideByZeroException> exceção.</span><span class="sxs-lookup"><span data-stu-id="cfab5-126">If `expression2` evaluates to zero, the `\` operator throws a <xref:System.DivideByZeroException> exception.</span></span> <span data-ttu-id="cfab5-127">Isso é verdadeiro para todos os tipos de dados numéricos dos operandos.</span><span class="sxs-lookup"><span data-stu-id="cfab5-127">This is true for all numeric data types of the operands.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cfab5-128">O `\` operador pode ser *sobrecarregado*, o que significa que uma classe ou estrutura pode redefinir seu comportamento quando um operando tem o tipo dessa classe ou estrutura.</span><span class="sxs-lookup"><span data-stu-id="cfab5-128">The `\` operator can be *overloaded*, which means that a class or structure can redefine its behavior when an operand has the type of that class or structure.</span></span> <span data-ttu-id="cfab5-129">Se o seu código usar esse operador em uma classe ou estrutura desse tipo, certifique-se de entender seu comportamento redefinido.</span><span class="sxs-lookup"><span data-stu-id="cfab5-129">If your code uses this operator on such a class or structure, be sure you understand its redefined behavior.</span></span> <span data-ttu-id="cfab5-130">Para obter mais informações, consulte [procedimentos de operador](../../programming-guide/language-features/procedures/operator-procedures.md).</span><span class="sxs-lookup"><span data-stu-id="cfab5-130">For more information, see [Operator Procedures](../../programming-guide/language-features/procedures/operator-procedures.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cfab5-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cfab5-131">Example</span></span>  

 <span data-ttu-id="cfab5-132">O exemplo a seguir usa o `\` operador para executar a divisão de inteiro.</span><span class="sxs-lookup"><span data-stu-id="cfab5-132">The following example uses the `\` operator to perform integer division.</span></span> <span data-ttu-id="cfab5-133">O resultado é um inteiro que representa o quociente inteiro dos dois operandos, com o restante Descartado.</span><span class="sxs-lookup"><span data-stu-id="cfab5-133">The result is an integer that represents the integer quotient of the two operands, with the remainder discarded.</span></span>  
  
 [!code-vb[VbVbalrOperators#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#18)]  
  
 <span data-ttu-id="cfab5-134">As expressões no exemplo anterior retornam valores de 2, 3, 33 e-22, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="cfab5-134">The expressions in the preceding example return values of 2, 3, 33, and -22, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfab5-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="cfab5-135">See also</span></span>

- [<span data-ttu-id="cfab5-136">\\= Operador</span><span class="sxs-lookup"><span data-stu-id="cfab5-136">\\= Operator</span></span>](integer-division-assignment-operator.md)
- [<span data-ttu-id="cfab5-137">Operador/(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="cfab5-137">/ Operator (Visual Basic)</span></span>](floating-point-division-operator.md)
- [<span data-ttu-id="cfab5-138">Instrução Option Strict</span><span class="sxs-lookup"><span data-stu-id="cfab5-138">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
- [<span data-ttu-id="cfab5-139">Operadores aritméticos</span><span class="sxs-lookup"><span data-stu-id="cfab5-139">Arithmetic Operators</span></span>](arithmetic-operators.md)
- [<span data-ttu-id="cfab5-140">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cfab5-140">Operator Precedence in Visual Basic</span></span>](operator-precedence.md)
- [<span data-ttu-id="cfab5-141">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="cfab5-141">Operators Listed by Functionality</span></span>](operators-listed-by-functionality.md)
- [<span data-ttu-id="cfab5-142">Operadores aritméticos no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="cfab5-142">Arithmetic Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
