---
title: '{1&gt;Precedência do operador&lt;1}'
ms.date: 07/20/2015
helpviewer_keywords:
- arithmetic operators [Visual Basic], precedence
- operator precedence
- logical operators [Visual Basic], precedence
- operators [Visual Basic], associativity
- operators [Visual Basic], resolution
- associativity of operators [Visual Basic]
- operators [Visual Basic], precedence
- precedence [Visual Basic], of operators
- comparison operators [Visual Basic], precedence
- math operators [Visual Basic]
- order of precedence
ms.assetid: cbbdb282-f572-458e-a520-008a675f8063
ms.openlocfilehash: 318fcc3f35276ba0b2061ba9677c5fde29429f6f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348274"
---
# <a name="operator-precedence-in-visual-basic"></a><span data-ttu-id="0f271-102">Precedência do operador no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0f271-102">Operator Precedence in Visual Basic</span></span>
<span data-ttu-id="0f271-103">Quando várias operações ocorrem em uma expressão, cada parte é avaliada e resolvida em uma ordem predeterminada chamada *prioridade do operador*.</span><span class="sxs-lookup"><span data-stu-id="0f271-103">When several operations occur in an expression, each part is evaluated and resolved in a predetermined order called *operator precedence*.</span></span>

## <a name="precedence-rules"></a><span data-ttu-id="0f271-104">Regras de precedência</span><span class="sxs-lookup"><span data-stu-id="0f271-104">Precedence Rules</span></span>
 <span data-ttu-id="0f271-105">Quando as expressões contêm operadores de mais de uma categoria, elas são avaliadas de acordo com as seguintes regras:</span><span class="sxs-lookup"><span data-stu-id="0f271-105">When expressions contain operators from more than one category, they are evaluated according to the following rules:</span></span>

- <span data-ttu-id="0f271-106">Os operadores aritméticos e de concatenação têm a ordem de precedência descrita na seção a seguir, e todos têm maior precedência do que os operadores de comparação, lógico e bit-a.</span><span class="sxs-lookup"><span data-stu-id="0f271-106">The arithmetic and concatenation operators have the order of precedence described in the following section, and all have greater precedence than the comparison, logical, and bitwise operators.</span></span>

- <span data-ttu-id="0f271-107">Todos os operadores de comparação têm precedência igual, e todos têm maior precedência do que os operadores lógicos e de bit-inteiro, mas precedência menor do que os operadores aritméticos e de concatenação.</span><span class="sxs-lookup"><span data-stu-id="0f271-107">All comparison operators have equal precedence, and all have greater precedence than the logical and bitwise operators, but lower precedence than the arithmetic and concatenation operators.</span></span>

- <span data-ttu-id="0f271-108">Os operadores lógicos e bits de bit têm a ordem de precedência descrita na seção a seguir, e todos têm precedência mais baixa do que os operadores aritméticos, de concatenação e de comparação.</span><span class="sxs-lookup"><span data-stu-id="0f271-108">The logical and bitwise operators have the order of precedence described in the following section, and all have lower precedence than the arithmetic, concatenation, and comparison operators.</span></span>

- <span data-ttu-id="0f271-109">Os operadores com precedência igual são avaliados da esquerda para a direita na ordem em que aparecem na expressão.</span><span class="sxs-lookup"><span data-stu-id="0f271-109">Operators with equal precedence are evaluated left to right in the order in which they appear in the expression.</span></span>

## <a name="precedence-order"></a><span data-ttu-id="0f271-110">Ordem de precedência</span><span class="sxs-lookup"><span data-stu-id="0f271-110">Precedence Order</span></span>
 <span data-ttu-id="0f271-111">Os operadores são avaliados na seguinte ordem de precedência:</span><span class="sxs-lookup"><span data-stu-id="0f271-111">Operators are evaluated in the following order of precedence:</span></span>

### <a name="await-operator"></a><span data-ttu-id="0f271-112">Operador Await</span><span class="sxs-lookup"><span data-stu-id="0f271-112">Await Operator</span></span>
 <span data-ttu-id="0f271-113">Expressões</span><span class="sxs-lookup"><span data-stu-id="0f271-113">Await</span></span>

