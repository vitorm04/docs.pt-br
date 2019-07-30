---
title: Correspondência padrão
description: Saiba como os padrões são usados F# no para comparar dados com estruturas lógicas, decompor dados em partes constituintes ou extrair informações de dados.
ms.date: 05/16/2016
ms.openlocfilehash: 156bb670e0c494a3d515eab03e2e4672d6743dec
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627302"
---
# <a name="pattern-matching"></a><span data-ttu-id="46a4d-103">Correspondência padrão</span><span class="sxs-lookup"><span data-stu-id="46a4d-103">Pattern Matching</span></span>

<span data-ttu-id="46a4d-104">Padrões são regras para transformar dados de entrada.</span><span class="sxs-lookup"><span data-stu-id="46a4d-104">Patterns are rules for transforming input data.</span></span> <span data-ttu-id="46a4d-105">Eles são usados em toda F# a linguagem para comparar dados com estruturas lógicas, decompor dados em partes constituintes ou extrair informações de dados de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="46a4d-105">They are used throughout the F# language to compare data with a logical structure or structures, decompose data into constituent parts, or extract information from data in various ways.</span></span>

## <a name="remarks"></a><span data-ttu-id="46a4d-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="46a4d-106">Remarks</span></span>

<span data-ttu-id="46a4d-107">Padrões são usados em muitas construções de linguagem, como a `match` expressão.</span><span class="sxs-lookup"><span data-stu-id="46a4d-107">Patterns are used in many language constructs, such as the `match` expression.</span></span> <span data-ttu-id="46a4d-108">Eles são usados quando você está processando argumentos para funções `let` em associações, expressões lambda e nos manipuladores de exceção associados `try...with` à expressão.</span><span class="sxs-lookup"><span data-stu-id="46a4d-108">They are used when you are processing arguments for functions in `let` bindings, lambda expressions, and in the exception handlers associated with the `try...with` expression.</span></span> <span data-ttu-id="46a4d-109">Para obter mais informações, consulte [corresponder expressões](match-expressions.md), [permitir associações](./functions/let-bindings.md), [expressões lambda: A `fun` palavra](./functions/lambda-expressions-the-fun-keyword.md)-chave [e as exceções: A `try...with` expressão](/.exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="46a4d-109">For more information, see [Match Expressions](match-expressions.md), [let Bindings](./functions/let-bindings.md), [Lambda Expressions: The `fun` Keyword](./functions/lambda-expressions-the-fun-keyword.md), and [Exceptions: The `try...with` Expression](/.exception-handling/the-try-with-expression.md).</span></span>

<span data-ttu-id="46a4d-110">Por exemplo, na `match` expressão, o *padrão* é o que segue o símbolo de pipe.</span><span class="sxs-lookup"><span data-stu-id="46a4d-110">For example, in the `match` expression, the *pattern* is what follows the pipe symbol.</span></span>

```fsharp
match expression with
| pattern [ when condition ] -> result-expression
...
```

<span data-ttu-id="46a4d-111">Cada padrão atua como uma regra para transformar a entrada de alguma maneira.</span><span class="sxs-lookup"><span data-stu-id="46a4d-111">Each pattern acts as a rule for transforming input in some way.</span></span> <span data-ttu-id="46a4d-112">`match` Na expressão, cada padrão é examinado, por sua vez, para ver se os dados de entrada são compatíveis com o padrão.</span><span class="sxs-lookup"><span data-stu-id="46a4d-112">In the `match` expression, each pattern is examined in turn to see if the input data is compatible with the pattern.</span></span> <span data-ttu-id="46a4d-113">Se uma correspondência for encontrada, a expressão de resultado será executada.</span><span class="sxs-lookup"><span data-stu-id="46a4d-113">If a match is found, the result expression is executed.</span></span> <span data-ttu-id="46a4d-114">Se uma correspondência não for encontrada, a próxima regra de padrão será testada.</span><span class="sxs-lookup"><span data-stu-id="46a4d-114">If a match is not found, the next pattern rule is tested.</span></span> <span data-ttu-id="46a4d-115">A parte de *condição* opcional quando é explicada em [expressões de correspondência](match-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="46a4d-115">The optional when *condition* part is explained in [Match Expressions](match-expressions.md).</span></span>

<span data-ttu-id="46a4d-116">Os padrões com suporte são mostrados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="46a4d-116">Supported patterns are shown in the following table.</span></span> <span data-ttu-id="46a4d-117">Em tempo de execução, a entrada é testada em relação a cada um dos seguintes padrões na ordem listada na tabela, e os padrões são aplicados recursivamente, de primeiro até o último, conforme aparecem no seu código e da esquerda para a direita para os padrões em cada linha.</span><span class="sxs-lookup"><span data-stu-id="46a4d-117">At run time, the input is tested against each of the following patterns in the order listed in the table, and patterns are applied recursively, from first to last as they appear in your code, and from left to right for the patterns on each line.</span></span>

|<span data-ttu-id="46a4d-118">Nome</span><span class="sxs-lookup"><span data-stu-id="46a4d-118">Name</span></span>|<span data-ttu-id="46a4d-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="46a4d-119">Description</span></span>|<span data-ttu-id="46a4d-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="46a4d-120">Example</span></span>|
|----|-----------|-------|
|<span data-ttu-id="46a4d-121">Padrão de constante</span><span class="sxs-lookup"><span data-stu-id="46a4d-121">Constant pattern</span></span>|<span data-ttu-id="46a4d-122">Qualquer literal numérico, de caractere ou de cadeia de caracteres, uma constante de enumeração ou um identificador literal definido</span><span class="sxs-lookup"><span data-stu-id="46a4d-122">Any numeric, character, or string literal, an enumeration constant, or a defined literal identifier</span></span>|<span data-ttu-id="46a4d-123">`1.0`, `"test"`, `30`, `Color.Red`</span><span class="sxs-lookup"><span data-stu-id="46a4d-123">`1.0`, `"test"`, `30`, `Color.Red`</span></span>|
|<span data-ttu-id="46a4d-124">Padrão de identificador</span><span class="sxs-lookup"><span data-stu-id="46a4d-124">Identifier pattern</span></span>|<span data-ttu-id="46a4d-125">Um valor de case de uma união discriminada, um rótulo de exceção ou um caso de padrão ativo</span><span class="sxs-lookup"><span data-stu-id="46a4d-125">A case value of a discriminated union, an exception label, or an active pattern case</span></span>|`Some(x)`<br /><br />`Failure(msg)`|
|<span data-ttu-id="46a4d-126">Padrão de variável</span><span class="sxs-lookup"><span data-stu-id="46a4d-126">Variable pattern</span></span>|<span data-ttu-id="46a4d-127">*identifier*</span><span class="sxs-lookup"><span data-stu-id="46a4d-127">*identifier*</span></span>|`a`|
|<span data-ttu-id="46a4d-128">`as`padrão</span><span class="sxs-lookup"><span data-stu-id="46a4d-128">`as` pattern</span></span>|<span data-ttu-id="46a4d-129">*padrão* como *identificador*</span><span class="sxs-lookup"><span data-stu-id="46a4d-129">*pattern* as *identifier*</span></span>|`(a, b) as tuple1`|
|<span data-ttu-id="46a4d-130">OU padrão</span><span class="sxs-lookup"><span data-stu-id="46a4d-130">OR pattern</span></span>|<span data-ttu-id="46a4d-131">*pattern1* &#124; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="46a4d-131">*pattern1* &#124; *pattern2*</span></span>|<code>([h] &#124; [h; _])</code>|
|<span data-ttu-id="46a4d-132">E padrão</span><span class="sxs-lookup"><span data-stu-id="46a4d-132">AND pattern</span></span>|<span data-ttu-id="46a4d-133">*pattern1* &amp; *pattern2*</span><span class="sxs-lookup"><span data-stu-id="46a4d-133">*pattern1* &amp; *pattern2*</span></span>|`(a, b) & (_, "test")`|
|<span data-ttu-id="46a4d-134">Padrão de contras</span><span class="sxs-lookup"><span data-stu-id="46a4d-134">Cons pattern</span></span>|<span data-ttu-id="46a4d-135">*identificador* :: *lista-identificador*</span><span class="sxs-lookup"><span data-stu-id="46a4d-135">*identifier* :: *list-identifier*</span></span>|`h :: t`|
|<span data-ttu-id="46a4d-136">Padrão de lista</span><span class="sxs-lookup"><span data-stu-id="46a4d-136">List pattern</span></span>|<span data-ttu-id="46a4d-137">[ *pattern_1*; ... ; *pattern_n* ]</span><span class="sxs-lookup"><span data-stu-id="46a4d-137">[ *pattern_1*; ... ; *pattern_n* ]</span></span>|`[ a; b; c ]`|
|<span data-ttu-id="46a4d-138">Padrão de matriz</span><span class="sxs-lookup"><span data-stu-id="46a4d-138">Array pattern</span></span>|<span data-ttu-id="46a4d-139">[&#124; *pattern_1*; ..; *pattern_n* &#124;]</span><span class="sxs-lookup"><span data-stu-id="46a4d-139">[&#124; *pattern_1*; ..; *pattern_n* &#124;]</span></span>|<code>[&#124; a; b; c &#124;]</code>|
|<span data-ttu-id="46a4d-140">Padrão entre parênteses</span><span class="sxs-lookup"><span data-stu-id="46a4d-140">Parenthesized pattern</span></span>|<span data-ttu-id="46a4d-141">( *pattern* )</span><span class="sxs-lookup"><span data-stu-id="46a4d-141">( *pattern* )</span></span>|`( a )`|
|<span data-ttu-id="46a4d-142">Padrão de tupla</span><span class="sxs-lookup"><span data-stu-id="46a4d-142">Tuple pattern</span></span>|<span data-ttu-id="46a4d-143">( *pattern_1*, ... , *pattern_n* )</span><span class="sxs-lookup"><span data-stu-id="46a4d-143">( *pattern_1*, ... , *pattern_n* )</span></span>|`( a, b )`|
|<span data-ttu-id="46a4d-144">Padrão de registro</span><span class="sxs-lookup"><span data-stu-id="46a4d-144">Record pattern</span></span>|<span data-ttu-id="46a4d-145">{ *identifier1* = *pattern_1*;...; *identifier_n*  =  *pattern_n* }</span><span class="sxs-lookup"><span data-stu-id="46a4d-145">{ *identifier1* = *pattern_1*; ... ; *identifier_n* = *pattern_n* }</span></span>|`{ Name = name; }`|
|<span data-ttu-id="46a4d-146">Padrão de curinga</span><span class="sxs-lookup"><span data-stu-id="46a4d-146">Wildcard pattern</span></span>|<span data-ttu-id="46a4d-147">_</span><span class="sxs-lookup"><span data-stu-id="46a4d-147">_</span></span>|`_`|
|<span data-ttu-id="46a4d-148">Padrão junto com a anotação de tipo</span><span class="sxs-lookup"><span data-stu-id="46a4d-148">Pattern together with type annotation</span></span>|<span data-ttu-id="46a4d-149">*padrão* : *tipo*</span><span class="sxs-lookup"><span data-stu-id="46a4d-149">*pattern* : *type*</span></span>|`a : int`|
|<span data-ttu-id="46a4d-150">Padrão de teste de tipo</span><span class="sxs-lookup"><span data-stu-id="46a4d-150">Type test pattern</span></span>|<span data-ttu-id="46a4d-151">:?</span><span class="sxs-lookup"><span data-stu-id="46a4d-151">:?</span></span> <span data-ttu-id="46a4d-152">*tipo* de [como *identificador* ]</span><span class="sxs-lookup"><span data-stu-id="46a4d-152">*type* [ as *identifier* ]</span></span>|`:? System.DateTime as dt`|
|<span data-ttu-id="46a4d-153">Padrão nulo</span><span class="sxs-lookup"><span data-stu-id="46a4d-153">Null pattern</span></span>|<span data-ttu-id="46a4d-154">nulo</span><span class="sxs-lookup"><span data-stu-id="46a4d-154">null</span></span>|`null`|

## <a name="constant-patterns"></a><span data-ttu-id="46a4d-155">Padrões constantes</span><span class="sxs-lookup"><span data-stu-id="46a4d-155">Constant Patterns</span></span>

<span data-ttu-id="46a4d-156">Os padrões constantes são numéricos, caracteres e literais de cadeia de caracteres, constantes de enumeração (com o nome do tipo de enumeração incluído).</span><span class="sxs-lookup"><span data-stu-id="46a4d-156">Constant patterns are numeric, character, and string literals, enumeration constants (with the enumeration type name included).</span></span> <span data-ttu-id="46a4d-157">Uma `match` expressão que tem apenas padrões constantes pode ser comparada a uma instrução Case em outras linguagens.</span><span class="sxs-lookup"><span data-stu-id="46a4d-157">A `match` expression that has only constant patterns can be compared to a case statement in other languages.</span></span> <span data-ttu-id="46a4d-158">A entrada é comparada com o valor literal e o padrão corresponde se os valores são iguais.</span><span class="sxs-lookup"><span data-stu-id="46a4d-158">The input is compared with the literal value and the pattern matches if the values are equal.</span></span> <span data-ttu-id="46a4d-159">O tipo do literal deve ser compatível com o tipo de entrada.</span><span class="sxs-lookup"><span data-stu-id="46a4d-159">The type of the literal must be compatible with the type of the input.</span></span>

<span data-ttu-id="46a4d-160">O exemplo a seguir demonstra o uso de padrões literais e também usa um padrão variável e um padrão ou.</span><span class="sxs-lookup"><span data-stu-id="46a4d-160">The following example demonstrates the use of literal patterns, and also uses a variable pattern and an OR pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4801.fs)]

<span data-ttu-id="46a4d-161">Outro exemplo de um padrão literal é um padrão baseado em constantes de enumeração.</span><span class="sxs-lookup"><span data-stu-id="46a4d-161">Another example of a literal pattern is a pattern based on enumeration constants.</span></span> <span data-ttu-id="46a4d-162">Você deve especificar o nome do tipo de enumeração ao usar constantes de enumeração.</span><span class="sxs-lookup"><span data-stu-id="46a4d-162">You must specify the enumeration type name when you use enumeration constants.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4802.fs)]

