---
title: Instale o tempo de execução do .NET Core no Windows, Linux e macOS - .NET Core
description: Saiba como instalar o .NET Core no Windows, Linux e macOS. Descubra as dependências necessárias para executar aplicativos .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: ca55b8fab4aa9ca9f7e308cce57181e2c7e89f4b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399010"
---
# <a name="install-the-net-core-runtime"></a>Instale o tempo de execução do .NET Core

Neste artigo, você aprenderá como baixar e instalar o tempo de execução do .NET Core. O tempo de execução do .NET Core é usado para executar aplicativos criados com o .NET Core.

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>Instale com um instalador

O Windows tem instaladores autônomos que podem ser usados para instalar o tempo de execução do .NET Core 3.1:

- [CPUs x64 (64 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [CPUs x86 (32 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>Instale com um instalador

O macOS possui instaladores autônomos que podem ser usados para instalar o tempo de execução do .NET Core 3.1:

- [CPUs x64 (64 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a>Baixe e instale manualmente

Como uma alternativa aos instaladores do macOS para .NET Core, você pode baixar e instalar manualmente o tempo de execução.

Para instalar o tempo de execução e ativar os comandos .NET Core CLI disponíveis no terminal, [primeiro baixe](#all-net-core-downloads) uma versão binária .NET Core. Em seguida, abra um terminal e execute os seguintes comandos. Presume-se que o tempo de `~/Downloads/dotnet-runtime.pkg` execução seja baixado para o arquivo.

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-runtime.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Instale com um gerenciador de pacotes

Você pode instalar o .NET Core Runtime com muitos dos gerentes de pacotes Linux comuns. Para obter mais informações, consulte [O Linux Package Manager - Install .NET Core](linux-package-managers.md).

Instalá-lo com um gerenciador de pacotes só é suportado na arquitetura x64. Se você estiver instalando o .NET Core Runtime com uma arquitetura diferente, como o ARM, siga as instruções na seção [Download e instale manualmente.](#download-and-manually-install) Para obter mais informações sobre quais arquiteturas são suportadas, consulte [as dependências e os requisitos do .NET Core](dependencies.md).

## <a name="download-and-manually-install"></a>Baixe e instale manualmente

Para extrair o tempo de execução e disponibilizar os comandos .NET Core CLI no terminal, [primeiro baixe](#all-net-core-downloads) uma versão binária .NET Core. Em seguida, abra um terminal e execute os seguintes comandos.

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> Os `export` comandos anteriores só disponibilizam os comandos .NET Core CLI para a sessão de terminal em que foi executado.
>
> Você pode editar seu perfil shell para adicionar permanentemente os comandos. Existem vários shells diferentes disponíveis para Linux e cada um tem um perfil diferente. Por exemplo: 
>
> - **Bash Shell**: *~/.bash_profile*, *~/.bashrc*
> - **Korn Shell**: *~/.kshrc* ou *.profile*
> - **Z Shell**: *~/.zshrc* ou *.zprofile*
>
> Edite o arquivo de origem `:$HOME/dotnet` apropriado para o `PATH` shell e adicione ao final da declaração existente. Se `PATH` nenhuma declaração estiver incluída, `export PATH=$PATH:$HOME/dotnet`adicione uma nova linha com .
>
> Além disso, adicione `export DOTNET_ROOT=$HOME/dotnet` ao final do arquivo.

Essa abordagem permite instalar diferentes versões em locais separados e escolher explicitamente qual usar por qual aplicativo.

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>Instale com a automação PowerShell

Os [scripts de instalação dotnet](../tools/dotnet-install-script.md) são usados para automação e instalações não-admin do tempo de execução. Você pode baixar o script da página de [referência de script dotnet-install](../tools/dotnet-install-script.md).

O script é padrão para instalar a versão [lts (support) de longo prazo](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) mais recente, que é o .NET Core 3.1. Você pode escolher uma versão `Channel` específica especificando o switch. Inclua `Runtime` o interruptor para instalar um tempo de execução. Caso contrário, o script instala o [SDK](sdk.md).

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> O comando acima instala o tempo de execução do ASP.NET Core para máxima compatibilidade. O tempo de execução do ASP.NET Core também inclui o tempo de execução padrão do .NET Core.

## <a name="download-and-manually-install"></a>Baixe e instale manualmente

Para extrair o tempo de execução e disponibilizar os comandos .NET Core CLI no terminal, [primeiro baixe](#all-net-core-downloads) uma versão binária .NET Core. Em seguida, crie um diretório para `%USERPROFILE%\dotnet`instalar, por exemplo. Finalmente, extraia o arquivo zip baixado nesse diretório.

Por padrão, os comandos e aplicativos .NET Core CLI não usarão o .NET Core instalado desta forma. Você tem que escolher explicitamente usá-lo. Para isso, altere as variáveis de ambiente com as quais um aplicativo é iniciado:

```console
set DOTNET_ROOT=%USERPROFILE%\dotnet
set PATH=%USERPROFILE%\dotnet;%PATH%
```

Essa abordagem permite que você instale várias versões em locais separados e escolha explicitamente qual local de instalação um aplicativo deve usar executando o aplicativo com variáveis de ambiente apontando para esse local.

Mesmo quando essas variáveis de ambiente são definidas, o .NET Core ainda considera o local de instalação global padrão ao selecionar a melhor estrutura para executar o aplicativo. O padrão é `C:\Program Files\dotnet`tipicamente , que os instaladores usam. Você pode instruir o tempo de execução para usar apenas o local de instalação personalizado definindo essa variável de ambiente também:

```console
set DOTNET_MULTILEVEL_LOOKUP=0
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Instale com automação de bash

Os [scripts de instalação dotnet](../tools/dotnet-install-script.md) são usados para automação e instalações não-admin do tempo de execução. Você pode baixar o script da página de [referência de script dotnet-install](../tools/dotnet-install-script.md).

O script é padrão para instalar a versão [lts (support) de longo prazo](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) mais recente, que é o .NET Core 3.1. Você pode escolher uma versão `current` específica especificando o switch. Inclua `runtime` o interruptor para instalar um tempo de execução. Caso contrário, o script instala o [SDK](sdk.md).

```bash
./dotnet-install.sh --channel 3.1 --runtime aspnetcore
```

> [!NOTE]
> O comando acima instala o tempo de execução do ASP.NET Core para máxima compatibilidade. O tempo de execução do ASP.NET Core também inclui o tempo de execução padrão do .NET Core.

::: zone-end

## <a name="all-net-core-downloads"></a>Todos os downloads do .NET Core

Você pode baixar e instalar o .NET Core diretamente com um dos seguintes links:

- [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

Os contêineres fornecem uma maneira leve de isolar sua aplicação do resto do sistema host. Os contêineres na mesma máquina compartilham apenas o kernel e usam os recursos dados à sua aplicação.

O .NET Core pode ser executado em um contêiner Docker. As imagens oficiais do Docker do .NET Core são publicadas no MCR (Registro de Contêiner da Microsoft) e podem ser encontradas no [repositório do Hub do Docker do .NET Core da Microsoft](https://hub.docker.com/_/microsoft-dotnet-core/). Cada repositório contém imagens para diferentes combinações do .NET (SDK ou Runtime) e do sistema operacional que você pode usar.

A Microsoft fornece imagens personalizadas para cenários específicos. Por exemplo, o [repositório do ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) fornece imagens que são criadas para a execução de aplicativos ASP.NET Core na produção.

Para obter mais informações sobre como usar o .NET Core em um contêiner Docker, consulte [Introdução a .NET e Docker](../docker/introduction.md) e [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Próximas etapas

- [Como verificar se o .NET Core já está instalado](how-to-detect-installed-versions.md).
