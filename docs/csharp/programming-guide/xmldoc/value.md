---
title: <value> - Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 120805346672738e614743ab8c98388b8dbac0f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793345"
---
# <a name="value-c-programming-guide"></a>\<valor> (guia de programação C#)

## <a name="syntax"></a>Sintaxe

```xml
<value>property-description</value>
```

## <a name="parameters"></a>parâmetros

- `property-description`

  Uma descrição da propriedade.

## <a name="remarks"></a>Comentários

A marca \<value> permite descrever o valor que uma propriedade representa. Observe que quando você adicionar uma propriedade via assistente de código no [ \<](./summary.md) ambiente de desenvolvimento do Visual Studio .NET, ele adicionará um resumo>tag para a nova propriedade. Então, você deve adicionar manualmente uma marca \<value> para descrever o valor que a propriedade representa.

Compilar com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação para um arquivo.

## <a name="example"></a>Exemplo

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a>Confira também

- [Guia de programação em C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
