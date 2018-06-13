---
title: explicit (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: c8a05aef3318eb34242ed1268ea26663592e4d1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216471"
---
# <a name="explicit-c-reference"></a>explicit (Referência de C#)
A palavra-chave `explicit` declara um operador de conversão de tipo definido pelo usuário que deve ser invocado com uma conversão. Por exemplo, esse operador converte de uma classe chamada Fahrenheit para uma classe chamada Celsius:  
  
 [!code-csharp[csrefKeywordsConversion#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_1.cs)]  
  
 Esse operador de conversão pode ser invocado assim:  
  
 [!code-csharp[csrefKeywordsConversion#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_2.cs)]  
  
 O operador de conversão converte de um tipo de origem para um tipo de destino. O tipo de origem fornece o operador de conversão. Ao contrário da conversão implícita, os operadores de conversão explícita devem ser invocados por meio de uma conversão. Se uma operação de conversão pode causar exceções ou perda de informações, você deve marcá-la como `explicit`. Isso impede que o compilador invoque silenciosamente a operação de conversão com consequências possivelmente imprevisíveis.  
  
 A omissão da conversão resulta no erro em tempo de compilação CS0266.  
  
 Para obter mais informações, consulte [Usando Operadores de Conversão](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir fornece uma classe `Fahrenheit` e uma classe `Celsius` e cada uma delas fornece um operador de conversão explícita para a outra classe.  
  
 [!code-csharp[csrefKeywordsConversion#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_3.cs)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define um struct `Digit`, que representa um único dígito decimal. Um operador é definido para conversões de `byte` para `Digit`, mas como nem todos os bytes podem ser convertidos para um `Digit`, a conversão é explícita.  
  
 [!code-csharp[csrefKeywordsConversion#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/explicit_4.cs)]  
  
## <a name="c-language-specification"></a>Especificação da Linguagem C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Referência de C#](../../../csharp/language-reference/index.md)  
 [Guia de Programação em C#](../../../csharp/programming-guide/index.md)  
 [Palavras-chave do C#](../../../csharp/language-reference/keywords/index.md)  
 [implicit](../../../csharp/language-reference/keywords/implicit.md)  
 [operator (Referência de C#)](../../../csharp/language-reference/keywords/operator.md)  
 [Como implementar conversões definidas pelo usuário entre structs](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
 [Conversões explícitas encadeadas definidas pelo usuário em C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
