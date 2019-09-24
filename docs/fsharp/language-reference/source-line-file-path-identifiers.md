---
title: Identificadores de linha, arquivo e caminho de origem
description: Saiba como usar valores de F# identificador internos que permitem que você acesse o número da linha de origem, o diretório e o nome do arquivo em seu código.
ms.date: 05/16/2016
ms.openlocfilehash: f22c3dfb3cb106fbe45883ffd7de01feac30db00
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216753"
---
# <a name="source-line-file-and-path-identifiers"></a>Identificadores de linha, arquivo e caminho de origem

Os identificadores `__LINE__` `__SOURCE_DIRECTORY__` e`__SOURCE_FILE__` são valores internos que permitem que você acesse o número da linha de origem, o diretório e o nome do arquivo em seu código.

## <a name="syntax"></a>Sintaxe

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a>Comentários

Cada um desses valores tem o `string`tipo.

A tabela a seguir resume os identificadores de linha de origem, arquivo e caminho que estão disponíveis F#no. Esses identificadores não são macros de pré-processador; Eles são valores internos que são reconhecidos pelo compilador.

|Identificador predefinido|Descrição|
|---------------------|-----------|
|`__LINE__`|Avalia o número da linha atual, considerando `#line` as diretivas.|
|`__SOURCE_DIRECTORY__`|Avalia o caminho completo atual do diretório de origem, considerando `#line` as diretivas.|
|`__SOURCE_FILE__`|Avalia o nome do arquivo de origem atual, sem o caminho, considerando `#line` as diretivas.|

Para obter mais informações sobre `#line` a diretiva, consulte [diretivas do compilador](compiler-directives.md).

## <a name="example"></a>Exemplo

O exemplo de código a seguir demonstra o uso desses valores.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

Saída:

```console
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: Program.fs
```

## <a name="see-also"></a>Consulte também

- [Diretivas de Compilador](compiler-directives.md)
- [Referência da Linguagem F#](index.md)
