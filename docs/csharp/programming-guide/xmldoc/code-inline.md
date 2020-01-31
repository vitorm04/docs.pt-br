---
title: Guia de C# programação de <c>
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
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793449"
---
# <a name="c-c-programming-guide"></a>\<c > (C# guia de programação)

## <a name="syntax"></a>Sintaxe

```xml
<c>text</c>
```

## <a name="parameters"></a>Parâmetros

- `text`

  O texto que você deseja indicar como código.

## <a name="remarks"></a>Comentários

A marca \<c> oferece uma maneira de indicar que o texto em uma descrição deve ser marcado como código. Use [\<code>](./code.md) para indicar várias linhas como código.

Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.

## <a name="example"></a>Exemplo

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a>Veja também

- [Guia de programação em C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
