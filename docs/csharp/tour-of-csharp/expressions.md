---
title: Expressões C# - um tour pela linguagem C#
description: expressões, operandos e operadores são blocos de compilação da linguagem C#
ms.date: 11/06/2016
ms.assetid: 20d5eb10-7381-47b9-ad90-f1cc895aa27e
ms.openlocfilehash: 4ffe947a4cb8c36a5925a4b3846486e44a9d8ec4
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/11/2019
ms.locfileid: "59480749"
---
# <a name="expressions"></a><span data-ttu-id="e786d-103">Expressões</span><span class="sxs-lookup"><span data-stu-id="e786d-103">Expressions</span></span>

<span data-ttu-id="e786d-104">*Expressões* são construídas a partir de *operandos* e *operadores*.</span><span class="sxs-lookup"><span data-stu-id="e786d-104">*Expressions* are constructed from *operands* and *operators*.</span></span> <span data-ttu-id="e786d-105">Os operadores de uma expressão indicam quais operações devem ser aplicadas aos operandos.</span><span class="sxs-lookup"><span data-stu-id="e786d-105">The operators of an expression indicate which operations to apply to the operands.</span></span> <span data-ttu-id="e786d-106">Exemplos de operadores incluem `+`, `-`, `*`, `/` e `new`.</span><span class="sxs-lookup"><span data-stu-id="e786d-106">Examples of operators include `+`, `-`, `*`, `/`, and `new`.</span></span> <span data-ttu-id="e786d-107">Exemplos de operandos incluem literais, campos, variáveis locais e expressões.</span><span class="sxs-lookup"><span data-stu-id="e786d-107">Examples of operands include literals, fields, local variables, and expressions.</span></span>

<span data-ttu-id="e786d-108">Quando uma expressão contiver vários operadores, a *precedência* dos operadores controla a ordem na qual os operadores individuais são avaliados.</span><span class="sxs-lookup"><span data-stu-id="e786d-108">When an expression contains multiple operators, the *precedence* of the operators controls the order in which the individual operators are evaluated.</span></span> <span data-ttu-id="e786d-109">Por exemplo, a expressão `x + y * z` é avaliada como `x + (y * z)` porque o operador `*` tem precedência maior do que o operador `+`.</span><span class="sxs-lookup"><span data-stu-id="e786d-109">For example, the expression `x + y * z` is evaluated as `x + (y * z)` because the `*` operator has higher precedence than the `+` operator.</span></span>

<span data-ttu-id="e786d-110">Quando ocorre um operando entre dois operadores com a mesma precedência, a *associatividade* dos operadores controla a ordem na qual as operações são executadas:</span><span class="sxs-lookup"><span data-stu-id="e786d-110">When an operand occurs between two operators with the same precedence, the *associativity* of the operators controls the order in which the operations are performed:</span></span>

* <span data-ttu-id="e786d-111">Exceto para os operadores de atribuição, todos os operadores binários são *associativos à esquerda*, o que significa que as operações são executadas da esquerda para a direita.</span><span class="sxs-lookup"><span data-stu-id="e786d-111">Except for the assignment operators, all binary operators are *left-associative*, meaning that operations are performed from left to right.</span></span> <span data-ttu-id="e786d-112">Por exemplo, `x + y + z` é avaliado como `(x + y) + z`.</span><span class="sxs-lookup"><span data-stu-id="e786d-112">For example, `x + y + z` is evaluated as `(x + y) + z`.</span></span>
* <span data-ttu-id="e786d-113">Os operadores de atribuição e o operador condicional (`?:`) são *associativos à direita*, o que significa que as operações são executadas da direita para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="e786d-113">The assignment operators and the conditional operator (`?:`) are *right-associative*, meaning that operations are performed from right to left.</span></span> <span data-ttu-id="e786d-114">Por exemplo, `x = y = z` é avaliado como `x = (y = z)`.</span><span class="sxs-lookup"><span data-stu-id="e786d-114">For example, `x = y = z` is evaluated as `x = (y = z)`.</span></span>

<span data-ttu-id="e786d-115">Precedência e associatividade podem ser controladas usando parênteses.</span><span class="sxs-lookup"><span data-stu-id="e786d-115">Precedence and associativity can be controlled using parentheses.</span></span> <span data-ttu-id="e786d-116">Por exemplo, `x + y * z` primeiro multiplica `y` por `z` e, em seguida, adiciona o resultado a `x`, mas `(x + y) * z` primeiro adiciona `x` e `y` e, em seguida, multiplica o resultado por `z`.</span><span class="sxs-lookup"><span data-stu-id="e786d-116">For example, `x + y * z` first multiplies `y` by `z` and then adds the result to `x`, but `(x + y) * z` first adds `x` and `y` and then multiplies the result by `z`.</span></span>

