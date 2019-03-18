---
title: Expressões C# - um tour pela linguagem C#
description: expressões, operandos e operadores são blocos de compilação da linguagem C#
ms.date: 11/06/2016
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 7a7f65eb7ba3da3f9630bbcb92d8578d60d2095d
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2019
ms.locfileid: "57846591"
---
# <a name="expressions"></a><span data-ttu-id="f0e6a-103">Expressões</span><span class="sxs-lookup"><span data-stu-id="f0e6a-103">Expressions</span></span>

<span data-ttu-id="f0e6a-104">*Expressões* são construídas a partir de *operandos* e *operadores*.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-104">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="f0e6a-105">Os operadores de uma expressão indicam quais operações devem ser aplicadas aos operandos.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-105">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="f0e6a-106">Exemplos de operadores incluem `+`, `-`, `*`, `/` e `new`.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-106">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="f0e6a-107">Exemplos de operandos incluem literais, campos, variáveis locais e expressões.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-107">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="f0e6a-108">Quando uma expressão contiver vários operadores, a *precedência* dos operadores controla a ordem na qual os operadores individuais são avaliados.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-108">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="f0e6a-109">Por exemplo, a expressão `x + y * z` é avaliada como `x + (y * z)` porque o operador `*` tem precedência maior do que o operador `+`.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-109">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="f0e6a-110">Quando ocorre um operando entre dois operadores com a mesma precedência, a *associatividade* dos operadores controla a ordem na qual as operações são executadas:</span><span class="sxs-lookup"><span data-stu-id="f0e6a-110">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

* <span data-ttu-id="f0e6a-111">Exceto para os operadores de atribuição, todos os operadores binários são *associativos à esquerda*, o que significa que as operações são executadas da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-111">Except for the assignment operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="f0e6a-112">Por exemplo, `x + y + z` é avaliado como `(x + y) + z`.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-112">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
* <span data-ttu-id="f0e6a-113">Os operadores de atribuição e o operador condicional (`?:`) são *associativos à direita*, o que significa que as operações são executadas da direita para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-113">The assignment operators and the conditional operator (`?:`) are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="f0e6a-114">Por exemplo, `x = y = z` é avaliado como `x = (y = z)`.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-114">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="f0e6a-115">Precedência e associatividade podem ser controladas usando parênteses.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-115">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="f0e6a-116">Por exemplo, `x + y * z` primeiro multiplica `y` por `z` e, em seguida, adiciona o resultado a `x`, mas `(x + y) * z` primeiro adiciona `x` e `y` e, em seguida, multiplica o resultado por `z`.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-116">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="f0e6a-117">A maioria dos operadores pode ser *sobrecarregada*.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-117">Most operators can be *overloaded*.</span></span> <span data-ttu-id="f0e6a-118">A sobrecarga de operador permite que implementações de operador definidas pelo usuário sejam especificadas para operações em que um ou ambos os operandos são de um tipo struct ou de classe definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-118">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="f0e6a-119">O item a seguir resume os operadores do C#, listando as categorias de operador em ordem de precedência da mais alta para a mais baixa.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-119">The following summarizes C#’s operators, listing the operator categories in order of precedence from highest to lowest.</span></span> <span data-ttu-id="f0e6a-120">Operadores na mesma categoria têm a mesma precedência.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-120">Operators in the same category have equal precedence.</span></span> <span data-ttu-id="f0e6a-121">Em cada categoria está uma lista de expressões da categoria juntamente com a descrição do tipo de expressão.</span><span class="sxs-lookup"><span data-stu-id="f0e6a-121">Under each category is a list of expressions in that category along with the description of that expression type.</span></span>