## <a name="identifier-patterns"></a><span data-ttu-id="46a4d-163">Padrões de identificador</span><span class="sxs-lookup"><span data-stu-id="46a4d-163">Identifier Patterns</span></span>

<span data-ttu-id="46a4d-164">Se o padrão for uma cadeia de caracteres que forma um identificador válido, a forma do identificador determinará como o padrão é correspondido.</span><span class="sxs-lookup"><span data-stu-id="46a4d-164">If the pattern is a string of characters that forms a valid identifier, the form of the identifier determines how the pattern is matched.</span></span> <span data-ttu-id="46a4d-165">Se o identificador for maior que um único caractere e começar com um caractere maiúsculo, o compilador tentará fazer uma correspondência com o padrão de identificador.</span><span class="sxs-lookup"><span data-stu-id="46a4d-165">If the identifier is longer than a single character and starts with an uppercase character, the compiler tries to make a match to the identifier pattern.</span></span> <span data-ttu-id="46a4d-166">O identificador desse padrão pode ser um valor marcado com o atributo literal, um caso união discriminado, um identificador de exceção ou um caso de padrão ativo.</span><span class="sxs-lookup"><span data-stu-id="46a4d-166">The identifier for this pattern could be a value marked with the Literal attribute, a discriminated union case, an exception identifier, or an active pattern case.</span></span> <span data-ttu-id="46a4d-167">Se nenhum identificador correspondente for encontrado, a correspondência falhará e a próxima regra de padrão, o padrão variável, será comparada com a entrada.</span><span class="sxs-lookup"><span data-stu-id="46a4d-167">If no matching identifier is found, the match fails and the next pattern rule, the variable pattern, is compared to the input.</span></span>

