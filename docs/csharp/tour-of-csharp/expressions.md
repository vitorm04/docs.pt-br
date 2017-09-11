---
title: "Expressões C# - um tour pela linguagem C#"
description: "expressões, operandos e operadores são blocos de compilação da linguagem C#"
keywords: ".NET, csharp, expressão, operador, operando"
author: BillWagner
ms.author: wiwagn
ms.date: 11/06/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 155804dd212d8eda8d81ce7e296a9fe308e9c69b
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="expressions"></a><span data-ttu-id="f3e2f-104">Expressões</span><span class="sxs-lookup"><span data-stu-id="f3e2f-104">Expressions</span></span>

<span data-ttu-id="f3e2f-105">*Expressões* são construídas a partir de *operandos* e *operadores*.</span><span class="sxs-lookup"><span data-stu-id="f3e2f-105">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="f3e2f-106">Os operadores de uma expressão indicam quais operações devem ser aplicadas aos operandos.</span><span class="sxs-lookup"><span data-stu-id="f3e2f-106">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="f3e2f-107">Exemplos de operadores incluem `+`, `-`, `*`, `/` e `new`.</span><span class="sxs-lookup"><span data-stu-id="f3e2f-107">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="f3e2f-108">Exemplos de operandos incluem literais, campos, variáveis locais e expressões.</span><span class="sxs-lookup"><span data-stu-id="f3e2f-108">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="f3e2f-109">Quando uma expressão contiver vários operadores, a *precedência* dos operadores controla a ordem na qual os operadores individuais são avaliados.</span><span class="sxs-lookup"><span data-stu-id="f3e2f-109">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="f3e2f-110">Por exemplo, a expressão `x + y * z` é avaliada como `x + (y * z)` porque o operador `*` tem precedência maior do que o operador `+`.</span><span class="sxs-lookup"><span data-stu-id="f3e2f-110">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="f3e2f-111">Quando ocorre um operando entre dois operadores com a mesma precedência, a *associatividade* dos operadores controla a ordem na qual as operações são executadas:</span><span class="sxs-lookup"><span data-stu-id="f3e2f-111">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

*   <span data-ttu-id="f3e2f-112">Exceto para os operadores de atribuição, todos os operadores binários são *associativos à esquerda*, o que significa que as operações são executadas da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="f3e2f-112">Except for the assignment operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="f3e2f-113">Por exemplo, `x + y + z` é avaliado como `(x + y) + z`.</span><span class="sxs-lookup"><span data-stu-id="f3e2f-113">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
*   <span data-ttu-id="f3e2f-114">Os operadores de atribuição e o operador condicional (`?:`) são *associativos à direita*, o que significa que as operações são executadas da direita para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="f3e2f-114">The assignment operators and the conditional operator (`?:`) are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="f3e2f-115">Por exemplo, `x = y = z` é avaliado como `x = (y = z)`.</span><span class="sxs-lookup"><span data-stu-id="f3e2f-115">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="f3e2f-116">Precedência e associatividade podem ser controladas usando parênteses.</span><span class="sxs-lookup"><span data-stu-id="f3e2f-116">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="f3e2f-117">Por exemplo, `x + y * z` primeiro multiplica `y` por `z` e, em seguida, adiciona o resultado a `x`, mas `(x + y) * z` primeiro adiciona `x` e `y` e, em seguida, multiplica o resultado por `z`.</span><span class="sxs-lookup"><span data-stu-id="f3e2f-117">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="f3e2f-118">A maioria dos operadores pode ser *sobrecarregada*.</span><span class="sxs-lookup"><span data-stu-id="f3e2f-118">Most operators can be *overloaded*.</span></span> <span data-ttu-id="f3e2f-119">A sobrecarga de operador permite que implementações de operador definidas pelo usuário sejam especificadas para operações em que um ou ambos os operandos são de um tipo struct ou de classe definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="f3e2f-119">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="f3e2f-120">O item a seguir resume os operadores do C#, listando as categorias de operador em ordem de precedência da mais alta para a mais baixa.</span><span class="sxs-lookup"><span data-stu-id="f3e2f-120">The following summarizes C#’s operators, listing the operator categories in order of precedence from highest to lowest.</span></span> <span data-ttu-id="f3e2f-121">Operadores na mesma categoria têm a mesma precedência.</span><span class="sxs-lookup"><span data-stu-id="f3e2f-121">Operators in the same category have equal precedence.</span></span> <span data-ttu-id="f3e2f-122">Em cada categoria está uma lista de expressões da categoria juntamente com a descrição do tipo de expressão.</span><span class="sxs-lookup"><span data-stu-id="f3e2f-122">Under each category is a list of expressions in that category along with the description of that expression type.</span></span>

