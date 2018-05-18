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
---
# <a name="if-else-c-reference"></a>if-else (Referência de C#)
Uma instrução `if` identifica qual instrução executar com base no valor de uma expressão `Boolean`. No exemplo a seguir, a variável `Boolean` `result` deve ser definida como `true` e, em seguida, verificada na instrução `if`. A saída é `The condition is true`.  
  
 [!code-csharp[csrefKeywordsSelection#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_1.cs)]  
  
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
  
 [!code-csharp[csrefKeywordsSelection#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_2.cs)]  
  
 Se, em vez disso, você desejar que `Result2` apareça quando `(m > 10)` for falso, pode especificar essa associação usando chaves para estabelecer o início e o fim da instrução `if` aninhada, como o exemplo a seguir mostra.  
  
 [!code-csharp[csrefKeywordsSelection#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_3.cs)]  
  
 `Result2` aparecerá se a condição `(m > 10)` for avaliada como falsa.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, você insere um caractere do teclado e o programa usa uma instrução `if` aninhada para determinar se o caractere de entrada é um caractere alfabético. Se o caractere de entrada for um caractere alfabético, o programa verificará se o caractere de entrada está em maiúscula ou minúscula. Será exibida uma mensagem para cada caso.  
  
 [!code-csharp[csrefKeywordsSelection#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_4.cs)]  
  
## <a name="example"></a>Exemplo  
 Você também pode aninhar uma instrução `if` dentro de um bloco else, como mostra o código parcial a seguir. O exemplo aninha instruções `if` em dois blocos else e um bloco then. Os comentários especificam quais condições são verdadeiras ou falsas em cada bloco.  
  
 [!code-csharp[csrefKeywordsSelection#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_5.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir determina se um caractere de entrada é um número, uma letra maiúscula ou uma letra minúscula. Se todas as três condições forem falsas, o caractere não será um caractere alfanumérico. O exemplo exibe uma mensagem para cada caso.  
  
 [!code-csharp[csrefKeywordsSelection#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/if-else_6.cs)]  
  
 Assim como uma instrução no bloco else ou no bloco then pode ser qualquer instrução válida, você pode usar qualquer expressão booliana válida para a condição. Você pode usar operadores lógicos como [&&](../../../csharp/language-reference/operators/conditional-and-operator.md), [&](../../../csharp/language-reference/operators/and-operator.md), [&#124;&#124;](../../../csharp/language-reference/operators/conditional-or-operator.md), [&#124;](../../../csharp/language-reference/operators/or-operator.md) e [!](../../../csharp/language-reference/operators/logical-negation-operator.md) para criar condições compostas. O código a seguir mostra exemplos.  
  
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
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [Operador ?:](../../../csharp/language-reference/operators/conditional-operator.md)  
 [Instrução if-else (C++)](/cpp/cpp/if-else-statement-cpp)  
 [switch](../../../csharp/language-reference/keywords/switch.md)
