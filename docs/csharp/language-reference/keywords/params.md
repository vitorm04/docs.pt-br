---
title: palavra-chave params para matrizes de parâmetros - referência C#
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
- parameter array
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 77d7fd19ff57f80f401191027e2fae95026e1966
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/21/2020
ms.locfileid: "81738840"
---
# <a name="params-c-reference"></a>params (Referência de C#)

Usando a palavra-chave `params`, você pode especificar um [parâmetro do método](method-parameters.md) que aceita um número variável de argumentos. O tipo de parâmetro deve ser uma matriz unidimensional.

Nenhum parâmetro adicional é permitido após a palavra-chave `params` em uma declaração de método e apenas uma palavra-chave `params` é permitida em uma declaração de método.

Se o tipo declarado `params` do parâmetro não for uma matriz unidimensional, ocorrerá o erro de compilador [CS0225.](../../misc/cs0225.md)

Quando você chama um `params` método com um parâmetro, você pode passar em:

- Uma lista separada por vírgulas de argumentos do tipo dos elementos da matriz.
- Uma matriz de argumentos do tipo especificado.
- Sem argumentos. Se você não enviar nenhum argumento, o comprimento da lista `params` será zero.

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra várias maneiras em que os argumentos podem ser enviados para um parâmetro `params`.

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a>especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Confira também

- [C# Referência](../index.md)
- [C# Guia de Programação](../../programming-guide/index.md)
- [C# Palavras-chave](index.md)
- [Parâmetros de método](method-parameters.md)