* <span data-ttu-id="f0e6a-122">Primária</span><span class="sxs-lookup"><span data-stu-id="f0e6a-122">Primary</span></span>
    - <span data-ttu-id="f0e6a-123">`x.m`: Acesso de membros</span><span class="sxs-lookup"><span data-stu-id="f0e6a-123">`x.m`: Member access</span></span>
    - <span data-ttu-id="f0e6a-124">`x(...)`: Invocação de método e delegado</span><span class="sxs-lookup"><span data-stu-id="f0e6a-124">`x(...)`: Method and delegate invocation</span></span>
    - <span data-ttu-id="f0e6a-125">`x[...]`: Acesso de matriz e indexador</span><span class="sxs-lookup"><span data-stu-id="f0e6a-125">`x[...]`: Array and indexer access</span></span>
    - <span data-ttu-id="f0e6a-126">`x++`: Pós-incremento</span><span class="sxs-lookup"><span data-stu-id="f0e6a-126">`x++`: Post-increment</span></span>
    - <span data-ttu-id="f0e6a-127">`x--`: Pós-decremento</span><span class="sxs-lookup"><span data-stu-id="f0e6a-127">`x--`: Post-decrement</span></span>
    - <span data-ttu-id="f0e6a-128">`new T(...)`: Criação de objeto e delegado</span><span class="sxs-lookup"><span data-stu-id="f0e6a-128">`new T(...)`: Object and delegate creation</span></span>
    - <span data-ttu-id="f0e6a-129">`new T(...){...}`: Criação de objeto com inicializador</span><span class="sxs-lookup"><span data-stu-id="f0e6a-129">`new T(...){...}`: Object creation with initializer</span></span>
    - <span data-ttu-id="f0e6a-130">`new {...}`:  Inicializador de objeto anônimo</span><span class="sxs-lookup"><span data-stu-id="f0e6a-130">`new {...}`:  Anonymous object initializer</span></span>
    - <span data-ttu-id="f0e6a-131">`new T[...]`: Criação de matriz</span><span class="sxs-lookup"><span data-stu-id="f0e6a-131">`new T[...]`: Array creation</span></span>
    - <span data-ttu-id="f0e6a-132">`typeof(T)`: Obter objeto <xref:System.Type> para `T`</span><span class="sxs-lookup"><span data-stu-id="f0e6a-132">`typeof(T)`: Obtain <xref:System.Type> object for `T`</span></span>
    - <span data-ttu-id="f0e6a-133">`checked(x)`: Avalia expressão no contexto selecionado</span><span class="sxs-lookup"><span data-stu-id="f0e6a-133">`checked(x)`: Evaluate expression in checked context</span></span>
    - <span data-ttu-id="f0e6a-134">`unchecked(x)`: Avalia expressão no contexto desmarcado</span><span class="sxs-lookup"><span data-stu-id="f0e6a-134">`unchecked(x)`: Evaluate expression in unchecked context</span></span>
    - <span data-ttu-id="f0e6a-135">`default(T)`: Obter valor padrão do tipo `T`</span><span class="sxs-lookup"><span data-stu-id="f0e6a-135">`default(T)`: Obtain default value of type `T`</span></span>
    - <span data-ttu-id="f0e6a-136">`delegate {...}`: Função anônima (método anônimo)</span><span class="sxs-lookup"><span data-stu-id="f0e6a-136">`delegate {...}`: Anonymous function (anonymous method)</span></span>
* <span data-ttu-id="f0e6a-137">Unário</span><span class="sxs-lookup"><span data-stu-id="f0e6a-137">Unary</span></span>
    - <span data-ttu-id="f0e6a-138">`+x`: Identidade</span><span class="sxs-lookup"><span data-stu-id="f0e6a-138">`+x`: Identity</span></span>
    - <span data-ttu-id="f0e6a-139">`-x`: Negação</span><span class="sxs-lookup"><span data-stu-id="f0e6a-139">`-x`: Negation</span></span>
    - <span data-ttu-id="f0e6a-140">`!x`: Negação lógica</span><span class="sxs-lookup"><span data-stu-id="f0e6a-140">`!x`: Logical negation</span></span>
    - <span data-ttu-id="f0e6a-141">`~x`: Negação bit a bit</span><span class="sxs-lookup"><span data-stu-id="f0e6a-141">`~x`: Bitwise negation</span></span>
    - <span data-ttu-id="f0e6a-142">`++x`: Pré-incremento</span><span class="sxs-lookup"><span data-stu-id="f0e6a-142">`++x`: Pre-increment</span></span>
    - <span data-ttu-id="f0e6a-143">`--x`: Pré-decremento</span><span class="sxs-lookup"><span data-stu-id="f0e6a-143">`--x`: Pre-decrement</span></span>
    - <span data-ttu-id="f0e6a-144">`(T)x`: Converter explicitamente `x` no tipo `T`</span><span class="sxs-lookup"><span data-stu-id="f0e6a-144">`(T)x`: Explicitly convert `x` to type `T`</span></span>
    - <span data-ttu-id="f0e6a-145">`await x`: Aguardar assincronamente `x` para concluir</span><span class="sxs-lookup"><span data-stu-id="f0e6a-145">`await x`: Asynchronously wait for `x` to complete</span></span>
