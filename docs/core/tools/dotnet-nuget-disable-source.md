---
title: dotnet nuget desativar comando fonte
description: O comando dotnet nuget desabilita uma fonte existente em seus arquivos de configuração NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 5aa16c842bcddeead180fdeec3d9dcdda33f7ed9
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148550"
---
# <a name="dotnet-nuget-disable-source"></a>dotnet nuget desativar fonte

**Este artigo se aplica a:** ✔️ .NET Core 3.1.200 SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet nuget disable source`- Desabilite uma fonte NuGet.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet nuget disable source <NAME> [--configfile]
dotnet nuget disable source [-h|--help]
```

## <a name="description"></a>Descrição

O `dotnet nuget disable source` comando desativa uma fonte existente em seus arquivos de configuração NuGet.

## <a name="arguments"></a>Argumentos

- **`NAME`**

  Nome da fonte.

## <a name="options"></a>Opções

- **`--configfile`**

  O arquivo de configuração NuGet. Se especificado, apenas as configurações deste arquivo serão usadas. Se não for especificado, a hierarquia dos arquivos de configuração do diretório atual será usada. Para obter mais informações, consulte [Configurações comuns de NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

## <a name="examples"></a>Exemplos

- Desativar uma fonte com `mySource`o nome de:

  ```dotnetcli
  dotnet nuget disable source mySource
  ```

## <a name="see-also"></a>Confira também

- [Seções de origem do pacote em arquivos NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [comando fontes (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
