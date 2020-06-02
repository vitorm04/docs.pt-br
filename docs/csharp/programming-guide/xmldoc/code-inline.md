---
title: <c>-Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: a09bcd069e2f85f4a21736cb218c42c0e481d70b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287461"
---
# <a name="c-c-programming-guide"></a>\<c>(Guia de programação C#)

## <a name="syntax"></a>Sintaxe

```xml
<c>text</c>
```

## <a name="parameters"></a>Parâmetros

- `text`

  O texto que você deseja indicar como código.

## <a name="remarks"></a>Comentários

A `<c>` marca fornece uma maneira de indicar que o texto dentro de uma descrição deve ser marcado como código. Use [\<code>](./code.md) para indicar várias linhas como código.

Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.

## <a name="example"></a>Exemplo

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a>Confira também

- [Guia de programação em C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
