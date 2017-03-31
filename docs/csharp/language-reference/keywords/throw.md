---
title: "throw (Referência de C#) | Microsoft Docs"
ms.date: 2015-03-02
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- throw
- throw_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- throw statement [C#]
- throw expression [C#]
- throw keyword [C#]
ms.assetid: 5ac4feef-4b1a-4c61-aeb4-61d549e5dd42
caps.latest.revision: 22
author: rpetrusha
ms.author: ronpet
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 095a86f5ab2ce50f5931643161a44b5759583e4e
ms.lasthandoff: 03/13/2017

---
# <a name="throw-c-reference"></a>throw (Referência de C#)
Indica a ocorrência de uma exceção durante a execução do programa.  
  
## <a name="remarks"></a>Comentários

A sintaxe de `throw` é:

```csharp
throw [e]
```
em que `e` é uma instância de uma classe derivada de <xref:System.Exception?displayProperty=fullName>. O exemplo a seguir usará a instrução `throw` para gerar um @System.IndexOutOfRangeException se o argumento passado para um método chamado `GetNumber` não corresponder a um índice válido de uma matriz interna.

[!code-cs[csrefKeyword#1](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#1)]  

Os chamadores do método, então, usam um bloco `try-catch` ou `try-catch-finally` para tratar a exceção gerada. O exemplo a seguir trata a exceção gerada pelo método `GetNumber`.

[!code-cs[csrefKeyword#2](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-1.cs#2)]  

## <a name="re-throwing-an-exception"></a>Gerando uma exceção novamente

`throw` também pode ser usado em um bloco `catch` para gerar novamente uma exceção tratada em um bloco `catch`.  Nesse caso, `throw` não usa um operando de exceção. Ele é mais útil quando um método passa um argumento de um chamador para algum outro método de biblioteca e o método de biblioteca gera uma exceção que deve ser passada para o chamador. O exemplo a seguir gera novamente um @System.NullReferenceException que é gerado ao tentar recuperar o primeiro caractere de uma cadeia de caracteres não inicializada. 

[!code-cs[csrefKeyword#3](../../../../samples/snippets/csharp/language-reference/keywords/throw/throw-3.cs#3)]  

> [!IMPORTANT]
> Também é possível usar a sintaxe `throw e` em um bloco `catch` para instanciar uma nova exceção que você passa para o chamador. Nesse caso, o rastreamento de pilha da exceção original, que fica disponível na propriedade @System.Exception.Stacktrace, não é preservado.
 
## <a name="the-throw-expression"></a>A expressão `throw`

A partir do C# 7, `throw` pode ser usado como uma expressão e como uma instrução. Isso permite que uma exceção seja gerada em contextos que não tinham suporte anteriormente. Elas incluem:

- [o operador condicional](../operators/conditional-operator.md). O exemplo a seguir usará uma expressão `throw` para gerar um @System.ArgumentException se uma matriz de cadeia de caracteres vazia for passada para um método. Antes do C# 7, essa lógica precisaria aparecer em uma instrução `if`/`else`.

   [!code-cs[csrefKeyword#4](../../../../samples/snippets/csharp/language-reference/keywords/throw/conditional.cs#1)]  
  
- [o operador de união nula](../operators/null-conditional-operator.md). No exemplo a seguir, uma expressão `throw` será usada com um operador de união nula para gerar uma exceção se a cadeia de caracteres atribuída a uma propriedade `Name` for `null`.
 
   [!code-cs[csrefKeyword#5](../../../../samples/snippets/csharp/language-reference/keywords/throw/coalescing.cs#1)]  
 
- um método ou [lambda](../../lambda-expressions.md) com corpo de expressão. O exemplo a seguir ilustra um método com corpo de expressão que gera um @System.InvalidCastException porque uma conversão para um valor @System.DateTime não tem suporte.
 
   [!code-cs[csrefKeyword#6](../../../../samples/snippets/csharp/language-reference/keywords/throw/exp-bodied.cs#1)]  
 
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)   
 [Guia de programação em C#](../../../csharp/programming-guide/index.md)   
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)   
 [As instruções try, catch e throw em C++](../../../csharp/language-reference/keywords/try-catch.md)   
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)   
 [Instruções para tratamento de exceções](../../../csharp/language-reference/keywords/exception-handling-statements.md)   
 [Como gerar exceções explicitamente](https://msdn.microsoft.com/library/xhcbs8fz)