<span data-ttu-id="46a4d-168">Os padrões de União discriminados podem ser casos nomeados simples ou podem ter um valor, ou uma tupla contendo vários valores.</span><span class="sxs-lookup"><span data-stu-id="46a4d-168">Discriminated union patterns can be simple named cases or they can have a value, or a tuple containing multiple values.</span></span> <span data-ttu-id="46a4d-169">Se houver um valor, você deverá especificar um identificador para o valor.</span><span class="sxs-lookup"><span data-stu-id="46a4d-169">If there is a value, you must specify an identifier for the value.</span></span> <span data-ttu-id="46a4d-170">No caso de uma tupla, você deve fornecer um padrão de tupla com um identificador para cada elemento da tupla ou um identificador com um nome de campo para um ou mais campos de União nomeados.</span><span class="sxs-lookup"><span data-stu-id="46a4d-170">In the case of a tuple, you must supply a tuple pattern with an identifier for each element of the tuple or an identifier with a field name for one or more named union fields.</span></span> <span data-ttu-id="46a4d-171">Consulte os exemplos de código nesta seção para obter exemplos.</span><span class="sxs-lookup"><span data-stu-id="46a4d-171">See the code examples in this section for examples.</span></span>

<span data-ttu-id="46a4d-172">O `option` tipo é uma união discriminada que tem dois `Some` casos e `None`.</span><span class="sxs-lookup"><span data-stu-id="46a4d-172">The `option` type is a discriminated union that has two cases, `Some` and `None`.</span></span> <span data-ttu-id="46a4d-173">Um case (`Some`) tem um valor, mas o outro (`None`) é apenas um caso nomeado.</span><span class="sxs-lookup"><span data-stu-id="46a4d-173">One case (`Some`) has a value, but the other (`None`) is just a named case.</span></span> <span data-ttu-id="46a4d-174">Portanto, `Some` o precisa ter uma variável para o valor associado `Some` ao caso, mas `None` deve aparecer por si só.</span><span class="sxs-lookup"><span data-stu-id="46a4d-174">Therefore, `Some` needs to have a variable for the value associated with the `Some` case, but `None` must appear by itself.</span></span> <span data-ttu-id="46a4d-175">No código a seguir, a variável `var1` recebe o valor obtido pela correspondência `Some` ao caso.</span><span class="sxs-lookup"><span data-stu-id="46a4d-175">In the following code, the variable `var1` is given the value that is obtained by matching to the `Some` case.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4803.fs)]

