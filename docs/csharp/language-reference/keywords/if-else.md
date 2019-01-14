---
title: if-else – Referência de C#
ms.custom: seodec18
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
ms.openlocfilehash: ccb783d8d478b14078ab6fe09f12e480c12ac06b
ms.sourcegitcommit: d09c77414e9e4fc72c79b04deee7a756a120674e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54084765"
---
# <a name="if-else-c-reference"></a>if-else (Referência de C#)

Uma instrução `if` identifica qual instrução executar com base no valor de uma expressão booliana. No exemplo a seguir, a variável `bool` `condition` deve ser definida como `true` e, em seguida, verificada na instrução `if`. A saída é `The variable is set to true.`.

[!code-csharp[csrefKeywordsSelection#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#1)]

Você pode executar os exemplos neste tópico colocando-os no método `Main` de um aplicativo de console.

Uma instrução `if` no C# pode ocorrer de duas formas, como mostra o exemplo a seguir.

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

Em uma instrução `if-else`, se `condition` for avaliada como verdadeira, a `then-statement` será executada. Se `condition` for falsa, a `else-statement` será executada. Como `condition` não pode ser verdadeira e falsa simultaneamente, a `then-statement` e a `else-statement` de uma instrução `if-else` nunca podem ser executadas juntas. Após `then-statement` ou `else-statement` ser executada, o controle é transferido para a próxima instrução após a instrução `if`.

Em uma instrução `if` que não inclui uma instrução `else`, se `condition` for verdadeira, a `then-statement` será executada. Se `condition` for falsa, o controle será transferido para a próxima instrução após a instrução `if`.

Tanto a `then-statement` como a `else-statement` podem consistir em uma única instrução ou várias instruções entre chaves (`{}`). Para uma única instrução, as chaves são opcionais, mas recomendadas.

A instrução ou instruções na `then-statement` e na `else-statement` podem ser de qualquer tipo, incluindo outra instrução `if` aninhada na instrução `if` original. Em instruções `if` aninhadas, cada cláusula `else` pertence ao último `if` que não tem um `else` correspondente. No exemplo a seguir, `Result1` aparecerá se `m > 10` e `n > 20` forem avaliadas como verdadeiras. Se `m > 10` for verdadeiro, mas `n > 20` for falso, `Result2` será exibido.

[!code-csharp[csrefKeywordsSelection#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#2)]

Se, em vez disso, você desejar que `Result2` apareça quando `(m > 10)` for falso, pode especificar essa associação usando chaves para estabelecer o início e o fim da instrução `if` aninhada, como o exemplo a seguir mostra.

[!code-csharp[csrefKeywordsSelection#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#3)]

`Result2` aparecerá se a condição `(m > 10)` for avaliada como falsa.

## <a name="example"></a>Exemplo

No exemplo a seguir, você insere um caractere do teclado e o programa usa uma instrução `if` aninhada para determinar se o caractere de entrada é um caractere alfabético. Se o caractere de entrada for um caractere alfabético, o programa verificará se o caractere de entrada está em maiúscula ou minúscula. Será exibida uma mensagem para cada caso.

[!code-csharp[csrefKeywordsSelection#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#4)]

## <a name="example"></a>Exemplo

Você também pode aninhar uma instrução `if` dentro de um bloco else, como mostra o código parcial a seguir. O exemplo aninha instruções `if` em dois blocos else e um bloco then. Os comentários especificam quais condições são verdadeiras ou falsas em cada bloco.

[!code-csharp[csrefKeywordsSelection#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#5)]

## <a name="example"></a>Exemplo

O exemplo a seguir determina se um caractere de entrada é um número, uma letra maiúscula ou uma letra minúscula. Se todas as três condições forem falsas, o caractere não será um caractere alfanumérico. O exemplo exibe uma mensagem para cada caso.

[!code-csharp[csrefKeywordsSelection#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsSelection/CS/csrefKeywordsSelection.cs#6)]

Assim como uma instrução no bloco else ou no bloco then pode ser qualquer instrução válida, você pode usar qualquer expressão booliana válida para a condição. Você pode usar operadores lógicos como [&&](../operators/conditional-and-operator.md), [&](../operators/and-operator.md), [&#124;&#124;](../operators/conditional-or-operator.md), [&#124;](../operators/or-operator.md) e [!](../operators/logical-negation-operator.md) para criar condições compostas. O código a seguir mostra exemplos.

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

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)  
- [Guia de Programação em C#](../../programming-guide/index.md)  
- [Palavras-chave do C#](index.md)  
- [?: ??](../operators/conditional-operator.md)  
- [Instrução if-else (C++)](/cpp/cpp/if-else-statement-cpp)  
- [switch](switch.md)  