* <span data-ttu-id="f0e6a-146">Multiplicativo</span><span class="sxs-lookup"><span data-stu-id="f0e6a-146">Multiplicative</span></span>
    - <span data-ttu-id="f0e6a-147">`x * y`: Multiplicação</span><span class="sxs-lookup"><span data-stu-id="f0e6a-147">`x * y`: Multiplication</span></span>
    - <span data-ttu-id="f0e6a-148">`x / y`: Divisão</span><span class="sxs-lookup"><span data-stu-id="f0e6a-148">`x / y`: Division</span></span>
    - <span data-ttu-id="f0e6a-149">`x % y`: Restante</span><span class="sxs-lookup"><span data-stu-id="f0e6a-149">`x % y`: Remainder</span></span>
* <span data-ttu-id="f0e6a-150">Aditivo</span><span class="sxs-lookup"><span data-stu-id="f0e6a-150">Additive</span></span>
    - <span data-ttu-id="f0e6a-151">`x + y`: Adição, concatenação de cadeia de caracteres, combinação de delegados</span><span class="sxs-lookup"><span data-stu-id="f0e6a-151">`x + y`: Addition, string concatenation, delegate combination</span></span>
    - <span data-ttu-id="f0e6a-152">`x – y`: Subtração, remoção de delegado</span><span class="sxs-lookup"><span data-stu-id="f0e6a-152">`x – y`: Subtraction, delegate removal</span></span>
* <span data-ttu-id="f0e6a-153">Shift</span><span class="sxs-lookup"><span data-stu-id="f0e6a-153">Shift</span></span>
    - <span data-ttu-id="f0e6a-154">`x << y`: Shift esquerdo</span><span class="sxs-lookup"><span data-stu-id="f0e6a-154">`x << y`: Shift left</span></span>
    - <span data-ttu-id="f0e6a-155">`x >> y`: Shift direito</span><span class="sxs-lookup"><span data-stu-id="f0e6a-155">`x >> y`: Shift right</span></span>
* <span data-ttu-id="f0e6a-156">Teste de tipo e relacional</span><span class="sxs-lookup"><span data-stu-id="f0e6a-156">Relational and type testing</span></span>
    - <span data-ttu-id="f0e6a-157">`x < y`: Menor que</span><span class="sxs-lookup"><span data-stu-id="f0e6a-157">`x < y`: Less than</span></span>
    - <span data-ttu-id="f0e6a-158">`x > y`: Maior que</span><span class="sxs-lookup"><span data-stu-id="f0e6a-158">`x > y`: Greater than</span></span>
    - <span data-ttu-id="f0e6a-159">`x <= y`: Menor ou igual a</span><span class="sxs-lookup"><span data-stu-id="f0e6a-159">`x <= y`: Less than or equal</span></span>
    - <span data-ttu-id="f0e6a-160">`x >= y`: Maior que ou igual a</span><span class="sxs-lookup"><span data-stu-id="f0e6a-160">`x >= y`: Greater than or equal</span></span>
    - <span data-ttu-id="f0e6a-161">`x is T`: Retorna `true` se `x` for um `T`, caso contrário, `false`</span><span class="sxs-lookup"><span data-stu-id="f0e6a-161">`x is T`: Return `true` if `x` is a `T`, `false` otherwise</span></span>
    - <span data-ttu-id="f0e6a-162">`x as T`: Retorna `x` digitado como `T` ou `null`, se `x` não for um `T`</span><span class="sxs-lookup"><span data-stu-id="f0e6a-162">`x as T`: Return `x` typed as `T`, or `null` if `x` is not a `T`</span></span>
* <span data-ttu-id="f0e6a-163">Igualdade</span><span class="sxs-lookup"><span data-stu-id="f0e6a-163">Equality</span></span>
    - <span data-ttu-id="f0e6a-164">`x == y`: Igual a</span><span class="sxs-lookup"><span data-stu-id="f0e6a-164">`x == y`: Equal</span></span>
    - <span data-ttu-id="f0e6a-165">`x != y`: Diferente de</span><span class="sxs-lookup"><span data-stu-id="f0e6a-165">`x != y`: Not equal</span></span>
