---
title: <example> - C# guia de programação
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: 615eccbc427b6a5bbbed061acd0c8b0b9be7f46c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789809"
---
# <a name="example-c-programming-guide"></a>\<exemplo > (C# guia de programação)

## <a name="syntax"></a>Sintaxe

```xml
<example>description</example>
```

## <a name="parameters"></a>Parâmetros

- `description`

  Uma descrição do exemplo de código.

## <a name="remarks"></a>Comentários

A marca \<example> permite especificar um exemplo de como usar um método ou outro membro da biblioteca. Normalmente, isso envolve o uso da marca [\<code>](./code.md).

Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.

## <a name="example"></a>Exemplo

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a>Veja também

- [Guia de Programação em C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
