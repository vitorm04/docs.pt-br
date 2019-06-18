---
title: Identificadores de linha, arquivo e caminho de origem
description: Saiba como usar interno F# valores do identificador que permitem que você acessar a fonte de linha número, diretório e nome de arquivo em seu código.
ms.date: 05/16/2016
ms.openlocfilehash: 3f2048aed9ef75037b43cd091a749e3d6bbaf9a3
ms.sourcegitcommit: 5e05f983e63d5bbd8c0b246d02c6e4f23d2fc1db
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/17/2019
ms.locfileid: "67152059"
---
# <a name="source-line-file-and-path-identifiers"></a>Identificadores de linha, arquivo e caminho de origem

Os identificadores `__LINE__`, `__SOURCE_DIRECTORY__` e `__SOURCE_FILE__` são valores internos que permitem que você acesse o nome de arquivo e diretório, número da linha de código-fonte em seu código.

## <a name="syntax"></a>Sintaxe

```fsharp
__LINE__
__SOURCE_DIRECTORY__
__SOURCE_FILE__
```

## <a name="remarks"></a>Comentários

Cada um desses valores tem tipo `string`.

A tabela a seguir resume os identificadores de linha, arquivo e caminho de origem que estão disponíveis no F#. Esses identificadores não são macros de pré-processador; eles são valores internos que são reconhecidos pelo compilador.

|Identificador predefinido|Descrição|
|---------------------|-----------|
|`__LINE__`|Retorna o número de linha atual, considerando `#line` diretivas.|
|`__SOURCE_DIRECTORY__`|É avaliada como o caminho completo atual do diretório de origem, considerando `#line` diretivas.|
|`__SOURCE_FILE__`|É avaliada como o nome de arquivo de origem atual, sem o caminho, considerando `#line` diretivas.|

Para obter mais informações sobre o `#line` diretiva, consulte [diretivas de compilador](compiler-directives.md).

## <a name="example"></a>Exemplo

O exemplo de código a seguir demonstra o uso desses valores.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

Saída:

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: Program.fs
```

## <a name="see-also"></a>Consulte também

- [Diretivas de Compilador](compiler-directives.md)
- [Referência da Linguagem F#](index.md)