<span data-ttu-id="46a4d-176">No exemplo a seguir, a `PersonName` união discriminada contém uma mistura de cadeias e caracteres que representam possíveis formas de nomes.</span><span class="sxs-lookup"><span data-stu-id="46a4d-176">In the following example, the `PersonName` discriminated union contains a mixture of strings and characters that represent possible forms of names.</span></span> <span data-ttu-id="46a4d-177">Os casos da união discriminada são `FirstOnly`, `LastOnly`e `FirstLast`.</span><span class="sxs-lookup"><span data-stu-id="46a4d-177">The cases of the discriminated union are `FirstOnly`, `LastOnly`, and `FirstLast`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4804.fs)]

<span data-ttu-id="46a4d-178">Para uniões discriminadas que têm campos nomeados, use o sinal de igual (=) para extrair o valor de um campo nomeado.</span><span class="sxs-lookup"><span data-stu-id="46a4d-178">For discriminated unions that have named fields, you use the equals sign (=) to extract the value of a named field.</span></span> <span data-ttu-id="46a4d-179">Por exemplo, considere uma união discriminada com uma declaração como a seguinte.</span><span class="sxs-lookup"><span data-stu-id="46a4d-179">For example, consider a discriminated union with a declaration like the following.</span></span>

```fsharp
type Shape =
    | Rectangle of height : float * width : float
    | Circle of radius : float
```