* <span data-ttu-id="f0e6a-166">AND lógico</span><span class="sxs-lookup"><span data-stu-id="f0e6a-166">Logical AND</span></span>
    - <span data-ttu-id="f0e6a-167">`x & y`: AND bit a bit inteiro, AND lógico booliano</span><span class="sxs-lookup"><span data-stu-id="f0e6a-167">`x & y`: Integer bitwise AND, boolean logical AND</span></span>
* <span data-ttu-id="f0e6a-168">XOR lógico</span><span class="sxs-lookup"><span data-stu-id="f0e6a-168">Logical XOR</span></span>
    - <span data-ttu-id="f0e6a-169">`x ^ y`: XOR bit a bit inteiro, XOR lógico booliano</span><span class="sxs-lookup"><span data-stu-id="f0e6a-169">`x ^ y`: Integer bitwise XOR, boolean logical XOR</span></span>
* <span data-ttu-id="f0e6a-170">OR lógico</span><span class="sxs-lookup"><span data-stu-id="f0e6a-170">Logical OR</span></span>
    - <span data-ttu-id="f0e6a-171">`x | y`: OR bit a bit inteiro, OR lógico booliano</span><span class="sxs-lookup"><span data-stu-id="f0e6a-171">`x | y`: Integer bitwise OR, boolean logical OR</span></span>
* <span data-ttu-id="f0e6a-172">AND condicional</span><span class="sxs-lookup"><span data-stu-id="f0e6a-172">Conditional AND</span></span>
    - <span data-ttu-id="f0e6a-173">`x && y`: Avalia `y` somente se `x` não for `false`</span><span class="sxs-lookup"><span data-stu-id="f0e6a-173">`x && y`: Evaluates `y` only if `x` is not `false`</span></span>
* <span data-ttu-id="f0e6a-174">OR condicional</span><span class="sxs-lookup"><span data-stu-id="f0e6a-174">Conditional OR</span></span>
    - <span data-ttu-id="f0e6a-175">`x || y`: Avalia `y` somente se `x` não for `true`</span><span class="sxs-lookup"><span data-stu-id="f0e6a-175">`x || y`: Evaluates `y` only if `x` is not `true`</span></span>
* <span data-ttu-id="f0e6a-176">Coalescência nula</span><span class="sxs-lookup"><span data-stu-id="f0e6a-176">Null coalescing</span></span>
    - <span data-ttu-id="f0e6a-177">`x ?? y`: Avalia como `y` se `x` for nulo, caso contrário, como `x`</span><span class="sxs-lookup"><span data-stu-id="f0e6a-177">`x ?? y`: Evaluates to `y` if `x` is null, to `x` otherwise</span></span>
* <span data-ttu-id="f0e6a-178">Condicional</span><span class="sxs-lookup"><span data-stu-id="f0e6a-178">Conditional</span></span>
    - <span data-ttu-id="f0e6a-179">`x ? y : z`: Avalia `y` se `x` for `true`, `z` se `x` for `false`</span><span class="sxs-lookup"><span data-stu-id="f0e6a-179">`x ? y : z`: Evaluates `y` if `x` is `true`, `z` if `x` is `false`</span></span>
* <span data-ttu-id="f0e6a-180">Atribuição ou função anônima</span><span class="sxs-lookup"><span data-stu-id="f0e6a-180">Assignment or anonymous function</span></span>
    - <span data-ttu-id="f0e6a-181">`x = y`: Atribuição</span><span class="sxs-lookup"><span data-stu-id="f0e6a-181">`x = y`: Assignment</span></span>
    - <span data-ttu-id="f0e6a-182">`x op= y`: Atribuição composta; operadores com suporte</span><span class="sxs-lookup"><span data-stu-id="f0e6a-182">`x op= y`: Compound assignment; supported operators are</span></span>
        - <span data-ttu-id="f0e6a-183">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span><span class="sxs-lookup"><span data-stu-id="f0e6a-183">`*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`</span></span>
    - <span data-ttu-id="f0e6a-184">`(T x) => y`: Função anônima (expressão lambda)</span><span class="sxs-lookup"><span data-stu-id="f0e6a-184">`(T x) => y`: Anonymous function (lambda expression)</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="f0e6a-185">[Anterior](types-and-variables.md)
> [Próximo](statements.md)</span><span class="sxs-lookup"><span data-stu-id="f0e6a-185">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>
