---
title: dotnet nuget ativar comando fonte
description: O comando dotnet nuget enable source enable a source in your NuGet configuration files..com
ms.date: 03/20/2020
ms.openlocfilehash: 1f18e7db6a6c8631bb432676dd97dabfad5b0ab8
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148557"
---
# <a name="dotnet-nuget-enable-source"></a>dotnet nuget habilitar fonte

**Este artigo se aplica a:** ✔️ .NET Core 3.1.200 SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet nuget enable source`- Habilite uma fonte NuGet.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet nuget enable source <NAME> [--configfile]
dotnet nuget enable source [-h|--help]
```

## <a name="description"></a>Descrição

O `dotnet nuget enable source` comando habilita uma fonte existente em seus arquivos de configuração NuGet.

## <a name="arguments"></a>Argumentos

- **`NAME`**

  Nome da fonte.

## <a name="options"></a>Opções

- **`--configfile`**

  O arquivo de configuração NuGet. Se especificado, apenas as configurações deste arquivo serão usadas. Se não for especificado, a hierarquia dos arquivos de configuração do diretório atual será usada. Para obter mais informações, consulte [Configurações comuns de NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

## <a name="examples"></a>Exemplos

- Habilite uma `mySource`fonte com o nome de:

  ```dotnetcli
  dotnet nuget enable source mySource
  ```

## <a name="see-also"></a>Confira também

- [Seções de origem do pacote em arquivos NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [comando fontes (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
