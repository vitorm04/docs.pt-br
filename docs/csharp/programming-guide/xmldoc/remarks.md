---
title: <remarks> - C# guia de programação
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: e37dac9cb9fed1df6ca027f09f2c95dbbc8ea66d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793381"
---
# <a name="remarks-c-programming-guide"></a>\<Comentários > (C# guia de programação)

## <a name="syntax"></a>Sintaxe

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a>Parâmetros

- `Description`

  Uma descrição do membro.

## <a name="remarks"></a>Comentários

A marca \<remarks> é usada para adicionar informações sobre o tipo, complementando as informações especificadas com [\<summary>](./summary.md). Essas informações são exibidas na janela do Pesquisador de Objetos.

Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.

## <a name="example"></a>Exemplo

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a>Veja também

- [Guia de Programação em C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
