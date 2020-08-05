---
title: expressão nameof-referência C#
ms.date: 04/23/2020
f1_keywords:
- nameof_CSharpKeyword
- nameof
helpviewer_keywords:
- nameof expression [C#]
ms.assetid: 33601bf3-cc2c-4496-846d-f9679bccf2a7
ms.openlocfilehash: 1bd8800a553eb9b3363da8a3b5f230caecddf223
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556404"
---
# <a name="nameof-expression-c-reference"></a>expressão nameof (referência C#)

Uma `nameof` expressão produz o nome de uma variável, tipo ou membro como a constante de cadeia de caracteres:

[!code-csharp-interactive[nameof expression](snippets/NameOfOperator.cs#Examples)]

Como mostra o exemplo anterior, no caso de um tipo e um namespace, o nome produzido geralmente não é [totalmente qualificado](~/_csharplang/spec/basic-concepts.md#fully-qualified-names).

No caso de [identificadores textuais](../tokens/verbatim.md), o `@` caractere não é a parte de um nome, como mostra o exemplo a seguir:

[!code-csharp-interactive[nameof verbatim](snippets/NameOfOperator.cs#Verbatim)]

Uma `nameof` expressão é avaliada em tempo de compilação e não tem nenhum efeito no tempo de execução.

Você pode usar uma `nameof` expressão para tornar o código de verificação de argumento mais passível de manutenção:

[!code-csharp[nameof and argument check](snippets/NameOfOperator.cs#ExceptionMessage)]

Uma `nameof` expressão está disponível no C# 6 e posterior.

## <a name="c-language-specification"></a>especificação da linguagem C#

Para saber mais, confira a seção [Expressões nameof](~/_csharplang/spec/expressions.md#nameof-expressions) da [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Confira também

- [Referência de C#](../index.md)
- [Operadores e expressões C#](index.md)
