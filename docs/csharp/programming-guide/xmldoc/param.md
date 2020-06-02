---
title: <param> -Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: 396ed716c246091a674268020261069f36dd2be8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287318"
---
# <a name="param-c-programming-guide"></a>\<param>(Guia de programação C#)

## <a name="syntax"></a>Sintaxe

```xml
<param name="name">description</param>
```

## <a name="parameters"></a>Parâmetros

- `name`

  O nome do parâmetro de um método. Coloque o nome entre aspas duplas (" ").

- `description`

  Uma descrição do parâmetro.

## <a name="remarks"></a>Comentários

A `<param>` marca deve ser usada no comentário para uma declaração de método para descrever um dos parâmetros para o método. Para documentar vários parâmetros, use várias `<param>` marcas.

O texto da `<param>` marca é exibido no IntelliSense, no Pesquisador de objetos e no relatório da Web de comentários de código.

Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.

## <a name="example"></a>Exemplo

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a>Confira também

- [Guia de programação em C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
