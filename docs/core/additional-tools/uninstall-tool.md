---
title: Ferramenta de desinstalação
description: Uma visão geral da ferramenta de desinstalação do .NET Core, uma ferramenta guiada que permite a limpeza controlada de SDKs e tempos de execução do .NET Core.
author: sfoslund
ms.date: 12/17/2019
ms.openlocfilehash: 5a1a419d5ad09643a7063cc03ec727c547268cc6
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75443543"
---
# <a name="net-core-uninstall-tool"></a>Ferramenta de desinstalação do .NET Core

A [ferramenta de desinstalação do .NET Core](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) permite remover SDKs do .NET Core e tempos de execução de um sistema. Uma coleção de opções está disponível para especificar quais versões você deseja desinstalar.

A ferramenta dá suporte ao Windows e ao macOS. O Linux não tem suporte no momento.

No Windows, a ferramenta só pode desinstalar SDKs e tempos de execução que foram instalados usando um dos seguintes instaladores:

- O SDK do .NET Core e o instalador de tempo de execução.
- O instalador do Visual Studio em versões anteriores ao Visual Studio 2019 versão 16,3.

No macOS, a ferramenta só pode desinstalar SDKs e tempos de execução localizados na pasta */usr/local/share/dotnet*

Devido a essas limitações, a ferramenta pode não ser capaz de desinstalar todos os SDKs do .NET Core e os tempos de execução em seu computador. Você pode usar o comando `dotnet --info` para localizar todos os SDKs do .NET Core e os tempos de execução instalados, incluindo os SDKs e os tempos de execução que essa ferramenta não pode remover. O comando `dotnet-core-uninstall list` exibe quais SDKs podem ser desinstalados com a ferramenta.

## <a name="install-the-tool"></a>Instalar a ferramenta

