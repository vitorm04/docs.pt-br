---
title: Operadores de conversão definidos pelo usuário – Referência de C#
description: Saiba como definir conversões de tipo implícitas e explícitas personalizadas em C#.
ms.date: 07/09/2019
f1_keywords:
- explicit_CSharpKeyword
- implicit_CSharpKeyword
helpviewer_keywords:
- explicit keyword [C#]
- implicit keyword [C#]
- conversion operator [C#]
- user-defined conversion [C#]
ms.openlocfilehash: 5d1882048b2af12c29a3771055cbeba9565b7dab
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67787392"
---
# <a name="user-defined-conversion-operators-c-reference"></a>Operadores de conversão definidos pelo usuário (Referência de C#)

Um tipo definido pelo usuário pode definir uma conversão implícita ou explícita personalizada de outro tipo ou para outro.

Conversões implícitas não requerem que uma sintaxe especial seja invocada e podem ocorrer em uma variedade de situações, por exemplo, em atribuições e invocações de método. Conversões implícitas em C# predefinidas sempre têm êxito e nunca geram uma exceção ou perdem informações. Conversões implícitas definidas pelo usuário devem se comportam dessa forma também. Se uma conversão personalizada puder gerar uma exceção ou perder informações, defina-a como uma conversão explícita.

Conversões definidas pelo usuário não são consideradas pelos operadores [is](type-testing-and-conversion-operators.md#is-operator) e [as](type-testing-and-conversion-operators.md#as-operator). Use o [operador cast ()](type-testing-and-conversion-operators.md#cast-operator-) para invocar uma conversão explícita definida pelo usuário.

Use `operator` e as palavras-chave `implicit` ou `explicit` para definir uma conversão implícita ou explícita, respectivamente. O tipo que define uma conversão deve ser um tipo de origem ou e destino dessa conversão. Uma conversão entre os dois tipos definidos pelo usuário pode ser definida em qualquer um dos dois tipos.

O exemplo a seguir demonstra como definir uma conversão implícita e explícita:

[!code-csharp[implicit an explicit conversions](~/samples/csharp/language-reference/operators/UserDefinedConversions.cs)]

Use também a palavra-chave `operator` para sobrecarregar um operador C# predefinido. Para obter mais informações, consulte [Sobrecarga de operador](operator-overloading.md).

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Operadores de conversão](~/_csharplang/spec/classes.md#conversion-operators)
- [Conversões Definidas pelo Usuário](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [Conversões implícitas](~/_csharplang/spec/conversions.md#implicit-conversions)
- [Conversões explícitas](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Operadores do C#](index.md)
- [Sobrecarga de operador](operator-overloading.md)
- [Operadores de conversão e teste de tipo](type-testing-and-conversion-operators.md)
- [Conversão e conversão de tipo](../../programming-guide/types/casting-and-type-conversions.md)
- [Conversões explícitas encadeadas definidas pelo usuário em C#](https://blogs.msdn.microsoft.com/ericlippert/2007/04/16/chained-user-defined-explicit-conversions-in-c/)
