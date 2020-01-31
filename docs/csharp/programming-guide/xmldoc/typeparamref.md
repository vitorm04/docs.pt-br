---
title: Guia de C# programação de <typeparamref>
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 266eadad322fd3c4167c7a911cb57ef1e1333012
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789652"
---
# <a name="typeparamref-c-programming-guide"></a>\<typeparamref > (C# guia de programação)

## <a name="syntax"></a>Sintaxe

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a>Parâmetros

- `name`

  O nome do parâmetro de tipo. Coloque o nome entre aspas duplas (" ").

## <a name="remarks"></a>Comentários

Para obter mais informações sobre parâmetros de tipo em tipos e métodos genéricos, consulte [Genéricos](../generics/index.md).

Use essa marca para habilitar os consumidores do arquivo de documentação a formatar a palavra de alguma forma distinta, por exemplo, em itálico.

Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.

## <a name="example"></a>Exemplo

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>Veja também

- [Guia de programação em C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
