---
title: <c>- Guia de programação C#
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
ms.openlocfilehash: d5b28ee6db52d191f8454592d792ac0a1e1dc73b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793449"
---
# <a name="c-c-programming-guide"></a>\<c> (guia de programação C#)

## <a name="syntax"></a>Sintaxe

```xml
<c>text</c>
```

## <a name="parameters"></a>parâmetros

- `text`

  O texto que você deseja indicar como código.

## <a name="remarks"></a>Comentários

A marca \<c> oferece uma maneira de indicar que o texto em uma descrição deve ser marcado como código. Use [ \<código>](./code.md) para indicar várias linhas como código.

Compilar com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação para um arquivo.

## <a name="example"></a>Exemplo

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a>Confira também

- [Guia de programação em C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
