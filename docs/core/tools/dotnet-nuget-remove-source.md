---
title: dotnet nuget remover comando fonte
description: O comando dotnet nuget remove source remove uma fonte existente de seus arquivos de configuração NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 65c97b98ab50121fb4ebc184da65f021c16e0634
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148536"
---
# <a name="dotnet-nuget-remove-source"></a>dotnet nuget remover fonte

**Este artigo se aplica a:** ✔️ .NET Core 3.1.200 SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet nuget remove source`- Remova uma fonte NuGet.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet nuget remove source <NAME> [--configfile]
dotnet nuget remove source [-h|--help]
```

## <a name="description"></a>Descrição

O `dotnet nuget remove source` comando remove uma fonte existente dos arquivos de configuração nuGet.

## <a name="arguments"></a>Argumentos

- **`NAME`**

  Nome da fonte.

## <a name="options"></a>Opções

- **`--configfile`**

  O arquivo de configuração NuGet. Se especificado, apenas as configurações deste arquivo serão usadas. Se não for especificado, a hierarquia dos arquivos de configuração do diretório atual será usada. Para obter mais informações, consulte [Configurações comuns de NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

## <a name="examples"></a>Exemplos

- Remover uma fonte `mySource`com o nome de:

  ```dotnetcli
  dotnet nuget remove source mySource
  ```

## <a name="see-also"></a>Confira também

- [Seções de origem do pacote em arquivos NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [comando fontes (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
