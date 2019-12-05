---
title: Instalar o SDK do .NET Core no Windows, Linux e macOS – .NET Core
description: Saiba como instalar o .NET Core no Windows, Linux e macOS. Descubra as dependências necessárias para desenvolver aplicativos .NET Core.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 290bdfb05b328bb311e6ff5ef493048b05985899
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801942"
---
# <a name="install-the-net-core-sdk"></a>Instalar o SDK do .NET Core

Neste artigo, você aprenderá a instalar o SDK do .NET Core. O SDK do .NET Core é usado para criar aplicativos e bibliotecas do .NET Core. O tempo de execução do .NET Core é sempre instalado com o SDK.

::: zone pivot="os-windows"

## <a name="install-with-an-installer"></a>Instalar com um instalador

O Windows tem instaladores autônomos que podem ser usados para instalar o SDK do .NET Core 3,0:

- [CPUs x64 (64 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.0) 
- [CPUs x86 (32 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.0)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-an-installer"></a>Instalar com um instalador

o macOS tem instaladores autônomos que podem ser usados para instalar o SDK do .NET Core 3,0:

- [CPUs x64 (64 bits)](https://dotnet.microsoft.com/download/dotnet-core/3.0)

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Instalar com um Gerenciador de pacotes

Você pode instalar o SDK do .NET Core com muitos dos gerenciadores de pacotes do Linux comuns. Para obter mais informações, consulte [Gerenciador de pacotes do Linux – instalar o .NET Core](linux-package-managers.md).

## <a name="download-and-manually-install"></a>Baixar e instalar manualmente

Para extrair o SDK e tornar os comandos disponíveis no terminal, primeiro [Baixe](#all-net-core-downloads) uma versão binária do .NET Core. Em seguida, abra um terminal e execute os comandos a seguir.

```bash
mkdir -p $HOME/dotnet && tar zxf dotnet-sdk-3.0.101-linux-musl-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> Os comandos acima só disponibilizarão os comandos do SDK do .NET para a sessão de terminal na qual ele foi executado.
>
> Você pode editar seu perfil de Shell para adicionar os comandos permanentemente. Há vários shells diferentes disponíveis para o Linux e cada um deles tem um perfil diferente. Por exemplo:
>
> - **Shell bash**: *~/. bash_profile*, *~/.bashrc*
> - **Shell Korn**: *~/.Kshrc* ou *. Profile*
> - **Shell Z**: *~/.zshrc* ou *. zprofile*
> 
> Edite o arquivo de origem apropriado para o Shell e adicione `:$HOME/dotnet` ao final da instrução `PATH` existente. Se nenhuma instrução de `PATH` for incluída, adicione uma nova linha com `export PATH=$PATH:$HOME/dotnet`.
>
> Além disso, adicione `export DOTNET_ROOT=$HOME/dotnet` ao final do arquivo.

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a>Instalar com o Visual Studio

Se você estiver usando o Visual Studio para desenvolver aplicativos .NET Core, a tabela a seguir descreve a versão mínima necessária do Visual Studio com base na versão de SDK do .NET Core de destino.

| Versão do SDK do .NET Core | Versão do Visual Studio                      |
| --------------------- | ------------------------------------------ |
| visualização de 3,1           | Visual Studio 2019 versão 16,4 Preview ou superior. |
| 3.0                   | Visual Studio 2019 versão 16,3 ou superior. |
| 2.2                   | Visual Studio 2017 versão 15,9 ou superior. |
| 2.1                   | Visual Studio 2017 versão 15,7 ou superior. |

Se você já tiver o Visual Studio instalado, poderá verificar sua versão com as etapas a seguir.

01. {1&gt;Abra o Visual Studio.&lt;1}
01. Selecione **ajuda** > **sobre Microsoft Visual Studio**.
01. Leia o número de versão na caixa de diálogo **sobre** .

O Visual Studio pode instalar o SDK do .NET Core e o tempo de execução mais recentes.

- [Baixar o Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).

### <a name="select-a-workload"></a>Selecionar uma carga de trabalho

Ao instalar ou modificar o Visual Studio, selecione uma das cargas de trabalho a seguir, dependendo do tipo de aplicativo que você está criando:

- A carga de trabalho de **desenvolvimento de plataforma cruzada do .NET Core** na seção **outros conjuntos de ferramentas** .
- A carga de trabalho de **desenvolvimento da Web e ASP.net** na seção **Web & nuvem** .
- A carga de trabalho de **desenvolvimento do Azure** na seção **Web & nuvem** .
- A carga de trabalho **.net desktop Development** na seção **Desktop & Mobile** .

[![o Windows Visual Studio 2019 com carga de trabalho do .NET Core](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a>Instalar com o Visual Studio para Mac

Visual Studio para Mac instala o SDK do .NET Core quando a carga de trabalho do **.NET Core** é selecionada. Para começar a usar o desenvolvimento do .NET Core no macOS, consulte [instalar o Visual Studio 2019 para Mac](/visualstudio/mac/installation).

[![macOS Visual Studio 2019 para Mac com o recurso de carga de trabalho do .NET Core](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)

::: zone-end

## <a name="install-alongside-visual-studio-code"></a>Instalar junto com Visual Studio Code

Visual Studio Code é um editor de código-fonte leve e avançado que é executado em sua área de trabalho. Visual Studio Code está disponível para Windows, macOS e Linux.

Embora Visual Studio Code não venha com um instalador .NET Core automatizado como o Visual Studio, adicionar o suporte ao .NET Core é simples.

01. [Baixe e instale o Visual Studio Code](https://code.visualstudio.com/Download).
01. [Baixe e instale o SDK do .NET Core](https://dotnet.microsoft.com/download/dotnet-core).
01. [Instale a C# extensão do Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a>Instalar com a automação do PowerShell

Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do SDK. Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).

O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 2,1. Para instalar a versão atual do .NET Core, execute o script com a opção a seguir.

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Instalar com a automação do bash

Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do SDK. Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).

O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 2,1. Para instalar a versão atual do .NET Core, execute o script com a opção a seguir.

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="all-net-core-downloads"></a>Todos os downloads do .NET Core

Você pode baixar e instalar o .NET Core diretamente com um dos seguintes links:

- [Downloads da versão prévia do .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [Downloads do .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [Downloads do .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [Downloads do .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

Os contêineres fornecem uma maneira leve de isolar seu aplicativo do restante do sistema host. Os contêineres no mesmo computador compartilham apenas o kernel e usam os recursos fornecidos ao seu aplicativo.

O .NET Core pode ser executado em um contêiner do Docker. As imagens oficiais do Docker do .NET Core são publicadas no MCR (Registro de Contêiner da Microsoft) e podem ser encontradas no [repositório do Hub do Docker do .NET Core da Microsoft](https://hub.docker.com/_/microsoft-dotnet-core/). Cada repositório contém imagens para diferentes combinações do .NET (SDK ou Runtime) e do sistema operacional que você pode usar.

A Microsoft fornece imagens personalizadas para cenários específicos. Por exemplo, o [repositório do ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) fornece imagens que são criadas para a execução de aplicativos ASP.NET Core na produção.

Para obter mais informações sobre como usar o .NET Core em um contêiner do Docker, consulte [introdução ao .net e ao Docker](../docker/introduction.md) e [amostras](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

::: zone pivot="os-windows"

- [Tutorial: C# tutorial de Olá, mundo](../tutorials/with-visual-studio.md).
- [Tutorial: Visual Basic Olá, mundo tutorial](../tutorials/vb-with-visual-studio.md).
- [Tutorial: criar um novo aplicativo com Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).
- [Tutorial: colocar em contêiner um aplicativo .NET Core](../docker/build-container.md).

::: zone-end

::: zone pivot="os-macos"

- [Tutorial: introdução ao MacOS](../tutorials/using-on-mac-vs.md).
- [Tutorial: criar um novo aplicativo com Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).
- [Tutorial: colocar em contêiner um aplicativo .NET Core](../docker/build-container.md).

::: zone-end
