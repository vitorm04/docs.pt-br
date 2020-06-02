---
title: <value> -Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: bd6630a8d5894fda39ad289c8dd584f6d84e5490
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287188"
---
# <a name="value-c-programming-guide"></a>\<value>(Guia de programação C#)

## <a name="syntax"></a>Sintaxe

```xml
<value>property-description</value>
```

## <a name="parameters"></a>Parâmetros

- `property-description`

  Uma descrição da propriedade.

## <a name="remarks"></a>Comentários

A `<value>` marca permite descrever o valor que uma propriedade representa. Quando você adiciona uma propriedade por meio do assistente de código no ambiente de desenvolvimento .NET do Visual Studio, ela adiciona uma [\<summary>](./summary.md) marca para a nova propriedade. Em seguida, você deve adicionar manualmente uma `<value>` marca para descrever o valor que a propriedade representa.

Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.

## <a name="example"></a>Exemplo

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a>Confira também

- [Guia de programação em C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
