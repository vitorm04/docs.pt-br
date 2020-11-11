---
ms.openlocfilehash: 3932cf51b5194dba7956cd62ced3985a2e6311f0
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506787"
---

<!-- Note, this content is copied in ../macos.md. Any fixes should be applied there too, though content may be different -->

Como alternativa para os gerenciadores de pacotes, você pode baixar e instalar manualmente o SDK e o tempo de execução. A instalação manual geralmente é executada como parte do teste de integração contínua ou em uma distribuição do Linux sem suporte. Para um desenvolvedor ou usuário, geralmente é melhor usar um Gerenciador de pacotes.

Se você instalar o SDK do .NET, não precisará instalar o tempo de execução correspondente. Primeiro, Baixe uma versão **binária** para o SDK ou o tempo de execução de um dos seguintes sites:

- downloads do ✔️ [.net 5,0](https://dotnet.microsoft.com/download/dotnet/5.0)
- downloads do ✔️ [.NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- downloads do ✔️ [.NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)
- [Todos os downloads do .NET Core](https://dotnet.microsoft.com/download/dotnet-core)

Em seguida, extraia o arquivo baixado e use o `export` comando para definir as variáveis usadas pelo .net e, em seguida, verifique se o .net está no caminho.

Para extrair o tempo de execução e tornar os comandos da CLI do .NET disponíveis no terminal, primeiro Baixe uma versão binária do .NET. Em seguida, abra um terminal e execute os seguintes comandos no diretório em que o arquivo foi salvo. O nome do arquivo morto pode ser diferente dependendo do que você baixou.

**Use o seguinte comando para extrair o tempo de execução** :

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-5.0.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

**Use o seguinte comando para extrair o SDK** :

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-5.0.100-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> Os `export` comandos anteriores tornam os comandos da CLI do .net disponíveis para a sessão de terminal na qual ele foi executado.
>
> Você pode editar seu perfil de Shell para adicionar os comandos permanentemente. Há vários shells diferentes disponíveis para o Linux e cada um deles tem um perfil diferente. Por exemplo:
>
> - **Shell bash** : *~/.bash_profile* , *~/.bashrc*
> - **Shell Korn** : *~/.Kshrc* ou *. Profile*
> - **Shell Z** : *~/.zshrc* ou *. zprofile*
>
> Edite o arquivo de origem apropriado para o Shell e adicione `:$HOME/dotnet` ao final da `PATH` instrução existente. Se nenhuma `PATH` instrução for incluída, adicione uma nova linha com `export PATH=$PATH:$HOME/dotnet` .
>
> Além disso, adicione `export DOTNET_ROOT=$HOME/dotnet` ao final do arquivo.

Essa abordagem permite que você instale versões diferentes em locais separados e escolha explicitamente qual deles usar por qual aplicativo.
