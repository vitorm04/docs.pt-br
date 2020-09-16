---
title: Comando dotnet add package
description: O comando 'dotnet add package' fornece uma opção conveniente para adicionar uma referência de pacote NuGet a um projeto.
ms.date: 02/14/2020
ms.openlocfilehash: 1bdda241c1301b926ba2fd322f969407038b7b62
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538062"
---
# <a name="dotnet-add-package"></a><span data-ttu-id="632dc-103">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="632dc-103">dotnet add package</span></span>

<span data-ttu-id="632dc-104">**Este artigo aplica-se a:** ✔️ SDK do .NET Core 2. x e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="632dc-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="632dc-105">Name</span><span class="sxs-lookup"><span data-stu-id="632dc-105">Name</span></span>

<span data-ttu-id="632dc-106">`dotnet add package` – adiciona uma referência de pacote a um arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="632dc-106">`dotnet add package` - Adds a package reference to a project file.</span></span>

## <a name="synopsis"></a><span data-ttu-id="632dc-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="632dc-107">Synopsis</span></span>

```dotnetcli
dotnet add [<PROJECT>] package <PACKAGE_NAME>
    [-f|--framework <FRAMEWORK>] [--interactive]
    [-n|--no-restore] [--package-directory <PACKAGE_DIRECTORY>]
    [-s|--source <SOURCE>] [-v|--version <VERSION>]

dotnet add package -h|--help
```

## <a name="description"></a><span data-ttu-id="632dc-108">Description</span><span class="sxs-lookup"><span data-stu-id="632dc-108">Description</span></span>

<span data-ttu-id="632dc-109">O comando `dotnet add package` fornece uma opção conveniente para adicionar uma referência de pacote a um arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="632dc-109">The `dotnet add package` command provides a convenient option to add a package reference to a project file.</span></span> <span data-ttu-id="632dc-110">Depois de executar o comando, há uma verificação de compatibilidade para garantir que o pacote seja compatível com as estruturas do projeto.</span><span class="sxs-lookup"><span data-stu-id="632dc-110">After running the command, there's a compatibility check to ensure the package is compatible with the frameworks in the project.</span></span> <span data-ttu-id="632dc-111">Se for aprovado na verificação, um elemento `<PackageReference>` será adicionado ao arquivo de projeto e [dotnet restore](dotnet-restore.md) será executada.</span><span class="sxs-lookup"><span data-stu-id="632dc-111">If the check passes, a `<PackageReference>` element is added to the project file and [dotnet restore](dotnet-restore.md) is run.</span></span>

<span data-ttu-id="632dc-112">Por exemplo, adicionar `Newtonsoft.Json` a *ToDo.csproj* produz uma saída semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="632dc-112">For example, adding `Newtonsoft.Json` to *ToDo.csproj* produces output similar to the following example:</span></span>

