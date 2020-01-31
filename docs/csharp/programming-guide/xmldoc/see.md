---
title: Guia de C# programação de <see>
ms.date: 07/20/2015
f1_keywords:
- <see>
- see
helpviewer_keywords:
- cref [C#], <see> tag
- <see> C# XML tag
- cross-references [C#]
- see C# XML tag
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
ms.openlocfilehash: 17d1d344b9a27ffd4995fa4849ee6d5ce7f90f29
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789696"
---
# <a name="see-c-programming-guide"></a>\<consulte > (C# guia de programação)

## <a name="syntax"></a>Sintaxe

```xml
<see cref="member"/>
```

## <a name="parameters"></a>Parâmetros

- cref = " `member`"

  Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual. O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome de elemento no XML de saída. Coloque *member* entre aspas duplas (“ ”).

## <a name="remarks"></a>Comentários

Use a marca \<see> para especificar um link de dentro do texto. Use [\<seealso>](./seealso.md) para indicar que o texto deve ser colocado em uma seção Consulte também. Use o [atributo cref](./cref-attribute.md) para criar hyperlinks internos para páginas de documentação para elementos de código.

Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.

O exemplo a seguir mostra uma marca \<see> dentro de uma seção de resumo.

[!code-csharp[csProgGuideDocComments#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#12)]

## <a name="see-also"></a>Veja também

- [Guia de programação em C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
