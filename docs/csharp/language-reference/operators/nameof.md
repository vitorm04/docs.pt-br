---
title: operador nameof – referência do C#
ms.date: 07/12/2019
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof operator [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: ffbc801acf61bf72db1c88912dc2142a478fa280
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846266"
---
# <a name="nameof-operator-c-reference"></a>operador nameof (referência do C#)

O operador `nameof` obtém o nome de uma variável, tipo ou membro como uma cadeia de caracteres constante:

[!code-csharp-interactive[nameof operator](snippets/NameOfOperator.cs#Examples)]

Como mostra o exemplo anterior, no caso de um tipo e um namespace, o nome produzido geralmente não é [totalmente qualificado](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

O `nameof` operador é avaliado no momento da compilação e não tem efeito no tempo de execução.

Você pode usar o operador `nameof` para tornar o código de verificação de argumentos mais passível de manutenção:

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

O operador `nameof` está disponível no C# 6 e versões posteriores.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para saber mais, confira a seção [Expressões nameof](~/_csharplang/spec/expressions.md#nameof-expressions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Operadores do C#](index.md)
