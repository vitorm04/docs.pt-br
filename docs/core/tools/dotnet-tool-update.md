---
title: Comando dotnet tool update
description: O comando dotnet ferramenta de atualização atualiza a ferramenta .NET Core especificada em seu computador.
ms.date: 02/14/2020
ms.openlocfilehash: 80e807a0fc06ad762334f888e701f6d9c448369a
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156940"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="877cd-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="877cd-103">dotnet tool update</span></span>

<span data-ttu-id="877cd-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="877cd-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="877cd-105">Nome</span><span class="sxs-lookup"><span data-stu-id="877cd-105">Name</span></span>

<span data-ttu-id="877cd-106">`dotnet tool update`-atualiza a [ferramenta .NET Core](global-tools.md) especificada em seu computador.</span><span class="sxs-lookup"><span data-stu-id="877cd-106">`dotnet tool update` - Updates the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="877cd-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="877cd-107">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <PACKAGE_NAME> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <-h|--help>
```

## <a name="description"></a><span data-ttu-id="877cd-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="877cd-108">Description</span></span>

<span data-ttu-id="877cd-109">O comando `dotnet tool update` fornece uma maneira de atualizar as ferramentas do .NET Core em seu computador para a versão estável mais recente do pacote.</span><span class="sxs-lookup"><span data-stu-id="877cd-109">The `dotnet tool update` command provides a way for you to update .NET Core tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="877cd-110">O comando desinstala e reinstala uma ferramenta, atualizando-a efetivamente.</span><span class="sxs-lookup"><span data-stu-id="877cd-110">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="877cd-111">Para usar o comando, especifique uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="877cd-111">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="877cd-112">Para atualizar uma ferramenta global que foi instalada no local padrão, use a opção `--global`</span><span class="sxs-lookup"><span data-stu-id="877cd-112">To update a global tool that was installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="877cd-113">Para atualizar uma ferramenta global que foi instalada em um local personalizado, use a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="877cd-113">To update a global tool that was installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="877cd-114">Para atualizar uma ferramenta local, omita as opções `--global` e `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="877cd-114">To update a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="877cd-115">**As ferramentas locais estão disponíveis a partir do SDK do .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="877cd-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="877cd-116">Argumentos</span><span class="sxs-lookup"><span data-stu-id="877cd-116">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="877cd-117">Nome/ID do pacote NuGet que contém a ferramenta global .NET Core a ser atualizada.</span><span class="sxs-lookup"><span data-stu-id="877cd-117">Name/ID of the NuGet package that contains the .NET Core global tool to update.</span></span> <span data-ttu-id="877cd-118">Encontre o nome do pacote usando o comando [dotnet tool list](dotnet-tool-list.md).</span><span class="sxs-lookup"><span data-stu-id="877cd-118">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="877cd-119">Opções</span><span class="sxs-lookup"><span data-stu-id="877cd-119">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="877cd-120">Adiciona outra origem do pacote NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="877cd-120">Adds an additional NuGet package source to use during installation.</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="877cd-121">O arquivo de configuração do NuGet (*nuget.config*) a ser usado.</span><span class="sxs-lookup"><span data-stu-id="877cd-121">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="877cd-122">Especifica a [estrutura de destino](../../standard/frameworks.md) para a qual atualizar a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="877cd-122">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

- **`-g|--global`**

  <span data-ttu-id="877cd-123">Especifica que a atualização destina-se a uma ferramenta de todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="877cd-123">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="877cd-124">Não pode ser combinada com a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="877cd-124">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="877cd-125">Omitir `--global` e `--tool-path` especifica que a ferramenta a ser atualizada é uma ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="877cd-125">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="877cd-126">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="877cd-126">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="877cd-127">Especifica o local onde a ferramenta global está instalada.</span><span class="sxs-lookup"><span data-stu-id="877cd-127">Specifies the location where the global tool is installed.</span></span> <span data-ttu-id="877cd-128">PATH pode ser absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="877cd-128">PATH can be absolute or relative.</span></span> <span data-ttu-id="877cd-129">Não pode ser combinada com a opção `--global`.</span><span class="sxs-lookup"><span data-stu-id="877cd-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="877cd-130">Omitir `--global` e `--tool-path` especifica que a ferramenta a ser atualizada é uma ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="877cd-130">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="877cd-131">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="877cd-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="877cd-132">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="877cd-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="877cd-133">Exemplos</span><span class="sxs-lookup"><span data-stu-id="877cd-133">Examples</span></span>

- **`dotnet tool update -g dotnetsay`**

  <span data-ttu-id="877cd-134">Atualiza a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) .</span><span class="sxs-lookup"><span data-stu-id="877cd-134">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="877cd-135">Atualiza a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) localizada em um diretório específico do Windows.</span><span class="sxs-lookup"><span data-stu-id="877cd-135">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Windows directory.</span></span>

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="877cd-136">Atualiza a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) localizada em um diretório específico do linux/MacOS.</span><span class="sxs-lookup"><span data-stu-id="877cd-136">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Linux/macOS directory.</span></span>

- **`dotnet tool update dotnetsay`**

  <span data-ttu-id="877cd-137">Atualiza a ferramenta local [dotnetsay](https://www.nuget.org/packages/dotnetsay/) instalada para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="877cd-137">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool installed for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="877cd-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="877cd-138">See also</span></span>

- [<span data-ttu-id="877cd-139">Ferramentas do .NET Core</span><span class="sxs-lookup"><span data-stu-id="877cd-139">.NET Core tools</span></span>](global-tools.md)