<span data-ttu-id="46a4d-180">Você pode usar os campos nomeados em uma expressão de correspondência de padrões da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="46a4d-180">You can use the named fields in a pattern matching expression as follows.</span></span>

```fsharp
let matchShape shape =
    match shape with
    | Rectangle(height = h) -> printfn "Rectangle with length %f" h
    | Circle(r) -> printfn "Circle with radius %f" r
```

<span data-ttu-id="46a4d-181">O uso do campo nomeado é opcional, portanto, no exemplo anterior, ambos `Circle(r)` e `Circle(radius = r)` têm o mesmo efeito.</span><span class="sxs-lookup"><span data-stu-id="46a4d-181">The use of the named field is optional, so in the previous example, both `Circle(r)` and `Circle(radius = r)` have the same effect.</span></span>

<span data-ttu-id="46a4d-182">Quando você especifica vários campos, use o ponto-e-vírgula (;) como um separador.</span><span class="sxs-lookup"><span data-stu-id="46a4d-182">When you specify multiple fields, use the semicolon (;) as a separator.</span></span>

```
match shape with
| Rectangle(height = h; width = w) -> printfn "Rectangle with height %f and width %f" h w
| _ -> ()
```

<span data-ttu-id="46a4d-183">Os padrões ativos permitem definir correspondência de padrões personalizados mais complexos.</span><span class="sxs-lookup"><span data-stu-id="46a4d-183">Active patterns enable you to define more complex custom pattern matching.</span></span> <span data-ttu-id="46a4d-184">Para obter mais informações sobre padrões ativos, consulte [padrões ativos](active-patterns.md).</span><span class="sxs-lookup"><span data-stu-id="46a4d-184">For more information about active patterns, see [Active Patterns](active-patterns.md).</span></span>

<span data-ttu-id="46a4d-185">O caso em que o identificador é uma exceção é usado na correspondência de padrões no contexto de manipuladores de exceção.</span><span class="sxs-lookup"><span data-stu-id="46a4d-185">The case in which the identifier is an exception is used in pattern matching in the context of exception handlers.</span></span> <span data-ttu-id="46a4d-186">Para obter informações sobre correspondência de padrões no tratamento de [exceção, consulte exceções: A `try...with` expressão](/.exception-handling/the-try-with-expression.md).</span><span class="sxs-lookup"><span data-stu-id="46a4d-186">For information about pattern matching in exception handling, see [Exceptions: The `try...with` Expression](/.exception-handling/the-try-with-expression.md).</span></span>

## <a name="variable-patterns"></a><span data-ttu-id="46a4d-187">Padrões de variáveis</span><span class="sxs-lookup"><span data-stu-id="46a4d-187">Variable Patterns</span></span>

<span data-ttu-id="46a4d-188">O padrão variável atribui o valor que está sendo correspondido a um nome de variável, que está disponível para uso na expressão de execução à direita do `->` símbolo.</span><span class="sxs-lookup"><span data-stu-id="46a4d-188">The variable pattern assigns the value being matched to a variable name, which is then available for use in the execution expression to the right of the `->` symbol.</span></span> <span data-ttu-id="46a4d-189">Um padrão variável sozinho corresponde A qualquer entrada, mas padrões de variáveis geralmente aparecem dentro de outros padrões, permitindo, portanto, estruturas mais complexas, como tuplas e matrizes a serem decompostas em variáveis.</span><span class="sxs-lookup"><span data-stu-id="46a4d-189">A variable pattern alone matches any input, but variable patterns often appear within other patterns, therefore enabling more complex structures such as tuples and arrays to be decomposed into variables.</span></span>

<span data-ttu-id="46a4d-190">O exemplo a seguir demonstra um padrão variável dentro de um padrão de tupla.</span><span class="sxs-lookup"><span data-stu-id="46a4d-190">The following example demonstrates a variable pattern within a tuple pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4805.fs)]

## <a name="as-pattern"></a><span data-ttu-id="46a4d-191">como padrão</span><span class="sxs-lookup"><span data-stu-id="46a4d-191">as Pattern</span></span>