* <span data-ttu-id="f3e2f-123">Primária</span><span class="sxs-lookup"><span data-stu-id="f3e2f-123">Primary</span></span>
    - <span data-ttu-id="f3e2f-124">`x.m`: acesso de membro</span><span class="sxs-lookup"><span data-stu-id="f3e2f-124">`x.m`: Member access</span></span>
    - <span data-ttu-id="f3e2f-125">`x(...)`: invocação de método e delegado</span><span class="sxs-lookup"><span data-stu-id="f3e2f-125">`x(...)`: Method and delegate invocation</span></span>
    - <span data-ttu-id="f3e2f-126">`x[...]`: acesso de matriz e indexador</span><span class="sxs-lookup"><span data-stu-id="f3e2f-126">`x[...]`: Array and indexer access</span></span>
    - <span data-ttu-id="f3e2f-127">`x++`: pós-incremento</span><span class="sxs-lookup"><span data-stu-id="f3e2f-127">`x++`: Post-increment</span></span>
    - <span data-ttu-id="f3e2f-128">`x--`: pós-decremento</span><span class="sxs-lookup"><span data-stu-id="f3e2f-128">`x--`: Post-decrement</span></span>
    - <span data-ttu-id="f3e2f-129">`new T(...)`: criação de objeto e delegado</span><span class="sxs-lookup"><span data-stu-id="f3e2f-129">`new T(...)`: Object and delegate creation</span></span>
    - <span data-ttu-id="f3e2f-130">`new T(...){...}`: criação de objeto com inicializador</span><span class="sxs-lookup"><span data-stu-id="f3e2f-130">`new T(...){...}`: Object creation with initializer</span></span>
    - <span data-ttu-id="f3e2f-131">`new {...}`: inicializador de objeto anônimo</span><span class="sxs-lookup"><span data-stu-id="f3e2f-131">`new {...}`:  Anonymous object initializer</span></span>
    - <span data-ttu-id="f3e2f-132">`new T[...]`: criação de matriz</span><span class="sxs-lookup"><span data-stu-id="f3e2f-132">`new T[...]`: Array creation</span></span>
    - <span data-ttu-id="f3e2f-133">`typeof(T)`: obter @System.Type objeto para `T`</span><span class="sxs-lookup"><span data-stu-id="f3e2f-133">`typeof(T)`: Obtain @System.Type object for `T`</span></span>
    - <span data-ttu-id="f3e2f-134">`checked(x)`: avaliar expressão no contexto marcado</span><span class="sxs-lookup"><span data-stu-id="f3e2f-134">`checked(x)`: Evaluate expression in checked context</span></span>
    - <span data-ttu-id="f3e2f-135">`unchecked(x)`: avaliar expressão no contexto desmarcado</span><span class="sxs-lookup"><span data-stu-id="f3e2f-135">`unchecked(x)`: Evaluate expression in unchecked context</span></span>
    - <span data-ttu-id="f3e2f-136">`default(T)`: obter valor padrão do tipo `T`</span><span class="sxs-lookup"><span data-stu-id="f3e2f-136">`default(T)`: Obtain default value of type `T`</span></span>
    - <span data-ttu-id="f3e2f-137">`delegate {...}`: função anônima (método anônimo)</span><span class="sxs-lookup"><span data-stu-id="f3e2f-137">`delegate {...}`: Anonymous function (anonymous method)</span></span>
* <span data-ttu-id="f3e2f-138">Unário</span><span class="sxs-lookup"><span data-stu-id="f3e2f-138">Unary</span></span>
    - <span data-ttu-id="f3e2f-139">`+x`: identidade</span><span class="sxs-lookup"><span data-stu-id="f3e2f-139">`+x`: Identity</span></span>
    - <span data-ttu-id="f3e2f-140">`-x`: negação</span><span class="sxs-lookup"><span data-stu-id="f3e2f-140">`-x`: Negation</span></span>
    - <span data-ttu-id="f3e2f-141">`!x`: negação lógica</span><span class="sxs-lookup"><span data-stu-id="f3e2f-141">`!x`: Logical negation</span></span>
    - <span data-ttu-id="f3e2f-142">`~x`: negação bit a bit</span><span class="sxs-lookup"><span data-stu-id="f3e2f-142">`~x`: Bitwise negation</span></span>
    - <span data-ttu-id="f3e2f-143">`++x`: pré-incremento</span><span class="sxs-lookup"><span data-stu-id="f3e2f-143">`++x`: Pre-increment</span></span>
    - <span data-ttu-id="f3e2f-144">`--x`: pré-decremento</span><span class="sxs-lookup"><span data-stu-id="f3e2f-144">`--x`: Pre-decrement</span></span>
    - <span data-ttu-id="f3e2f-145">`(T)x`: converter explicitamente `x` no tipo `T`</span><span class="sxs-lookup"><span data-stu-id="f3e2f-145">`(T)x`: Explicitly convert `x` to type `T`</span></span>
    - <span data-ttu-id="f3e2f-146">`await x`: aguardar assincronamente `x` para concluir</span><span class="sxs-lookup"><span data-stu-id="f3e2f-146">`await x`: Asynchronously wait for `x` to complete</span></span>
