---
title: Palavra-chave explicit (Referência de C#)
ms.date: 08/24/2018
f1_keywords:
- explicit_CSharpKeyword
- explicit
helpviewer_keywords:
- explicit keyword [C#]
ms.assetid: cfb8f42a-e411-4db2-af9b-796b05644846
ms.openlocfilehash: 3567a2c5aa549aa3141ed59c3e93e7b07975da70
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525455"
---
# <a name="explicit-c-reference"></a>explicit (Referência de C#)

A palavra-chave `explicit` declara um operador de conversão de tipo definido pelo usuário que deve ser invocado com uma conversão.

O exemplo a seguir define o operador que converte de uma classe `Fahrenheit` a uma classe `Celsius`. O operador deve ser definido dentro uma classe `Fahrenheit` ou uma classe `Celsius`:

[!code-csharp[csrefKeywordsConversion#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#2)]

Você invoca o operador de conversão definido com uma conversão, como mostra o exemplo a seguir:

[!code-csharp[csrefKeywordsConversion#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#3)]

O operador de conversão converte de um tipo de origem para um tipo de destino. O tipo de origem fornece o operador de conversão. Ao contrário da conversão implícita, os operadores de conversão explícita devem ser invocados por meio de uma conversão. Se uma operação de conversão pode causar exceções ou perda de informações, você deve marcá-la como `explicit`. Isso impede que o compilador invoque silenciosamente a operação de conversão com consequências possivelmente imprevisíveis.

A omissão da conversão resulta no erro em tempo de compilação CS0266.

Para obter mais informações, consulte [Usando Operadores de Conversão](../../programming-guide/statements-expressions-operators/using-conversion-operators.md).

## <a name="example"></a>Exemplo

O exemplo a seguir fornece uma classe `Fahrenheit` e uma classe `Celsius` e cada uma delas fornece um operador de conversão explícita para a outra classe.

[!code-csharp[csrefKeywordsConversion#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#1)]

## <a name="example"></a>Exemplo

O exemplo a seguir define um struct `Digit`, que representa um único dígito decimal. Um operador é definido para conversões de `byte` para `Digit`, mas como nem todos os bytes podem ser convertidos para um `Digit`, a conversão é explícita.

[!code-csharp[csrefKeywordsConversion#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsConversion/CS/csrefKeywordsConversion.cs#4)]

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)  
- [Guia de Programação em C#](../../programming-guide/index.md)  
- [Palavras-chave do C#](index.md)  
- [implicit](implicit.md)  
- [operator (Referência de C#)](operator.md)  
- [Como implementar conversões definidas pelo usuário entre structs](../../programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)  
- [Conversões explícitas encadeadas definidas pelo usuário em C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)  
