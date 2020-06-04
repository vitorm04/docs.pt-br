---
title: Como usar ponteiros para copiar uma matriz de bytes-guia de programação C#
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 8c1afc06fb567a923d604ad53dc26f94178a8d60
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397409"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a>Como usar ponteiros para copiar uma matriz de bytes (guia de programação C#)

O exemplo a seguir usa ponteiros para copiar bytes de uma matriz para outra.

Este exemplo usa a palavra-chave [não seguro](../../language-reference/keywords/unsafe.md), que permite que você use ponteiros no método `Copy`. A instrução [fixo](../../language-reference/keywords/fixed-statement.md) é usada para declarar ponteiros para as matrizes de origem e de destino. A instrução `fixed`*fixa* o local das matrizes de origem e de destino na memória para que elas não sejam movidas pela coleta de lixo. Os blocos de memória para as matrizes não serão fixado quando o bloco `fixed` for concluído. Como o método `Copy` neste exemplo usa a palavra-chave `unsafe`, ele precisa ser compilado com a opção do compilador [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md).

Este exemplo acessa os elementos das duas matrizes usando índices em vez de um segundo ponteiro não gerenciado. A declaração dos ponteiros `pSource` e `pTarget` fixa as matrizes. Esse recurso está disponível começando com o C# 7.3.

## <a name="example"></a>Exemplo

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>Confira também

- [Guia de programação C#](../index.md)
- [Código não seguro e ponteiros](index.md)
- [-Não seguro (opções do compilador C#)](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [Coleta de lixo](../../../standard/garbage-collection/index.md)
