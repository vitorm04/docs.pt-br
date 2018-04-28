---
title: Criando um pacote NuGet com várias Ferramentas de Plataforma Cruzada
description: Saiba como criar um pacote do NuGet com o comando 'dotnet pack'.
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: b85f6d53787cb513ae4c1e8147a066188b0e56c6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-create-a-nuget-package-with-cross-platform-tools"></a><span data-ttu-id="46b0f-103">Como criar um pacote NuGet com várias Ferramentas de Plataforma Cruzada</span><span class="sxs-lookup"><span data-stu-id="46b0f-103">How to Create a NuGet Package with Cross Platform Tools</span></span>

> [!NOTE]
> <span data-ttu-id="46b0f-104">Veja a seguir exemplos de linha de comando usando o Unix.</span><span class="sxs-lookup"><span data-stu-id="46b0f-104">The following shows command-line samples using Unix.</span></span>  <span data-ttu-id="46b0f-105">O comando `dotnet pack` mostrado aqui funciona da mesma maneira no Windows.</span><span class="sxs-lookup"><span data-stu-id="46b0f-105">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="46b0f-106">Para .NET Core 1.0, espera-se que as bibliotecas sejam distribuídas como pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="46b0f-106">For .NET Core 1.0, libraries are expected to be distributed as NuGet packages.</span></span>  <span data-ttu-id="46b0f-107">Isso na verdade mostra como todas as bibliotecas .NET Standard são distribuídas e consumidas.</span><span class="sxs-lookup"><span data-stu-id="46b0f-107">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span>  <span data-ttu-id="46b0f-108">Isso é realizado mais facilmente com o comando `dotnet pack`.</span><span class="sxs-lookup"><span data-stu-id="46b0f-108">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="46b0f-109">Imagine que você acabou de criar uma nova biblioteca incrível e deseja distribuí-la no NuGet.</span><span class="sxs-lookup"><span data-stu-id="46b0f-109">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span>  <span data-ttu-id="46b0f-110">Você pode criar um pacote NuGet com várias ferramentas de plataforma cruzada para fazer exatamente isso.</span><span class="sxs-lookup"><span data-stu-id="46b0f-110">You can create a NuGet package with cross platform tools to do exactly that!</span></span>  <span data-ttu-id="46b0f-111">O exemplo a seguir pressupõe uma biblioteca chamada **SuperAwesomeLibrary** direcionada para `netstandard1.0`.</span><span class="sxs-lookup"><span data-stu-id="46b0f-111">The following example assumes a library called **SuperAwesomeLibrary** which targets `netstandard1.0`.</span></span>

<span data-ttu-id="46b0f-112">Se você tiver dependências transitivas, ou seja, um projeto que depende de outro projeto, precisará verificar se os pacotes foram restaurados para toda sua solução com o comando `dotnet restore` antes de criar um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="46b0f-112">If you have transitive dependencies; that is, a project which depends on another project, you'll need to make sure to restore packages for your entire solution with the `dotnet restore` command before creating a NuGet package.</span></span>  <span data-ttu-id="46b0f-113">Caso contrario, o comando `dotnet pack` não funcionará corretamente.</span><span class="sxs-lookup"><span data-stu-id="46b0f-113">Failing to do so will result in the `dotnet pack` command to not work properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]


<span data-ttu-id="46b0f-114">Depois de verificar se os pacotes foram restaurados, você poderá navegar até o diretório em que uma biblioteca reside:</span><span class="sxs-lookup"><span data-stu-id="46b0f-114">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

`$ cd src/SuperAwesomeLibrary`

<span data-ttu-id="46b0f-115">Depois disso, basta apenas um único comando da linha de comando:</span><span class="sxs-lookup"><span data-stu-id="46b0f-115">Then it's just a single command from the command line:</span></span>
    
`$ dotnet pack`

<span data-ttu-id="46b0f-116">Sua pasta `/bin/Debug` agora será assemelhará a esta:</span><span class="sxs-lookup"><span data-stu-id="46b0f-116">Your `/bin/Debug` folder will now look like this:</span></span>

```
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="46b0f-117">Observe que isso gerará um pacote que pode ser depurado.</span><span class="sxs-lookup"><span data-stu-id="46b0f-117">Note that this will produce a package which is capable of being debugged.</span></span>  <span data-ttu-id="46b0f-118">Se você deseja criar um pacote NuGet com binários de versão, tudo que você precisa fazer é adicionar o comutador `-c`/`--configuration` e usar `release` como argumento.</span><span class="sxs-lookup"><span data-stu-id="46b0f-118">If you want to build a NuGet package with release binaries, all you need to do is add the `-c`/`--configuration` switch and use `release` as the argument.</span></span>

`$ dotnet pack --configuration release`

<span data-ttu-id="46b0f-119">Sua pasta `/bin` agora terá uma pasta `release` que contém o pacote NuGet com binários de versão:</span><span class="sxs-lookup"><span data-stu-id="46b0f-119">Your `/bin` folder will now have a `release` folder containing your NuGet package with release binaries:</span></span>

```
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="46b0f-120">E agora você tem os arquivos necessários para publicar um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="46b0f-120">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="46b0f-121">Não confunda `dotnet pack` com `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="46b0f-121">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="46b0f-122">É importante observar que em nenhum momento o comando `dotnet publish` está envolvido.</span><span class="sxs-lookup"><span data-stu-id="46b0f-122">It is important to note that at no point is the `dotnet publish` command involved.</span></span>  <span data-ttu-id="46b0f-123">O comando `dotnet publish` é usado para implantar aplicativos com todas as suas dependências no mesmo pacote, não para gerar um pacote NuGet para ser distribuído e consumidos por meio do NuGet.</span><span class="sxs-lookup"><span data-stu-id="46b0f-123">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -  not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>
