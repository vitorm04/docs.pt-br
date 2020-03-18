---
title: Instale o .NET Core SDK no Windows, Linux e macOS - .NET Core
description: Saiba como instalar o .NET Core no Windows, Linux e macOS. Descubra as dependências necessárias para desenvolver aplicativos .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 13600ea01e18ad47e6295653ba3b79ce53ff3257
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399003"
---
# <a name="install-the-net-core-sdk"></a>Instalar o SDK do .NET Core

Neste artigo, você aprenderá como instalar o .NET Core SDK. O .NET Core SDK é usado para criar aplicativos e bibliotecas .NET Core. O tempo de execução do .NET Core está sempre instalado com o SDK.

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>Instale com um instalador

O Windows possui instaladores autônomos que podem ser usados para instalar o SDK .NET Core 3.1:

- [CPUs x64 (64 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [CPUs x86 (32 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.1)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>Instale com um instalador

O macOS possui instaladores autônomos que podem ser usados para instalar o SDK .NET Core 3.1:

- [CPUs x64 (64 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.1)

## <a name="download-and-manually-install"></a>Baixe e instale manualmente

Como uma alternativa aos instaladores do macOS para .NET Core, você pode baixar e instalar manualmente o SDK.

Para extrair o SDK e disponibilizar os comandos .NET Core CLI no terminal, [primeiro baixe](#all-net-core-downloads) uma versão binária .NET Core. Em seguida, abra um terminal e execute os seguintes comandos. Presume-se que o tempo de `~/Downloads/dotnet-sdk.pkg` execução seja baixado para o arquivo.

```bash
mkdir -p $HOME/dotnet
sudo installer -pkg ~/Downloads/dotnet-sdk.pkg -target $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Instale com um gerenciador de pacotes

Você pode instalar o .NET Core SDK com muitos dos gerentes de pacotes Linux comuns. Para obter mais informações, consulte [O Linux Package Manager - Install .NET Core](linux-package-managers.md).

A instalação com um gerenciador de pacotes só é suportada na arquitetura x64. Se você estiver instalando o .NET Core SDK com uma arquitetura diferente, como o ARM, siga o [Download e instale manualmente](#download-and-manually-install) as instruções abaixo. Para obter mais informações sobre quais arquiteturas são suportadas, consulte [as dependências e os requisitos do .NET Core](dependencies.md).

## <a name="download-and-manually-install"></a>Baixe e instale manualmente

Para extrair o SDK e disponibilizar os comandos .NET Core CLI no terminal, [primeiro baixe](#all-net-core-downloads) uma versão binária .NET Core. Em seguida, abra um terminal e execute os seguintes comandos.

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.1.100-linux-x64.tar.gz -C $HOME/dotnet
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

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a>Instale com o Visual Studio

Se você estiver usando o Visual Studio para desenvolver aplicativos .NET Core, a tabela a seguir descreve a versão mínima necessária do Visual Studio com base na versão target .NET Core SDK.

| Versão .NET Core SDK | Versão do Visual Studio                      |
| --------------------- | ------------------------------------------ |
| 3.1                   | Visual Studio 2019 versão 16.4 ou superior. |
| 3.0                   | Visual Studio 2019 versão 16.3 ou superior. |
| 2.2                   | Visual Studio 2017 versão 15.9 ou superior. |
| 2.1                   | Visual Studio 2017 versão 15.7 ou superior. |

Se você já tiver o Visual Studio instalado, você pode verificar sua versão com as seguintes etapas.

01. Abra o Visual Studio.
01. Selecione **ajuda** > **sobre o Microsoft Visual Studio**.
01. Leia o número da versão da caixa de diálogo **Sobre.**

O Visual Studio pode instalar o SDK do Núcleo .NET mais recente e o tempo de execução.

- [Baixe Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).

### <a name="select-a-workload"></a>Selecione uma carga de trabalho

Ao instalar ou modificar o Visual Studio, selecione uma ou mais das seguintes cargas de trabalho, dependendo do tipo de aplicativo que você está construindo:

- A carga de trabalho **de desenvolvimento multiplataforma .NET Core** na seção Outros **conjuntos de ferramentas.**
- A **carga de trabalho de desenvolvimento ASP.NET e web** na seção Nuvem de & **Web.**
- A carga de trabalho de desenvolvimento do **Azure** na seção **Nuvem de & da Web.**
- A carga de **trabalho de desenvolvimento de desktop .NET** na seção Desktop & **Mobile.**

[![Windows Visual Studio 2019 com carga de trabalho .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

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

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a>Instale com o Visual Studio para Mac

O Visual Studio for Mac instala o .NET Core SDK quando a carga de trabalho **.NET Core** é selecionada. Para começar com o desenvolvimento do .NET Core no macOS, consulte [Install Visual Studio 2019 para Mac](/visualstudio/mac/installation). Para a versão mais recente, .NET Core 3.1, você deve usar o Visual Studio para Visualização Mac 8.4.

[![macOS Visual Studio 2019 para Mac com o recurso de carga de trabalho .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)

::: zone-end

## <a name="install-alongside-visual-studio-code"></a>Instale ao lado do Visual Studio Code

Visual Studio Code é um poderoso e leve editor de código-fonte que é executado na sua área de trabalho. Visual Studio Code está disponível para Windows, macOS e Linux.

Enquanto o Visual Studio Code não vem com um instalador automatizado .NET Core como o Visual Studio faz, adicionar suporte ao .NET Core é simples.

01. [Baixe e instale o Visual Studio Code](https://code.visualstudio.com/Download).
01. [Baixe e instale o .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core).
01. [Instale a extensão C# do mercado Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp).

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>Instale com a automação PowerShell

Os [scripts de instalação dotnet](../tools/dotnet-install-script.md) são usados para automação e instalações não-admin do SDK. Você pode baixar o script da página de [referência de script dotnet-install](../tools/dotnet-install-script.md).

O script é padrão para instalar a versão [lts (support) de longo prazo](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) mais recente, que é o .NET Core 3.1. Para instalar a versão atual do .NET Core, execute o script com o seguinte switch.

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Instale com automação de bash

Os [scripts de instalação dotnet](../tools/dotnet-install-script.md) são usados para automação e instalações não-admin do SDK. Você pode baixar o script da página de [referência de script dotnet-install](../tools/dotnet-install-script.md).

O script é padrão para instalar a versão [lts (support) de longo prazo](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) mais recente, que é o .NET Core 3.1. Para instalar a versão atual do .NET Core, execute o script com o seguinte switch.

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a>Todos os downloads do .NET Core

Você pode baixar e instalar o .NET Core diretamente com um dos seguintes links:

- [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

Os contêineres fornecem uma maneira leve de isolar sua aplicação do resto do sistema host. Os contêineres na mesma máquina compartilham apenas o kernel e usam os recursos dados à sua aplicação.

O .NET Core pode ser executado em um contêiner Docker. As imagens oficiais do Docker do .NET Core são publicadas no MCR (Registro de Contêiner da Microsoft) e podem ser encontradas no [repositório do Hub do Docker do .NET Core da Microsoft](https://hub.docker.com/_/microsoft-dotnet-core/). Cada repositório contém imagens para diferentes combinações do .NET (SDK ou Runtime) e do sistema operacional que você pode usar.

A Microsoft fornece imagens personalizadas para cenários específicos. Por exemplo, o [repositório do ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) fornece imagens que são criadas para a execução de aplicativos ASP.NET Core na produção.

Para obter mais informações sobre como usar o .NET Core em um contêiner Docker, consulte [Introdução a .NET e Docker](../docker/introduction.md) e [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>Próximas etapas

::: zone pivot="os-windows"

- [Tutorial: Tutorial do Hello World](../tutorials/with-visual-studio.md).
- [Tutorial: Crie um novo aplicativo com visual studio code](../tutorials/with-visual-studio-code.md).
- [Tutorial: Containerize um aplicativo .NET Core](../docker/build-container.md).

::: zone-end

::: zone pivot="os-macos"

- [Trabalhando com nota notatrização macOS Catalina](macos-notarization-issues.md).
- [Tutorial: Comece no macOS](../tutorials/using-on-mac-vs.md).
- [Tutorial: Crie um novo aplicativo com visual studio code](../tutorials/with-visual-studio-code.md).
- [Tutorial: Containerize um aplicativo .NET Core](../docker/build-container.md).

::: zone-end

::: zone pivot="os-linux"

- [Tutorial: Crie um novo aplicativo com visual studio code](../tutorials/with-visual-studio-code.md).
- [Tutorial: Containerize um aplicativo .NET Core](../docker/build-container.md).

::: zone-end
