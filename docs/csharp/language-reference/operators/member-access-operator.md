---
title: . Operador – referência do C#
ms.custom: seodec18
ms.date: 02/25/2019
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: 2661676d53deb874c5e5a90b4443b301730e09df
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836455"
---
# <a name="-operator-c-reference"></a>. operator (Referência de C#)

O ponto, `.`, normalmente é usado para acesso de membro.

Use o token `.` para acessar um membro de um namespace ou um tipo, como demonstram os exemplos a seguir:

- Use `.` para acessar um namespace aninhado dentro de um namespace, como mostra o exemplo a seguir de uma [diretiva `using`](../keywords/using-directive.md):

  [!code-csharp[nested namespaces](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#NestedNamespace)]

- Use `.` para formar um *nome qualificado* para acessar um tipo dentro de um namespace, como mostra o código a seguir:

  [!code-csharp[qualified name](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#QualifiedName)]

  Use a [diretiva `using`](../keywords/using-directive.md) para tornar opcional o uso de nomes qualificados.

- Use `.` para acessar [membros de tipo](../../programming-guide/classes-and-structs/index.md#members), estático e não-estático, como mostra o código a seguir:

  [!code-csharp-interactive[type members](~/samples/snippets/csharp/language-reference/operators/MemberAccessExamples.cs#TypeMemberAccess)]

Também pode-se usar `.` para invocar um [método de extensão](../../programming-guide/classes-and-structs/extension-methods.md).

## <a name="operator-overloadability"></a>Capacidade de sobrecarga do operador

O operador `.` não pode ser sobrecarregado.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Saiva mais na seção [Acesso de membro](~/_csharplang/spec/expressions.md#member-access) na [especificação da linguagem C#](../language-specification/index.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Operadores do C#](index.md)
- [Operadores ?. e ?[]](null-conditional-operators.md)