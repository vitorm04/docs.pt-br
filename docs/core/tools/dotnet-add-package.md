---
title: Comando dotnet add package – CLI do .NET Core
description: O comando 'dotnet add package' fornece uma opção conveniente para adicionar uma referência de pacote NuGet a um projeto.
author: mairaw
ms.author: mairaw
ms.date: 08/11/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 3a8752ff83e069d21ebbda346efef34b17360e3b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-add-package"></a><span data-ttu-id="0d463-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="0d463-103">dotnet add package</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0d463-104">Nome</span><span class="sxs-lookup"><span data-stu-id="0d463-104">Name</span></span>

<span data-ttu-id="0d463-105">`dotnet add package` – adiciona uma referência de pacote a um arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="0d463-105">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0d463-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="0d463-106">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-v|--version] [-f|--framework] [-n|--no-restore] [-s|--source] [--package-directory]`

## <a name="description"></a><span data-ttu-id="0d463-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="0d463-107">Description</span></span>

<span data-ttu-id="0d463-108">O comando `dotnet add package` fornece uma opção conveniente para adicionar uma referência de pacote a um arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="0d463-108">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="0d463-109">Depois de executar o comando, há uma verificação de compatibilidade para garantir que o pacote seja compatível com as estruturas do projeto.</span><span class="sxs-lookup"><span data-stu-id="0d463-109">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="0d463-110">Se for aprovado na verificação, um elemento `<PackageReference>` será adicionado ao arquivo de projeto e [dotnet restore](dotnet-restore.md) será executada.</span><span class="sxs-lookup"><span data-stu-id="0d463-110">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="0d463-111">Por exemplo, adicionar `Newtonsoft.Json` a *ToDo.csproj* produz uma saída semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="0d463-111">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

```
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\projects\ToDo\ToDo.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 235ms
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '10.0.3' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

<span data-ttu-id="0d463-112">O arquivo *ToDo.csproj* agora contém um elemento [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) para o pacote referenciado.</span><span class="sxs-lookup"><span data-stu-id="0d463-112">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="0d463-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="0d463-113">Arguments</span></span>

`PROJECT`

<span data-ttu-id="0d463-114">Especifica o arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="0d463-114">Specifies the project file.</span></span> <span data-ttu-id="0d463-115">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="0d463-115">If not specified, the command searches the current directory for one.</span></span>

`PACKAGE_NAME`

<span data-ttu-id="0d463-116">A referência de pacote a ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="0d463-116">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="0d463-117">Opções</span><span class="sxs-lookup"><span data-stu-id="0d463-117">Options</span></span>

`-h|--help`

<span data-ttu-id="0d463-118">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="0d463-118">Prints out a short help for the command.</span></span>

`-v|--version <VERSION>`

<span data-ttu-id="0d463-119">Versão do pacote.</span><span class="sxs-lookup"><span data-stu-id="0d463-119">Version of the package.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="0d463-120">Adiciona uma referência de pacote somente quando há uma [estrutura](../../standard/frameworks.md) específica como destino.</span><span class="sxs-lookup"><span data-stu-id="0d463-120">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

`-n|--no-restore`

<span data-ttu-id="0d463-121">Adiciona uma referência de pacote sem executar a visualização de restauração e a verificação de compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="0d463-121">Adds a package reference without performing a restore preview and compatibility check.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="0d463-122">Usa uma fonte de pacote NuGet específica durante a operação de restauração.</span><span class="sxs-lookup"><span data-stu-id="0d463-122">Uses a specific NuGet package source during the restore operation.</span></span>

`--package-directory <PACKAGE_DIRECTORY>`

<span data-ttu-id="0d463-123">Restaura o pacote no diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="0d463-123">Restores the package to the specified directory.</span></span>

## <a name="examples"></a><span data-ttu-id="0d463-124">Exemplos</span><span class="sxs-lookup"><span data-stu-id="0d463-124">Examples</span></span>

<span data-ttu-id="0d463-125">Adicionar um pacote NuGet `Newtonsoft.Json` a um projeto:</span><span class="sxs-lookup"><span data-stu-id="0d463-125">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

`dotnet add package Newtonsoft.Json`

<span data-ttu-id="0d463-126">Adicionar uma versão específica de um pacote a um projeto:</span><span class="sxs-lookup"><span data-stu-id="0d463-126">Add a specific version of a package to a project:</span></span>

`dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0`

<span data-ttu-id="0d463-127">Adicionar um pacote usando uma fonte específica do NuGet:</span><span class="sxs-lookup"><span data-stu-id="0d463-127">Add a package using a specific NuGet source:</span></span>

`dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json`
