---
title: Restrição new – Referência em C#
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: cd67aeb82d736b8941b0637494089723e7815505
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713348"
---
# <a name="new-constraint-c-reference"></a>Restrição new (Referência em C#)

A restrição `new` especifica que um argumento de tipo em uma declaração de classe genérica deve ter um construtor público sem parâmetros. Para usar a restrição `new`, o tipo não pode ser abstrato.

Aplique a restrição `new` a um parâmetro de tipo quando uma classe genérica criar novas instâncias do tipo, conforme mostrado no exemplo a seguir:

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

Quando você usa a restrição `new()` com outras restrições, ela deve ser especificada por último:

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

Para obter mais informações, consulte [Restrições a parâmetros de tipo](../../programming-guide/generics/constraints-on-type-parameters.md).

Você também pode usar a palavra-chave `new` para [criar uma instância de um tipo](../operators/new-operator.md) ou como um [modificador de declaração de membro](new-modifier.md).

## <a name="c-language-specification"></a>especificação da linguagem C#

Para obter mais informações, confira a seção [Restrições de parâmetro de tipo](~/_csharplang/spec/classes.md#type-parameter-constraints) na [Especificação da linguagem C#](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Confira também

- [C# Referência](../../language-reference/index.md)
- [C# Guia de Programação](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Genéricos](../../programming-guide/generics/index.md)
