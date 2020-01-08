---
title: Instalar o tempo de execução do .NET Core no Windows, Linux e macOS – .NET Core
description: Saiba como instalar o .NET Core no Windows, Linux e macOS. Descubra as dependências necessárias para executar aplicativos .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: a45cb570ccf572a699359598319fd3867fb5e5dd
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75340954"
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

::: zone-end

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a>Instalar com um Gerenciador de pacotes

Você pode instalar o tempo de execução do .NET Core com muitos dos gerenciadores de pacotes do Linux comuns. Para obter mais informações, consulte [Gerenciador de pacotes do Linux – instalar o .NET Core](linux-package-managers.md).

A instalação com um Gerenciador de pacotes só tem suporte na arquitetura x64. Se você estiver instalando o tempo de execução do .NET Core com uma arquitetura diferente, como o ARM, siga as instruções na seção [baixar e instalar manualmente](#download-and-manually-install) . Para obter mais informações sobre quais arquiteturas têm suporte, consulte [dependências e requisitos do .NET Core](dependencies.md).

## <a name="download-and-manually-install"></a>Baixar e instalar manualmente

Para extrair o tempo de execução e tornar os comandos do CLI do .NET Core disponíveis no terminal, primeiro [Baixe](#all-net-core-downloads) uma versão binária do .NET Core. Em seguida, abra um terminal e execute os comandos a seguir.

```bash
mkdir -p $HOME/dotnet && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C $HOME/dotnet
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> Os comandos de `export` anteriores disponibilizam apenas os comandos CLI do .NET Core disponíveis para a sessão de terminal na qual ele foi executado.
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

## <a name="install-with-powershell-automation"></a>Instalar com a automação do PowerShell

Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do tempo de execução. Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).

O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 3,1. Você pode escolher uma versão específica especificando a opção `Channel`. Inclua a opção `Runtime` para instalar um tempo de execução. Caso contrário, o script instalará o [SDK](sdk.md).

```powershell
dotnet-install.ps1 -Channel 3.1 -Runtime aspnetcore
```

> [!NOTE]
> O comando acima instala o tempo de execução de ASP.NET Core para compatibilidade máxima. O tempo de execução de ASP.NET Core também inclui o tempo de execução padrão do .NET Core.

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a>Instalar com a automação do bash

Os [scripts dotnet-install](../tools/dotnet-install-script.md) são usados para automação e instalações não administrativas do tempo de execução. Você pode baixar o script na [página de referência de script dotnet-install](../tools/dotnet-install-script.md).

O script assume como padrão a instalação da versão mais recente do [LTS (suporte a longo prazo)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) , que é o .net Core 3,1. Você pode escolher uma versão específica especificando a opção `current`. Inclua a opção `runtime` para instalar um tempo de execução. Caso contrário, o script instalará o [SDK](sdk.md).

```bash
./dotnet-install.sh --current 3.1 --runtime aspnetcore
```

> [!NOTE]
> O comando acima instala o tempo de execução de ASP.NET Core para compatibilidade máxima. O tempo de execução de ASP.NET Core também inclui o tempo de execução padrão do .NET Core.

::: zone-end

## <a name="all-net-core-downloads"></a>Todos os downloads do .NET Core

Você pode baixar e instalar o .NET Core diretamente com um dos seguintes links:

- [Downloads do .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [Downloads do .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [Downloads do .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [Downloads do .NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)

## <a name="docker"></a>Docker

Os contêineres fornecem uma maneira leve de isolar seu aplicativo do restante do sistema host. Os contêineres no mesmo computador compartilham apenas o kernel e usam os recursos fornecidos ao seu aplicativo.

O .NET Core pode ser executado em um contêiner do Docker. As imagens oficiais do Docker do .NET Core são publicadas no MCR (Registro de Contêiner da Microsoft) e podem ser encontradas no [repositório do Hub do Docker do .NET Core da Microsoft](https://hub.docker.com/_/microsoft-dotnet-core/). Cada repositório contém imagens para diferentes combinações do .NET (SDK ou Runtime) e do sistema operacional que você pode usar.

A Microsoft fornece imagens personalizadas para cenários específicos. Por exemplo, o [repositório do ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) fornece imagens que são criadas para a execução de aplicativos ASP.NET Core na produção.

Para obter mais informações sobre como usar o .NET Core em um contêiner do Docker, consulte [introdução ao .net e ao Docker](../docker/introduction.md) e [amostras](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).

## <a name="next-steps"></a>{1&gt;{2&gt;Próximas etapas&lt;2}&lt;1}

- [Como verificar se o .NET Core já está instalado](how-to-detect-installed-versions.md).
