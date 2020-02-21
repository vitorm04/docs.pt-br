---
title: Comando dotnet tool install
description: O comando dotnet ferramenta de instalação instala a ferramenta .NET Core especificada em seu computador.
ms.date: 02/14/2020
ms.openlocfilehash: 2705defe9b77009ca1411da28dd86d144ccc19e6
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543463"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="bf7d8-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="bf7d8-103">dotnet tool install</span></span>

<span data-ttu-id="bf7d8-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="bf7d8-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="bf7d8-105">Nome</span><span class="sxs-lookup"><span data-stu-id="bf7d8-105">Name</span></span>

<span data-ttu-id="bf7d8-106">`dotnet tool install`-instala a [ferramenta .NET Core](global-tools.md) especificada em seu computador.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-106">`dotnet tool install` - Installs the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bf7d8-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="bf7d8-107">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a><span data-ttu-id="bf7d8-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="bf7d8-108">Description</span></span>

<span data-ttu-id="bf7d8-109">O comando `dotnet tool install` fornece uma maneira de instalar as ferramentas do .NET Core em seu computador.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-109">The `dotnet tool install` command provides a way for you to install .NET Core tools on your machine.</span></span> <span data-ttu-id="bf7d8-110">Para usar o comando, especifique uma das seguintes opções de instalação:</span><span class="sxs-lookup"><span data-stu-id="bf7d8-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="bf7d8-111">Para instalar uma ferramenta global no local padrão, use a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-111">To install a global tool in the default location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="bf7d8-112">Para instalar uma ferramenta global em um local personalizado, use a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="bf7d8-113">Para instalar uma ferramenta local, omita as opções `--global` e `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="bf7d8-114">**As ferramentas locais estão disponíveis a partir do SDK do .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="bf7d8-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="bf7d8-115">As ferramentas globais são instaladas nos diretórios a seguir por padrão, quando você especifica a opção `-g` ou `--global`:</span><span class="sxs-lookup"><span data-stu-id="bf7d8-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="bf7d8-116">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="bf7d8-116">OS</span></span>          | <span data-ttu-id="bf7d8-117">Caminho</span><span class="sxs-lookup"><span data-stu-id="bf7d8-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="bf7d8-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="bf7d8-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="bf7d8-119">Windows</span><span class="sxs-lookup"><span data-stu-id="bf7d8-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="bf7d8-120">As ferramentas locais são adicionadas a um arquivo de *ferramenta-manifest. JSON* em um diretório *. config* no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-120">Local tools are added to a *tool-manifest.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="bf7d8-121">Se um arquivo de manifesto ainda não existir, crie-o executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="bf7d8-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="bf7d8-122">Para obter mais informações, consulte [instalar uma ferramenta local](global-tools.md#install-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="bf7d8-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="bf7d8-123">Argumentos</span><span class="sxs-lookup"><span data-stu-id="bf7d8-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="bf7d8-124">Nome/ID do pacote NuGet que contém a ferramenta .NET Core a ser instalada.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-124">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="bf7d8-125">Opções</span><span class="sxs-lookup"><span data-stu-id="bf7d8-125">Options</span></span>

- **`add-source <SOURCE>`**

  <span data-ttu-id="bf7d8-126">Adiciona outra origem do pacote NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-126">Adds an additional NuGet package source to use during installation.</span></span>

- **`configfile <FILE>`**

  <span data-ttu-id="bf7d8-127">O arquivo de configuração do NuGet (*nuget.config*) a ser usado.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-127">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`framework <FRAMEWORK>`**

  <span data-ttu-id="bf7d8-128">Especifica a [estrutura de destino](../../standard/frameworks.md) para a qual instalar a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-128">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="bf7d8-129">Por padrão, o SDK do .NET Core tenta escolher a estrutura de destino mais apropriada.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-129">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="bf7d8-130">Especifica que a instalação é de todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-130">Specifies that the installation is user wide.</span></span> <span data-ttu-id="bf7d8-131">Não pode ser combinada com a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-131">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="bf7d8-132">Omitir `--global` e `--tool-path` especifica uma instalação de ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-132">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span> 

- **`-h|--help`**

  <span data-ttu-id="bf7d8-133">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-133">Prints out a short help for the command.</span></span>

- **`tool-path <PATH>`**

  <span data-ttu-id="bf7d8-134">Especifica o local do qual a Ferramenta Global será instalada.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-134">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="bf7d8-135">PATH pode ser absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-135">PATH can be absolute or relative.</span></span> <span data-ttu-id="bf7d8-136">Se PATH não existir, o comando tentará criá-lo.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-136">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="bf7d8-137">Omitir `--global` e `--tool-path` especifica uma instalação de ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-137">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span> 

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="bf7d8-138">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="bf7d8-139">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="bf7d8-140">A versão da ferramenta a ser instalada.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-140">The version of the tool to install.</span></span> <span data-ttu-id="bf7d8-141">Por padrão, a última versão estável do pacote é instalada.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-141">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="bf7d8-142">Use essa opção para instalar a versão prévia ou versões mais antigas da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-142">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="bf7d8-143">Exemplos</span><span class="sxs-lookup"><span data-stu-id="bf7d8-143">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="bf7d8-144">Instala o [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta global no local padrão.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-144">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="bf7d8-145">Instala o [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta global em um diretório específico do Windows.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-145">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="bf7d8-146">Instala o [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta global em um diretório específico do linux/MacOS.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-146">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="bf7d8-147">Instala a versão 2.0.0 do [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta global.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-147">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="bf7d8-148">Instala o [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta local para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="bf7d8-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="bf7d8-149">Confira também</span><span class="sxs-lookup"><span data-stu-id="bf7d8-149">See also</span></span>

- [<span data-ttu-id="bf7d8-150">Ferramentas do .NET Core</span><span class="sxs-lookup"><span data-stu-id="bf7d8-150">.NET Core tools</span></span>](global-tools.md)
