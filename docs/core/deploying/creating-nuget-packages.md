---
title: "Criando um pacote NuGet com várias Ferramentas de Plataforma Cruzada"
description: Saiba como criar um pacote do NuGet com o comando 'dotnet pack'.
keywords: .NET, .NET Core, NuGet
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 2f0415c1-110b-433d-87c1-ae3d543a8844
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9e5c762de0a14407c92c9752edc9619caa07d500
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="how-to-create-a-nuget-package-with-cross-platform-tools"></a><span data-ttu-id="92d6c-104">Como criar um pacote NuGet com várias Ferramentas de Plataforma Cruzada</span><span class="sxs-lookup"><span data-stu-id="92d6c-104">How to Create a NuGet Package with Cross Platform Tools</span></span>

> [!NOTE]
> <span data-ttu-id="92d6c-105">Veja a seguir exemplos de linha de comando usando o Unix.</span><span class="sxs-lookup"><span data-stu-id="92d6c-105">The following shows command-line samples using Unix.</span></span>  <span data-ttu-id="92d6c-106">O comando `dotnet pack` mostrado aqui funciona da mesma maneira no Windows.</span><span class="sxs-lookup"><span data-stu-id="92d6c-106">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="92d6c-107">Para .NET Core 1.0, espera-se que as bibliotecas sejam distribuídas como pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="92d6c-107">For .NET Core 1.0, libraries are expected to be distributed as NuGet packages.</span></span>  <span data-ttu-id="92d6c-108">Isso na verdade mostra como todas as bibliotecas .NET Standard são distribuídas e consumidas.</span><span class="sxs-lookup"><span data-stu-id="92d6c-108">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span>  <span data-ttu-id="92d6c-109">Isso é realizado mais facilmente com o comando `dotnet pack`.</span><span class="sxs-lookup"><span data-stu-id="92d6c-109">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="92d6c-110">Imagine que você acabou de criar uma nova biblioteca incrível e deseja distribuí-la no NuGet.</span><span class="sxs-lookup"><span data-stu-id="92d6c-110">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span>  <span data-ttu-id="92d6c-111">Você pode criar um pacote NuGet com várias ferramentas de plataforma cruzada para fazer exatamente isso.</span><span class="sxs-lookup"><span data-stu-id="92d6c-111">You can create a NuGet package with cross platform tools to do exactly that!</span></span>  <span data-ttu-id="92d6c-112">O exemplo a seguir pressupõe uma biblioteca chamada **SuperAwesomeLibrary** direcionada para `netstandard1.0`.</span><span class="sxs-lookup"><span data-stu-id="92d6c-112">The following example assumes a library called **SuperAwesomeLibrary** which targets `netstandard1.0`.</span></span>

<span data-ttu-id="92d6c-113">Se você tiver dependências transitivas, ou seja, um projeto que depende de outro projeto, precisará verificar se os pacotes foram restaurados para toda sua solução com o comando `dotnet restore` antes de criar um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="92d6c-113">If you have transitive dependencies; that is, a project which depends on another project, you'll need to make sure to restore packages for your entire solution with the `dotnet restore` command before creating a NuGet package.</span></span>  <span data-ttu-id="92d6c-114">Caso contrario, o comando `dotnet pack` não funcionará corretamente.</span><span class="sxs-lookup"><span data-stu-id="92d6c-114">Failing to do so will result in the `dotnet pack` command to not work properly.</span></span>

<span data-ttu-id="92d6c-115">Depois de verificar se os pacotes foram restaurados, você poderá navegar até o diretório em que uma biblioteca reside:</span><span class="sxs-lookup"><span data-stu-id="92d6c-115">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

`$ cd src/SuperAwesomeLibrary`

<span data-ttu-id="92d6c-116">Depois disso, basta apenas um único comando da linha de comando:</span><span class="sxs-lookup"><span data-stu-id="92d6c-116">Then it's just a single command from the command line:</span></span>
    
`$ dotnet pack`

<span data-ttu-id="92d6c-117">Sua pasta `/bin/Debug` agora será assemelhará a esta:</span><span class="sxs-lookup"><span data-stu-id="92d6c-117">Your `/bin/Debug` folder will now look like this:</span></span>

```
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="92d6c-118">Observe que isso gerará um pacote que pode ser depurado.</span><span class="sxs-lookup"><span data-stu-id="92d6c-118">Note that this will produce a package which is capable of being debugged.</span></span>  <span data-ttu-id="92d6c-119">Se você deseja criar um pacote NuGet com binários de versão, tudo que você precisa fazer é adicionar o comutador `-c`/`--configuration` e usar `release` como argumento.</span><span class="sxs-lookup"><span data-stu-id="92d6c-119">If you want to build a NuGet package with release binaries, all you need to do is add the `-c`/`--configuration` switch and use `release` as the argument.</span></span>

`$ dotnet pack --configuration release`

<span data-ttu-id="92d6c-120">Sua pasta `/bin` agora terá uma pasta `release` que contém o pacote NuGet com binários de versão:</span><span class="sxs-lookup"><span data-stu-id="92d6c-120">Your `/bin` folder will now have a `release` folder containing your NuGet package with release binaries:</span></span>

```
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="92d6c-121">E agora você tem os arquivos necessários para publicar um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="92d6c-121">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="92d6c-122">Não confunda `dotnet pack` com `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="92d6c-122">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="92d6c-123">É importante observar que em nenhum momento o comando `dotnet publish` está envolvido.</span><span class="sxs-lookup"><span data-stu-id="92d6c-123">It is important to note that at no point is the `dotnet publish` command involved.</span></span>  <span data-ttu-id="92d6c-124">O comando `dotnet publish` é usado para implantar aplicativos com todas as suas dependências no mesmo pacote, não para gerar um pacote NuGet para ser distribuído e consumidos por meio do NuGet.</span><span class="sxs-lookup"><span data-stu-id="92d6c-124">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -  not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>