<span data-ttu-id="46a4d-192">O `as` padrão é um padrão que tem uma `as` cláusula acrescentada a ele.</span><span class="sxs-lookup"><span data-stu-id="46a4d-192">The `as` pattern is a pattern that has an `as` clause appended to it.</span></span> <span data-ttu-id="46a4d-193">A `as` cláusula associa o valor correspondente a um nome que pode ser usado na expressão de execução de uma `match` expressão ou, no caso em que esse padrão é usado em uma `let` associação, o nome é adicionado como uma associação ao escopo local.</span><span class="sxs-lookup"><span data-stu-id="46a4d-193">The `as` clause binds the matched value to a name that can be used in the execution expression of a `match` expression, or, in the case where this pattern is used in a `let` binding, the name is added as a binding to the local scope.</span></span>

<span data-ttu-id="46a4d-194">O exemplo a seguir usa `as` um padrão.</span><span class="sxs-lookup"><span data-stu-id="46a4d-194">The following example uses an `as` pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4806.fs)]

## <a name="or-pattern"></a><span data-ttu-id="46a4d-195">OU padrão</span><span class="sxs-lookup"><span data-stu-id="46a4d-195">OR Pattern</span></span>

<span data-ttu-id="46a4d-196">O padrão ou é usado quando os dados de entrada podem corresponder a vários padrões e você deseja executar o mesmo código como resultado.</span><span class="sxs-lookup"><span data-stu-id="46a4d-196">The OR pattern is used when input data can match multiple patterns, and you want to execute the same code as a result.</span></span> <span data-ttu-id="46a4d-197">Os tipos de ambos os lados do padrão ou devem ser compatíveis.</span><span class="sxs-lookup"><span data-stu-id="46a4d-197">The types of both sides of the OR pattern must be compatible.</span></span>

<span data-ttu-id="46a4d-198">O exemplo a seguir demonstra o padrão ou.</span><span class="sxs-lookup"><span data-stu-id="46a4d-198">The following example demonstrates the OR pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4807.fs)]

## <a name="and-pattern"></a><span data-ttu-id="46a4d-199">E padrão</span><span class="sxs-lookup"><span data-stu-id="46a4d-199">AND Pattern</span></span>

<span data-ttu-id="46a4d-200">O padrão AND requer que a entrada corresponda a dois padrões.</span><span class="sxs-lookup"><span data-stu-id="46a4d-200">The AND pattern requires that the input match two patterns.</span></span> <span data-ttu-id="46a4d-201">Os tipos de ambos os lados do padrão e devem ser compatíveis.</span><span class="sxs-lookup"><span data-stu-id="46a4d-201">The types of both sides of the AND pattern must be compatible.</span></span>

<span data-ttu-id="46a4d-202">O exemplo a seguir é `detectZeroTuple` como mostrado na seção [padrão de tupla](https://msdn.microsoft.com/library/#tuple) mais adiante neste tópico `var1` , mas aqui e `var2` são obtidos como valores usando o padrão e.</span><span class="sxs-lookup"><span data-stu-id="46a4d-202">The following example is like `detectZeroTuple` shown in the [Tuple Pattern](https://msdn.microsoft.com/library/#tuple) section later in this topic, but here both `var1` and `var2` are obtained as values by using the AND pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4808.fs)]

## <a name="cons-pattern"></a><span data-ttu-id="46a4d-203">Padrão de contras</span><span class="sxs-lookup"><span data-stu-id="46a4d-203">Cons Pattern</span></span>

<span data-ttu-id="46a4d-204">O padrão de contras de contras é usado para decompor uma lista no primeiro elemento, no *cabeçalho*e em uma lista que contém os elementos restantes, a *parte final*.</span><span class="sxs-lookup"><span data-stu-id="46a4d-204">The cons pattern is used to decompose a list into the first element, the *head*, and a list that contains the remaining elements, the *tail*.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4809.fs)]

## <a name="list-pattern"></a><span data-ttu-id="46a4d-205">Padrão de lista</span><span class="sxs-lookup"><span data-stu-id="46a4d-205">List Pattern</span></span>

<span data-ttu-id="46a4d-206">O padrão de lista permite que as listas sejam decompostas em vários elementos.</span><span class="sxs-lookup"><span data-stu-id="46a4d-206">The list pattern enables lists to be decomposed into a number of elements.</span></span> <span data-ttu-id="46a4d-207">O próprio padrão de lista pode corresponder apenas a listas de um número específico de elementos.</span><span class="sxs-lookup"><span data-stu-id="46a4d-207">The list pattern itself can match only lists of a specific number of elements.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4810.fs)]

## <a name="array-pattern"></a><span data-ttu-id="46a4d-208">Padrão de matriz</span><span class="sxs-lookup"><span data-stu-id="46a4d-208">Array Pattern</span></span>

