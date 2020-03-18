---
title: Comando dotnet tool update
description: O comando dotnet tool update update atualiza a ferramenta .NET Core especificada em sua máquina.
ms.date: 02/14/2020
ms.openlocfilehash: 497b052a8b9cfa9dca8d80316075fe7565d6b35a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847814"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="f15ec-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="f15ec-103">dotnet tool update</span></span>

<span data-ttu-id="f15ec-104">**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="f15ec-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f15ec-105">Nome</span><span class="sxs-lookup"><span data-stu-id="f15ec-105">Name</span></span>

<span data-ttu-id="f15ec-106">`dotnet tool update`- Atualiza a [ferramenta .NET Core](global-tools.md) especificada em sua máquina.</span><span class="sxs-lookup"><span data-stu-id="f15ec-106">`dotnet tool update` - Updates the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f15ec-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="f15ec-107">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global>
    [--configfile] [--framework] [-v|--verbosity]
    [--add-source]

dotnet tool update <PACKAGE_NAME> <--tool-path>
    [--configfile] [--framework] [-v|--verbosity]
    [--add-source]

dotnet tool update <PACKAGE_NAME>
    [--configfile] [--framework] [-v|--verbosity]
    [--add-source]

dotnet tool update <-h|--help>
```

## <a name="description"></a><span data-ttu-id="f15ec-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="f15ec-108">Description</span></span>

<span data-ttu-id="f15ec-109">O `dotnet tool update` comando fornece uma maneira de atualizar as ferramentas .NET Core em sua máquina para a versão estável mais recente do pacote.</span><span class="sxs-lookup"><span data-stu-id="f15ec-109">The `dotnet tool update` command provides a way for you to update .NET Core tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="f15ec-110">O comando desinstala e reinstala uma ferramenta, atualizando-a efetivamente.</span><span class="sxs-lookup"><span data-stu-id="f15ec-110">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="f15ec-111">Para usar o comando, você especifica uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="f15ec-111">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="f15ec-112">Para atualizar uma ferramenta global que foi instalada `--global` no local padrão, use a opção</span><span class="sxs-lookup"><span data-stu-id="f15ec-112">To update a global tool that was installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="f15ec-113">Para atualizar uma ferramenta global que foi instalada `--tool-path` em um local personalizado, use a opção.</span><span class="sxs-lookup"><span data-stu-id="f15ec-113">To update a global tool that was installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="f15ec-114">Para atualizar uma ferramenta local, `--global` `--tool-path` omita as opções e opções.</span><span class="sxs-lookup"><span data-stu-id="f15ec-114">To update a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="f15ec-115">**As ferramentas locais estão disponíveis a partir do .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="f15ec-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="f15ec-116">Argumentos</span><span class="sxs-lookup"><span data-stu-id="f15ec-116">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="f15ec-117">Nome/ID do pacote NuGet que contém a ferramenta global .NET Core para atualizar.</span><span class="sxs-lookup"><span data-stu-id="f15ec-117">Name/ID of the NuGet package that contains the .NET Core global tool to update.</span></span> <span data-ttu-id="f15ec-118">Encontre o nome do pacote usando o comando [dotnet tool list](dotnet-tool-list.md).</span><span class="sxs-lookup"><span data-stu-id="f15ec-118">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="f15ec-119">Opções</span><span class="sxs-lookup"><span data-stu-id="f15ec-119">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="f15ec-120">Adiciona outra origem do pacote NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="f15ec-120">Adds an additional NuGet package source to use during installation.</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="f15ec-121">O arquivo de configuração do NuGet (*nuget.config*) a ser usado.</span><span class="sxs-lookup"><span data-stu-id="f15ec-121">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="f15ec-122">Especifica a [estrutura de destino](../../standard/frameworks.md) para a qual atualizar a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="f15ec-122">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

- **`-g|--global`**

  <span data-ttu-id="f15ec-123">Especifica que a atualização destina-se a uma ferramenta de todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="f15ec-123">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="f15ec-124">Não pode ser combinada com a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="f15ec-124">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="f15ec-125">Omitir ambos `--global` e `--tool-path` especificar que a ferramenta a ser atualizada é uma ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="f15ec-125">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f15ec-126">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="f15ec-126">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="f15ec-127">Especifica o local onde a ferramenta global está instalada.</span><span class="sxs-lookup"><span data-stu-id="f15ec-127">Specifies the location where the global tool is installed.</span></span> <span data-ttu-id="f15ec-128">PATH pode ser absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="f15ec-128">PATH can be absolute or relative.</span></span> <span data-ttu-id="f15ec-129">Não pode ser combinada com a opção `--global`.</span><span class="sxs-lookup"><span data-stu-id="f15ec-129">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="f15ec-130">Omitir ambos `--global` e `--tool-path` especificar que a ferramenta a ser atualizada é uma ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="f15ec-130">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="f15ec-131">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="f15ec-131">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f15ec-132">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="f15ec-132">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="f15ec-133">Exemplos</span><span class="sxs-lookup"><span data-stu-id="f15ec-133">Examples</span></span>

- **`dotnet tool update -g dotnetsay`**

  <span data-ttu-id="f15ec-134">Atualiza a ferramenta global [dotnetsay.](https://www.nuget.org/packages/dotnetsay/)</span><span class="sxs-lookup"><span data-stu-id="f15ec-134">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="f15ec-135">Atualiza a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) localizada em um diretório específico do Windows.</span><span class="sxs-lookup"><span data-stu-id="f15ec-135">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Windows directory.</span></span>

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="f15ec-136">Atualiza a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) localizada em um diretório específico do Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="f15ec-136">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Linux/macOS directory.</span></span>

- **`dotnet tool update dotnetsay`**

  <span data-ttu-id="f15ec-137">Atualiza a ferramenta local [dotnetsay](https://www.nuget.org/packages/dotnetsay/) instalada para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="f15ec-137">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool installed for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="f15ec-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="f15ec-138">See also</span></span>

- [<span data-ttu-id="f15ec-139">.NET Core ferramentas</span><span class="sxs-lookup"><span data-stu-id="f15ec-139">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="f15ec-140">Tutorial: Instale e use uma ferramenta global .NET Core usando o .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="f15ec-140">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="f15ec-141">Tutorial: Instale e use uma ferramenta local .NET Core usando o .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="f15ec-141">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
