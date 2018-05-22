---
title: Matrizes em C# - um tour pela linguagem C#
description: Matrizes são o tipo mais básico de coleção da linguagem C#
ms.date: 08/10/2016
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: c0fe65348ab2d41852ed9150571dcb0e5b8553f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="arrays"></a>Matrizes

Uma ***matriz*** é uma estrutura de dados que contém algumas variáveis acessadas por meio de índices calculados. As variáveis contidas em uma matriz, também chamadas de ***elementos*** da matriz, são todas do mesmo tipo, e esse tipo é chamado de ***tipo de elemento*** da matriz.

Os tipos de matriz são tipos de referência, e a declaração de uma variável de matriz simplesmente reserva espaço para uma referência a uma instância de matriz. As instâncias reais da matriz são criadas dinamicamente em tempo de execução usando o operador new. A operação new especifica a ***duração*** da nova instância de matriz, que depois fica fixa para o tempo de vida da instância. Os índices dos elementos de uma matriz variam de `0` a `Length - 1`. O operador `new` inicializa automaticamente os elementos de uma matriz usando o valor padrão, que, por exemplo, é zero para todos os tipos numéricos e `null` para todos os tipos de referência.

O exemplo a seguir cria uma matriz de elementos `int`, inicializa a matriz e imprime o conteúdo da matriz.

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

Este exemplo cria e opera em uma ***matriz unidimensional***. O C# também oferece suporte a ***matrizes multidimensionais***. O número de dimensões de um tipo de matriz, também conhecido como ***classificação*** do tipo de matriz, é o número um mais o número de vírgulas escrito entre os colchetes do tipo de matriz. O exemplo a seguir aloca uma matriz unidimensional, bidimensional e tridimensional, respectivamente.

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

A matriz `a1` contém 10 elementos, a matriz `a2` contém 50 (10 × 5) elementos e a matriz `a3` contém 100 (10 × 5 × 2) elementos.
O tipo do elemento de uma matriz pode ser qualquer tipo, incluindo um tipo de matriz. Uma matriz com elementos de um tipo de matriz é chamada às vezes de ***matriz denteada***, pois os tamanhos das matrizes do elemento nem sempre precisam ser iguais. O exemplo a seguir aloca uma matriz de matrizes de `int`:

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

A primeira linha cria uma matriz com três elementos, cada um do tipo `int[]`, e cada um com um valor inicial de `null`. As linhas subsequentes inicializam os três elementos com referências às instâncias individuais da matriz de tamanhos variados.

O operador new permite que os valores iniciais dos elementos da matriz sejam especificados com um ***inicializador de matriz***, que é uma lista de expressões escritas entre os delimitadores `{` e `}`. O exemplo a seguir aloca e inicializa um `int[]` com três elementos.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

Observe que o tamanho da matriz é inferido do número de expressões entre { e }. A variável local e declarações de campo podem ser reduzidas ainda mais, de modo que o tipo de matriz não precise ser redefinido.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

Os dois exemplos anteriores são equivalentes ao seguinte:

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
[Anterior](structs.md)
[Próximo](interfaces.md)
