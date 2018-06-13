---
title: if-else (Referência de C#)
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
ms.openlocfilehash: eb8fe4c3a02cab8f8c887ec37244bede04b8a663
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218736"
---
# <a name="if-else-c-reference"></a><span data-ttu-id="f5afd-102">if-else (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="f5afd-102">if-else (C# Reference)</span></span>
<span data-ttu-id="f5afd-103">Uma instrução `if` identifica qual instrução executar com base no valor de uma expressão `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="f5afd-103">An `if` statement identifies which statement to run based on the value of a `Boolean` expression.</span></span> <span data-ttu-id="f5afd-104">No exemplo a seguir, a variável `Boolean` `result` deve ser definida como `true` e, em seguida, verificada na instrução `if`.</span><span class="sxs-lookup"><span data-stu-id="f5afd-104">In the following example, the `Boolean` variable `result` is set to `true` and then checked in the `if` statement.</span></span> <span data-ttu-id="f5afd-105">A saída é `The condition is true`.</span><span class="sxs-lookup"><span data-stu-id="f5afd-105">The output is `The condition is true`.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_1.cs)]  
  
 <span data-ttu-id="f5afd-106">Você pode executar os exemplos neste tópico colocando-os no método `Main` de um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="f5afd-106">You can run the examples in this topic by placing them in the `Main` method of a console app.</span></span>  
  
 <span data-ttu-id="f5afd-107">Uma instrução `if` no C# pode ocorrer de duas formas, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="f5afd-107">An `if` statement in C# can take two forms, as the following example shows.</span></span>  
  
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
  
 <span data-ttu-id="f5afd-108">Em uma instrução `if-else`, se `condition` for avaliada como verdadeira, a `then-statement` será executada.</span><span class="sxs-lookup"><span data-stu-id="f5afd-108">In an `if-else` statement, if `condition` evaluates to true, the `then-statement` runs.</span></span> <span data-ttu-id="f5afd-109">Se `condition` for falsa, a `else-statement` será executada.</span><span class="sxs-lookup"><span data-stu-id="f5afd-109">If `condition` is false, the `else-statement` runs.</span></span> <span data-ttu-id="f5afd-110">Como `condition` não pode ser verdadeira e falsa simultaneamente, a `then-statement` e a `else-statement` de uma instrução `if-else` nunca podem ser executadas juntas.</span><span class="sxs-lookup"><span data-stu-id="f5afd-110">Because `condition` can’t be simultaneously true and false, the `then-statement` and the `else-statement` of an `if-else` statement can never both run.</span></span> <span data-ttu-id="f5afd-111">Após `then-statement` ou `else-statement` ser executada, o controle é transferido para a próxima instrução após a instrução `if`.</span><span class="sxs-lookup"><span data-stu-id="f5afd-111">After the `then-statement` or the `else-statement` runs, control is transferred to the next statement after the `if` statement.</span></span>  
  
 <span data-ttu-id="f5afd-112">Em uma instrução `if` que não inclui uma instrução `else`, se `condition` for verdadeira, a `then-statement` será executada.</span><span class="sxs-lookup"><span data-stu-id="f5afd-112">In an `if` statement that doesn’t include an `else` statement, if `condition` is true, the `then-statement` runs.</span></span> <span data-ttu-id="f5afd-113">Se `condition` for falsa, o controle será transferido para a próxima instrução após a instrução `if`.</span><span class="sxs-lookup"><span data-stu-id="f5afd-113">If `condition` is false, control is transferred to the next statement after the `if` statement.</span></span>  
  
 <span data-ttu-id="f5afd-114">Tanto a `then-statement` como a `else-statement` podem consistir em uma única instrução ou várias instruções entre chaves (`{}`).</span><span class="sxs-lookup"><span data-stu-id="f5afd-114">Both the `then-statement` and the `else-statement` can consist of a single statement or multiple statements that are enclosed in braces (`{}`).</span></span> <span data-ttu-id="f5afd-115">Para uma única instrução, as chaves são opcionais, mas recomendadas.</span><span class="sxs-lookup"><span data-stu-id="f5afd-115">For a single statement, the braces are optional but recommended.</span></span>  
  
 <span data-ttu-id="f5afd-116">A instrução ou instruções na `then-statement` e na `else-statement` podem ser de qualquer tipo, incluindo outra instrução `if` aninhada na instrução `if` original.</span><span class="sxs-lookup"><span data-stu-id="f5afd-116">The statement or statements in the `then-statement` and the `else-statement` can be of any kind, including another `if` statement nested inside the original `if` statement.</span></span> <span data-ttu-id="f5afd-117">Em instruções `if` aninhadas, cada cláusula `else` pertence ao último `if` que não tem um `else` correspondente.</span><span class="sxs-lookup"><span data-stu-id="f5afd-117">In nested `if` statements, each `else` clause belongs to the last `if` that doesn’t have a corresponding `else`.</span></span> <span data-ttu-id="f5afd-118">No exemplo a seguir, `Result1` aparecerá se `m > 10` e `n > 20` forem avaliadas como verdadeiras.</span><span class="sxs-lookup"><span data-stu-id="f5afd-118">In the following example, `Result1` appears if both `m > 10` and `n > 20` evaluate to true.</span></span> <span data-ttu-id="f5afd-119">Se `m > 10` for verdadeiro, mas `n > 20` for falso, `Result2` será exibido.</span><span class="sxs-lookup"><span data-stu-id="f5afd-119">If `m > 10` is true but `n > 20` is false, `Result2` appears.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_2.cs)]  
  
 <span data-ttu-id="f5afd-120">Se, em vez disso, você desejar que `Result2` apareça quando `(m > 10)` for falso, pode especificar essa associação usando chaves para estabelecer o início e o fim da instrução `if` aninhada, como o exemplo a seguir mostra.</span><span class="sxs-lookup"><span data-stu-id="f5afd-120">If, instead, you want `Result2` to appear when `(m > 10)` is false, you can specify that association by using braces to establish the start and end of the nested `if` statement, as the following example shows.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_3.cs)]  
  
 <span data-ttu-id="f5afd-121">`Result2` aparecerá se a condição `(m > 10)` for avaliada como falsa.</span><span class="sxs-lookup"><span data-stu-id="f5afd-121">`Result2` appears if the condition `(m > 10)` evaluates to false.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5afd-122">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f5afd-122">Example</span></span>  
 <span data-ttu-id="f5afd-123">No exemplo a seguir, você insere um caractere do teclado e o programa usa uma instrução `if` aninhada para determinar se o caractere de entrada é um caractere alfabético.</span><span class="sxs-lookup"><span data-stu-id="f5afd-123">In the following example, you enter a character from the keyboard, and the program uses a nested `if` statement to determine whether the input character is an alphabetic character.</span></span> <span data-ttu-id="f5afd-124">Se o caractere de entrada for um caractere alfabético, o programa verificará se o caractere de entrada está em maiúscula ou minúscula.</span><span class="sxs-lookup"><span data-stu-id="f5afd-124">If the input character is an alphabetic character, the program checks whether the input character is lowercase or uppercase.</span></span> <span data-ttu-id="f5afd-125">Será exibida uma mensagem para cada caso.</span><span class="sxs-lookup"><span data-stu-id="f5afd-125">A message appears for each case.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_4.cs)]  
  
## <a name="example"></a><span data-ttu-id="f5afd-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f5afd-126">Example</span></span>  
 <span data-ttu-id="f5afd-127">Você também pode aninhar uma instrução `if` dentro de um bloco else, como mostra o código parcial a seguir.</span><span class="sxs-lookup"><span data-stu-id="f5afd-127">You also can nest an `if` statement inside an else block, as the following partial code shows.</span></span> <span data-ttu-id="f5afd-128">O exemplo aninha instruções `if` em dois blocos else e um bloco then.</span><span class="sxs-lookup"><span data-stu-id="f5afd-128">The example nests `if` statements inside two else blocks and one then block.</span></span> <span data-ttu-id="f5afd-129">Os comentários especificam quais condições são verdadeiras ou falsas em cada bloco.</span><span class="sxs-lookup"><span data-stu-id="f5afd-129">The comments specify which conditions are true or false in each block.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_5.cs)]  
  
## <a name="example"></a><span data-ttu-id="f5afd-130">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f5afd-130">Example</span></span>  
 <span data-ttu-id="f5afd-131">O exemplo a seguir determina se um caractere de entrada é um número, uma letra maiúscula ou uma letra minúscula.</span><span class="sxs-lookup"><span data-stu-id="f5afd-131">The following example determines whether an input character is a lowercase letter, an uppercase letter, or a number.</span></span> <span data-ttu-id="f5afd-132">Se todas as três condições forem falsas, o caractere não será um caractere alfanumérico.</span><span class="sxs-lookup"><span data-stu-id="f5afd-132">If all three conditions are false, the character isn’t an alphanumeric character.</span></span> <span data-ttu-id="f5afd-133">O exemplo exibe uma mensagem para cada caso.</span><span class="sxs-lookup"><span data-stu-id="f5afd-133">The example displays a message for each case.</span></span>  
  
 [!code-csharp[csrefKeywordsSelection#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_6.cs)]  
  
 <span data-ttu-id="f5afd-134">Assim como uma instrução no bloco else ou no bloco then pode ser qualquer instrução válida, você pode usar qualquer expressão booliana válida para a condição.</span><span class="sxs-lookup"><span data-stu-id="f5afd-134">Just as a statement in the else block or the then block can be any valid statement, you can use any valid Boolean expression for the condition.</span></span> <span data-ttu-id="f5afd-135">Você pode usar operadores lógicos como [&&](../../../csharp/language-reference/operators/conditional-and-operator.md), [&](../../../csharp/language-reference/operators/and-operator.md), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), [&#124;](../../../csharp/language-reference/operators/or-operator.md) e [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span><span class="sxs-lookup"><span data-stu-id="f5afd-135">You can use logical operators such as [&&](../../../csharp/language-reference/operators/conditional-and-operator.md), [&](../../../csharp/language-reference/operators/and-operator.md), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), [&#124;](../../../csharp/language-reference/operators/or-operator.md) and [!](../../../csharp/language-reference/operators/logical-negation-operator.md)</span></span> <span data-ttu-id="f5afd-136">para criar condições compostas.</span><span class="sxs-lookup"><span data-stu-id="f5afd-136">to make compound conditions.</span></span> <span data-ttu-id="f5afd-137">O código a seguir mostra exemplos.</span><span class="sxs-lookup"><span data-stu-id="f5afd-137">The following code shows examples.</span></span>  
  
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
  
## <a name="c-language-specification"></a><span data-ttu-id="f5afd-138">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="f5afd-138">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f5afd-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5afd-139">See Also</span></span>  
 [<span data-ttu-id="f5afd-140">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="f5afd-140">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="f5afd-141">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="f5afd-141">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f5afd-142">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="f5afd-142">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="f5afd-143">Operador ?:</span><span class="sxs-lookup"><span data-stu-id="f5afd-143">?: Operator</span></span>](../../../csharp/language-reference/operators/conditional-operator.md)  
 [<span data-ttu-id="f5afd-144">Instrução if-else (C++)</span><span class="sxs-lookup"><span data-stu-id="f5afd-144">if-else Statement (C++)</span></span>](/cpp/cpp/if-else-statement-cpp)  
 [<span data-ttu-id="f5afd-145">switch</span><span class="sxs-lookup"><span data-stu-id="f5afd-145">switch</span></span>](../../../csharp/language-reference/keywords/switch.md)
