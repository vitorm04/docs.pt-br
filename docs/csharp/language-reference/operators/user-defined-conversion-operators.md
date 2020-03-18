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
ms.openlocfilehash: b6061492cc1a4f756196fb8a9050b68651431e38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847255"
---
# <a name="user-defined-conversion-operators-c-reference"></a>Operadores de conversão definidos pelo usuário (Referência de C#)

Um tipo definido pelo usuário pode definir uma conversão implícita ou explícita personalizada de outro tipo ou para outro.

Conversões implícitas não requerem que uma sintaxe especial seja invocada e podem ocorrer em uma variedade de situações, por exemplo, em atribuições e invocações de método. Conversões implícitas C# predefinidas sempre têm sucesso e nunca lançam uma exceção. Conversões implícitas definidas pelo usuário devem se comportam dessa forma também. Se uma conversão personalizada puder gerar uma exceção ou perder informações, defina-a como uma conversão explícita.

Conversões definidas pelo usuário não são consideradas pelos operadores [is](type-testing-and-cast.md#is-operator) e [as](type-testing-and-cast.md#as-operator). Use o [operador cast ()](type-testing-and-cast.md#cast-operator-) para invocar uma conversão explícita definida pelo usuário.

Use `operator` e as palavras-chave `implicit` ou `explicit` para definir uma conversão implícita ou explícita, respectivamente. O tipo que define uma conversão deve ser um tipo de origem ou e destino dessa conversão. Uma conversão entre os dois tipos definidos pelo usuário pode ser definida em qualquer um dos dois tipos.

O exemplo a seguir demonstra como definir uma conversão implícita e explícita:

[!code-csharp[implicit an explicit conversions](snippets/UserDefinedConversions.cs)]

Use também a palavra-chave `operator` para sobrecarregar um operador C# predefinido. Para obter mais informações, consulte [Sobrecarga de operador](operator-overloading.md).

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, confira as seguintes seções da [especificação da linguagem C#](~/_csharplang/spec/introduction.md):

- [Operadores de conversão](~/_csharplang/spec/classes.md#conversion-operators)
- [Conversões definidas pelo usuário](~/_csharplang/spec/conversions.md#user-defined-conversions)
- [Conversões implícitas](~/_csharplang/spec/conversions.md#implicit-conversions)
- [Conversões explícitas](~/_csharplang/spec/conversions.md#explicit-conversions)

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Operadores do C#](index.md)
- [Sobrecarga de operador](operator-overloading.md)
- [Operadores cast e teste de tipo](type-testing-and-cast.md)
- [Conversão e conversão de tipo](../../programming-guide/types/casting-and-type-conversions.md)
- [Diretrizes de design - Operadores de conversão](../../../standard/design-guidelines/operator-overloads.md#conversion-operators)
- [Conversões explícitas encadeadas definidas pelo usuário em C#](https://docs.microsoft.com/archive/blogs/ericlippert/chained-user-defined-explicit-conversions-in-c)
