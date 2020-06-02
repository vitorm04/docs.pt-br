---
title: <paramref>-Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 4f3b521d24c8b4677a05b0b145cb36c31b2793f2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287305"
---
# <a name="paramref-c-programming-guide"></a>\<paramref>(Guia de programação C#)

## <a name="syntax"></a>Sintaxe

```xml
<paramref name="name"/>
```

## <a name="parameters"></a>Parâmetros

- `name`

  O nome do parâmetro ao qual você deseja se referir. Coloque o nome entre aspas duplas (" ").

## <a name="remarks"></a>Comentários

A `<paramref>` marca fornece uma maneira de indicar que uma palavra nos comentários do código, por exemplo, em um `<summary>` `<remarks>` bloco ou se refere a um parâmetro. O arquivo XML pode ser processado para formatar essa palavra de alguma forma distinta, como com uma fonte em negrito ou itálico.

Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.

## <a name="example"></a>Exemplo

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a>Confira também

- [Guia de programação C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
