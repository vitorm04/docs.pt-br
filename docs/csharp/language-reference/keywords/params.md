---
title: Palavra-chave params – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- params_CSharpKeyword
- params
helpviewer_keywords:
- parameters [C#], params
- params keyword [C#]
ms.assetid: 1690815e-b52b-4967-8380-5780aff08012
ms.openlocfilehash: 772c8da879eeccbe484c631a47de7fe8a32ec8d2
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633578"
---
# <a name="params-c-reference"></a>params (Referência de C#)

Usando a palavra-chave `params`, você pode especificar um [parâmetro do método](method-parameters.md) que aceita um número variável de argumentos.

Você pode enviar uma lista separada por vírgulas dos argumentos do tipo especificado na declaração de parâmetros ou uma matriz de argumentos do tipo especificado. Você também pode não enviar nenhum argumento. Se você não enviar nenhum argumento, o comprimento da lista `params` será zero.

Nenhum parâmetro adicional é permitido após a palavra-chave `params` em uma declaração de método e apenas uma palavra-chave `params` é permitida em uma declaração de método.

O tipo declarado do parâmetro `params` precisa ser uma matriz unidimensional, como mostra o exemplo a seguir. Caso contrário, ocorrerá o erro do compilador [CS0225](../../misc/cs0225.md).

## <a name="example"></a>Exemplo

O exemplo a seguir demonstra várias maneiras em que os argumentos podem ser enviados para um parâmetro `params`.

[!code-csharp[csrefKeywordsMethodParams#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsMethodParams/CS/csrefKeywordsMethodParams.cs#5)] 

## <a name="c-language-specification"></a>Especificação da linguagem C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Consulte também

- [Referência de C#](../index.md)
- [Guia de Programação em C#](../../programming-guide/index.md)
- [Palavras-chave do C#](index.md)
- [Parâmetros de método](method-parameters.md)
