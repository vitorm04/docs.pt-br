---
ms.openlocfilehash: ea2883912907843e4b6d65db5ba186af43f27aaa
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85805381"
---

<!-- Note, this content is copied in ../macos.md. Any fixes should be applied there too, though content may be different -->

<span data-ttu-id="d2528-101">Como alternativa para os gerenciadores de pacotes, você pode baixar e instalar manualmente o SDK e o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d2528-101">As an alternative to the package managers, you can download and manually install the SDK and runtime.</span></span> <span data-ttu-id="d2528-102">A instalação manual geralmente é executada como parte do teste de integração contínua ou em uma distribuição do Linux sem suporte.</span><span class="sxs-lookup"><span data-stu-id="d2528-102">Manual install is usually performed as part of continuous integration testing or on an unsupported Linux distribution.</span></span> <span data-ttu-id="d2528-103">Para um desenvolvedor ou usuário, geralmente é melhor usar um Gerenciador de pacotes.</span><span class="sxs-lookup"><span data-stu-id="d2528-103">For a developer or user, it's generally better to use a package manager.</span></span>

<span data-ttu-id="d2528-104">Se você instalar SDK do .NET Core, não será necessário instalar o tempo de execução correspondente.</span><span class="sxs-lookup"><span data-stu-id="d2528-104">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="d2528-105">Primeiro, Baixe uma versão **binária** para o SDK ou o tempo de execução de um dos seguintes sites:</span><span class="sxs-lookup"><span data-stu-id="d2528-105">First, download a **binary** release for either the SDK or the runtime from one of the following sites:</span></span>

- <span data-ttu-id="d2528-106">✔️ [downloads da versão prévia do .net 5,0](https://dotnet.microsoft.com/download/dotnet/5.0)</span><span class="sxs-lookup"><span data-stu-id="d2528-106">✔️ [.NET 5.0 preview downloads](https://dotnet.microsoft.com/download/dotnet/5.0)</span></span>
- <span data-ttu-id="d2528-107">downloads do ✔️ [.NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span><span class="sxs-lookup"><span data-stu-id="d2528-107">✔️ [.NET Core 3.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/3.1)</span></span>
- <span data-ttu-id="d2528-108">downloads do ✔️ [.NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span><span class="sxs-lookup"><span data-stu-id="d2528-108">✔️ [.NET Core 2.1 downloads](https://dotnet.microsoft.com/download/dotnet-core/2.1)</span></span>
- [<span data-ttu-id="d2528-109">Todos os downloads do .NET Core</span><span class="sxs-lookup"><span data-stu-id="d2528-109">All .NET Core downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core)

<span data-ttu-id="d2528-110">Em seguida, extraia o arquivo baixado e use o `export` comando para definir as variáveis usadas pelo .NET Core e, em seguida, verifique se o .NET Core está no caminho.</span><span class="sxs-lookup"><span data-stu-id="d2528-110">Next, extract the downloaded file and use the `export` command to set variables used by .NET Core and then ensure .NET Core is in PATH.</span></span>

<span data-ttu-id="d2528-111">Para extrair o tempo de execução e tornar os comandos do CLI do .NET Core disponíveis no terminal, primeiro Baixe uma versão binária do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d2528-111">To extract the runtime and make the .NET Core CLI commands available at the terminal, first download a .NET Core binary release.</span></span> <span data-ttu-id="d2528-112">Em seguida, abra um terminal e execute os seguintes comandos no diretório em que o arquivo foi salvo.</span><span class="sxs-lookup"><span data-stu-id="d2528-112">Then, open a terminal and run the following commands from the directory where the file was saved.</span></span> <span data-ttu-id="d2528-113">O nome do arquivo morto pode ser diferente dependendo do que você baixou.</span><span class="sxs-lookup"><span data-stu-id="d2528-113">The archive file name may be different depending on what you downloaded.</span></span>

<span data-ttu-id="d2528-114">**Use o seguinte comando para extrair o tempo de execução**:</span><span class="sxs-lookup"><span data-stu-id="d2528-114">**Use the following command to extract the runtime**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf aspnetcore-runtime-3.1.0-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

<span data-ttu-id="d2528-115">**Use o seguinte comando para extrair o SDK**:</span><span class="sxs-lookup"><span data-stu-id="d2528-115">**Use the following command to extract the SDK**:</span></span>

```bash
mkdir -p "$HOME/dotnet" && tar zxf dotnet-sdk-3.1.301-linux-x64.tar.gz -C "$HOME/dotnet"
export DOTNET_ROOT=$HOME/dotnet
export PATH=$PATH:$HOME/dotnet
```

> [!TIP]
> <span data-ttu-id="d2528-116">Os `export` comandos anteriores disponibilizam apenas os comandos CLI do .NET Core disponíveis para a sessão de terminal na qual ele foi executado.</span><span class="sxs-lookup"><span data-stu-id="d2528-116">The preceding `export` commands only make the .NET Core CLI commands available for the terminal session in which it was run.</span></span>
>
> <span data-ttu-id="d2528-117">Você pode editar seu perfil de Shell para adicionar os comandos permanentemente.</span><span class="sxs-lookup"><span data-stu-id="d2528-117">You can edit your shell profile to permanently add the commands.</span></span> <span data-ttu-id="d2528-118">Há vários shells diferentes disponíveis para o Linux e cada um deles tem um perfil diferente.</span><span class="sxs-lookup"><span data-stu-id="d2528-118">There are a number of different shells available for Linux and each has a different profile.</span></span> <span data-ttu-id="d2528-119">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="d2528-119">For example:</span></span>
>
> - <span data-ttu-id="d2528-120">**Shell bash**: *~/. bash_profile*, *~/.bashrc*</span><span class="sxs-lookup"><span data-stu-id="d2528-120">**Bash Shell**: *~/.bash_profile*, *~/.bashrc*</span></span>
> - <span data-ttu-id="d2528-121">**Shell Korn**: *~/.Kshrc* ou *. Profile*</span><span class="sxs-lookup"><span data-stu-id="d2528-121">**Korn Shell**: *~/.kshrc* or *.profile*</span></span>
> - <span data-ttu-id="d2528-122">**Shell Z**: *~/.zshrc* ou *. zprofile*</span><span class="sxs-lookup"><span data-stu-id="d2528-122">**Z Shell**: *~/.zshrc* or *.zprofile*</span></span>
>
> <span data-ttu-id="d2528-123">Edite o arquivo de origem apropriado para o Shell e adicione `:$HOME/dotnet` ao final da `PATH` instrução existente.</span><span class="sxs-lookup"><span data-stu-id="d2528-123">Edit the appropriate source file for your shell and add `:$HOME/dotnet` to the end of the existing `PATH` statement.</span></span> <span data-ttu-id="d2528-124">Se nenhuma `PATH` instrução for incluída, adicione uma nova linha com `export PATH=$PATH:$HOME/dotnet` .</span><span class="sxs-lookup"><span data-stu-id="d2528-124">If no `PATH` statement is included, add a new line with `export PATH=$PATH:$HOME/dotnet`.</span></span>
>
> <span data-ttu-id="d2528-125">Além disso, adicione `export DOTNET_ROOT=$HOME/dotnet` ao final do arquivo.</span><span class="sxs-lookup"><span data-stu-id="d2528-125">Also, add `export DOTNET_ROOT=$HOME/dotnet` to the end of the file.</span></span>

<span data-ttu-id="d2528-126">Essa abordagem permite que você instale versões diferentes em locais separados e escolha explicitamente qual deles usar por qual aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d2528-126">This approach lets you install different versions into separate locations and choose explicitly which one to use by which application.</span></span>
