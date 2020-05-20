---
title: Comando dotnet tool install
description: O comando dotnet ferramenta de instalação instala a ferramenta .NET Core especificada em seu computador.
ms.date: 02/14/2020
ms.openlocfilehash: 067f90124833da537370a36934ff212aba7577f3
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702820"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="fa633-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="fa633-103">dotnet tool install</span></span>

<span data-ttu-id="fa633-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="fa633-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="fa633-105">Name</span><span class="sxs-lookup"><span data-stu-id="fa633-105">Name</span></span>

<span data-ttu-id="fa633-106">`dotnet tool install`-Instala a [ferramenta .NET Core](global-tools.md) especificada em seu computador.</span><span class="sxs-lookup"><span data-stu-id="fa633-106">`dotnet tool install` - Installs the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="fa633-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="fa633-107">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> -g|--global
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME> --tool-path <PATH>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install <PACKAGE_NAME>
    [--add-source <SOURCE>] [--configfile <FILE>]
    [--framework <FRAMEWORK>] [-v|--verbosity <LEVEL>]
    [--version <VERSION_NUMBER>]

dotnet tool install -h|--help
```

## <a name="description"></a><span data-ttu-id="fa633-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa633-108">Description</span></span>

<span data-ttu-id="fa633-109">O `dotnet tool install` comando fornece uma maneira de instalar as ferramentas do .NET Core em seu computador.</span><span class="sxs-lookup"><span data-stu-id="fa633-109">The `dotnet tool install` command provides a way for you to install .NET Core tools on your machine.</span></span> <span data-ttu-id="fa633-110">Para usar o comando, especifique uma das seguintes opções de instalação:</span><span class="sxs-lookup"><span data-stu-id="fa633-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="fa633-111">Para instalar uma ferramenta global no local padrão, use a `--global` opção.</span><span class="sxs-lookup"><span data-stu-id="fa633-111">To install a global tool in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="fa633-112">Para instalar uma ferramenta global em um local personalizado, use a `--tool-path` opção.</span><span class="sxs-lookup"><span data-stu-id="fa633-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="fa633-113">Para instalar uma ferramenta local, omita as `--global` `--tool-path` Opções e.</span><span class="sxs-lookup"><span data-stu-id="fa633-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="fa633-114">**As ferramentas locais estão disponíveis a partir do SDK do .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="fa633-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="fa633-115">As ferramentas globais são instaladas nos diretórios a seguir por padrão, quando você especifica a `-g` `--global` opção ou:</span><span class="sxs-lookup"><span data-stu-id="fa633-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="fa633-116">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="fa633-116">OS</span></span>          | <span data-ttu-id="fa633-117">Caminho</span><span class="sxs-lookup"><span data-stu-id="fa633-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="fa633-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="fa633-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="fa633-119">Windows</span><span class="sxs-lookup"><span data-stu-id="fa633-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="fa633-120">As ferramentas locais são adicionadas a um arquivo *dotnet-Tools. JSON* em um diretório *. config* no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="fa633-120">Local tools are added to a *dotnet-tools.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="fa633-121">Se um arquivo de manifesto ainda não existir, crie-o executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="fa633-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="fa633-122">Para obter mais informações, consulte [instalar uma ferramenta local](global-tools.md#install-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="fa633-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="fa633-123">Argumentos</span><span class="sxs-lookup"><span data-stu-id="fa633-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="fa633-124">Nome/ID do pacote NuGet que contém a ferramenta .NET Core a ser instalada.</span><span class="sxs-lookup"><span data-stu-id="fa633-124">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="fa633-125">Opções</span><span class="sxs-lookup"><span data-stu-id="fa633-125">Options</span></span>

- **`add-source <SOURCE>`**

  <span data-ttu-id="fa633-126">Adiciona outra origem do pacote NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="fa633-126">Adds an additional NuGet package source to use during installation.</span></span>

- **`configfile <FILE>`**

  <span data-ttu-id="fa633-127">O arquivo de configuração do NuGet (*nuget.config*) a ser usado.</span><span class="sxs-lookup"><span data-stu-id="fa633-127">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`framework <FRAMEWORK>`**

  <span data-ttu-id="fa633-128">Especifica a [estrutura de destino](../../standard/frameworks.md) para a qual instalar a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="fa633-128">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="fa633-129">Por padrão, o SDK do .NET Core tenta escolher a estrutura de destino mais apropriada.</span><span class="sxs-lookup"><span data-stu-id="fa633-129">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="fa633-130">Especifica que a instalação é de todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="fa633-130">Specifies that the installation is user wide.</span></span> <span data-ttu-id="fa633-131">Não pode ser combinada com a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="fa633-131">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="fa633-132">Omitir ambos `--global` e `--tool-path` especificar uma instalação de ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="fa633-132">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-h|--help`**

  <span data-ttu-id="fa633-133">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="fa633-133">Prints out a short help for the command.</span></span>

- **`tool-path <PATH>`**

  <span data-ttu-id="fa633-134">Especifica o local do qual a Ferramenta Global será instalada.</span><span class="sxs-lookup"><span data-stu-id="fa633-134">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="fa633-135">PATH pode ser absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="fa633-135">PATH can be absolute or relative.</span></span> <span data-ttu-id="fa633-136">Se PATH não existir, o comando tentará criá-lo.</span><span class="sxs-lookup"><span data-stu-id="fa633-136">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="fa633-137">Omitir ambos `--global` e `--tool-path` especificar uma instalação de ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="fa633-137">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="fa633-138">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="fa633-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="fa633-139">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="fa633-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="fa633-140">A versão da ferramenta a ser instalada.</span><span class="sxs-lookup"><span data-stu-id="fa633-140">The version of the tool to install.</span></span> <span data-ttu-id="fa633-141">Por padrão, a última versão estável do pacote é instalada.</span><span class="sxs-lookup"><span data-stu-id="fa633-141">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="fa633-142">Use essa opção para instalar a versão prévia ou versões mais antigas da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="fa633-142">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="fa633-143">Exemplos</span><span class="sxs-lookup"><span data-stu-id="fa633-143">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="fa633-144">Instala o [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta global no local padrão.</span><span class="sxs-lookup"><span data-stu-id="fa633-144">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="fa633-145">Instala o [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta global em um diretório específico do Windows.</span><span class="sxs-lookup"><span data-stu-id="fa633-145">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="fa633-146">Instala o [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta global em um diretório específico do linux/MacOS.</span><span class="sxs-lookup"><span data-stu-id="fa633-146">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="fa633-147">Instala a versão 2.0.0 do [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta global.</span><span class="sxs-lookup"><span data-stu-id="fa633-147">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="fa633-148">Instala o [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta local para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="fa633-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="fa633-149">Veja também</span><span class="sxs-lookup"><span data-stu-id="fa633-149">See also</span></span>

- [<span data-ttu-id="fa633-150">Ferramentas do .NET Core</span><span class="sxs-lookup"><span data-stu-id="fa633-150">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="fa633-151">Tutorial: instalar e usar uma ferramenta global do .NET Core usando o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="fa633-151">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="fa633-152">Tutorial: instalar e usar uma ferramenta local do .NET Core usando o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="fa633-152">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