Você pode baixar a ferramenta de desinstalação do .NET Core no repositório do GitHub [dotnet/CLI-Lab](https://github.com/dotnet/cli-lab/releases) .

> [!NOTE]
> A ferramenta requer elevação para desinstalar SDKs e tempos de execução do .NET Core. Portanto, ele deve ser instalado em um diretório protegido contra gravação, como *c:\Arquivos de programas* no Windows ou */usr/local/bin* no MacOS. Consulte também [acesso elevado para comandos dotnet](../tools/elevated-access.md). As instruções de instalação detalhadas estão disponíveis na [página versões do GitHub](https://github.com/dotnet/cli-lab/releases).

## <a name="run-the-tool"></a>Executar a ferramenta

As etapas a seguir mostram a abordagem recomendada para executar a ferramenta de desinstalação:

- [Etapa 1-exibir os SDKs e os tempos de execução do .NET Core instalados](#step-1---display-installed-net-core-sdks-and-runtimes)
- [Etapa 2 – fazer uma simulação](#step-2---do-a-dry-run)
- [Etapa 3-desinstalar SDKs e tempos de execução do .NET Core](#step-3---uninstall-net-core-sdks-and-runtimes)
- [Etapa 4-excluir a pasta de fallback do NuGet (opcional)](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a>Etapa 1-exibir os SDKs e os tempos de execução do .NET Core instalados

O comando `dotnet-core-uninstall list` lista os SDKs e os tempos de execução do .NET Core instalados que podem ser removidos com essa ferramenta. Alguns SDKs e tempos de execução podem ser exigidos pelo Visual Studio e são exibidos com uma observação de por que não é recomendável desinstalá-los.

**dotnet-núcleo-desinstalação da lista**

#### <a name="synopsis"></a>Sinopse

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a>Opções

## <a name="windowstabwindows"></a>[Windows](#tab/windows)

* **`--aspnet-runtime`**

  Lista todos os tempos de execução de ASP.NET Core que podem ser desinstalados com essa ferramenta.

* **`--hosting-bundle`**

  Lista todos os pacotes de hospedagem e de tempo de execução do .NET Core que podem ser desinstalados com essa ferramenta.

* **`--runtime`**

  Lista todos os tempos de execução do .NET Core que podem ser desinstalados com essa ferramenta.

* **`--sdk`**

  Lista todos os SDKs do .NET Core que podem ser desinstalados com essa ferramenta.

* **`-v, --verbosity <LEVEL>`**

  Define o nível de detalhes. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`. O valor padrão é `normal`.

* **`--x64`**

  Lista todos os SDKs e tempos de execução do .NET Core x64 que podem ser desinstalados com essa ferramenta.

* **`--x86`**

  Lista todos os SDKs e tempos de execução do .NET Core x86 que podem ser desinstalados com essa ferramenta.

## <a name="macostabmacos"></a>[macOS](#tab/macos)

* **`--runtime`**

  Lista todos os tempos de execução do .NET Core que podem ser desinstalados com essa ferramenta.

* **`--sdk`**

  Lista todos os SDKs do .NET Core que podem ser desinstalados com essa ferramenta.

* **`-v, --verbosity <LEVEL>`**

  Define o nível de detalhes. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`. O valor padrão é `normal`.
  
---

#### <a name="examples"></a>Exemplos

* Listar todos os SDKs e tempos de execução do .NET Core que podem ser removidos com esta ferramenta:

  ```console
  dotnet-core-uninstall list
  ```

* Listar todos os SDKs e tempos de execução do .NET Core x64:

  ```console
  dotnet-core-uninstall list --x64
  ```

* Listar todos os SDKs do .NET Core x86:

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a>Etapa 2 – fazer uma simulação

Os comandos `dotnet-core-uninstall dry-run` e `dotnet-core-uninstall whatif` exibem os SDKs e os tempos de execução do .NET Core que serão removidos com base nas opções fornecidas sem executar a desinstalação. Esses comandos são sinônimos.

**dotnet-Core-Uninstall secat-Run e dotnet-Core-Uninstall WhatIf**

#### <a name="synopsis"></a>Sinopse

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a>Arguments

* **`VERSION`**

  A versão especificada a ser desinstalada. Você pode listar várias versões uma após a outra, separadas por espaços. Também há suporte para arquivos de resposta.

  > [!TIP]
  > Os arquivos de resposta são uma alternativa para colocar todas as versões na linha de comando.
  > São arquivos de texto, normalmente com uma extensão \*. rsp, e cada versão é listada em uma linha separada.
  > Para especificar um arquivo de resposta para o argumento `VERSION`, use o caractere \@ seguido imediatamente pelo nome do arquivo de resposta.

#### <a name="options"></a>Opções

## <a name="windowstabwindows"></a>[Windows](#tab/windows)

* **`--all`**

  Remove todos os SDKs e tempos de execução do .NET Core.

* **`--all-below <VERSION>`**

  Remove somente os SDKs do .NET Core e os tempos de execução com uma versão menor do que a versão especificada. A versão especificada permanece instalada.

* **`--all-but <VERSIONS>`**

  Remove todos os SDKs e tempos de execução do .NET Core, exceto as versões especificadas.

* **`--all-but-latest`**

  Remove SDKs e tempos de execução do .NET Core, exceto a versão mais recente.

* **`--all-lower-patches`**

  Remove os SDKs do .NET Core e os tempos de execução substituídos por patches mais altos. Essa opção protege global. JSON.

* **`--all-previews`**

  Remove SDKs e tempos de execução do .NET Core marcados como visualizações.

* **`--all-previews-but-latest`**

  Remove os SDKs e os tempos de execução do .NET Core marcados como versões prévias, exceto a visualização mais alta.

* **`--aspnet-runtime`**

  Remove somente ASP.NET Core tempo de execução.

* **`--hosting-bundle`**

  Remove somente os agrupamentos de hospedagem e de tempo de execução do .NET Core.

* **`--major-minor <MAJOR_MINOR>`**

  Remove SDKs e tempos de execução do .NET Core que correspondem à versão de `major.minor` especificada.

* **`--runtime`**

  Remove somente os tempos de execução do .NET Core.

* **`--sdk`**

  Remove somente SDKs do .NET Core.

* **`-v, --verbosity <LEVEL>`**

  Define o nível de detalhes. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`. O valor padrão é `normal`.

* **`--x64`**

  Deve ser usado com `--sdk`, `--runtime`e `--aspnet-runtime` para remover SDKs ou tempos de execução de x64.

* **`--x86`**

  Deve ser usado com `--sdk`, `--runtime`e `--aspnet-runtime` para remover SDKs ou tempos de execução do x86.

* **`--force`** Força a remoção de versões que podem ser usadas pelo Visual Studio.

Observações:

1. É necessário ter exatamente um dos `--sdk`, `--runtime`, `--aspnet-runtime`e `--hosting-bundle`.
2. `--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`e `[<VERSION>...]` são exclusivos.
3. Se `--x64` ou `--x86` não forem especificados, tanto o x64 quanto o x86 serão removidos.

## <a name="macostabmacos"></a>[macOS](#tab/macos)

* **`--all`**

  Remove todos os SDKs e tempos de execução do .NET Core.

* **`--all-below <VERSION>`**

  Remove os SDKs do .NET Core e os tempos de execução abaixo da versão especificada. A versão especificada permanecerá.

* **`--all-but <VERSIONS>`**

  Remove SDKs e tempos de execução do .NET Core, exceto as versões especificadas.

* **`--all-but-latest`**

  Remove SDKs e tempos de execução do .NET Core, exceto a versão mais recente.

* **`--all-lower-patches`**

  Remove os SDKs do .NET Core e os tempos de execução substituídos por patches mais altos. Essa opção protege global. JSON.

* **`--all-previews`**

  Remove SDKs e tempos de execução do .NET Core marcados como visualizações.

* **`--all-previews-but-latest`**

  Remove os SDKs e os tempos de execução do .NET Core marcados como versões prévias, exceto a visualização mais alta.

* **`--major-minor <MAJOR_MINOR>`**

  Remove SDKs e tempos de execução do .NET Core que correspondem à versão de `major.minor` especificada.

* **`--runtime`**

  Remove somente os tempos de execução do .NET Core.

* **`--sdk`**

  Remove somente SDKs do .NET Core.

* **`-v, --verbosity <LEVEL>`**

  Define o nível de detalhes. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`. O valor padrão é `normal`.
  
* **`--force`** Força a remoção de versões que podem ser usadas pelo Visual Studio ou SDKs.

Observações:

1. É necessário ter exatamente um dos `--sdk` e `--runtime`.
2. `--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`e `[<VERSION>...]` são exclusivos.

---

#### <a name="examples"></a>Exemplos

> [!NOTE]
> Por padrão, os SDKs do .NET Core e os tempos de execução que podem ser exigidos pelo Visual Studio ou outros SDKs não são incluídos na saída `dotnet-core-uninstall dry-run`. Nos exemplos a seguir, alguns dos SDKs e tempos de execução especificados podem não ser incluídos na saída, dependendo do estado do computador. Para incluir todos os SDKs e tempos de execução, liste-os explicitamente como argumentos ou use a opção `--force`.

* Simulação da execução da remoção de todos os tempos de execução do .NET Core que foram substituídos por patches mais altos:

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* Simulação da execução da remoção de todos os SDKs do .NET Core abaixo da versão `2.2.301`:

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a>Etapa 3-desinstalar SDKs e tempos de execução do .NET Core

`dotnet-core-uninstall remove` desinstala SDKs e tempos de execução do .NET Core que são especificados por uma coleção de opções. A ferramenta não pode ser usada para desinstalar SDKs e tempos de execução com a versão 5,0 ou superior.

Como essa ferramenta tem um comportamento destrutivo, é **altamente** recomendável que você execute uma simulação antes de executar o comando remover. A execução seca mostrará quais SDKs e tempos de execução do .NET Core serão removidos quando você usar o comando `remove`. Consulte devo [remover uma versão?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version) para saber quais SDKs e tempos de execução são seguros de remover.

> [!CAUTION]
> Tenha em mente as seguintes advertências:
>
>- Essa ferramenta pode desinstalar versões do SDK do .NET Core que são necessárias para `global.json` arquivos em seu computador. Você pode reinstalar SDKs do .NET Core na página [baixar o .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .
>- Essa ferramenta pode desinstalar versões do tempo de execução do .NET Core que são exigidas por aplicativos dependentes da estrutura em seu computador. Você pode reinstalar os tempos de execução do .NET Core na página [baixar o .NET Core](https://dotnet.microsoft.com/download/dotnet-core) .
>- Essa ferramenta pode desinstalar versões do SDK do .NET Core e do tempo de execução dos quais o Visual Studio depende. Se você interromper a instalação do Visual Studio, execute "reparar" no instalador do Visual Studio para voltar a um estado de funcionamento.

Por padrão, todos os comandos mantêm os SDKs do .NET Core e os tempos de execução que podem ser exigidos pelo Visual Studio ou outros SDKs. Esses SDKs e tempos de execução podem ser desinstalados, listando-os explicitamente como argumentos ou usando a opção `--force`.

A ferramenta requer elevação para desinstalar SDKs e tempos de execução do .NET Core. Execute a ferramenta em um prompt de comando do administrador no Windows e com `sudo` no macOS. Os comandos `dry-run` e `whatif` não exigem elevação.

**dotnet-núcleo-desinstalar remover**

#### <a name="synopsis"></a>Sinopse

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a>Arguments

* **`VERSION`**

  A versão especificada a ser desinstalada. Você pode listar várias versões uma após a outra, separadas por espaços. Também há suporte para arquivos de resposta.

  > [!TIP]
  > Os arquivos de resposta são uma alternativa para colocar todas as versões na linha de comando.
  > São arquivos de texto, normalmente com uma extensão \*. rsp, e cada versão é listada em uma linha separada.
  > Para especificar um arquivo de resposta para o argumento `VERSION`, use o caractere \@ seguido imediatamente pelo nome do arquivo de resposta.

#### <a name="options"></a>Opções

## <a name="windowstabwindows"></a>[Windows](#tab/windows)

* **`--all`**

  Remove todos os SDKs e tempos de execução do .NET Core.

* **`--all-below <VERSION>`**

  Remove somente os SDKs do .NET Core e os tempos de execução com uma versão menor do que a versão especificada. A versão especificada permanece instalada.

* **`--all-but <VERSIONS>`**

  Remove todos os SDKs e tempos de execução do .NET Core, exceto as versões especificadas.

* **`--all-but-latest`**

  Remove SDKs e tempos de execução do .NET Core, exceto a versão mais recente.

* **`--all-lower-patches`**

  Remove os SDKs do .NET Core e os tempos de execução substituídos por patches mais altos. Essa opção protege global. JSON.

* **`--all-previews`**

  Remove SDKs e tempos de execução do .NET Core marcados como visualizações.

* **`--all-previews-but-latest`**

  Remove os SDKs e os tempos de execução do .NET Core marcados como versões prévias, exceto a visualização mais alta.

* **`--aspnet-runtime`**

  Remove somente ASP.NET Core tempo de execução.

* **`--hosting-bundle`**

  Remove somente os agrupamentos de hospedagem e de tempo de execução do .NET Core.

* **`--major-minor <MAJOR_MINOR>`**

  Remove SDKs e tempos de execução do .NET Core que correspondem à versão de `major.minor` especificada.

* **`--runtime`**

  Remove somente os tempos de execução do .NET Core.

* **`--sdk`**

  Remove somente SDKs do .NET Core.

* **`-v, --verbosity <LEVEL>`**

  Define o nível de detalhes. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`. O valor padrão é `normal`.

* **`--x64`**

  Deve ser usado com `--sdk`, `--runtime`e `--aspnet-runtime` para remover SDKs ou tempos de execução de x64.

* **`--x86`**

  Deve ser usado com `--sdk`, `--runtime`e `--aspnet-runtime` para remover SDKs ou tempos de execução do x86.

* **`-y, --yes`** Executa o comando sem a necessidade de uma confirmação Sim ou não.

* **`--force`** Força a remoção de versões que podem ser usadas pelo Visual Studio.

Observações:

1. É necessário ter exatamente um dos `--sdk`, `--runtime`, `--aspnet-runtime`e `--hosting-bundle`.
2. `--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`e `[<VERSION>...]` são exclusivos.
3. Se `--x64` ou `--x86` não forem especificados, tanto o x64 quanto o x86 serão removidos.

## <a name="macostabmacos"></a>[macOS](#tab/macos)

* **`--all`**

  Remove todos os SDKs e tempos de execução do .NET Core.

* **`--all-below <VERSION>`**

  Remove os SDKs do .NET Core e os tempos de execução abaixo da versão especificada. A versão especificada permanecerá.

* **`--all-but <VERSIONS>`**

  Remove SDKs e tempos de execução do .NET Core, exceto as versões especificadas.

* **`--all-but-latest`**

  Remove SDKs e tempos de execução do .NET Core, exceto a versão mais recente.

* **`--all-lower-patches`**

  Remove os SDKs do .NET Core e os tempos de execução substituídos por patches mais altos. Essa opção protege global. JSON.

* **`--all-previews`**

  Remove SDKs e tempos de execução do .NET Core marcados como visualizações.

* **`--all-previews-but-latest`**

  Remove os SDKs e os tempos de execução do .NET Core marcados como versões prévias, exceto a visualização mais alta.

* **`--major-minor <MAJOR_MINOR>`**

  Remove SDKs e tempos de execução do .NET Core que correspondem à versão de `major.minor` especificada.

* **`--runtime`**

  Remove somente os tempos de execução do .NET Core.

* **`--sdk`**

  Remove somente SDKs do .NET Core.

* **`-v, --verbosity <LEVEL>`**

  Define o nível de detalhes. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`. O valor padrão é `normal`.

* **`-y, --yes`** Executa o comando sem a necessidade de confirmação de Y/n.
  
* **`--force`** Força a remoção de versões que podem ser usadas pelo Visual Studio ou SDKs.

Observações:

1. É necessário ter exatamente um dos `--sdk` e `--runtime`.
2. `--all`, `--all-below`, `--all-but`, `--all-but-latest`, `--all-lower-patches`, `--all-previews`, `--all-previews-but-latest`, `--major-minor`e `[<VERSION>...]` são exclusivos.

---

#### <a name="examples"></a>Exemplos

> [!NOTE]
> Por padrão, os SDKs do .NET Core e os tempos de execução que podem ser exigidos pelo Visual Studio ou outros SDKs são mantidos. Nos exemplos a seguir, alguns dos SDKs e tempos de execução especificados podem permanecer, dependendo do estado do computador. Para remover todos os SDKs e tempos de execução, liste-os explicitamente como argumentos ou use a opção `--force`.

* Remova todos os tempos de execução do .NET Core x86, exceto a versão `3.0.0-preview6-27804-01` sem exigir confirmação de Y/n:

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* Remova todos os SDKs do .NET Core 1,1 sem exigir confirmação de s/n:

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* Remova o SDK do .NET Core 1.1.11 sem saída de console:

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes -verbosity q
  ```

* Remova todos os SDKs do .NET Core que podem ser removidos com segurança por essa ferramenta:

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* Remova todos os SDKs do .NET Core que podem ser removidos por essa ferramenta, incluindo os SDKs que podem ser exigidos pelo Visual Studio (não recomendado):

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* Remova todos os SDKs do .NET Core especificados no arquivo de resposta `versions.rsp`

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  O conteúdo de *Versions. rsp* é o seguinte:
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a>Etapa 4-excluir a pasta de fallback do NuGet (opcional)

Em alguns casos, você não precisa mais do `NuGetFallbackFolder` e talvez queira excluí-lo. Para obter mais informações sobre como excluir essa pasta, consulte [remover o NuGetFallbackFolder](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).

## <a name="uninstall-the-tool"></a>Desinstalar a ferramenta

## <a name="windowstabwindows"></a>[Windows](#tab/windows)

1. Abra **Adicionar ou remover programas**.
2. Pesquise por `Microsoft .NET Core SDK Uninstall Tool`.
3. Selecione **Desinstalar**.

## <a name="macostabmacos"></a>[macOS](#tab/macos)

Exclua o arquivo *dotnet-Core-Uninstall. tar. gz* baixado do diretório em que ele foi instalado. Se você descompactou o conteúdo desse arquivo em outro diretório, certifique-se de excluir esse conteúdo também.

---
