---
title: Desinstalar ferramenta
description: Uma visão geral da Ferramenta de Desinstalação do Núcleo .NET, uma ferramenta guiada que permite a limpeza controlada de SDKs e tempos de execução do Núcleo .NET.
author: sfoslund
ms.date: 01/06/2020
ms.openlocfilehash: bd20cba133cbb754dcca48e48b76a391a9efacba
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846992"
---
# <a name="net-core-uninstall-tool"></a>Ferramenta de Desinstalação do .NET Core

A`dotnet-core-uninstall` [ferramenta de desinstalação do núcleo .NET](https://aka.ms/dotnet-core-uninstall-tool) permite remover SDKs e runtimes do .NET Core de um sistema. Uma coleção de opções está disponível para especificar quais versões você deseja desinstalar.

A ferramenta suporta Windows e macOS. O Linux não tem suporte no momento.

No Windows, a ferramenta só pode desinstalar SDKs e Runtimes que foram instalados usando um dos seguintes instaladores:

- O .NET Core SDK e o instalador de tempo de execução.
- O instalador do Visual Studio em versões anteriores ao Visual Studio 2019 versão 16.3.

No macOS, a ferramenta só pode desinstalar SDKs e runtimes localizados na pasta */usr/local/share/dotnet.*

Devido a essas limitações, a ferramenta pode não ser capaz de desinstalar todos os SDKs e tempos de execução do .NET Core na sua máquina. Você pode `dotnet --info` usar o comando para encontrar todos os SDKs e tempos de execução do .NET Core instalados, incluindo os SDKs e tempos de execução que esta ferramenta não pode remover. O `dotnet-core-uninstall list` comando exibe quais SDKs podem ser desinstalados com a ferramenta.

## <a name="install-the-tool"></a>Instale a ferramenta

Você pode baixar a Ferramenta de Desinstalação do Núcleo .NET [daqui](https://aka.ms/dotnet-core-uninstall-tool) e encontrar o código-fonte no repositório [dotnet/cli-lab](https://github.com/dotnet/cli-lab) GitHub.

> [!NOTE]
> A ferramenta requer elevação para desinstalar SDKs e tempos de execução do Núcleo .NET. Portanto, ele deve ser instalado em um diretório protegido por gravação, como *C:\Arquivos de programa* no Windows ou */usr/local/bin* no macOS. Veja também [acesso elevado para comandos dotnet](../tools/elevated-access.md). Para obter mais informações, consulte as [instruções detalhadas de instalação](https://aka.ms/dotnet-core-uninstall-tool).

## <a name="run-the-tool"></a>Execute a ferramenta

As etapas a seguir mostram a abordagem recomendada para executar a ferramenta de desinstalação:

- [Passo 1 - Exibir SDKs e tempos de execução instalados .NET Core](#step-1---display-installed-net-core-sdks-and-runtimes)
- [Passo 2 - Faça uma corrida a seco](#step-2---do-a-dry-run)
- [Passo 3 - Desinstalar SDKs e runtimes do núcleo .NET](#step-3---uninstall-net-core-sdks-and-runtimes)
- [Passo 4 - Excluir a pasta de recuo NuGet (opcional)](#step-4---delete-the-nuget-fallback-folder-optional)

### <a name="step-1---display-installed-net-core-sdks-and-runtimes"></a>Passo 1 - Exibir SDKs e tempos de execução instalados .NET Core

O `dotnet-core-uninstall list` comando lista os SDKs do Núcleo .NET instalados e os tempos de execução que podem ser removidos com esta ferramenta. Alguns SDKs e tempos de execução podem ser exigidos pelo Visual Studio e eles são exibidos com uma nota de por que não é recomendado desinstalá-los.

**dotnet-core-uninstall list**

#### <a name="synopsis"></a>Sinopse

```console
dotnet-core-uninstall list [options]
```

#### <a name="options"></a>Opções

## <a name="windows"></a>[Windows](#tab/windows)

* **`--aspnet-runtime`**

  Lista todos os tempos de execução do ASP.NET Core que podem ser desinstalados com esta ferramenta.

* **`--hosting-bundle`**

  Lista todos os pacotes de tempo de execução do .NET Core e de hospedagem que podem ser desinstalados com esta ferramenta.

* **`--runtime`**

  Lista todos os tempos de execução do .NET Core que podem ser desinstalados com esta ferramenta.

* **`--sdk`**

  Lista todos os SDKs do Núcleo .NET que podem ser desinstalados com esta ferramenta.

* **`-v, --verbosity <LEVEL>`**

  Define o nível de verbosidade. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`. O valor padrão é `normal`.

* **`--x64`**

  Lista todos os SDKs do Núcleo .NET x64 e tempos de execução que podem ser desinstalados com esta ferramenta.

* **`--x86`**

  Lista todos os SDKs do Núcleo .NET x86 e tempos de execução que podem ser desinstalados com esta ferramenta.

## <a name="macos"></a>[macOS](#tab/macos)

* **`--runtime`**

  Lista todos os tempos de execução do .NET Core que podem ser desinstalados com esta ferramenta.

* **`--sdk`**

  Lista todos os SDKs do Núcleo .NET que podem ser desinstalados com esta ferramenta.

* **`-v, --verbosity <LEVEL>`**

  Define o nível de verbosidade. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`. O valor padrão é `normal`.
  
---

#### <a name="examples"></a>Exemplos

* Liste todos os SDKs e tempos de execução do .NET Core que podem ser removidos com esta ferramenta:

  ```console
  dotnet-core-uninstall list
  ```

* Liste todos os SDKs do Núcleo .NET x64 e tempos de execução:

  ```console
  dotnet-core-uninstall list --x64
  ```

* Liste todos os SDKs do núcleo x86 .NET:

  ```console
  dotnet-core-uninstall list --sdk --x86
  ```

### <a name="step-2---do-a-dry-run"></a>Passo 2 - Faça uma corrida a seco

Os `dotnet-core-uninstall dry-run` `dotnet-core-uninstall whatif` comandos exibem os SDKs do Núcleo .NET e os tempos de execução que serão removidos com base nas opções fornecidas sem realizar a desinstalação. Esses comandos são sinônimos.

**dotnet-core-desinstalar dry-run e dotnet-core-desinstalar whatif**

#### <a name="synopsis"></a>Sinopse

```console
dotnet-core-uninstall dry-run [options] [<VERSION>...]

dotnet-core-uninstall whatif [options] [<VERSION>...]
```

#### <a name="arguments"></a>Argumentos

* **`VERSION`**

  A versão especificada para desinstalar. Você pode listar várias versões uma após a outra, separadas por espaços. Os arquivos de resposta também são suportados.

  > [!TIP]
  > Os arquivos de resposta são uma alternativa para colocar todas as versões na linha de comando.
  > São arquivos de texto, normalmente com uma \*extensão .rsp, e cada versão é listada em uma linha separada.
  > Para especificar um `VERSION` arquivo de \@ resposta para o argumento, use o caractere imediatamente seguido pelo nome do arquivo de resposta.

#### <a name="options"></a>Opções

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  Remove todos os SDKs do Núcleo .NET e tempos de execução.

* **`--all-below <VERSION>`**

  Remove apenas os SDKs do Núcleo .NET e os tempos de execução com uma versão menor que a especificada. A versão especificada permanece instalada.

* **`--all-but <VERSIONS>`**

  Remove todos os SDKs e tempos de execução do .NET Core, exceto as versões especificadas.

* **`--all-but-latest`**

  Remove SDKs e tempos de execução do .NET Core, exceto a versão mais alta.

* **`--all-lower-patches`**

  Remove SDKs do Núcleo .NET e tempos de execução substituídos por patches mais altos. Esta opção protege global.json.

* **`--all-previews`**

  Remove SDKs do Núcleo .NET e tempos de execução marcados como visualizações.

* **`--all-previews-but-latest`**

  Remove SDKs do Núcleo .NET e tempos de execução marcados como visualizações, exceto a visualização mais alta.

* **`--aspnet-runtime`**

  Remove apenas ASP.NET tempos de execução do Core.

* **`--hosting-bundle`**

  Remove apenas o tempo de execução do .NET Core e os pacotes de hospedagem.

* **`--major-minor <MAJOR_MINOR>`**

  Remove SDKs do Núcleo .NET e tempos `major.minor` de execução que correspondem à versão especificada.

* **`--runtime`**

  Remove apenas os tempos de execução do .NET Core.

* **`--sdk`**

  Remove apenas SDKs do Núcleo .NET.

* **`-v, --verbosity <LEVEL>`**

  Define o nível de verbosidade. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`. O valor padrão é `normal`.

* **`--x64`**

  Deve ser `--sdk`usado `--runtime`com `--aspnet-runtime` , e para remover sdks x64 ou tempos de execução.

* **`--x86`**

  Deve ser `--sdk`usado `--runtime`com `--aspnet-runtime` , e para remover sdks x86 ou tempos de execução.

* **`--force`** Força a remoção de versões que podem ser usadas pelo Visual Studio.

Observações:

1. Exatamente um `--sdk` `--runtime`dos `--aspnet-runtime`, `--hosting-bundle` , e é necessário.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , , , , e são exclusivos.
3. Se `--x64` `--x86` ou não forem especificados, então tanto x64 quanto x86 serão removidos.

## <a name="macos"></a>[macOS](#tab/macos)

* **`--all`**

  Remove todos os SDKs do Núcleo .NET e tempos de execução.

* **`--all-below <VERSION>`**

  Remove SDKs do Núcleo .NET e tempos de execução abaixo da versão especificada. A versão especificada permanecerá.

* **`--all-but <VERSIONS>`**

  Remove SDKs e tempos de execução do .NET Core, exceto as versões especificadas.

* **`--all-but-latest`**

  Remove SDKs e tempos de execução do .NET Core, exceto a versão mais alta.

* **`--all-lower-patches`**

  Remove SDKs do Núcleo .NET e tempos de execução substituídos por patches mais altos. Esta opção protege global.json.

* **`--all-previews`**

  Remove SDKs do Núcleo .NET e tempos de execução marcados como visualizações.

* **`--all-previews-but-latest`**

  Remove SDKs do Núcleo .NET e tempos de execução marcados como visualizações, exceto a visualização mais alta.

* **`--major-minor <MAJOR_MINOR>`**

  Remove SDKs do Núcleo .NET e tempos `major.minor` de execução que correspondem à versão especificada.

* **`--runtime`**

  Remove apenas os tempos de execução do .NET Core.

* **`--sdk`**

  Remove apenas SDKs do Núcleo .NET.

* **`-v, --verbosity <LEVEL>`**

  Define o nível de verbosidade. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`. O valor padrão é `normal`.
  
* **`--force`** Força a remoção de versões que podem ser usadas pelo Visual Studio ou SDKs.

Observações:

1. Exatamente um `--sdk` `--runtime` dos mais necessários.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , , , , e são exclusivos.

---

#### <a name="examples"></a>Exemplos

> [!NOTE]
> Por padrão, Os SDKs do Núcleo .NET e os tempos de execução `dotnet-core-uninstall dry-run` que podem ser exigidos pelo Visual Studio ou outros SDKs não estão incluídos na saída. Nos exemplos a seguir, alguns dos SDKs e tempos de execução especificados podem não ser incluídos na saída, dependendo do estado da máquina. Para incluir todos os SDKs e tempos de execução, liste-os explicitamente como argumentos ou use a `--force` opção.

* Dry run of removeall .NET Core runtimes que foram substituídos por patches mais altos:

  ```console
  dotnet-core-uninstall dry-run --all-lower-patches --runtime
  ```

* Dry run de remover todos os SDKs `2.2.301`do Núcleo .NET abaixo da versão :

  ```console
  dotnet-core-uninstall whatif --all-below 2.2.301 --sdk
  ```

### <a name="step-3---uninstall-net-core-sdks-and-runtimes"></a>Passo 3 - Desinstalar SDKs e runtimes do núcleo .NET

`dotnet-core-uninstall remove`desinstala SDKs e Runtimes do Núcleo .NET especificados por uma coleção de opções. A ferramenta não pode ser usada para desinstalar SDKs e Runtimes com a versão 5.0 ou superior.

Uma vez que esta ferramenta tem um comportamento destrutivo, é **altamente** recomendável que você faça uma corrida a seco antes de executar o comando remover. A corrida a seco mostrará quais SDKs e tempos de `remove` execução do .NET Core serão removidos quando você usar o comando. Consulte [Devo remover uma versão?](../versions/remove-runtime-sdk-versions.md#should-i-remove-a-version)

> [!CAUTION]
> Tenha em mente as seguintes advertências:
>
>- Esta ferramenta pode desinstalar versões do .NET `global.json` Core SDK que são exigidas por arquivos em sua máquina. Você pode reinstalar SDKs do Núcleo .NET na página [Download .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)
>- Esta ferramenta pode desinstalar versões do tempo de execução do .NET Core que são exigidas por aplicativos dependentes de framework na sua máquina. Você pode reinstalar os tempos de execução do .NET Core a partir da página [Download .NET Core.](https://dotnet.microsoft.com/download/dotnet-core)
>- Esta ferramenta pode desinstalar versões do .NET Core SDK e tempo de execução que o Visual Studio conta. Se você interromper a instalação do Visual Studio, execute "Repair" no instalador do Visual Studio para voltar a um estado de trabalho.

Por padrão, todos os comandos mantêm os SDKs do Núcleo .NET e os tempos de execução que podem ser exigidos pelo Visual Studio ou outros SDKs. Esses SDKs e tempos de execução podem ser desinstalados `--force` listando-os explicitamente como argumentos ou usando a opção.

A ferramenta requer elevação para desinstalar SDKs e tempos de execução do Núcleo .NET. Execute a ferramenta em um prompt `sudo` de comando administrador no Windows e com o macOS. Os `dry-run` `whatif` comandos não requerem elevação.

**dotnet-core-desinstalar remover**

#### <a name="synopsis"></a>Sinopse

```console
dotnet-core-uninstall remove [options] [<VERSION>...]
```

#### <a name="arguments"></a>Argumentos

* **`VERSION`**

  A versão especificada para desinstalar. Você pode listar várias versões uma após a outra, separadas por espaços. Os arquivos de resposta também são suportados.

  > [!TIP]
  > Os arquivos de resposta são uma alternativa para colocar todas as versões na linha de comando.
  > São arquivos de texto, normalmente com uma \*extensão .rsp, e cada versão é listada em uma linha separada.
  > Para especificar um `VERSION` arquivo de \@ resposta para o argumento, use o caractere imediatamente seguido pelo nome do arquivo de resposta.

#### <a name="options"></a>Opções

## <a name="windows"></a>[Windows](#tab/windows)

* **`--all`**

  Remove todos os SDKs do Núcleo .NET e tempos de execução.

* **`--all-below <VERSION>`**

  Remove apenas os SDKs do Núcleo .NET e os tempos de execução com uma versão menor que a especificada. A versão especificada permanece instalada.

* **`--all-but <VERSIONS>`**

  Remove todos os SDKs e tempos de execução do .NET Core, exceto as versões especificadas.

* **`--all-but-latest`**

  Remove SDKs e tempos de execução do .NET Core, exceto a versão mais alta.

* **`--all-lower-patches`**

  Remove SDKs do Núcleo .NET e tempos de execução substituídos por patches mais altos. Esta opção protege global.json.

* **`--all-previews`**

  Remove SDKs do Núcleo .NET e tempos de execução marcados como visualizações.

* **`--all-previews-but-latest`**

  Remove SDKs do Núcleo .NET e tempos de execução marcados como visualizações, exceto a visualização mais alta.

* **`--aspnet-runtime`**

  Remove apenas ASP.NET tempos de execução do Core.

* **`--hosting-bundle`**

  Remove apenas o tempo de execução do .NET Core e os pacotes de hospedagem.

* **`--major-minor <MAJOR_MINOR>`**

  Remove SDKs do Núcleo .NET e tempos `major.minor` de execução que correspondem à versão especificada.

* **`--runtime`**

  Remove apenas os tempos de execução do .NET Core.

* **`--sdk`**

  Remove apenas SDKs do Núcleo .NET.

* **`-v, --verbosity <LEVEL>`**

  Define o nível de verbosidade. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`. O valor padrão é `normal`.

* **`--x64`**

  Deve ser `--sdk`usado `--runtime`com `--aspnet-runtime` , e para remover sdks x64 ou tempos de execução.

* **`--x86`**

  Deve ser `--sdk`usado `--runtime`com `--aspnet-runtime` , e para remover sdks x86 ou tempos de execução.

* **`-y, --yes`** Executa o comando sem exigir uma confirmação de sim ou não.

* **`--force`** Força a remoção de versões que podem ser usadas pelo Visual Studio.

Observações:

1. Exatamente um `--sdk` `--runtime`dos `--aspnet-runtime`, `--hosting-bundle` , e é necessário.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , , , , e são exclusivos.
3. Se `--x64` `--x86` ou não forem especificados, então tanto x64 quanto x86 serão removidos.

## <a name="macos"></a>[macOS](#tab/macos)

* **`--all`**

  Remove todos os SDKs do Núcleo .NET e tempos de execução.

* **`--all-below <VERSION>`**

  Remove SDKs do Núcleo .NET e tempos de execução abaixo da versão especificada. A versão especificada permanecerá.

* **`--all-but <VERSIONS>`**

  Remove SDKs e tempos de execução do .NET Core, exceto as versões especificadas.

* **`--all-but-latest`**

  Remove SDKs e tempos de execução do .NET Core, exceto a versão mais alta.

* **`--all-lower-patches`**

  Remove SDKs do Núcleo .NET e tempos de execução substituídos por patches mais altos. Esta opção protege global.json.

* **`--all-previews`**

  Remove SDKs do Núcleo .NET e tempos de execução marcados como visualizações.

* **`--all-previews-but-latest`**

  Remove SDKs do Núcleo .NET e tempos de execução marcados como visualizações, exceto a visualização mais alta.

* **`--major-minor <MAJOR_MINOR>`**

  Remove SDKs do Núcleo .NET e tempos `major.minor` de execução que correspondem à versão especificada.

* **`--runtime`**

  Remove apenas os tempos de execução do .NET Core.

* **`--sdk`**

  Remove apenas SDKs do Núcleo .NET.

* **`-v, --verbosity <LEVEL>`**

  Define o nível de verbosidade. Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`. O valor padrão é `normal`.

* **`-y, --yes`** Executa o comando sem exigir confirmação de Y/N.
  
* **`--force`** Força a remoção de versões que podem ser usadas pelo Visual Studio ou SDKs.

Observações:

1. Exatamente um `--sdk` `--runtime` dos mais necessários.
2. `--all`, `--all-below` `--all-but`, `--all-but-latest` `--all-lower-patches`, `--all-previews` `--all-previews-but-latest`, `--major-minor`, `[<VERSION>...]` , , , , , e são exclusivos.

---

#### <a name="examples"></a>Exemplos

> [!NOTE]
> Por padrão, os SDKs do Núcleo .NET e os tempos de execução que podem ser exigidos pelo Visual Studio ou outros SDKs são mantidos. Nos exemplos a seguir, alguns dos SDKs e tempos de execução especificados podem permanecer, dependendo do estado da máquina. Para remover todos os SDKs e tempos de execução, liste-os explicitamente como argumentos ou use a `--force` opção.

* Remova todos os tempos de `3.0.0-preview6-27804-01` execução do .NET Core, exceto a versão, sem exigir a confirmação de Y/N:

  ```console
  dotnet-core-uninstall remove --all-but 3.0.0-preview6-27804-01 --runtime --yes
  ```

* Remova todos os SDKs .NET Core 1.1 sem exigir confirmação de Y/n:

  ```console
  dotnet-core-uninstall remove --sdk --major-minor 1.1 -y
  ```

* Remova o SDK .NET Core 1.1.11 sem saída do console:

  ```console
  dotnet-core-uninstall remove 1.1.11 --sdk --yes --verbosity q
  ```

* Remova todos os SDKs do Núcleo .NET que podem ser removidos com segurança por esta ferramenta:

  ```console
  dotnet-core-uninstall remove --all --sdk
  ```

* Remova todos os SDKs do Núcleo .NET que podem ser removidos por esta ferramenta, incluindo os SDKs que podem ser exigidos pelo Visual Studio (não recomendado):

  ```console
  dotnet-core-uninstall remove --all --sdk --force
  ```

* Remova todos os SDKs do Núcleo .NET especificados no arquivo de resposta`versions.rsp`

  ```console
  dotnet-core-uninstall remove --sdk @versions.rsp
  ```

  O conteúdo de *versions.rsp* é o seguinte:
  
  ```text
  2.2.300
  2.1.700
  ```

### <a name="step-4---delete-the-nuget-fallback-folder-optional"></a>Passo 4 - Excluir a pasta de recuo NuGet (opcional)

Em alguns casos, você `NuGetFallbackFolder` não precisa mais e pode querer excluí-lo. Para obter mais informações sobre a exclusão desta pasta, consulte [Remover a pasta NuGetFallback](../versions/remove-runtime-sdk-versions.md#remove-the-nuget-fallback-folder).

## <a name="uninstall-the-tool"></a>Desinstale a ferramenta

## <a name="windows"></a>[Windows](#tab/windows)

1. Abra **adicionar ou remover programas**.
2. Pesquise `Microsoft .NET Core SDK Uninstall Tool`.
3. Selecionar **Desinstalar**.

## <a name="macos"></a>[macOS](#tab/macos)

Exclua o arquivo *dotnet-core-uninstall.tar.gz* baixado do diretório onde ele foi instalado. Se você descompactou o conteúdo deste arquivo em outro diretório, certifique-se de excluir esse conteúdo também.

---
