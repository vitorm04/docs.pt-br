---
title: Restrição new – Referência em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- new constraint keyword [C#]
ms.assetid: 58850b64-cb97-4136-be50-1f3bc7fc1da9
ms.openlocfilehash: de0798319d91032143cb806d6d39338c4f51ac8f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237838"
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