---
title: <seealso> - Guia de programação C#
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
ms.openlocfilehash: e24d5910ab21f01aebb5a32ce7646cf56886a81a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77093455"
---
# <a name="seealso-c-programming-guide"></a>\<vejatambém> (guia de programação C#)

## <a name="syntax"></a>Sintaxe

```xml
<seealso cref="member"/>
```

## <a name="parameters"></a>parâmetros

- cref = " `member`"

  Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual. O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome de elemento no XML de saída.`member` deve ser exibido entre aspas duplas (" ").

  Para obter informações sobre como criar uma referência de cref a um tipo genérico, consulte [o atributo cref](./cref-attribute.md).

## <a name="remarks"></a>Comentários

A marca \<seealso > permite especificar o texto que você quer que seja exibido na seção Ver também. Consulte [ \<>](./see.md) para especificar um link de dentro do texto.

Compilar com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação para um arquivo.

## <a name="example"></a>Exemplo

Veja [ \<resumo>](./summary.md) para um \<exemplo de uso de seealso>.

## <a name="see-also"></a>Confira também

- [Guia de programação em C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
