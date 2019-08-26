---
title: Operadores – Guia de Programação em C#
ms.custom: seodec18
ms.date: 04/30/2019
helpviewer_keywords:
- operators [C#]
- C# language, operators
- operators [C#], about operators
ms.assetid: 214e7b83-1a41-4f7c-9867-64e9c0bab39f
ms.openlocfilehash: 4870c744383205c2b7e3832c01fb838a545f085f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588611"
---
# <a name="operators-c-programming-guide"></a><span data-ttu-id="9e028-102">Operadores (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="9e028-102">Operators (C# Programming Guide)</span></span>

<span data-ttu-id="9e028-103">Em C#, um *operador* é um elemento de programa aplicado a um ou mais *operandos* em uma expressão ou instrução.</span><span class="sxs-lookup"><span data-stu-id="9e028-103">In C#, an *operator* is a program element that is applied to one or more *operands* in an expression or statement.</span></span> <span data-ttu-id="9e028-104">Os operadores que usam um operando, como o operador de incremento (`++`) ou `new`, são referidos como operadores *unários*.</span><span class="sxs-lookup"><span data-stu-id="9e028-104">Operators that take one operand, such as the increment operator (`++`) or `new`, are referred to as *unary* operators.</span></span> <span data-ttu-id="9e028-105">Os operadores que usam dois operandos, como operadores aritméticos (`+`,`-`,`*`,`/`), são referidos como operadores *binários*.</span><span class="sxs-lookup"><span data-stu-id="9e028-105">Operators that take two operands, such as arithmetic operators (`+`,`-`,`*`,`/`), are referred to as *binary* operators.</span></span> <span data-ttu-id="9e028-106">Um operador, o operador condicional (`?:`), usa três operandos e é o único operador ternário em C#.</span><span class="sxs-lookup"><span data-stu-id="9e028-106">One operator, the conditional operator (`?:`), takes three operands and is the sole ternary operator in C#.</span></span>  
  
 <span data-ttu-id="9e028-107">A seguinte instrução de C# contém um único operador unário e um operando único.</span><span class="sxs-lookup"><span data-stu-id="9e028-107">The following C# statement contains a single unary operator and a single operand.</span></span> <span data-ttu-id="9e028-108">O operador de incremento, `++`, modifica o valor do operando `y`.</span><span class="sxs-lookup"><span data-stu-id="9e028-108">The increment operator, `++`, modifies the value of the operand `y`.</span></span>  
  
 [!code-csharp[csProgGuideStatements#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#5)]  
  
 <span data-ttu-id="9e028-109">A seguinte instrução de C# contém dois operadores binários, cada um com dois operandos.</span><span class="sxs-lookup"><span data-stu-id="9e028-109">The following C# statement contains two binary operators, each with two operands.</span></span> <span data-ttu-id="9e028-110">O operador de atribuição, `=`, contém a variável inteira `y` e a expressão `2 + 3` como operandos.</span><span class="sxs-lookup"><span data-stu-id="9e028-110">The assignment operator, `=`, has the integer variable `y` and the expression `2 + 3` as operands.</span></span> <span data-ttu-id="9e028-111">A expressão `2 + 3` em si consiste no operador de adição e dois operandos, `2` e `3`.</span><span class="sxs-lookup"><span data-stu-id="9e028-111">The expression `2 + 3` itself consists of the addition operator and two operands, `2` and `3`.</span></span>  
  
 [!code-csharp[csProgGuideStatements#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#6)]  
  
<span data-ttu-id="9e028-112">Um operando pode ser uma expressão válida composta por qualquer comprimento de código e pode incluir qualquer número de subexpressões.</span><span class="sxs-lookup"><span data-stu-id="9e028-112">An operand can be a valid expression that is composed of any length of code, and it can comprise any number of sub expressions.</span></span> <span data-ttu-id="9e028-113">Em uma expressão que contém vários operadores, a ordem em que os operadores são aplicados é determinada pela *precedência de operadores*, *associatividade* e parênteses.</span><span class="sxs-lookup"><span data-stu-id="9e028-113">In an expression that contains multiple operators, the order in which the operators are applied is determined by *operator precedence*, *associativity*, and parentheses.</span></span>  

## <a name="operator-precedence"></a><span data-ttu-id="9e028-114">Precedência do operador</span><span class="sxs-lookup"><span data-stu-id="9e028-114">Operator precedence</span></span>
  
<span data-ttu-id="9e028-115">Cada operador possui uma precedência definida.</span><span class="sxs-lookup"><span data-stu-id="9e028-115">Each operator has a defined precedence.</span></span> <span data-ttu-id="9e028-116">Em uma expressão com vários operadores e diferentes níveis de precedência, a precedência dos operadores determina a ordem em que os operadores são avaliados.</span><span class="sxs-lookup"><span data-stu-id="9e028-116">In an expression that contains multiple operators that have different precedence levels, the precedence of the operators determines the order in which the operators are evaluated.</span></span> <span data-ttu-id="9e028-117">Por exemplo, a seguinte instrução atribui 3 a `n1`:</span><span class="sxs-lookup"><span data-stu-id="9e028-117">For example, the following statement assigns 3 to `n1`:</span></span>

```csharp
n1 = 11 - 2 * 4;
```

<span data-ttu-id="9e028-118">A multiplicação é executada primeiro porque ela tem precedência sobre a subtração.</span><span class="sxs-lookup"><span data-stu-id="9e028-118">The multiplication is executed first because multiplication takes precedence over subtraction.</span></span>

<span data-ttu-id="9e028-119">Para obter a lista completa de operadores do C# ordenada pelo nível de precedência, confira [Operadores do C#](../../language-reference/operators/index.md).</span><span class="sxs-lookup"><span data-stu-id="9e028-119">For the complete list of C# operators ordered by precedence level, see [C# operators](../../language-reference/operators/index.md).</span></span>
  
## <a name="associativity"></a><span data-ttu-id="9e028-120">Associatividade</span><span class="sxs-lookup"><span data-stu-id="9e028-120">Associativity</span></span>

 <span data-ttu-id="9e028-121">Quando dois ou mais operadores com a mesma precedência estiverem presentes em uma expressão, eles serão avaliados com base em associatividade.</span><span class="sxs-lookup"><span data-stu-id="9e028-121">When two or more operators that have the same precedence are present in an expression, they are evaluated based on associativity.</span></span> <span data-ttu-id="9e028-122">Os operadores associativos esquerdos são avaliados em ordem da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="9e028-122">Left-associative operators are evaluated in order from left to right.</span></span> <span data-ttu-id="9e028-123">Por exemplo, `x * y / z` é avaliado como `(x * y) / z`.</span><span class="sxs-lookup"><span data-stu-id="9e028-123">For example, `x * y / z` is evaluated as `(x * y) / z`.</span></span> <span data-ttu-id="9e028-124">Os operadores associativos direitos são avaliados em ordem da direita para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="9e028-124">Right-associative operators are evaluated in order from right to left.</span></span> <span data-ttu-id="9e028-125">Por exemplo, o operador de atribuição é associativo direito.</span><span class="sxs-lookup"><span data-stu-id="9e028-125">For example, the assignment operator is right associative.</span></span> <span data-ttu-id="9e028-126">Se ele não fosse, o código a seguir resultaria em um erro.</span><span class="sxs-lookup"><span data-stu-id="9e028-126">If it were not, the following code would result in an error.</span></span>  
  
```csharp  
int a, b, c;  
c = 1;  
// The following two lines are equivalent.  
a = b = c;  
a = (b = c);  
  
// The following line, which forces left associativity, causes an error.  
//(a = b) = c;  
```  
  
 <span data-ttu-id="9e028-127">Como outro exemplo, o operador ternário ([?:](../../language-reference/operators/conditional-operator.md)) é associativo à direita.</span><span class="sxs-lookup"><span data-stu-id="9e028-127">As another example the ternary operator ([?:](../../language-reference/operators/conditional-operator.md)) is right associative.</span></span> <span data-ttu-id="9e028-128">A maioria dos operadores binários são associativos à esquerda.</span><span class="sxs-lookup"><span data-stu-id="9e028-128">Most binary operators are left associative.</span></span>  
  
 <span data-ttu-id="9e028-129">Se os operadores em uma expressão forem associativos direitos ou esquerdos, os operandos de cada expressão serão avaliados primeiro, da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="9e028-129">Whether the operators in an expression are left associative or right associative, the operands of each expression are evaluated first, from left to right.</span></span> <span data-ttu-id="9e028-130">Os exemplos a seguir ilustram a ordem de avaliação de operadores e operandos.</span><span class="sxs-lookup"><span data-stu-id="9e028-130">The following examples illustrate the order of evaluation of operators and operands.</span></span>  
  
|<span data-ttu-id="9e028-131">Instrução</span><span class="sxs-lookup"><span data-stu-id="9e028-131">Statement</span></span>|<span data-ttu-id="9e028-132">Ordem de avaliação</span><span class="sxs-lookup"><span data-stu-id="9e028-132">Order of evaluation</span></span>|  
|---------------|-------------------------|  
|`a = b`|<span data-ttu-id="9e028-133">a, b, =</span><span class="sxs-lookup"><span data-stu-id="9e028-133">a, b, =</span></span>|  
|`a = b + c`|<span data-ttu-id="9e028-134">a, b, c, +, =</span><span class="sxs-lookup"><span data-stu-id="9e028-134">a, b, c, +, =</span></span>|  
|`a = b + c * d`|<span data-ttu-id="9e028-135">a, b, c, d, \*, +, =</span><span class="sxs-lookup"><span data-stu-id="9e028-135">a, b, c, d, \*, +, =</span></span>|  
|`a = b * c + d`|<span data-ttu-id="9e028-136">a, b, c, \*, d, +, =</span><span class="sxs-lookup"><span data-stu-id="9e028-136">a, b, c, \*, d, +, =</span></span>|  
|`a = b - c + d`|<span data-ttu-id="9e028-137">a, b, c, -, d, +, =</span><span class="sxs-lookup"><span data-stu-id="9e028-137">a, b, c, -, d, +, =</span></span>|  
|`a += b -= c`|<span data-ttu-id="9e028-138">a, b, c, -=, +=</span><span class="sxs-lookup"><span data-stu-id="9e028-138">a, b, c, -=, +=</span></span>|  
  
## <a name="adding-parentheses"></a><span data-ttu-id="9e028-139">Adicionando parênteses</span><span class="sxs-lookup"><span data-stu-id="9e028-139">Adding parentheses</span></span>

 <span data-ttu-id="9e028-140">Você pode alterar a ordem imposta pela precedência de operadores e a associatividade ao usar parênteses.</span><span class="sxs-lookup"><span data-stu-id="9e028-140">You can change the order imposed by operator precedence and associativity by using parentheses.</span></span> <span data-ttu-id="9e028-141">Por exemplo, `2 + 3 * 2` resulta normalmente em 8, pois operadores multiplicativos têm precedência sobre operadores aditivos.</span><span class="sxs-lookup"><span data-stu-id="9e028-141">For example, `2 + 3 * 2` ordinarily evaluates to 8, because multiplicative operators take precedence over additive operators.</span></span> <span data-ttu-id="9e028-142">No entanto, se você escrever a expressão como `(2 + 3) * 2`, a adição será avaliada antes da multiplicação e o resultado será 10.</span><span class="sxs-lookup"><span data-stu-id="9e028-142">However, if you write the expression as `(2 + 3) * 2`, the addition is evaluated before the multiplication, and the result is 10.</span></span> <span data-ttu-id="9e028-143">Os exemplos a seguir ilustram a ordem de avaliação em expressões com parênteses.</span><span class="sxs-lookup"><span data-stu-id="9e028-143">The following examples illustrate the order of evaluation in parenthesized expressions.</span></span> <span data-ttu-id="9e028-144">Como nos exemplos anteriores, os operandos são avaliados antes que o operador seja aplicado.</span><span class="sxs-lookup"><span data-stu-id="9e028-144">As in previous examples, the operands are evaluated before the operator is applied.</span></span>  
  
|<span data-ttu-id="9e028-145">Instrução</span><span class="sxs-lookup"><span data-stu-id="9e028-145">Statement</span></span>|<span data-ttu-id="9e028-146">Ordem de avaliação</span><span class="sxs-lookup"><span data-stu-id="9e028-146">Order of evaluation</span></span>|  
|---------------|-------------------------|  
|`a = (b + c) * d`|<span data-ttu-id="9e028-147">a, b, c, +, d, \*, =</span><span class="sxs-lookup"><span data-stu-id="9e028-147">a, b, c, +, d, \*, =</span></span>|  
|`a = b - (c + d)`|<span data-ttu-id="9e028-148">a, b, c, d, +, -, =</span><span class="sxs-lookup"><span data-stu-id="9e028-148">a, b, c, d, +, -, =</span></span>|  
|`a = (b + c) * (d - e)`|<span data-ttu-id="9e028-149">a, b, c, +, d, e, -, \*, =</span><span class="sxs-lookup"><span data-stu-id="9e028-149">a, b, c, +, d, e, -, \*, =</span></span>|  
  
## <a name="operator-overloading"></a><span data-ttu-id="9e028-150">Sobrecarga de operador</span><span class="sxs-lookup"><span data-stu-id="9e028-150">Operator overloading</span></span>

<span data-ttu-id="9e028-151">Você pode define o comportamento de determinados operadores para classes e structs personalizados.</span><span class="sxs-lookup"><span data-stu-id="9e028-151">You can define the behavior of certain operators for custom classes and structs.</span></span> <span data-ttu-id="9e028-152">Esse processo é chamado *sobrecarga de operador*.</span><span class="sxs-lookup"><span data-stu-id="9e028-152">This process is referred to as *operator overloading*.</span></span> <span data-ttu-id="9e028-153">Para obter mais informações, consulte [Sobrecarga de operador](../../language-reference/operators/operator-overloading.md).</span><span class="sxs-lookup"><span data-stu-id="9e028-153">For more information, see [Operator overloading](../../language-reference/operators/operator-overloading.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9e028-154">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9e028-154">See also</span></span>

- [<span data-ttu-id="9e028-155">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="9e028-155">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9e028-156">Instruções, expressões e operadores</span><span class="sxs-lookup"><span data-stu-id="9e028-156">Statements, Expressions, and Operators</span></span>](index.md)
- [<span data-ttu-id="9e028-157">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="9e028-157">C# Operators</span></span>](../../language-reference/operators/index.md)