<span data-ttu-id="e786d-117">A maioria dos operadores pode ser *sobrecarregada*.</span><span class="sxs-lookup"><span data-stu-id="e786d-117">Most operators can be *overloaded*.</span></span> <span data-ttu-id="e786d-118">A sobrecarga de operador permite que implementações de operador definidas pelo usuário sejam especificadas para operações em que um ou ambos os operandos são de um tipo struct ou de classe definida pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="e786d-118">Operator overloading permits user-defined operator implementations to be specified for operations where one or both of the operands are of a user-defined class or struct type.</span></span>

<span data-ttu-id="e786d-119">O item a seguir resume os operadores do C#, listando as categorias de operador em ordem de precedência da mais alta para a mais baixa.</span><span class="sxs-lookup"><span data-stu-id="e786d-119">The following summarizes C#’s operators, listing the operator categories in order of precedence from highest to lowest.</span></span> <span data-ttu-id="e786d-120">Operadores na mesma categoria têm a mesma precedência.</span><span class="sxs-lookup"><span data-stu-id="e786d-120">Operators in the same category have equal precedence.</span></span> <span data-ttu-id="e786d-121">Em cada categoria está uma lista de expressões da categoria juntamente com a descrição do tipo de expressão.</span><span class="sxs-lookup"><span data-stu-id="e786d-121">Under each category is a list of expressions in that category along with the description of that expression type.</span></span>

* <span data-ttu-id="e786d-122">Primária</span><span class="sxs-lookup"><span data-stu-id="e786d-122">Primary</span></span>
  - `x.m`<span data-ttu-id="e786d-123">: Acesso de membros</span><span class="sxs-lookup"><span data-stu-id="e786d-123">: Member access</span></span>
  - `x(...)`<span data-ttu-id="e786d-124">: Invocação de método e delegado</span><span class="sxs-lookup"><span data-stu-id="e786d-124">: Method and delegate invocation</span></span>
  - `x[...]`<span data-ttu-id="e786d-125">: Acesso de matriz e indexador</span><span class="sxs-lookup"><span data-stu-id="e786d-125">: Array and indexer access</span></span>
  - `x++`<span data-ttu-id="e786d-126">: Pós-incremento</span><span class="sxs-lookup"><span data-stu-id="e786d-126">: Post-increment</span></span>
  - `x--`<span data-ttu-id="e786d-127">: Pós-decremento</span><span class="sxs-lookup"><span data-stu-id="e786d-127">: Post-decrement</span></span>
  - `new T(...)`<span data-ttu-id="e786d-128">: Criação de objeto e delegado</span><span class="sxs-lookup"><span data-stu-id="e786d-128">: Object and delegate creation</span></span>
  - `new T(...){...}`<span data-ttu-id="e786d-129">: Criação de objeto com inicializador</span><span class="sxs-lookup"><span data-stu-id="e786d-129">: Object creation with initializer</span></span>
  - `new {...}`<span data-ttu-id="e786d-130">:  Inicializador de objeto anônimo</span><span class="sxs-lookup"><span data-stu-id="e786d-130">:  Anonymous object initializer</span></span>
  - `new T[...]`<span data-ttu-id="e786d-131">: Criação de matriz</span><span class="sxs-lookup"><span data-stu-id="e786d-131">: Array creation</span></span>
  - `typeof(T)`<span data-ttu-id="e786d-132">: Obter objeto <xref:System.Type> para</span><span class="sxs-lookup"><span data-stu-id="e786d-132">: Obtain <xref:System.Type> object for</span></span> `T`
  - `checked(x)`<span data-ttu-id="e786d-133">: Avalia expressão no contexto selecionado</span><span class="sxs-lookup"><span data-stu-id="e786d-133">: Evaluate expression in checked context</span></span>
  - `unchecked(x)`<span data-ttu-id="e786d-134">: Avalia expressão no contexto desmarcado</span><span class="sxs-lookup"><span data-stu-id="e786d-134">: Evaluate expression in unchecked context</span></span>
  - `default(T)`<span data-ttu-id="e786d-135">: Obter valor padrão do tipo</span><span class="sxs-lookup"><span data-stu-id="e786d-135">: Obtain default value of type</span></span> `T`
  - `delegate {...}`<span data-ttu-id="e786d-136">: Função anônima (método anônimo)</span><span class="sxs-lookup"><span data-stu-id="e786d-136">: Anonymous function (anonymous method)</span></span>
