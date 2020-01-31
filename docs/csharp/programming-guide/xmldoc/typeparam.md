---
title: <typeparam> - C# guia de programação
ms.date: 07/20/2015
f1_keywords:
- typeparam
helpviewer_keywords:
- <typeparam> C# XML tag
- typeparam C# XML tag
ms.assetid: 9b99d400-e911-4e55-99c6-64367c96aa4f
ms.openlocfilehash: 867ecacf58f95533395ded203a8f17bc92558ccf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793359"
---
# <a name="typeparam-c-programming-guide"></a>\<typeparam > (C# guia de programação)

## <a name="syntax"></a>Sintaxe

```xml
<typeparam name="name">description</typeparam>
```

## <a name="parameters"></a>Parâmetros

- `name`

  O nome do parâmetro de tipo. Coloque o nome entre aspas duplas (" ").

- `description`

  Uma descrição do parâmetro de tipo.

## <a name="remarks"></a>Comentários

A marca `<typeparam>` deve ser usada no comentário para um tipo genérico ou para uma declaração de método descrever um dos parâmetros de tipo. Adicione uma marca para cada parâmetro de tipo do tipo ou do método genérico.

Para obter mais informações, consulte [Genéricos](../generics/index.md).

O texto da marca `<typeparam>` será exibido no IntelliSense, o relatório Web de comentários sobre código da [Janela do Pesquisador de Objetos](/visualstudio/ide/viewing-the-structure-of-code#BKMK_ObjectBrowser).

Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.

## <a name="example"></a>Exemplo

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a>Veja também

- [Referência de C#](../../language-reference/index.md)
- [Guia de programação em C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
