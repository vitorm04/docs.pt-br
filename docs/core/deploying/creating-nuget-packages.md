---
title: Criar um pacote NuGet com ferramentas da interface de linha de comando (CLI) do .NET Core
description: Saiba como criar um pacote do NuGet com o comando 'dotnet pack'.
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: 1add3470799b75ebb92c67eed3509523e510ab6c
ms.sourcegitcommit: 79066169e93d9d65203028b21983574ad9dcf6b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57211787"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a><span data-ttu-id="76f9a-103">Como criar um pacote NuGet com ferramentas da interface de linha de comando (CLI) do .NET Core</span><span class="sxs-lookup"><span data-stu-id="76f9a-103">How to create a NuGet package with .NET Core command-line interface (CLI) tools</span></span>

> [!NOTE]
> <span data-ttu-id="76f9a-104">Veja a seguir exemplos de linha de comando usando o Unix.</span><span class="sxs-lookup"><span data-stu-id="76f9a-104">The following shows command-line samples using Unix.</span></span> <span data-ttu-id="76f9a-105">O comando `dotnet pack` mostrado aqui funciona da mesma maneira no Windows.</span><span class="sxs-lookup"><span data-stu-id="76f9a-105">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="76f9a-106">Espera-se que as bibliotecas .NET Standard e .NET Core sejam distribuídas como pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="76f9a-106">.NET Standard and .NET Core libraries are expected to be distributed as NuGet packages.</span></span> <span data-ttu-id="76f9a-107">Isso na verdade mostra como todas as bibliotecas .NET Standard são distribuídas e consumidas.</span><span class="sxs-lookup"><span data-stu-id="76f9a-107">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span> <span data-ttu-id="76f9a-108">Isso é realizado mais facilmente com o comando `dotnet pack`.</span><span class="sxs-lookup"><span data-stu-id="76f9a-108">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="76f9a-109">Imagine que você acabou de criar uma nova biblioteca incrível e deseja distribuí-la no NuGet.</span><span class="sxs-lookup"><span data-stu-id="76f9a-109">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span> <span data-ttu-id="76f9a-110">Você pode criar um pacote NuGet com várias ferramentas de plataforma cruzada para fazer exatamente isso.</span><span class="sxs-lookup"><span data-stu-id="76f9a-110">You can create a NuGet package with cross platform tools to do exactly that!</span></span> <span data-ttu-id="76f9a-111">O exemplo a seguir pressupõe uma biblioteca chamada **SuperAwesomeLibrary** direcionada para `netstandard1.0`.</span><span class="sxs-lookup"><span data-stu-id="76f9a-111">The following example assumes a library called **SuperAwesomeLibrary** which targets `netstandard1.0`.</span></span>

<span data-ttu-id="76f9a-112">Se você tiver dependências transitivas, ou seja, um projeto que depende de outro pacote, será preciso garantir a restauração dos pacotes para toda a sua solução com o comando `dotnet restore` antes de criar um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="76f9a-112">If you have transitive dependencies; that is, a project which depends on another package, you'll need to make sure to restore packages for your entire solution with the `dotnet restore` command before creating a NuGet package.</span></span> <span data-ttu-id="76f9a-113">Caso contrario, o comando `dotnet pack` não funcionará corretamente.</span><span class="sxs-lookup"><span data-stu-id="76f9a-113">Failing to do so will result in the `dotnet pack` command to not work properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="76f9a-114">Depois de verificar se os pacotes foram restaurados, você poderá navegar até o diretório em que uma biblioteca reside:</span><span class="sxs-lookup"><span data-stu-id="76f9a-114">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

```console
cd src/SuperAwesomeLibrary
```

<span data-ttu-id="76f9a-115">Depois disso, basta apenas um único comando da linha de comando:</span><span class="sxs-lookup"><span data-stu-id="76f9a-115">Then it's just a single command from the command line:</span></span>

```console
dotnet pack
```

<span data-ttu-id="76f9a-116">Sua pasta `/bin/Debug` agora será assemelhará a esta:</span><span class="sxs-lookup"><span data-stu-id="76f9a-116">Your `/bin/Debug` folder will now look like this:</span></span>

```console
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="76f9a-117">Observe que isso gerará um pacote que pode ser depurado.</span><span class="sxs-lookup"><span data-stu-id="76f9a-117">Note that this will produce a package which is capable of being debugged.</span></span> <span data-ttu-id="76f9a-118">Se você deseja criar um pacote NuGet com binários de versão, tudo que você precisa fazer é adicionar o comutador `--configuration` (ou `-c`) e usar `release` como argumento.</span><span class="sxs-lookup"><span data-stu-id="76f9a-118">If you want to build a NuGet package with release binaries, all you need to do is add the `--configuration` (or `-c`) switch and use `release` as the argument.</span></span>

```console
dotnet pack --configuration release
```

<span data-ttu-id="76f9a-119">Sua pasta `/bin` agora terá uma pasta `release` que contém o pacote NuGet com binários de versão:</span><span class="sxs-lookup"><span data-stu-id="76f9a-119">Your `/bin` folder will now have a `release` folder containing your NuGet package with release binaries:</span></span>

```console
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="76f9a-120">E agora você tem os arquivos necessários para publicar um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="76f9a-120">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="76f9a-121">Não confunda `dotnet pack` com `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="76f9a-121">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="76f9a-122">É importante observar que em nenhum momento o comando `dotnet publish` está envolvido.</span><span class="sxs-lookup"><span data-stu-id="76f9a-122">It is important to note that at no point is the `dotnet publish` command involved.</span></span> <span data-ttu-id="76f9a-123">O comando `dotnet publish` é usado para implantar aplicativos com todas as suas dependências no mesmo pacote, não para gerar um pacote NuGet para ser distribuído e consumidos por meio do NuGet.</span><span class="sxs-lookup"><span data-stu-id="76f9a-123">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -- not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>

## <a name="see-also"></a><span data-ttu-id="76f9a-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="76f9a-124">See also</span></span>

- [<span data-ttu-id="76f9a-125">Início Rápido: Criar e publicar um pacote</span><span class="sxs-lookup"><span data-stu-id="76f9a-125">Quickstart: Create and publish a package</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)