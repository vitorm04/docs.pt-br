---
title: Identificadores de linha, arquivo e demarcador de origem
description: Saiba como usar interno F# valores do identificador que permitem que você acessar a fonte de linha número, diretório e nome de arquivo em seu código.
ms.date: 05/16/2016
ms.openlocfilehash: 4b145fe1fe20e3d7f868558e33bab26204fb0125
ms.sourcegitcommit: 3d0c29b878f00caec288dfecb3a5c959de5aa629
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/20/2018
ms.locfileid: "53656005"
---
# <a name="source-line-file-and-path-identifiers"></a>Identificadores de linha, arquivo e demarcador de origem

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
|`__SOURCE_FILE__`|É avaliada como o nome do arquivo de origem atual e seu caminho, considerando `#line` diretivas.|

Para obter mais informações sobre o `#line` diretiva, consulte [diretivas de compilador](compiler-directives.md).

## <a name="example"></a>Exemplo

O exemplo de código a seguir demonstra o uso desses valores.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet7401.fs)]

Saída:

```
Line: 4
Source Directory: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo
Source File: C:\Users\username\Documents\Visual Studio 2017\Projects\SourceInfo\SourceInfo\Program.fs
```

## <a name="see-also"></a>Consulte também

- [Diretivas de Compilador](compiler-directives.md)
- [Referência da Linguagem F#](index.md)
