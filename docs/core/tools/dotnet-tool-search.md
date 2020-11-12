---
title: comando de pesquisa da ferramenta dotnet
description: O comando de pesquisa da ferramenta dotnet pesquisa as ferramentas do .NET Core que são publicadas no NuGet.org.
ms.date: 11/11/2020
ms.openlocfilehash: 4357ce4864cad386968e4a76466066fbf2ce4060
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/12/2020
ms.locfileid: "94558067"
---
# <a name="dotnet-tool-search"></a>pesquisa da ferramenta dotnet

**Este artigo aplica-se a:** ✔️ SDK do .NET 5,0 e versões posteriores

## <a name="name"></a>Name

`dotnet tool search` -Pesquisa todas as [Ferramentas do .NET Core](global-tools.md) que são publicadas no NuGet.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet tool search [--detail]  [--prerelease]
    [--skip <NUMBER>] [--take <NUMBER>] <SEARCH TERM>

dotnet tool search -h|--help
```

## <a name="description"></a>Description

O `dotnet tool search` comando fornece uma maneira de Pesquisar o NuGet para ferramentas que podem ser usadas como .net global, ferramenta-caminho ou ferramentas locais. O comando pesquisa os nomes de ferramentas e os metadados, como títulos, descrições e marcas.

O comando usa a [API de pesquisa do NuGet](/nuget/api/search-query-service-resource#search-for-packages). Ele filtra `packageType=dotnettool` para selecionar apenas pacotes de ferramentas .net.

## <a name="options"></a>Opções

- **`--detail`**

  Mostra resultados detalhados da consulta.

- **`--prerelease`**

  Inclui pacotes de pré-lançamento.

- **`--skip <NUMBER>`**

  Especifica o número de resultados da consulta a serem ignorados. Usado para paginação.

- **`--take <NUMBER>`**

  Especifica o número de resultados da consulta a serem mostrados. Usado para paginação.

- **`-h|--help`**

  Mostra a ajuda da linha de comando.

## <a name="examples"></a>Exemplos

- Pesquise NuGet.org para ferramentas .NET que tenham "Format" em seu nome de pacote ou descrição:

  ```dotnetcli
  dotnet tool search format
  ```

  A saída se parece com o seguinte exemplo:

  ```output
  Package ID                              Latest Version      Authors                                                                     Downloads      Verified
  ---------------------------------------------------------------------------------------------------------------------------------------------------------------
  dotnet-format                           4.1.131201          Microsoft                                                                   496746
  bsoa.generator                          1.0.0               Microsoft                                                                   533
  ```

- Pesquise NuGet.org para ferramentas .NET que tenham "formato" em seu nome de pacote ou metadados, mostre apenas o primeiro resultado e mostre uma exibição detalhada.

  ```dotnetcli
  dotnet tool search format --take 1 --detail
  ```

  A saída se parece com o seguinte exemplo:

  ```output
  ----------------
  dotnet-format
  Latest Version: 4.1.131201
  Authors: Microsoft
  Tags:
  Downloads: 496746
  Verified: False
  Description: Command line tool for formatting C# and Visual Basic code files based on .editorconfig settings.
  Versions:
          3.0.2 Downloads: 1973
          3.0.4 Downloads: 9064
          3.1.37601 Downloads: 114730
          3.2.107702 Downloads: 13423
          3.3.111304 Downloads: 131195
          4.0.130203 Downloads: 78610
          4.1.131201 Downloads: 145927
  ```

## <a name="see-also"></a>Veja também

- [Ferramentas do .NET Core](global-tools.md)
- [Tutorial: instalar e usar uma ferramenta global do .NET Core usando o CLI do .NET Core](global-tools-how-to-use.md)
- [Tutorial: instalar e usar uma ferramenta local do .NET Core usando o CLI do .NET Core](local-tools-how-to-use.md)
