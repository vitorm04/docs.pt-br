---
title: Agrupar resultados por chaves contíguas (LINQ em C#)
description: Como agrupar resultados por chaves contíguas usando LINQ em C#.
ms.date: 12/1/2016
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: 8ad08d861e2d0f5ee0f8a2eceeb8d82a9aa2a5a6
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404756"
---
# <a name="group-results-by-contiguous-keys"></a>Agrupar resultados por chaves contíguas

O exemplo a seguir mostra como agrupar elementos em partes que representam subsequências de chaves contíguas. Por exemplo, suponha que você receba a seguinte sequência de pares chave-valor:

|Chave|Valor|
|---------|-----------|
|Um|We|
|Um|think|
|Um|that|
|B|Linq|
|C|is|
|Um|really|
|B|cool|
|B|!|

Os seguintes grupos serão criados nesta ordem:

1. We, think, that

2. Linq

3. is

4. really

5. cool, !

A solução é implementada como um método de extensão que é thread-safe e que retorna os resultados de uma maneira de streaming. Em outras palavras, ela produz seus grupos à medida que percorre a sequência de origem. Diferentemente dos operadores `group` ou `orderby`, ela pode começar a retornar grupos para o chamador antes que todas as sequências sejam lidas.

O acesso thread-safe é alcançado ao fazer uma cópia de cada grupo ou parte enquanto a sequência de origem é iterada, conforme explicado nos comentários do código-fonte. Se a sequência de origem tiver uma sequência grande de itens contíguos, o Common Language Runtime poderá lançar uma <xref:System.OutOfMemoryException>.

## <a name="example"></a>Exemplo

O exemplo a seguir mostra o método de extensão e o código do cliente que o usa:

[!code-csharp[cscsrefContiguousGroups#1](~/samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]

Para usar o método de extensão em seu projeto, copie a classe estática `MyExtensions` para um arquivo de código-fonte novo ou existente e se for necessário, adicione uma diretiva `using` para o namespace em que ele está localizado.

## <a name="see-also"></a>Consulte também

[LINQ (Consulta Integrada à Linguagem)](index.md)