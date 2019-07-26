---
title: operador nameof – referência do C#
ms.custom: seodec18
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 965b3e96a20906187df4c8693f050c550a747091
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331441"
---
# <a name="nameof-operator-c-reference"></a>operador nameof (referência do C#)

O operador `nameof` obtém o nome de uma variável, tipo ou membro como uma cadeia de caracteres constante:

[!code-csharp-interactive[nameof operator](~/samples/csharp/language-reference/operators/NameOfOperator.cs#Examples)]

Como mostra o exemplo anterior, no caso de um tipo e um namespace, o nome produzido geralmente não é [totalmente qualificado](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

O operador `nameof` é avaliado no tempo de compilação e não tem efeitos no tempo de execução.

Você pode usar o operador `nameof` para tornar o código de verificação de argumentos mais passível de manutenção:

[!code-csharp[nameof and argument check](~/samples/csharp/language-reference/operators/NameOfOperator.cs#ExceptionMessage)]

O operador `nameof` está disponível no C# 6 e versões posteriores.

## <a name="c-language-specification"></a>Especificação da linguagem C#

Para saber mais, confira a seção [Expressões nameof](~/_csharplang/spec/expressions.md#nameof-expressions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Operadores do C#](index.md)
