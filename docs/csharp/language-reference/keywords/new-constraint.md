---
title: Restrição new – Referência em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: 32fcb13e1f217707d53300c532169b1a1759fa7e
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633405"
---
# <a name="new-constraint-c-reference"></a>Restrição new (Referência em C#)

A restrição `new` especifica que qualquer argumento de tipo em uma declaração de classe genérica deve ter um construtor público sem parâmetros. Para usar a restrição new, o tipo não pode ser abstrato.

## <a name="example"></a>Exemplo

Aplique a restrição `new` a um parâmetro de tipo quando a classe genérica cria novas instâncias do tipo, conforme mostrado no exemplo a seguir:

[!code-csharp[csrefKeywordsOperator#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#5)]

## <a name="example"></a>Exemplo

Quando você usa a restrição `new()` com outras restrições, ela deve ser especificada por último:

[!code-csharp[csrefKeywordsOperator#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsOperator/CS/csrefKeywordsOperators.cs#6)]

Para obter mais informações, consulte [Restrições a parâmetros de tipo](../../programming-guide/generics/constraints-on-type-parameters.md).

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- <xref:System.Collections.Generic>
- [Referência de C#](../../language-reference/index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Palavras-chave do operador](operator-keywords.md)
- [Genéricos](../../programming-guide/generics/index.md)
