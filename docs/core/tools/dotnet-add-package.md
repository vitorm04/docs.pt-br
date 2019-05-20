---
title: Comando dotnet add package
description: O comando 'dotnet add package' fornece uma opção conveniente para adicionar uma referência de pacote NuGet a um projeto.
ms.date: 04/24/2019
ms.openlocfilehash: 07cb6cd8e7873def6f969a54c1f7b9a7325f9491
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632279"
---
# <a name="dotnet-add-package"></a><span data-ttu-id="492c7-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="492c7-103">dotnet add package</span></span>

<span data-ttu-id="492c7-104">**Este artigo se aplica a: ✓** SDK do .NET Core 1.x e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="492c7-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="492c7-105">Nome</span><span class="sxs-lookup"><span data-stu-id="492c7-105">Name</span></span>

<span data-ttu-id="492c7-106">`dotnet add package` – adiciona uma referência de pacote a um arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="492c7-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="492c7-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="492c7-107">Synopsis</span></span>

`dotnet add [<PROJECT>] package <PACKAGE_NAME> [-h|--help] [-f|--framework] [--interactive] [-n|--no-restore] [--package-directory] [-s|--source] [-v|--version]`

## <a name="description"></a><span data-ttu-id="492c7-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="492c7-108">Description</span></span>

<span data-ttu-id="492c7-109">O comando `dotnet add package` fornece uma opção conveniente para adicionar uma referência de pacote a um arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="492c7-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="492c7-110">Depois de executar o comando, há uma verificação de compatibilidade para garantir que o pacote seja compatível com as estruturas do projeto.</span><span class="sxs-lookup"><span data-stu-id="492c7-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="492c7-111">Se for aprovado na verificação, um elemento `<PackageReference>` será adicionado ao arquivo de projeto e [dotnet restore](dotnet-restore.md) será executada.</span><span class="sxs-lookup"><span data-stu-id="492c7-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

<span data-ttu-id="492c7-112">Por exemplo, adicionar `Newtonsoft.Json` a *ToDo.csproj* produz uma saída semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="492c7-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

```console
  Writing C:\Users\mairaw\AppData\Local\Temp\tmp95A8.tmp
info : Adding PackageReference for package 'Newtonsoft.Json' into project 'C:\projects\ToDo\ToDo.csproj'.
log  : Restoring packages for C:\Temp\projects\consoleproj\consoleproj.csproj...
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/index.json 79ms
info :   GET https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg
info :   OK https://api.nuget.org/v3-flatcontainer/newtonsoft.json/12.0.1/newtonsoft.json.12.0.1.nupkg 232ms
log  : Installing Newtonsoft.Json 12.0.1.
info : Package 'Newtonsoft.Json' is compatible with all the specified frameworks in project 'C:\projects\ToDo\ToDo.csproj'.
info : PackageReference for package 'Newtonsoft.Json' version '12.0.1' added to file 'C:\projects\ToDo\ToDo.csproj'.
```

<span data-ttu-id="492c7-113">O arquivo *ToDo.csproj* agora contém um elemento [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) para o pacote referenciado.</span><span class="sxs-lookup"><span data-stu-id="492c7-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

## <a name="arguments"></a><span data-ttu-id="492c7-114">Arguments</span><span class="sxs-lookup"><span data-stu-id="492c7-114">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="492c7-115">Especifica o arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="492c7-115">Specifies the project file.</span></span> <span data-ttu-id="492c7-116">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="492c7-116">If not specified, the command searches the current directory for one.</span></span>

* **`PACKAGE_NAME`**

  <span data-ttu-id="492c7-117">A referência de pacote a ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="492c7-117">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="492c7-118">Opções</span><span class="sxs-lookup"><span data-stu-id="492c7-118">Options</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="492c7-119">Adiciona uma referência de pacote somente quando há uma [estrutura](../../standard/frameworks.md) específica como destino.</span><span class="sxs-lookup"><span data-stu-id="492c7-119">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

* **`-h|--help`**

  <span data-ttu-id="492c7-120">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="492c7-120">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="492c7-121">Permite que o comando pare e aguarde a entrada ou uma ação do usuário (por exemplo, para concluir a autenticação).</span><span class="sxs-lookup"><span data-stu-id="492c7-121">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="492c7-122">Disponível desde o SDK 2.1 do .NET Core, versão 2.1.400 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="492c7-122">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

* **`-n|--no-restore`**

  <span data-ttu-id="492c7-123">Adiciona uma referência de pacote sem executar a visualização de restauração e a verificação de compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="492c7-123">Adds a package reference without performing a restore preview and compatibility check.</span></span>

* **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="492c7-124">O diretório no qual restaurar os pacotes.</span><span class="sxs-lookup"><span data-stu-id="492c7-124">The directory where to restore the packages.</span></span>

* **`-s|--source <SOURCE>`**

  <span data-ttu-id="492c7-125">A origem do pacote NuGet a ser usada durante a operação de restauração.</span><span class="sxs-lookup"><span data-stu-id="492c7-125">The NuGet package source to use during the restore operation.</span></span>

* **`-v|--version <VERSION>`**

  <span data-ttu-id="492c7-126">Versão do pacote.</span><span class="sxs-lookup"><span data-stu-id="492c7-126">Version of the package.</span></span>

## <a name="examples"></a><span data-ttu-id="492c7-127">Exemplos</span><span class="sxs-lookup"><span data-stu-id="492c7-127">Examples</span></span>

* <span data-ttu-id="492c7-128">Adicionar um pacote NuGet `Newtonsoft.Json` a um projeto:</span><span class="sxs-lookup"><span data-stu-id="492c7-128">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```console
  dotnet add package Newtonsoft.Json
  ```

* <span data-ttu-id="492c7-129">Adicionar uma versão específica de um pacote a um projeto:</span><span class="sxs-lookup"><span data-stu-id="492c7-129">Add a specific version of a package to a project:</span></span>

  ```console
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

* <span data-ttu-id="492c7-130">Adicionar um pacote usando uma fonte específica do NuGet:</span><span class="sxs-lookup"><span data-stu-id="492c7-130">Add a package using a specific NuGet source:</span></span>

  ```console
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```