```console
Writing C:\Users\me\AppData\Local\Temp\tmp95A8.tmp
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

<span data-ttu-id="632dc-113">O arquivo *ToDo.csproj* agora contém um elemento [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) para o pacote referenciado.</span><span class="sxs-lookup"><span data-stu-id="632dc-113">The *ToDo.csproj* file now contains a [`<PackageReference>`](/nuget/consume-packages/package-references-in-project-files) element for the referenced package.</span></span>

```xml
<PackageReference Include="Newtonsoft.Json" Version="12.0.1" />
```

### <a name="implicit-restore"></a><span data-ttu-id="632dc-114">Restauração implícita</span><span class="sxs-lookup"><span data-stu-id="632dc-114">Implicit restore</span></span>

[!INCLUDE[DotNet Restore Note](../../../includes/dotnet-restore-note.md)]

## <a name="arguments"></a><span data-ttu-id="632dc-115">Argumentos</span><span class="sxs-lookup"><span data-stu-id="632dc-115">Arguments</span></span>

- **`PROJECT`**

  <span data-ttu-id="632dc-116">Especifica o arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="632dc-116">Specifies the project file.</span></span> <span data-ttu-id="632dc-117">Se não for especificado, o comando pesquisará um no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="632dc-117">If not specified, the command searches the current directory for one.</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="632dc-118">A referência de pacote a ser adicionada.</span><span class="sxs-lookup"><span data-stu-id="632dc-118">The package reference to add.</span></span>

## <a name="options"></a><span data-ttu-id="632dc-119">Opções</span><span class="sxs-lookup"><span data-stu-id="632dc-119">Options</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="632dc-120">Adiciona uma referência de pacote somente quando há uma [estrutura](../../standard/frameworks.md) específica como destino.</span><span class="sxs-lookup"><span data-stu-id="632dc-120">Adds a package reference only when targeting a specific [framework](../../standard/frameworks.md).</span></span>

- **`-h|--help`**

  <span data-ttu-id="632dc-121">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="632dc-121">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="632dc-122">Permite que o comando pare e aguarde a entrada ou uma ação do usuário (por exemplo, para concluir a autenticação).</span><span class="sxs-lookup"><span data-stu-id="632dc-122">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="632dc-123">Disponível desde o SDK 2.1 do .NET Core, versão 2.1.400 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="632dc-123">Available since .NET Core 2.1 SDK, version 2.1.400 or later.</span></span>

- **`-n|--no-restore`**

  <span data-ttu-id="632dc-124">Adiciona uma referência de pacote sem executar a visualização de restauração e a verificação de compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="632dc-124">Adds a package reference without performing a restore preview and compatibility check.</span></span>

- **`--package-directory <PACKAGE_DIRECTORY>`**

  <span data-ttu-id="632dc-125">O diretório no qual restaurar os pacotes.</span><span class="sxs-lookup"><span data-stu-id="632dc-125">The directory where to restore the packages.</span></span> <span data-ttu-id="632dc-126">O local de restauração de pacote padrão é `%userprofile%\.nuget\packages` no Windows e `~/.nuget/packages` no macOS e Linux.</span><span class="sxs-lookup"><span data-stu-id="632dc-126">The default package restore location is `%userprofile%\.nuget\packages` on Windows and `~/.nuget/packages` on macOS and Linux.</span></span> <span data-ttu-id="632dc-127">Para obter mais informações, consulte [Como gerenciar as pastas de pacotes globais, de cache e temporárias no NuGet](/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span><span class="sxs-lookup"><span data-stu-id="632dc-127">For more information, see [Managing the global packages, cache, and temp folders in NuGet](/nuget/consume-packages/managing-the-global-packages-and-cache-folders).</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="632dc-128">O URI da origem do pacote NuGet a ser usado durante a operação de restauração.</span><span class="sxs-lookup"><span data-stu-id="632dc-128">The URI of the NuGet package source to use during the restore operation.</span></span>

- **`-v|--version <VERSION>`**

  <span data-ttu-id="632dc-129">Versão do pacote.</span><span class="sxs-lookup"><span data-stu-id="632dc-129">Version of the package.</span></span> <span data-ttu-id="632dc-130">Consulte [Controle de versão do pacote NuGet](/nuget/reference/package-versioning).</span><span class="sxs-lookup"><span data-stu-id="632dc-130">See [NuGet package versioning](/nuget/reference/package-versioning).</span></span>

## <a name="examples"></a><span data-ttu-id="632dc-131">Exemplos</span><span class="sxs-lookup"><span data-stu-id="632dc-131">Examples</span></span>

- <span data-ttu-id="632dc-132">Adicionar um pacote NuGet `Newtonsoft.Json` a um projeto:</span><span class="sxs-lookup"><span data-stu-id="632dc-132">Add `Newtonsoft.Json` NuGet package to a project:</span></span>

  ```dotnetcli
  dotnet add package Newtonsoft.Json
  ```

- <span data-ttu-id="632dc-133">Adicionar uma versão específica de um pacote a um projeto:</span><span class="sxs-lookup"><span data-stu-id="632dc-133">Add a specific version of a package to a project:</span></span>

  ```dotnetcli
  dotnet add ToDo.csproj package Microsoft.Azure.DocumentDB.Core -v 1.0.0
  ```

- <span data-ttu-id="632dc-134">Adicionar um pacote usando uma fonte específica do NuGet:</span><span class="sxs-lookup"><span data-stu-id="632dc-134">Add a package using a specific NuGet source:</span></span>

  ```dotnetcli
  dotnet add package Microsoft.AspNetCore.StaticFiles -s https://dotnet.myget.org/F/dotnet-core/api/v3/index.json
  ```

## <a name="see-also"></a><span data-ttu-id="632dc-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="632dc-135">See also</span></span>

- [<span data-ttu-id="632dc-136">Como gerenciar as pastas de pacotes globais, de cache e temporárias no NuGet</span><span class="sxs-lookup"><span data-stu-id="632dc-136">Managing the global packages, cache, and temp folders in NuGet</span></span>](/nuget/consume-packages/managing-the-global-packages-and-cache-folders)
- [<span data-ttu-id="632dc-137">Controle de versão do pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="632dc-137">NuGet package versioning</span></span>](/nuget/reference/package-versioning)