### <a name="arithmetic-and-concatenation-operators"></a><span data-ttu-id="0f271-114">Operadores aritméticos e de concatenação</span><span class="sxs-lookup"><span data-stu-id="0f271-114">Arithmetic and Concatenation Operators</span></span>
 <span data-ttu-id="0f271-115">Exponenciação (`^`)</span><span class="sxs-lookup"><span data-stu-id="0f271-115">Exponentiation (`^`)</span></span>

 <span data-ttu-id="0f271-116">Identidade unário e negação (`+`, `–`)</span><span class="sxs-lookup"><span data-stu-id="0f271-116">Unary identity and negation (`+`, `–`)</span></span>

 <span data-ttu-id="0f271-117">Divisão de ponto flutuante e multiplicação (`*`, `/`)</span><span class="sxs-lookup"><span data-stu-id="0f271-117">Multiplication and floating-point division (`*`, `/`)</span></span>

 <span data-ttu-id="0f271-118">Divisão de inteiro (`\`)</span><span class="sxs-lookup"><span data-stu-id="0f271-118">Integer division (`\`)</span></span>

 <span data-ttu-id="0f271-119">Aritmética modular (`Mod`)</span><span class="sxs-lookup"><span data-stu-id="0f271-119">Modular arithmetic (`Mod`)</span></span>

 <span data-ttu-id="0f271-120">Adição e subtração (`+`, `–`)</span><span class="sxs-lookup"><span data-stu-id="0f271-120">Addition and subtraction (`+`, `–`)</span></span>

 <span data-ttu-id="0f271-121">Concatenação de cadeia de caracteres (`&`)</span><span class="sxs-lookup"><span data-stu-id="0f271-121">String concatenation (`&`)</span></span>

 <span data-ttu-id="0f271-122">Deslocamento de bit aritmético (`<<`, `>>`)</span><span class="sxs-lookup"><span data-stu-id="0f271-122">Arithmetic bit shift (`<<`, `>>`)</span></span>

### <a name="comparison-operators"></a><span data-ttu-id="0f271-123">Operadores de comparação</span><span class="sxs-lookup"><span data-stu-id="0f271-123">Comparison Operators</span></span>
 <span data-ttu-id="0f271-124">Todos os operadores de comparação (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span><span class="sxs-lookup"><span data-stu-id="0f271-124">All comparison operators (`=`, `<>`, `<`, `<=`, `>`, `>=`, `Is`, `IsNot`, `Like`, `TypeOf`...`Is`)</span></span>

### <a name="logical-and-bitwise-operators"></a><span data-ttu-id="0f271-125">Operadores lógicos e bit a bit</span><span class="sxs-lookup"><span data-stu-id="0f271-125">Logical and Bitwise Operators</span></span>
 <span data-ttu-id="0f271-126">Negação (`Not`)</span><span class="sxs-lookup"><span data-stu-id="0f271-126">Negation (`Not`)</span></span>

 <span data-ttu-id="0f271-127">Conjunção (`And`, `AndAlso`)</span><span class="sxs-lookup"><span data-stu-id="0f271-127">Conjunction (`And`, `AndAlso`)</span></span>

 <span data-ttu-id="0f271-128">Disjunção inclusiva (`Or`, `OrElse`)</span><span class="sxs-lookup"><span data-stu-id="0f271-128">Inclusive disjunction (`Or`, `OrElse`)</span></span>

 <span data-ttu-id="0f271-129">Disjunção exclusiva (`Xor`)</span><span class="sxs-lookup"><span data-stu-id="0f271-129">Exclusive disjunction (`Xor`)</span></span>

### <a name="comments"></a><span data-ttu-id="0f271-130">Comments</span><span class="sxs-lookup"><span data-stu-id="0f271-130">Comments</span></span>
 <span data-ttu-id="0f271-131">O operador de `=` é apenas o operador de comparação de igualdade, não o operador de atribuição.</span><span class="sxs-lookup"><span data-stu-id="0f271-131">The `=` operator is only the equality comparison operator, not the assignment operator.</span></span>

 <span data-ttu-id="0f271-132">O operador de concatenação de cadeia de caracteres (`&`) não é um operador aritmético, mas, na precedência, ele é agrupado com os operadores aritméticos.</span><span class="sxs-lookup"><span data-stu-id="0f271-132">The string concatenation operator (`&`) is not an arithmetic operator, but in precedence it is grouped with the arithmetic operators.</span></span>

 <span data-ttu-id="0f271-133">Os operadores `Is` e `IsNot` são operadores de comparação de referência de objeto.</span><span class="sxs-lookup"><span data-stu-id="0f271-133">The `Is` and `IsNot` operators are object reference comparison operators.</span></span> <span data-ttu-id="0f271-134">Eles não comparam os valores de dois objetos; Eles só verificam se duas variáveis de objeto se referem à mesma instância de objeto.</span><span class="sxs-lookup"><span data-stu-id="0f271-134">They do not compare the values of two objects; they check only to determine whether two object variables refer to the same object instance.</span></span>

## <a name="associativity"></a><span data-ttu-id="0f271-135">Associatividade</span><span class="sxs-lookup"><span data-stu-id="0f271-135">Associativity</span></span>
 <span data-ttu-id="0f271-136">Quando os operadores de precedência igual aparecem juntos em uma expressão, por exemplo, multiplicação e divisão, o compilador avalia cada operação à medida que a encontra da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="0f271-136">When operators of equal precedence appear together in an expression, for example multiplication and division, the compiler evaluates each operation as it encounters it from left to right.</span></span> <span data-ttu-id="0f271-137">O exemplo a seguir mostra isso.</span><span class="sxs-lookup"><span data-stu-id="0f271-137">The following example illustrates this.</span></span>

```vb
Dim n1 As Integer = 96 / 8 / 4
Dim n2 As Integer = (96 / 8) / 4
Dim n3 As Integer = 96 / (8 / 4)
```

 <span data-ttu-id="0f271-138">A primeira expressão avalia a divisão 96/8 (que resulta em 12) e, em seguida, a divisão 12/4, que resulta em três.</span><span class="sxs-lookup"><span data-stu-id="0f271-138">The first expression evaluates the division 96 / 8 (which results in 12) and then the division 12 / 4, which results in three.</span></span> <span data-ttu-id="0f271-139">Como o compilador avalia as operações para `n1` da esquerda para a direita, a avaliação é a mesma quando essa ordem é explicitamente indicada para `n2`.</span><span class="sxs-lookup"><span data-stu-id="0f271-139">Because the compiler evaluates the operations for `n1` from left to right, the evaluation is the same when that order is explicitly indicated for `n2`.</span></span> <span data-ttu-id="0f271-140">Tanto `n1` quanto `n2` têm um resultado de três.</span><span class="sxs-lookup"><span data-stu-id="0f271-140">Both `n1` and `n2` have a result of three.</span></span> <span data-ttu-id="0f271-141">Por outro lado, `n3` tem um resultado de 48, porque os parênteses forçam o compilador a avaliar a 8/4 primeiro.</span><span class="sxs-lookup"><span data-stu-id="0f271-141">By contrast, `n3` has a result of 48, because the parentheses force the compiler to evaluate 8 / 4 first.</span></span>

 <span data-ttu-id="0f271-142">Devido a esse comportamento, os operadores são considerados *associativos à esquerda* no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0f271-142">Because of this behavior, operators are said to be *left associative* in Visual Basic.</span></span>

## <a name="overriding-precedence-and-associativity"></a><span data-ttu-id="0f271-143">Substituindo precedência e Associação</span><span class="sxs-lookup"><span data-stu-id="0f271-143">Overriding Precedence and Associativity</span></span>
 <span data-ttu-id="0f271-144">Você pode usar parênteses para forçar algumas partes de uma expressão a serem avaliadas antes de outras.</span><span class="sxs-lookup"><span data-stu-id="0f271-144">You can use parentheses to force some parts of an expression to be evaluated before others.</span></span> <span data-ttu-id="0f271-145">Isso pode substituir a ordem de precedência e a associação à esquerda.</span><span class="sxs-lookup"><span data-stu-id="0f271-145">This can override both the order of precedence and the left associativity.</span></span> <span data-ttu-id="0f271-146">Visual Basic sempre executa operações que são colocadas entre parênteses antes das externas.</span><span class="sxs-lookup"><span data-stu-id="0f271-146">Visual Basic always performs operations that are enclosed in parentheses before those outside.</span></span> <span data-ttu-id="0f271-147">No entanto, entre parênteses, ele mantém precedência comum e associação, a menos que você use parênteses dentro dos parênteses.</span><span class="sxs-lookup"><span data-stu-id="0f271-147">However, within parentheses, it maintains ordinary precedence and associativity, unless you use parentheses within the parentheses.</span></span> <span data-ttu-id="0f271-148">O exemplo a seguir mostra isso.</span><span class="sxs-lookup"><span data-stu-id="0f271-148">The following example illustrates this.</span></span>

```vb
Dim a, b, c, d, e, f, g As Double
a = 8.0
b = 3.0
c = 4.0
d = 2.0
e = 1.0
f = a - b + c / d * e
' The preceding line sets f to 7.0. Because of natural operator
' precedence and associativity, it is exactly equivalent to the
' following line.
f = (a - b) + ((c / d) * e)
' The following line overrides the natural operator precedence
' and left associativity.
g = (a - (b + c)) / (d * e)
' The preceding line sets g to 0.5.
```

## <a name="see-also"></a><span data-ttu-id="0f271-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f271-149">See also</span></span>

- [<span data-ttu-id="0f271-150">Operador =</span><span class="sxs-lookup"><span data-stu-id="0f271-150">= Operator</span></span>](../../../visual-basic/language-reference/operators/assignment-operator.md)
- [<span data-ttu-id="0f271-151">Operador Is</span><span class="sxs-lookup"><span data-stu-id="0f271-151">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="0f271-152">Operador IsNot</span><span class="sxs-lookup"><span data-stu-id="0f271-152">IsNot Operator</span></span>](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [<span data-ttu-id="0f271-153">Operador Like</span><span class="sxs-lookup"><span data-stu-id="0f271-153">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="0f271-154">Operador TypeOf</span><span class="sxs-lookup"><span data-stu-id="0f271-154">TypeOf Operator</span></span>](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [<span data-ttu-id="0f271-155">Operador Await</span><span class="sxs-lookup"><span data-stu-id="0f271-155">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)
- [<span data-ttu-id="0f271-156">Operadores Listados por Funcionalidade</span><span class="sxs-lookup"><span data-stu-id="0f271-156">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="0f271-157">Operadores e Expressões</span><span class="sxs-lookup"><span data-stu-id="0f271-157">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
