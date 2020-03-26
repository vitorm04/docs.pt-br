---
title: nomede expressão - C# referência
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 5a68161be7bb03122d2a63ccef4365c5853862b2
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507133"
---
# <a name="nameof-expression-c-reference"></a>nomeda expressão (referência C#)

Uma `nameof` expressão produz o nome de uma variável, tipo ou membro como a constante de seqüência de cordas:

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

Como mostra o exemplo anterior, no caso de um tipo e um namespace, o nome produzido geralmente não é [totalmente qualificado](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

Uma `nameof` expressão é avaliada no tempo de compilação e não tem efeito no tempo de execução.

Você pode `nameof` usar uma expressão para tornar o código de verificação de argumentos mais sustentável:

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

Uma `nameof` expressão está disponível em C # 6 e posterior.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para saber mais, confira a seção [Expressões nameof](~/_csharplang/spec/expressions.md#nameof-expressions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Operadores do C#](index.md)
