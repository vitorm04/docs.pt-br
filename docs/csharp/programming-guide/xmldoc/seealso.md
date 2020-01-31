---
title: <seealso> - C# guia de programação
ms.date: 07/20/2015
f1_keywords:
- cref
- <seealso>
- seealso
helpviewer_keywords:
- cref [C#], see also
- seealso C# XML tag
- cref [C#]
- cross-references [C#], tags
- <seealso> C# XML tag
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
ms.openlocfilehash: ad22b423d085a152f47c4e34d7ee4247ef9836b8
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789688"
---
# <a name="seealso-c-programming-guide"></a>\<seeAlso > (C# guia de programação)

## <a name="syntax"></a>Sintaxe

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a>Parâmetros

- cref = " `member`"

  Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual. O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome de elemento no XML de saída.`member` deve ser exibido entre aspas duplas (" ").

  Para obter informações sobre como criar uma referência cref para um tipo genérico, consulte [\<consulte>](./see.md).

## <a name="remarks"></a>Comentários

A marca \<seealso > permite especificar o texto que você quer que seja exibido na seção Ver também. Use [\<see>](./see.md) para especificar um link de dentro do texto.

Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.

## <a name="example"></a>Exemplo

Consulte [\<summary>](./summary.md) para obter um exemplo sobre o uso de \<seealso>.

## <a name="see-also"></a>Veja também

- [Guia de programação em C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
