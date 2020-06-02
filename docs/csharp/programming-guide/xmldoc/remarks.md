---
title: <remarks> -Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 739027786e02e559d86f990bf614e261b497c76f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287279"
---
# <a name="remarks-c-programming-guide"></a>\<remarks>(Guia de programação C#)

## <a name="syntax"></a>Sintaxe

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a>Parâmetros

- `Description`

  Uma descrição do membro.

## <a name="remarks"></a>Comentários

A `<remarks>` marca é usada para adicionar informações sobre um tipo, complementando as informações especificadas com [\<summary>](./summary.md) . Essas informações são exibidas na janela do Pesquisador de Objetos.

Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.

## <a name="example"></a>Exemplo

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a>Confira também

- [Guia de programação C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
