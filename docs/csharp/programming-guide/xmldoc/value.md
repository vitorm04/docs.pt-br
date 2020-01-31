---
title: <value> - C# guia de programação
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 120805346672738e614743ab8c98388b8dbac0f7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793345"
---
# <a name="value-c-programming-guide"></a>> de valor deC# \<(guia de programação)

## <a name="syntax"></a>Sintaxe

```xml
<value>property-description</value>
```

## <a name="parameters"></a>Parâmetros

- `property-description`

  Uma descrição da propriedade.

## <a name="remarks"></a>Comentários

A marca \<value> permite descrever o valor que uma propriedade representa. Observe que quando você adiciona uma propriedade por meio do assistente de código no ambiente de desenvolvimento do Visual Studio .NET, ele adicionará uma marca [\<summary>](./summary.md) para a nova propriedade. Então, você deve adicionar manualmente uma marca \<value> para descrever o valor que a propriedade representa.

Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.

## <a name="example"></a>Exemplo

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a>Veja também

- [Guia de programação em C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
