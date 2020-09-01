---
description: palavra-chave params para matrizes de parâmetros-referência C#
title: palavra-chave params para matrizes de parâmetros-referência C#
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
- parameter array
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: a2726c725508cd297001aaabddeff414704d1115
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134460"
---
# <a name="params-c-reference"></a>params (Referência de C#)

Usando a palavra-chave `params`, você pode especificar um [parâmetro do método](method-parameters.md) que aceita um número variável de argumentos. O tipo de parâmetro deve ser uma matriz unidimensional.

Nenhum parâmetro adicional é permitido após a palavra-chave `params` em uma declaração de método e apenas uma palavra-chave `params` é permitida em uma declaração de método.

Se o tipo declarado do `params` parâmetro não for uma matriz unidimensional, ocorrerá um erro [CS0225](../../misc/cs0225.md) do compilador.

Ao chamar um método com um `params` parâmetro, você pode passar:

- Uma lista separada por vírgulas de argumentos do tipo dos elementos da matriz.
- Uma matriz de argumentos do tipo especificado.
- Sem argumentos. Se você não enviar nenhum argumento, o comprimento da lista `params` será zero.

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra várias maneiras em que os argumentos podem ser enviados para um parâmetro `params`.

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)]

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Confira também

- [Referência do C#](../index.md)
- [Guia de programação C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Parâmetros de método](method-parameters.md)
