---
title: Criar um pacote NuGet com CLI do .NET Core
description: Saiba como criar um pacote do NuGet com o comando 'dotnet pack'.
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: ddc19faa7547637036686146f8600f40713541a8
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740869"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a><span data-ttu-id="cf704-103">Como criar um pacote NuGet com ferramentas da interface de linha de comando (CLI) do .NET Core</span><span class="sxs-lookup"><span data-stu-id="cf704-103">How to create a NuGet package with .NET Core command-line interface (CLI) tools</span></span>

> [!NOTE]
> <span data-ttu-id="cf704-104">Veja a seguir exemplos de linha de comando usando o Unix.</span><span class="sxs-lookup"><span data-stu-id="cf704-104">The following shows command-line samples using Unix.</span></span> <span data-ttu-id="cf704-105">O comando `dotnet pack` mostrado aqui funciona da mesma maneira no Windows.</span><span class="sxs-lookup"><span data-stu-id="cf704-105">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="cf704-106">Espera-se que as bibliotecas .NET Standard e .NET Core sejam distribuídas como pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="cf704-106">.NET Standard and .NET Core libraries are expected to be distributed as NuGet packages.</span></span> <span data-ttu-id="cf704-107">Isso na verdade mostra como todas as bibliotecas .NET Standard são distribuídas e consumidas.</span><span class="sxs-lookup"><span data-stu-id="cf704-107">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span> <span data-ttu-id="cf704-108">Isso é realizado mais facilmente com o comando `dotnet pack`.</span><span class="sxs-lookup"><span data-stu-id="cf704-108">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="cf704-109">Imagine que você acabou de criar uma nova biblioteca incrível e deseja distribuí-la no NuGet.</span><span class="sxs-lookup"><span data-stu-id="cf704-109">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span> <span data-ttu-id="cf704-110">Você pode criar um pacote NuGet com ferramentas de plataforma cruzada para fazer exatamente isso!</span><span class="sxs-lookup"><span data-stu-id="cf704-110">You can create a NuGet package with cross-platform tools to do exactly that!</span></span> <span data-ttu-id="cf704-111">O exemplo a seguir pressupõe uma biblioteca chamada **SuperAwesomeLibrary** que tem como destino `netstandard1.0`.</span><span class="sxs-lookup"><span data-stu-id="cf704-111">The following example assumes a library called **SuperAwesomeLibrary** that targets `netstandard1.0`.</span></span>

<span data-ttu-id="cf704-112">Se você tiver dependências transitivas, ou seja, um projeto que dependa de outro pacote, certifique-se de restaurar pacotes para toda a solução com o comando `dotnet restore` antes de criar um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="cf704-112">If you have transitive dependencies, that is, a project that depends on another package, make sure to restore packages for the entire solution with the `dotnet restore` command before you create a NuGet package.</span></span> <span data-ttu-id="cf704-113">A falha ao fazer isso resultará na `dotnet pack` comando não funcionar corretamente.</span><span class="sxs-lookup"><span data-stu-id="cf704-113">Failing to do so will result in the `dotnet pack` command not working properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="cf704-114">Depois de verificar se os pacotes foram restaurados, você poderá navegar até o diretório em que uma biblioteca reside:</span><span class="sxs-lookup"><span data-stu-id="cf704-114">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

```console
cd src/SuperAwesomeLibrary
```

<span data-ttu-id="cf704-115">Depois disso, basta apenas um único comando da linha de comando:</span><span class="sxs-lookup"><span data-stu-id="cf704-115">Then it's just a single command from the command line:</span></span>

```dotnetcli
dotnet pack
```

<span data-ttu-id="cf704-116">Sua pasta */bin/Debug* agora terá esta aparência:</span><span class="sxs-lookup"><span data-stu-id="cf704-116">Your */bin/Debug* folder will now look like this:</span></span>

```console
$ ls bin/Debug
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="cf704-117">Isso produz um pacote que é capaz de ser depurado.</span><span class="sxs-lookup"><span data-stu-id="cf704-117">This produces a package that is capable of being debugged.</span></span> <span data-ttu-id="cf704-118">Se você deseja criar um pacote NuGet com binários de versão, tudo que você precisa fazer é adicionar o comutador `--configuration` (ou `-c`) e usar `release` como argumento.</span><span class="sxs-lookup"><span data-stu-id="cf704-118">If you want to build a NuGet package with release binaries, all you need to do is add the `--configuration` (or `-c`) switch and use `release` as the argument.</span></span>

```dotnetcli
dotnet pack --configuration release
```

<span data-ttu-id="cf704-119">Sua pasta */bin* agora terá uma pasta *Release* que contém o pacote NuGet com binários de versão:</span><span class="sxs-lookup"><span data-stu-id="cf704-119">Your */bin* folder will now have a *release* folder containing your NuGet package with release binaries:</span></span>

```console
$ ls bin/release
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="cf704-120">E agora você tem os arquivos necessários para publicar um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="cf704-120">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="cf704-121">Não confunda `dotnet pack` com `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="cf704-121">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="cf704-122">É importante observar que em nenhum momento o comando `dotnet publish` está envolvido.</span><span class="sxs-lookup"><span data-stu-id="cf704-122">It is important to note that at no point is the `dotnet publish` command involved.</span></span> <span data-ttu-id="cf704-123">O comando `dotnet publish` é usado para implantar aplicativos com todas as suas dependências no mesmo pacote, não para gerar um pacote NuGet para ser distribuído e consumidos por meio do NuGet.</span><span class="sxs-lookup"><span data-stu-id="cf704-123">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -- not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>

## <a name="see-also"></a><span data-ttu-id="cf704-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="cf704-124">See also</span></span>

- [<span data-ttu-id="cf704-125">Início Rápido: Criar e publicar um pacote</span><span class="sxs-lookup"><span data-stu-id="cf704-125">Quickstart: Create and publish a package</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
