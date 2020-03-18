---
title: <typeparamref>- Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 266eadad322fd3c4167c7a911cb57ef1e1333012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789652"
---
# <a name="typeparamref-c-programming-guide"></a>\<typeparamref> (guia de programação C#)

## <a name="syntax"></a>Sintaxe

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a>parâmetros

- `name`

  O nome do parâmetro de tipo. Coloque o nome entre aspas duplas (" ").

## <a name="remarks"></a>Comentários

Para obter mais informações sobre parâmetros de tipo em tipos e métodos genéricos, consulte [Genéricos](../generics/index.md).

Use essa marca para habilitar os consumidores do arquivo de documentação a formatar a palavra de alguma forma distinta, por exemplo, em itálico.

Compilar com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação para um arquivo.

## <a name="example"></a>Exemplo

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>Confira também

- [Guia de programação em C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
