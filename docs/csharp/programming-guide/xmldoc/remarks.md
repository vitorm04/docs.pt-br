---
title: <remarks> - Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: e37dac9cb9fed1df6ca027f09f2c95dbbc8ea66d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793381"
---
# <a name="remarks-c-programming-guide"></a>\<observações> (guia de programação C#)

## <a name="syntax"></a>Sintaxe

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a>parâmetros

- `Description`

  Uma descrição do membro.

## <a name="remarks"></a>Comentários

As \<observações> tag é usada para adicionar informações sobre [ \< ](./summary.md)um tipo, complementando as informações especificadas com>de resumo . Essas informações são exibidas na janela do Pesquisador de Objetos.

Compilar com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação para um arquivo.

## <a name="example"></a>Exemplo

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a>Confira também

- [C# Guia de Programação](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