<span data-ttu-id="46a4d-209">O padrão de matriz é semelhante ao padrão de lista e pode ser usado para decompor matrizes de um comprimento específico.</span><span class="sxs-lookup"><span data-stu-id="46a4d-209">The array pattern resembles the list pattern and can be used to decompose arrays of a specific length.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4811.fs)]

## <a name="parenthesized-pattern"></a><span data-ttu-id="46a4d-210">Padrão entre parênteses</span><span class="sxs-lookup"><span data-stu-id="46a4d-210">Parenthesized Pattern</span></span>

<span data-ttu-id="46a4d-211">Os parênteses podem ser agrupados de acordo com os padrões para alcançar a associação desejada.</span><span class="sxs-lookup"><span data-stu-id="46a4d-211">Parentheses can be grouped around patterns to achieve the desired associativity.</span></span> <span data-ttu-id="46a4d-212">No exemplo a seguir, os parênteses são usados para controlar a associação entre um padrão e um padrão de contras.</span><span class="sxs-lookup"><span data-stu-id="46a4d-212">In the following example, parentheses are used to control associativity between an AND pattern and a cons pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4812.fs)]

## <a name="tuple-pattern"></a><span data-ttu-id="46a4d-213">Padrão de tupla</span><span class="sxs-lookup"><span data-stu-id="46a4d-213">Tuple Pattern</span></span>

<span data-ttu-id="46a4d-214">O padrão de tupla corresponde à entrada no formulário de tupla e permite que a tupla seja decomposta em seus elementos constituintes usando variáveis de correspondência de padrões para cada posição na tupla.</span><span class="sxs-lookup"><span data-stu-id="46a4d-214">The tuple pattern matches input in tuple form and enables the tuple to be decomposed into its constituent elements by using pattern matching variables for each position in the tuple.</span></span>

<span data-ttu-id="46a4d-215">O exemplo a seguir demonstra o padrão de tupla e também usa padrões literais, padrões variáveis e o padrão curinga.</span><span class="sxs-lookup"><span data-stu-id="46a4d-215">The following example demonstrates the tuple pattern and also uses literal patterns, variable patterns, and the wildcard pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4813.fs)]

## <a name="record-pattern"></a><span data-ttu-id="46a4d-216">Padrão de registro</span><span class="sxs-lookup"><span data-stu-id="46a4d-216">Record Pattern</span></span>

<span data-ttu-id="46a4d-217">O padrão de registro é usado para decompor registros para extrair os valores dos campos.</span><span class="sxs-lookup"><span data-stu-id="46a4d-217">The record pattern is used to decompose records to extract the values of fields.</span></span> <span data-ttu-id="46a4d-218">O padrão não precisa fazer referência a todos os campos do registro; os campos omitidos simplesmente não participam da correspondência e não são extraídos.</span><span class="sxs-lookup"><span data-stu-id="46a4d-218">The pattern does not have to reference all fields of the record; any omitted fields just do not participate in matching and are not extracted.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4814.fs)]

## <a name="wildcard-pattern"></a><span data-ttu-id="46a4d-219">Padrão de curinga</span><span class="sxs-lookup"><span data-stu-id="46a4d-219">Wildcard Pattern</span></span>

<span data-ttu-id="46a4d-220">O padrão de caractere curinga é representado pelo caractere de`_`sublinhado () e corresponde a qualquer entrada, assim como o padrão de variável, exceto que a entrada é descartada em vez de atribuída a uma variável.</span><span class="sxs-lookup"><span data-stu-id="46a4d-220">The wildcard pattern is represented by the underscore (`_`) character and matches any input, just like the variable pattern, except that the input is discarded instead of assigned to a variable.</span></span> <span data-ttu-id="46a4d-221">O padrão de caractere curinga geralmente é usado em outros padrões como um espaço reservado para valores que não são necessários na expressão à direita do `->` símbolo.</span><span class="sxs-lookup"><span data-stu-id="46a4d-221">The wildcard pattern is often used within other patterns as a placeholder for values that are not needed in the expression to the right of the `->` symbol.</span></span> <span data-ttu-id="46a4d-222">O padrão curinga também é usado frequentemente no final de uma lista de padrões para corresponder a qualquer entrada sem correspondência.</span><span class="sxs-lookup"><span data-stu-id="46a4d-222">The wildcard pattern is also frequently used at the end of a list of patterns to match any unmatched input.</span></span> <span data-ttu-id="46a4d-223">O padrão de curinga é demonstrado em muitos exemplos de código neste tópico.</span><span class="sxs-lookup"><span data-stu-id="46a4d-223">The wildcard pattern is demonstrated in many code examples in this topic.</span></span> <span data-ttu-id="46a4d-224">Consulte o código anterior para obter um exemplo.</span><span class="sxs-lookup"><span data-stu-id="46a4d-224">See the preceding code for one example.</span></span>

