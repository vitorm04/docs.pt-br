---
title: <example> -Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: e8d26f82562cc5140662f5b32ea9fedf5481d8f8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287371"
---
# <a name="example-c-programming-guide"></a>\<example>(Guia de programação C#)

## <a name="syntax"></a>Sintaxe

```xml
<example>description</example>
```

## <a name="parameters"></a>Parâmetros

- `description`

  Uma descrição do exemplo de código.

## <a name="remarks"></a>Comentários

A `<example>` marca permite especificar um exemplo de como usar um método ou outro membro da biblioteca. Isso geralmente envolve o uso da [\<code>](./code.md) marca.

Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.

## <a name="example"></a>Exemplo

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a>Confira também

- [Guia de programação C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
