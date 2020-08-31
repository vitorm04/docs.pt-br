---
description: if-else – Referência de C#
title: if-else – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- if_CSharpKeyword
- else
- else_CSharpKeyword
- if
helpviewer_keywords:
- else keyword [C#]
- if keyword [C#]
ms.assetid: d9a1d562-8cf5-4bd4-9ba7-8ad970cd25b2
ms.openlocfilehash: e2de84807a049bd47ea277db9fb010d0c2e4857d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118501"
---
# <a name="if-else-c-reference"></a><span data-ttu-id="cfae8-103">if-else (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="cfae8-103">if-else (C# Reference)</span></span>

<span data-ttu-id="cfae8-104">Uma instrução `if` identifica qual instrução executar com base no valor de uma expressão booliana.</span><span class="sxs-lookup"><span data-stu-id="cfae8-104">An `if` statement identifies which statement to run based on the value of a Boolean expression.</span></span> <span data-ttu-id="cfae8-105">No exemplo a seguir, a variável `bool``condition` deve ser definida como `true` e, em seguida, verificada na instrução `if`.</span><span class="sxs-lookup"><span data-stu-id="cfae8-105">In the following example, the `bool` variable `condition` is set to `true` and then checked in the `if` statement.</span></span> <span data-ttu-id="cfae8-106">A saída é `The variable is set to true.`.</span><span class="sxs-lookup"><span data-stu-id="cfae8-106">The output is `The variable is set to true.`.</span></span>

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

<span data-ttu-id="cfae8-107">Você pode executar os exemplos neste tópico colocando-os no método `Main` de um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="cfae8-107">You can run the examples in this topic by placing them in the `Main` method of a console app.</span></span>

<span data-ttu-id="cfae8-108">Uma instrução `if` no C# pode ocorrer de duas formas, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="cfae8-108">An `if` statement in C# can take two forms, as the following example shows.</span></span>

```csharp
// if-else statement
if (condition)
{
    then-statement;
}
else
{
    else-statement;
}
// Next statement in the program.

// if statement without an else
if (condition)
{
    then-statement;
}
// Next statement in the program.
```

<span data-ttu-id="cfae8-109">Em uma instrução `if-else`, se `condition` for avaliada como verdadeira, a `then-statement` será executada.</span><span class="sxs-lookup"><span data-stu-id="cfae8-109">In an `if-else` statement, if `condition` evaluates to true, the `then-statement` runs.</span></span> <span data-ttu-id="cfae8-110">Se `condition` for falsa, a `else-statement` será executada.</span><span class="sxs-lookup"><span data-stu-id="cfae8-110">If `condition` is false, the `else-statement` runs.</span></span> <span data-ttu-id="cfae8-111">Como `condition` não pode ser verdadeira e falsa simultaneamente, a `then-statement` e a `else-statement` de uma instrução `if-else` nunca podem ser executadas juntas.</span><span class="sxs-lookup"><span data-stu-id="cfae8-111">Because `condition` can’t be simultaneously true and false, the `then-statement` and the `else-statement` of an `if-else` statement can never both run.</span></span> <span data-ttu-id="cfae8-112">Após `then-statement` ou `else-statement` ser executada, o controle é transferido para a próxima instrução após a instrução `if`.</span><span class="sxs-lookup"><span data-stu-id="cfae8-112">After the `then-statement` or the `else-statement` runs, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="cfae8-113">Em uma instrução `if` que não inclui uma instrução `else`, se `condition` for verdadeira, a `then-statement` será executada.</span><span class="sxs-lookup"><span data-stu-id="cfae8-113">In an `if` statement that doesn’t include an `else` statement, if `condition` is true, the `then-statement` runs.</span></span> <span data-ttu-id="cfae8-114">Se `condition` for falsa, o controle será transferido para a próxima instrução após a instrução `if`.</span><span class="sxs-lookup"><span data-stu-id="cfae8-114">If `condition` is false, control is transferred to the next statement after the `if` statement.</span></span>

<span data-ttu-id="cfae8-115">Tanto a `then-statement` como a `else-statement` podem consistir em uma única instrução ou várias instruções entre chaves (`{}`).</span><span class="sxs-lookup"><span data-stu-id="cfae8-115">Both the `then-statement` and the `else-statement` can consist of a single statement or multiple statements that are enclosed in braces (`{}`).</span></span> <span data-ttu-id="cfae8-116">Para uma única instrução, as chaves são opcionais, mas recomendadas.</span><span class="sxs-lookup"><span data-stu-id="cfae8-116">For a single statement, the braces are optional but recommended.</span></span>

<span data-ttu-id="cfae8-117">A instrução ou instruções na `then-statement` e na `else-statement` podem ser de qualquer tipo, incluindo outra instrução `if` aninhada na instrução `if` original.</span><span class="sxs-lookup"><span data-stu-id="cfae8-117">The statement or statements in the `then-statement` and the `else-statement` can be of any kind, including another `if` statement nested inside the original `if` statement.</span></span> <span data-ttu-id="cfae8-118">Em instruções `if` aninhadas, cada cláusula `else` pertence ao último `if` que não tem um `else` correspondente.</span><span class="sxs-lookup"><span data-stu-id="cfae8-118">In nested `if` statements, each `else` clause belongs to the last `if` that doesn’t have a corresponding `else`.</span></span> <span data-ttu-id="cfae8-119">No exemplo a seguir, `Result1` aparecerá se `m > 10` e `n > 20` forem avaliadas como verdadeiras.</span><span class="sxs-lookup"><span data-stu-id="cfae8-119">In the following example, `Result1` appears if both `m > 10` and `n > 20` evaluate to true.</span></span> <span data-ttu-id="cfae8-120">Se `m > 10` for verdadeiro, mas `n > 20` for falso, `Result2` será exibido.</span><span class="sxs-lookup"><span data-stu-id="cfae8-120">If `m > 10` is true but `n > 20` is false, `Result2` appears.</span></span>

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

<span data-ttu-id="cfae8-121">Se, em vez disso, você desejar que `Result2` apareça quando `(m > 10)` for falso, pode especificar essa associação usando chaves para estabelecer o início e o fim da instrução `if` aninhada, como o exemplo a seguir mostra.</span><span class="sxs-lookup"><span data-stu-id="cfae8-121">If, instead, you want `Result2` to appear when `(m > 10)` is false, you can specify that association by using braces to establish the start and end of the nested `if` statement, as the following example shows.</span></span>

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

<span data-ttu-id="cfae8-122">`Result2` aparecerá se a condição `(m > 10)` for avaliada como falsa.</span><span class="sxs-lookup"><span data-stu-id="cfae8-122">`Result2` appears if the condition `(m > 10)` evaluates to false.</span></span>

## <a name="example"></a><span data-ttu-id="cfae8-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cfae8-123">Example</span></span>

<span data-ttu-id="cfae8-124">No exemplo a seguir, você insere um caractere do teclado e o programa usa uma instrução `if` aninhada para determinar se o caractere de entrada é um caractere alfabético.</span><span class="sxs-lookup"><span data-stu-id="cfae8-124">In the following example, you enter a character from the keyboard, and the program uses a nested `if` statement to determine whether the input character is an alphabetic character.</span></span> <span data-ttu-id="cfae8-125">Se o caractere de entrada for um caractere alfabético, o programa verificará se o caractere de entrada está em maiúscula ou minúscula.</span><span class="sxs-lookup"><span data-stu-id="cfae8-125">If the input character is an alphabetic character, the program checks whether the input character is lowercase or uppercase.</span></span> <span data-ttu-id="cfae8-126">Será exibida uma mensagem para cada caso.</span><span class="sxs-lookup"><span data-stu-id="cfae8-126">A message appears for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a><span data-ttu-id="cfae8-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cfae8-127">Example</span></span>

<span data-ttu-id="cfae8-128">Você também pode aninhar uma `if` instrução dentro de um bloco else, como mostra o código parcial a seguir.</span><span class="sxs-lookup"><span data-stu-id="cfae8-128">You can also nest an `if` statement inside an else block, as the following partial code shows.</span></span> <span data-ttu-id="cfae8-129">O exemplo aninha instruções `if` em dois blocos else e um bloco then.</span><span class="sxs-lookup"><span data-stu-id="cfae8-129">The example nests `if` statements inside two else blocks and one then block.</span></span> <span data-ttu-id="cfae8-130">Os comentários especificam quais condições são verdadeiras ou falsas em cada bloco.</span><span class="sxs-lookup"><span data-stu-id="cfae8-130">The comments specify which conditions are true or false in each block.</span></span>

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a><span data-ttu-id="cfae8-131">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cfae8-131">Example</span></span>

<span data-ttu-id="cfae8-132">O exemplo a seguir determina se um caractere de entrada é um número, uma letra maiúscula ou uma letra minúscula.</span><span class="sxs-lookup"><span data-stu-id="cfae8-132">The following example determines whether an input character is a lowercase letter, an uppercase letter, or a number.</span></span> <span data-ttu-id="cfae8-133">Se todas as três condições forem falsas, o caractere não será um caractere alfanumérico.</span><span class="sxs-lookup"><span data-stu-id="cfae8-133">If all three conditions are false, the character isn’t an alphanumeric character.</span></span> <span data-ttu-id="cfae8-134">O exemplo exibe uma mensagem para cada caso.</span><span class="sxs-lookup"><span data-stu-id="cfae8-134">The example displays a message for each case.</span></span>

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

<span data-ttu-id="cfae8-135">Assim como uma instrução no bloco else ou no bloco then pode ser qualquer instrução válida, você pode usar qualquer expressão booliana válida para a condição.</span><span class="sxs-lookup"><span data-stu-id="cfae8-135">Just as a statement in the else block or the then block can be any valid statement, you can use any valid Boolean expression for the condition.</span></span> <span data-ttu-id="cfae8-136">Você pode usar [operadores lógicos](../operators/boolean-logical-operators.md) , como,,,, `!` `&&` `||` `&` `|` e `^` para tomar condições compostas.</span><span class="sxs-lookup"><span data-stu-id="cfae8-136">You can use [logical operators](../operators/boolean-logical-operators.md) such as `!`, `&&`, `||`, `&`, `|`, and `^` to make compound conditions.</span></span> <span data-ttu-id="cfae8-137">O código a seguir mostra exemplos.</span><span class="sxs-lookup"><span data-stu-id="cfae8-137">The following code shows examples.</span></span>

```csharp
// NOT
bool result = true;
if (!result)
{
    Console.WriteLine("The condition is true (result is false).");
}
else
{
    Console.WriteLine("The condition is false (result is true).");
}

// Short-circuit AND
int m = 9;
int n = 7;
int p = 5;
if (m >= n && m >= p)
{
    Console.WriteLine("Nothing is larger than m.");
}

// AND and NOT
if (m >= n && !(p > m))
{
    Console.WriteLine("Nothing is larger than m.");
}

// Short-circuit OR
if (m > n || m > p)
{
    Console.WriteLine("m isn't the smallest.");
}

// NOT and OR
m = 4;
if (!(m >= n || m >= p))
{
    Console.WriteLine("Now m is the smallest.");
}
// Output:
// The condition is false (result is true).
// Nothing is larger than m.
// Nothing is larger than m.
// m isn't the smallest.
// Now m is the smallest.
```

## <a name="c-language-specification"></a><span data-ttu-id="cfae8-138">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="cfae8-138">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="cfae8-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="cfae8-139">See also</span></span>

- [<span data-ttu-id="cfae8-140">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="cfae8-140">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cfae8-141">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="cfae8-141">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cfae8-142">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="cfae8-142">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="cfae8-143">Operador?:</span><span class="sxs-lookup"><span data-stu-id="cfae8-143">?: Operator</span></span>](../operators/conditional-operator.md)
- [<span data-ttu-id="cfae8-144">Instrução if-else (C++)</span><span class="sxs-lookup"><span data-stu-id="cfae8-144">if-else Statement (C++)</span></span>](/cpp/cpp/if-else-statement-cpp)
- [<span data-ttu-id="cfae8-145">switch</span><span class="sxs-lookup"><span data-stu-id="cfae8-145">switch</span></span>](switch.md)
