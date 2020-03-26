---
title: dotnet nuget comando fonte de lista
description: O comando dotnet nuget list list all existing sources from your NuGet configuration files.
ms.date: 03/20/2020
ms.openlocfilehash: 4d7bc3dbd3ab5eb14c1ebf592044b685d28355cd
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148571"
---
# <a name="dotnet-nuget-list-source"></a>dotnet nuget fonte de lista

**Este artigo se aplica a:** ✔️ .NET Core 3.1.200 SDK e versões posteriores

## <a name="name"></a>Nome

`dotnet nuget list source`- Lista todas as fontes nuget configuradas.

## <a name="synopsis"></a>Sinopse

```dotnetcli
dotnet nuget list source [--format] [--configfile]
dotnet nuget list source [-h|--help]
```

## <a name="description"></a>Descrição

O `dotnet nuget list source` comando lista todas as fontes existentes dos arquivos de configuração do NuGet.

## <a name="options"></a>Opções

- **`--configfile`**

  O arquivo de configuração NuGet. Se especificado, apenas as configurações deste arquivo serão usadas. Se não for especificado, a hierarquia dos arquivos de configuração do diretório atual será usada. Para obter mais informações, consulte [Configurações comuns de NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).

- **`--format`**

  O formato da saída `Detailed` de comando da `Short`lista: (o padrão) e .

## <a name="examples"></a>Exemplos

- Listar fontes configuradas do diretório atual:

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a>Confira também

- [Seções de origem do pacote em arquivos NuGet.config](/nuget/reference/nuget-config-file#package-source-sections)

- [comando fontes (nuget.exe)](/nuget/reference/cli-reference/cli-ref-sources)