* <span data-ttu-id="f3e2f-147">Multiplicativo</span><span class="sxs-lookup"><span data-stu-id="f3e2f-147">Multiplicative</span></span>
    - <span data-ttu-id="f3e2f-148">`x * y`: multiplicação</span><span class="sxs-lookup"><span data-stu-id="f3e2f-148">`x * y`: Multiplication</span></span>
    - <span data-ttu-id="f3e2f-149">`x / y`: divisão</span><span class="sxs-lookup"><span data-stu-id="f3e2f-149">`x / y`: Division</span></span>
    - <span data-ttu-id="f3e2f-150">`x % y`: resto</span><span class="sxs-lookup"><span data-stu-id="f3e2f-150">`x % y`: Remainder</span></span>
* <span data-ttu-id="f3e2f-151">Aditivo</span><span class="sxs-lookup"><span data-stu-id="f3e2f-151">Additive</span></span>
    - <span data-ttu-id="f3e2f-152">`x + y`: adição, concatenação de cadeia de caracteres, combinação de delegados</span><span class="sxs-lookup"><span data-stu-id="f3e2f-152">`x + y`: Addition, string concatenation, delegate combination</span></span>
    - <span data-ttu-id="f3e2f-153">`x – y`: subtração, remoção de delegado</span><span class="sxs-lookup"><span data-stu-id="f3e2f-153">`x – y`: Subtraction, delegate removal</span></span>
* <span data-ttu-id="f3e2f-154">Shift</span><span class="sxs-lookup"><span data-stu-id="f3e2f-154">Shift</span></span>
    - <span data-ttu-id="f3e2f-155">`x << y`: Shift esquerdo</span><span class="sxs-lookup"><span data-stu-id="f3e2f-155">`x << y`: Shift left</span></span>
    - <span data-ttu-id="f3e2f-156">`x >> y`: Shift direito</span><span class="sxs-lookup"><span data-stu-id="f3e2f-156">`x >> y`: Shift right</span></span>
* <span data-ttu-id="f3e2f-157">Teste de tipo e relacional</span><span class="sxs-lookup"><span data-stu-id="f3e2f-157">Relational and type testing</span></span>
    - <span data-ttu-id="f3e2f-158">`x < y`: é menor que</span><span class="sxs-lookup"><span data-stu-id="f3e2f-158">`x < y`: Less than</span></span>
    - <span data-ttu-id="f3e2f-159">`x > y`: é maior que</span><span class="sxs-lookup"><span data-stu-id="f3e2f-159">`x > y`: Greater than</span></span>
    - <span data-ttu-id="f3e2f-160">`x <= y`: é menor que ou igual a</span><span class="sxs-lookup"><span data-stu-id="f3e2f-160">`x <= y`: Less than or equal</span></span>
    - <span data-ttu-id="f3e2f-161">`x >= y`: é maior que ou igual a</span><span class="sxs-lookup"><span data-stu-id="f3e2f-161">`x >= y`: Greater than or equal</span></span>
    - <span data-ttu-id="f3e2f-162">`x is T`: retornará `true` se `x` for um `T`, caso contrário, `false`</span><span class="sxs-lookup"><span data-stu-id="f3e2f-162">`x is T`: Return `true` if `x` is a `T`, `false` otherwise</span></span>
    - <span data-ttu-id="f3e2f-163">`x as T`: retornará `x` digitado como `T` ou `null` se `x` não for um `T`</span><span class="sxs-lookup"><span data-stu-id="f3e2f-163">`x as T`: Return `x` typed as `T`, or `null` if `x` is not a `T`</span></span>
* <span data-ttu-id="f3e2f-164">Igualdade</span><span class="sxs-lookup"><span data-stu-id="f3e2f-164">Equality</span></span>
    - <span data-ttu-id="f3e2f-165">`x == y`: igual a</span><span class="sxs-lookup"><span data-stu-id="f3e2f-165">`x == y`: Equal</span></span>
    - <span data-ttu-id="f3e2f-166">`x != y`: não é igual a</span><span class="sxs-lookup"><span data-stu-id="f3e2f-166">`x != y`: Not equal</span></span>
