---
title: <param> - C# guia de programação
ms.date: 07/20/2015
f1_keywords:
- param
- <param>
helpviewer_keywords:
- <param> C# XML tag
- param C# XML tag
ms.assetid: 46d329b1-5b84-4537-9e17-73ca97313e4e
ms.openlocfilehash: d16070a82531519dd276b2ea999623017769d716
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789766"
---
# <a name="param-c-programming-guide"></a>> de \<paramC# (guia de programação)

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

A marca \<param> deve ser usada no comentário para uma declaração de método para descrever um dos parâmetros do método. Para documentar vários parâmetros, use várias marcas \<param>.

O texto da marca \<param> será exibido no IntelliSense, o Pesquisador de Objetos e no relatório Web de comentários sobre código.

Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.

## <a name="example"></a>Exemplo

[!code-csharp[csProgGuideDocComments#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#1)]

## <a name="see-also"></a>Veja também

- [Guia de programação em C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