## <a name="patterns-that-have-type-annotations"></a><span data-ttu-id="46a4d-225">Padrões que têm anotações de tipo</span><span class="sxs-lookup"><span data-stu-id="46a4d-225">Patterns That Have Type Annotations</span></span>

<span data-ttu-id="46a4d-226">Os padrões podem ter anotações de tipo.</span><span class="sxs-lookup"><span data-stu-id="46a4d-226">Patterns can have type annotations.</span></span> <span data-ttu-id="46a4d-227">Eles se comportam como outras anotações de tipo e inferência de guia como outras anotações de tipo.</span><span class="sxs-lookup"><span data-stu-id="46a4d-227">These behave like other type annotations and guide inference like other type annotations.</span></span> <span data-ttu-id="46a4d-228">Os parênteses são necessários em relação a anotações de tipo em padrões.</span><span class="sxs-lookup"><span data-stu-id="46a4d-228">Parentheses are required around type annotations in patterns.</span></span> <span data-ttu-id="46a4d-229">O código a seguir mostra um padrão que tem uma anotação de tipo.</span><span class="sxs-lookup"><span data-stu-id="46a4d-229">The following code shows a pattern that has a type annotation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4815.fs)]

## <a name="type-test-pattern"></a><span data-ttu-id="46a4d-230">Padrão de teste de tipo</span><span class="sxs-lookup"><span data-stu-id="46a4d-230">Type Test Pattern</span></span>

<span data-ttu-id="46a4d-231">O padrão de teste de tipo é usado para corresponder à entrada em relação a um tipo.</span><span class="sxs-lookup"><span data-stu-id="46a4d-231">The type test pattern is used to match the input against a type.</span></span> <span data-ttu-id="46a4d-232">Se o tipo de entrada for uma correspondência (ou um tipo derivado) do tipo especificado no padrão, a correspondência será realizada com sucesso.</span><span class="sxs-lookup"><span data-stu-id="46a4d-232">If the input type is a match to (or a derived type of) the type specified in the pattern, the match succeeds.</span></span>

<span data-ttu-id="46a4d-233">O exemplo a seguir demonstra o tipo de padrão de teste.</span><span class="sxs-lookup"><span data-stu-id="46a4d-233">The following example demonstrates the type test pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4816.fs)]

## <a name="null-pattern"></a><span data-ttu-id="46a4d-234">Padrão nulo</span><span class="sxs-lookup"><span data-stu-id="46a4d-234">Null Pattern</span></span>

<span data-ttu-id="46a4d-235">O padrão nulo corresponde ao valor nulo que pode aparecer quando você está trabalhando com tipos que permitem um valor nulo.</span><span class="sxs-lookup"><span data-stu-id="46a4d-235">The null pattern matches the null value that can appear when you are working with types that allow a null value.</span></span> <span data-ttu-id="46a4d-236">Padrões nulos são usados frequentemente quando interoperam com código .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="46a4d-236">Null patterns are frequently used when interoperating with .NET Framework code.</span></span> <span data-ttu-id="46a4d-237">Por exemplo, o valor de retorno de uma API do .net pode ser a entrada `match` para uma expressão.</span><span class="sxs-lookup"><span data-stu-id="46a4d-237">For example, the return value of a .NET API might be the input to a `match` expression.</span></span> <span data-ttu-id="46a4d-238">Você pode controlar o fluxo do programa com base em se o valor de retorno é nulo e também em outras características do valor retornado.</span><span class="sxs-lookup"><span data-stu-id="46a4d-238">You can control program flow based on whether the return value is null, and also on other characteristics of the returned value.</span></span> <span data-ttu-id="46a4d-239">Você pode usar o padrão nulo para impedir que valores nulos se propaguem para o restante do seu programa.</span><span class="sxs-lookup"><span data-stu-id="46a4d-239">You can use the null pattern to prevent null values from propagating to the rest of your program.</span></span>

<span data-ttu-id="46a4d-240">O exemplo a seguir usa o padrão nulo e o padrão de variável.</span><span class="sxs-lookup"><span data-stu-id="46a4d-240">The following example uses the null pattern and the variable pattern.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4817.fs)]

## <a name="see-also"></a><span data-ttu-id="46a4d-241">Consulte também</span><span class="sxs-lookup"><span data-stu-id="46a4d-241">See also</span></span>

- [<span data-ttu-id="46a4d-242">Expressões Match</span><span class="sxs-lookup"><span data-stu-id="46a4d-242">Match Expressions</span></span>](match-expressions.md)
- [<span data-ttu-id="46a4d-243">Padrões Ativos</span><span class="sxs-lookup"><span data-stu-id="46a4d-243">Active Patterns</span></span>](active-patterns.md)
- [<span data-ttu-id="46a4d-244">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="46a4d-244">F# Language Reference</span></span>](index.md)
