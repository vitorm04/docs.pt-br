---
title: Instalar o tempo de execução do .NET Core no Windows, Linux e macOS – .NET Core
description: Saiba como instalar o .NET Core no Windows, Linux e macOS. Descubra as dependências necessárias para executar aplicativos .NET Core.
author: thraka
ms.author: adegeo
ms.date: 05/04/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: d3f7083366e2019d01884b5dff6e60d05ed565dd
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768281"
---
# <a name="install-the-net-core-runtime"></a>Instalar o tempo de execução do .NET Core

Neste artigo, você aprenderá a baixar e instalar o tempo de execução do .NET Core. O tempo de execução do .NET Core é usado para executar aplicativos criados com o .NET Core.

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>Instalar com um instalador

O Windows tem instaladores autônomos que podem ser usados para instalar o .NET Core 3,1 Runtime:

- [CPUs x64 (64 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [CPUs x86 (32 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>Instalar com um instalador

o macOS tem instaladores autônomos que podem ser usados para instalar o .NET Core 3,1 Runtime:

- [CPUs x64 (64 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a>Baixar e instalar manualmente

Como alternativa para os instaladores do macOS para .NET Core, você pode baixar e instalar manualmente o tempo de execução.

Para instalar o tempo de execução e habilitar os comandos de CLI do .NET Core disponíveis no terminal, primeiro [Baixe](#all-net-core-downloads) uma versão binária do .NET Core. Em seguida, abra um terminal e execute os comandos a seguir. Supõe-se que o tempo de execução seja baixado para o `~/Downloads/dotnet-runtime.pkg` arquivo.

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-on-linux"></a>Instalar no Linux

Este artigo será removido em breve. Atualmente, ele é substituído por [instalar o .NET Core no Linux](linux.md).

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>Instalar com a automação do PowerShell

Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do tempo de execução. Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).

O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 3,1. Você pode escolher uma versão específica especificando a `Channel` opção. Inclua a `Runtime` opção para instalar um tempo de execução. Caso contrário, o script instalará o [SDK](sdk.md).

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> O comando acima instala o tempo de execução de ASP.NET Core para compatibilidade máxima. O tempo de execução de ASP.NET Core também inclui o tempo de execução padrão do .NET Core.

## <a name="download-and-manually-install"></a>Baixar e instalar manualmente

Para extrair o tempo de execução e tornar os comandos do CLI do .NET Core disponíveis no terminal, primeiro [Baixe](#all-net-core-downloads) uma versão binária do .NET Core. Em seguida, crie um diretório para instalar, por exemplo `%USERPROFILE%\dotnet` . Por fim, extraia o arquivo zip baixado para esse diretório.

Por padrão, CLI do .NET Core comandos e aplicativos não usarão o .NET Core instalado dessa forma e você deverá optar por usá-lo explicitamente. Para fazer isso, altere as variáveis de ambiente com as quais um aplicativo é iniciado:

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

Essa abordagem permite que você instale várias versões em locais separados e escolha explicitamente qual local de instalação um aplicativo deve usar executando o aplicativo com variáveis de ambiente apontando para esse local.

Mesmo quando essas variáveis de ambiente são definidas, o .NET Core ainda considera o local de instalação global padrão ao selecionar a melhor estrutura para executar o aplicativo. O padrão é normalmente `C:\Program Files\dotnet` , que os instaladores usam. Você pode instruir o tempo de execução para usar apenas o local de instalação personalizado definindo essa variável de ambiente também:

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-bash-automation"></a>Instalar com a automação do bash

Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do tempo de execução. Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).

O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 3,1. Você pode escolher uma versão específica especificando a `current` opção. Inclua a `runtime` opção para instalar um tempo de execução. Caso contrário, o script instalará o [SDK](sdk.md).

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> O comando acima instala o tempo de execução de ASP.NET Core para compatibilidade máxima. O tempo de execução de ASP.NET Core também inclui o tempo de execução padrão do .NET Core.

::: zone-end

## <a name="all-net-core-downloads"></a>Todos os downloads do .NET Core

Você pode baixar e instalar o .NET Core diretamente com um dos seguintes links:

- [Downloads do .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [Downloads do .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

Os contêineres fornecem uma maneira leve de isolar seu aplicativo do restante do sistema host. Os contêineres no mesmo computador compartilham apenas o kernel e usam os recursos fornecidos ao seu aplicativo.

O .NET Core pode ser executado em um contêiner do Docker. As imagens oficiais do Docker do .NET Core são publicadas no MCR (Registro de Contêiner da Microsoft) e podem ser encontradas no [repositório do Hub do Docker do .NET Core da Microsoft](https://hub.docker.com/_/microsoft-dotnet-core/). Cada repositório contém imagens para diferentes combinações do .NET (SDK ou Runtime) e do sistema operacional que você pode usar.

A Microsoft fornece imagens personalizadas para cenários específicos. Por exemplo, o [repositório do ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) fornece imagens que são criadas para a execução de aplicativos ASP.NET Core na produção.

Para obter mais informações sobre como usar o .NET Core em um contêiner do Docker, consulte [introdução ao .net e ao Docker](../docker/introduction.md) e [amostras](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Próximas etapas

- [Como verificar se o .NET Core já está instalado](how-to-detect-installed-versions.md).