* <span data-ttu-id="e786d-137">Unário</span><span class="sxs-lookup"><span data-stu-id="e786d-137">Unary</span></span>
  - `+x`<span data-ttu-id="e786d-138">: Identidade</span><span class="sxs-lookup"><span data-stu-id="e786d-138">: Identity</span></span>
  - `-x`<span data-ttu-id="e786d-139">: Negação</span><span class="sxs-lookup"><span data-stu-id="e786d-139">: Negation</span></span>
  - `!x`<span data-ttu-id="e786d-140">: Negação lógica</span><span class="sxs-lookup"><span data-stu-id="e786d-140">: Logical negation</span></span>
  - `~x`<span data-ttu-id="e786d-141">: Negação bit a bit</span><span class="sxs-lookup"><span data-stu-id="e786d-141">: Bitwise negation</span></span>
  - `++x`<span data-ttu-id="e786d-142">: Pré-incremento</span><span class="sxs-lookup"><span data-stu-id="e786d-142">: Pre-increment</span></span>
  - `--x`<span data-ttu-id="e786d-143">: Pré-decremento</span><span class="sxs-lookup"><span data-stu-id="e786d-143">: Pre-decrement</span></span>
  - `(T)x`<span data-ttu-id="e786d-144">: Converter explicitamente `x` no tipo</span><span class="sxs-lookup"><span data-stu-id="e786d-144">: Explicitly convert `x` to type</span></span> `T`
  - `await x`<span data-ttu-id="e786d-145">: Aguardar assincronamente `x` para concluir</span><span class="sxs-lookup"><span data-stu-id="e786d-145">: Asynchronously wait for `x` to complete</span></span>
* <span data-ttu-id="e786d-146">Multiplicativo</span><span class="sxs-lookup"><span data-stu-id="e786d-146">Multiplicative</span></span>
  - `x * y`<span data-ttu-id="e786d-147">: Multiplicação</span><span class="sxs-lookup"><span data-stu-id="e786d-147">: Multiplication</span></span>
  - `x / y`<span data-ttu-id="e786d-148">: Divisão</span><span class="sxs-lookup"><span data-stu-id="e786d-148">: Division</span></span>
  - `x % y`<span data-ttu-id="e786d-149">: Restante</span><span class="sxs-lookup"><span data-stu-id="e786d-149">: Remainder</span></span>
* <span data-ttu-id="e786d-150">Aditivo</span><span class="sxs-lookup"><span data-stu-id="e786d-150">Additive</span></span>
  - `x + y`<span data-ttu-id="e786d-151">: Adição, concatenação de cadeia de caracteres, combinação de delegados</span><span class="sxs-lookup"><span data-stu-id="e786d-151">: Addition, string concatenation, delegate combination</span></span>
  - `x – y`<span data-ttu-id="e786d-152">: Subtração, remoção de delegado</span><span class="sxs-lookup"><span data-stu-id="e786d-152">: Subtraction, delegate removal</span></span>
* <span data-ttu-id="e786d-153">Shift</span><span class="sxs-lookup"><span data-stu-id="e786d-153">Shift</span></span>
  - `x << y`<span data-ttu-id="e786d-154">: Shift esquerdo</span><span class="sxs-lookup"><span data-stu-id="e786d-154">: Shift left</span></span>
  - `x >> y`<span data-ttu-id="e786d-155">: Shift direito</span><span class="sxs-lookup"><span data-stu-id="e786d-155">: Shift right</span></span>
* <span data-ttu-id="e786d-156">Teste de tipo e relacional</span><span class="sxs-lookup"><span data-stu-id="e786d-156">Relational and type testing</span></span>
  - `x < y`<span data-ttu-id="e786d-157">: Menor que</span><span class="sxs-lookup"><span data-stu-id="e786d-157">: Less than</span></span>
  - `x > y`<span data-ttu-id="e786d-158">: Maior que</span><span class="sxs-lookup"><span data-stu-id="e786d-158">: Greater than</span></span>
  - `x <= y`<span data-ttu-id="e786d-159">: Menor ou igual a</span><span class="sxs-lookup"><span data-stu-id="e786d-159">: Less than or equal</span></span>
  - `x >= y`<span data-ttu-id="e786d-160">: Maior que ou igual a</span><span class="sxs-lookup"><span data-stu-id="e786d-160">: Greater than or equal</span></span>
  - `x is T`<span data-ttu-id="e786d-161">: Retorna `true` se `x` for um `T`, caso contrário, `false`</span><span class="sxs-lookup"><span data-stu-id="e786d-161">: Return `true` if `x` is a `T`, `false` otherwise</span></span>
  - `x as T`<span data-ttu-id="e786d-162">: Retorna `x` digitado como `T` ou `null`, se `x` não for um</span><span class="sxs-lookup"><span data-stu-id="e786d-162">: Return `x` typed as `T`, or `null` if `x` is not a</span></span> `T`
