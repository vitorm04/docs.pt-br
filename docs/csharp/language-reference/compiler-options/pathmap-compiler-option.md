---
title: -pathmap (opções do compilador C#)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 48e96d2ec2ccbea83d573c0eb3630b1591c407a9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606632"
---
# <a name="-pathmap-c-compiler-options"></a>-pathmap (opções do compilador C#)

A opção do compilador **-pathmap** especifica como mapear caminhos físicos para os nomes de caminho de origem emitidos pelo compilador.

## <a name="syntax"></a>Sintaxe

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a>Arguments

 `path1` O caminho completo para os arquivos de origem no ambiente atual

 `sourcePath1` O caminho de origem substituído por `path1` em arquivos de saída.

Para especificar vários caminhos de origem mapeados, separe-os com uma vírgula.

## <a name="remarks"></a>Comentários

O compilador grava o caminho de origem em sua saída pelos seguintes motivos:

1. O caminho de origem é substituído por um argumento quando o <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> é aplicado a um parâmetro opcional.
1. O caminho de origem é inserido em um arquivo PDB.
1. O caminho do arquivo PDB é inserido em um arquivo PE (executável portátil).

Essa opção mapeia cada caminho físico no computador em que o compilador é executado para um caminho correspondente que deve ser gravado nos arquivos de saída.

## <a name="example"></a>Exemplo

Compilar `t.cs` no diretório **C:\\work\\tests** e mapear esse diretório para **\publish** na saída:

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a>Consulte também

- [Opções do compilador de C#](./index.md)
- [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
