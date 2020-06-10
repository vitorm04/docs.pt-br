---
ms.openlocfilehash: e7d35045892c62f759aad5067962ac5c15a9fb8b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602925"
---

<span data-ttu-id="07c13-101">O SDK do .NET Core e o tempo de execução do .NET Core podem ser instalados manualmente após terem sido baixados.</span><span class="sxs-lookup"><span data-stu-id="07c13-101">Both .NET Core SDK and .NET Core Runtime can be manually installed after they've been downloaded.</span></span> <span data-ttu-id="07c13-102">Se você instalar SDK do .NET Core, não será necessário instalar o tempo de execução correspondente.</span><span class="sxs-lookup"><span data-stu-id="07c13-102">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="07c13-103">Primeiro, Baixe uma versão binária para o SDK ou o tempo de execução de um dos seguintes sites:</span><span class="sxs-lookup"><span data-stu-id="07c13-103">First, download a binary release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="07c13-104">✔️ [downloads da versão prévia do .net 5,0](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="07c13-104">✔️ [.NET 5.0 preview downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="07c13-105">downloads do ✔️ [.NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="07c13-105">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="07c13-106">❌[Downloads do .NET Core 3,0](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span><span class="sxs-lookup"><span data-stu-id="07c13-106">❌ [.NET Core 3.0 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.0)</span></span>
- <span data-ttu-id="07c13-107">❌[Downloads do .NET Core 2,2](https://dotnet.microsoft.com/download/dotnet-core/2.2)</span><span class="sxs-lookup"><span data-stu-id="07c13-107">❌ [.NET Core 2.2 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.2)</span></span>
- <span data-ttu-id="07c13-108">downloads do ✔️ [.NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="07c13-108">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>

<span data-ttu-id="07c13-109">Em seguida, extraia o arquivo baixado e use o `export` comando para definir as variáveis usadas pelo .NET Core e, em seguida, verifique se o .NET Core está no caminho.</span><span class="sxs-lookup"><span data-stu-id="07c13-109">Next, extract the downloaded file and use the `export` command to set variables used by .NET Core and then ensure .NET Core is in PATH.</span></span>

<span data-ttu-id="07c13-110">Para extrair o tempo de execução e tornar os comandos do CLI do .NET Core disponíveis no terminal, primeiro Baixe uma versão binária do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07c13-110">To extract the runtime and make the .NET Core CLI commands available at the terminal, first download a .NET Core binary release.</span></span> <span data-ttu-id="07c13-111">Em seguida, abra um terminal e execute os seguintes comandos no diretório em que o arquivo foi salvo.</span><span class="sxs-lookup"><span data-stu-id="07c13-111">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="07c13-112">Os `export` comandos anteriores disponibilizam apenas os comandos CLI do .NET Core disponíveis para a sessão de terminal na qual ele foi executado.</span><span class="sxs-lookup"><span data-stu-id="07c13-112">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="07c13-113">Você pode editar seu perfil de Shell para adicionar os comandos permanentemente.</span><span class="sxs-lookup"><span data-stu-id="07c13-113">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="07c13-114">Há vários shells diferentes disponíveis para o Linux e cada um deles tem um perfil diferente.</span><span class="sxs-lookup"><span data-stu-id="07c13-114">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="07c13-115">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="07c13-115">For example:</span></span>
>
> - <span data-ttu-id="07c13-116">**Shell bash**: *~/. bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="07c13-116">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="07c13-117">**Shell Korn**: *~/.Kshrc* ou *. Profile*</span><span class="sxs-lookup"><span data-stu-id="07c13-117">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="07c13-118">**Shell Z**: *~/.zshrc* ou *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="07c13-118">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="07c13-119">Edite o arquivo de origem apropriado para o Shell e adicione `:$HOME/dotnet` ao final da `PATH` instrução existente.</span><span class="sxs-lookup"><span data-stu-id="07c13-119">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="07c13-120">Se nenhuma `PATH` instrução for incluída, adicione uma nova linha com `export PATH=$PATH:$HOME/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="07c13-120">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="07c13-121">Além disso, adicione `export DOTNET_ROOT=$HOME/dotnet` ao final do arquivo.</span><span class="sxs-lookup"><span data-stu-id="07c13-121">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="07c13-122">Essa abordagem permite que você instale versões diferentes em locais separados e escolha explicitamente qual deles usar por qual aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07c13-122">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>