* <span data-ttu-id="e786d-163">Igualdade</span><span class="sxs-lookup"><span data-stu-id="e786d-163">Equality</span></span>
  - `x == y`<span data-ttu-id="e786d-164">: Igual a</span><span class="sxs-lookup"><span data-stu-id="e786d-164">: Equal</span></span>
  - `x != y`<span data-ttu-id="e786d-165">: Diferente de</span><span class="sxs-lookup"><span data-stu-id="e786d-165">: Not equal</span></span>
* <span data-ttu-id="e786d-166">AND lógico</span><span class="sxs-lookup"><span data-stu-id="e786d-166">Logical AND</span></span>
  - `x & y`<span data-ttu-id="e786d-167">: AND bit a bit inteiro, AND lógico booliano</span><span class="sxs-lookup"><span data-stu-id="e786d-167">: Integer bitwise AND, boolean logical AND</span></span>
* <span data-ttu-id="e786d-168">XOR lógico</span><span class="sxs-lookup"><span data-stu-id="e786d-168">Logical XOR</span></span>
  - `x ^ y`<span data-ttu-id="e786d-169">: XOR bit a bit inteiro, XOR lógico booliano</span><span class="sxs-lookup"><span data-stu-id="e786d-169">: Integer bitwise XOR, boolean logical XOR</span></span>
* <span data-ttu-id="e786d-170">OR lógico</span><span class="sxs-lookup"><span data-stu-id="e786d-170">Logical OR</span></span>
  - `x | y`<span data-ttu-id="e786d-171">: OR bit a bit inteiro, OR lógico booliano</span><span class="sxs-lookup"><span data-stu-id="e786d-171">: Integer bitwise OR, boolean logical OR</span></span>
* <span data-ttu-id="e786d-172">AND condicional</span><span class="sxs-lookup"><span data-stu-id="e786d-172">Conditional AND</span></span>
  - `x && y`<span data-ttu-id="e786d-173">: Avalia `y` somente se `x` não for</span><span class="sxs-lookup"><span data-stu-id="e786d-173">: Evaluates `y` only if `x` is not</span></span> `false`
* <span data-ttu-id="e786d-174">OR condicional</span><span class="sxs-lookup"><span data-stu-id="e786d-174">Conditional OR</span></span>
  - `x || y`<span data-ttu-id="e786d-175">: Avalia `y` somente se `x` não for</span><span class="sxs-lookup"><span data-stu-id="e786d-175">: Evaluates `y` only if `x` is not</span></span> `true`
* <span data-ttu-id="e786d-176">Coalescência nula</span><span class="sxs-lookup"><span data-stu-id="e786d-176">Null coalescing</span></span>
  - `x ?? y`<span data-ttu-id="e786d-177">: Avalia como `y` se `x` for nulo, caso contrário, como `x`</span><span class="sxs-lookup"><span data-stu-id="e786d-177">: Evaluates to `y` if `x` is null, to `x` otherwise</span></span>
* <span data-ttu-id="e786d-178">Condicional</span><span class="sxs-lookup"><span data-stu-id="e786d-178">Conditional</span></span>
  - `x ? y : z`<span data-ttu-id="e786d-179">: Avalia `y` se `x` for `true`, `z` se `x` for</span><span class="sxs-lookup"><span data-stu-id="e786d-179">: Evaluates `y` if `x` is `true`, `z` if `x` is</span></span> `false`
* <span data-ttu-id="e786d-180">Atribuição ou função anônima</span><span class="sxs-lookup"><span data-stu-id="e786d-180">Assignment or anonymous function</span></span>
  - `x = y`<span data-ttu-id="e786d-181">: Atribuição</span><span class="sxs-lookup"><span data-stu-id="e786d-181">: Assignment</span></span>
  - `x op= y`<span data-ttu-id="e786d-182">: Atribuição composta; operadores com suporte</span><span class="sxs-lookup"><span data-stu-id="e786d-182">: Compound assignment; supported operators are</span></span>
    - `*=`   `/=`   `%=`   `+=`   `-=`   `<<=`   `>>=`   `&=`  `^=`  `|=`
  - `(T x) => y`<span data-ttu-id="e786d-183">: Função anônima (expressão lambda)</span><span class="sxs-lookup"><span data-stu-id="e786d-183">: Anonymous function (lambda expression)</span></span>

> [!div class="step-by-step"]
> <span data-ttu-id="e786d-184">[Anterior](types-and-variables.md)
> [Próximo](statements.md)</span><span class="sxs-lookup"><span data-stu-id="e786d-184">[Previous](types-and-variables.md)
[Next](statements.md)</span></span>