* <span data-ttu-id="f3e2f-167">AND lógico</span><span class="sxs-lookup"><span data-stu-id="f3e2f-167">Logical AND</span></span>
    - <span data-ttu-id="f3e2f-168">`x & y`: AND bit a bit inteiro, AND lógico booliano</span><span class="sxs-lookup"><span data-stu-id="f3e2f-168">`x & y`: Integer bitwise AND, boolean logical AND</span></span>
* <span data-ttu-id="f3e2f-169">XOR lógico</span><span class="sxs-lookup"><span data-stu-id="f3e2f-169">Logical XOR</span></span>
    - <span data-ttu-id="f3e2f-170">`x ^ y`: XOR bit a bit inteiro, XOR lógico booliano</span><span class="sxs-lookup"><span data-stu-id="f3e2f-170">`x ^ y`: Integer bitwise XOR, boolean logical XOR</span></span>
* <span data-ttu-id="f3e2f-171">OR lógico</span><span class="sxs-lookup"><span data-stu-id="f3e2f-171">Logical OR</span></span>
    - <span data-ttu-id="f3e2f-172">`x | y`: OR bit a bit inteiro, OR lógico booliano</span><span class="sxs-lookup"><span data-stu-id="f3e2f-172">`x | y`: Integer bitwise OR, boolean logical OR</span></span>
* <span data-ttu-id="f3e2f-173">AND condicional</span><span class="sxs-lookup"><span data-stu-id="f3e2f-173">Conditional AND</span></span>
    - <span data-ttu-id="f3e2f-174">`x && y`: avaliará `y` somente se `x` não for `false`</span><span class="sxs-lookup"><span data-stu-id="f3e2f-174">`x && y`: Evaluates `y` only if `x` is not `false`</span></span>
* <span data-ttu-id="f3e2f-175">OR condicional</span><span class="sxs-lookup"><span data-stu-id="f3e2f-175">Conditional OR</span></span>
    - <span data-ttu-id="f3e2f-176">`x || y`: avaliará `y` somente se `x` não for `true`</span><span class="sxs-lookup"><span data-stu-id="f3e2f-176">`x || y`: Evaluates `y` only if `x` is not `true`</span></span>
* <span data-ttu-id="f3e2f-177">Coalescência nula</span><span class="sxs-lookup"><span data-stu-id="f3e2f-177">Null coalescing</span></span>
    - <span data-ttu-id="f3e2f-178">`x ?? y`: avaliará como `y` se `x` for nulo, caso contrário, como `x`</span><span class="sxs-lookup"><span data-stu-id="f3e2f-178">`x ?? y`: Evaluates to `y` if `x` is null, to `x` otherwise</span></span>
* <span data-ttu-id="f3e2f-179">Condicional</span><span class="sxs-lookup"><span data-stu-id="f3e2f-179">Conditional</span></span>
    - <span data-ttu-id="f3e2f-180">`x ? y : z`: avaliará `y` se `x` for `true`, `z` se `x` for `false`</span><span class="sxs-lookup"><span data-stu-id="f3e2f-180">`x ? y : z`: Evaluates `y` if `x` is `true`, `z` if `x` is `false`</span></span>
* <span data-ttu-id="f3e2f-181">Atribuição ou função anônima</span><span class="sxs-lookup"><span data-stu-id="f3e2f-181">Assignment or anonymous function</span></span>
    - <span data-ttu-id="f3e2f-182">`x = y`: atribuição</span><span class="sxs-lookup"><span data-stu-id="f3e2f-182">`x = y`: Assignment</span></span>
    - <span data-ttu-id="f3e2f-183">`x op= y`: atribuição composta; operadores com suporte</span><span class="sxs-lookup"><span data-stu-id="f3e2f-183">`x op= y`: Compound assignment; supported operators are</span></span>
        - <span data-ttu-id="f3e2f-184">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span><span class="sxs-lookup"><span data-stu-id="f3e2f-184">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span></span>
    - <span data-ttu-id="f3e2f-185">`(T x) => y`: função anônima (expressão lambda)</span><span class="sxs-lookup"><span data-stu-id="f3e2f-185">`(T x) => y`: Anonymous function (lambda expression)</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="f3e2f-186">[Anterior](types-and-variables.md)
[Próximo](statements.md)</span><span class="sxs-lookup"><span data-stu-id="f3e2f-186">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>

