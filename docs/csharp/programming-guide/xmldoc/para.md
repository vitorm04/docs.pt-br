---
title: <para> -Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- <para>
- para
helpviewer_keywords:
- <para> C# XML tag
- para C# XML tag
ms.assetid: c74b8705-29df-40b1-bff5-237492b0e978
ms.openlocfilehash: d1fe81b1752d066c6b2e1ffe27f0c43fc4068edf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287292"
---
# <a name="para-c-programming-guide"></a>\<para>(Guia de programação C#)

## <a name="syntax"></a>Sintaxe

```xml
<para>content</para>
```

## <a name="parameters"></a>Parâmetros

- `content`

  O texto do parágrafo.

## <a name="remarks"></a>Comentários

A `<para>` marca é para uso dentro de uma marca, como [\<summary>](./summary.md) , [\<remarks>](./remarks.md) ou [\<returns>](./returns.md) , e permite que você adicione a estrutura ao texto.

Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.

## <a name="example"></a>Exemplo

Consulte [\<summary>](./summary.md) para obter um exemplo de como usar `<para>` .

## <a name="see-also"></a>Veja também

- [Guia de programação em C#](../index.md)
- [Marcas recomendadas para comentários de documentação](./recommended-tags-for-documentation-comments.md)
