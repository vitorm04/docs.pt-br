---
title: Comando dotnet tool install
description: O comando dotnet tool install instala a ferramenta .NET Core especificada na máquina.
ms.date: 02/14/2020
ms.openlocfilehash: 1e142773d1f981a8dc3b552d5a23d2864cdd82c0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146457"
---
# <a name="dotnet-tool-install"></a><span data-ttu-id="b6f94-103">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="b6f94-103">dotnet tool install</span></span>

<span data-ttu-id="b6f94-104">**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="b6f94-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="b6f94-105">Nome</span><span class="sxs-lookup"><span data-stu-id="b6f94-105">Name</span></span>

<span data-ttu-id="b6f94-106">`dotnet tool install`- Instala a [ferramenta .NET Core](global-tools.md) especificada na sua máquina.</span><span class="sxs-lookup"><span data-stu-id="b6f94-106">`dotnet tool install` - Installs the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b6f94-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="b6f94-107">Synopsis</span></span>

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global>
    [--add-source] [--configfile] [--framework]
    [-v|--verbosity] [--version]

dotnet tool install <PACKAGE_NAME> <--tool-path>
    [--add-source] [--configfile] [--framework]
    [-v|--verbosity] [--version]

dotnet tool install <PACKAGE_NAME>
    [--add-source] [--configfile] [--framework]
    [-v|--verbosity] [--version]

dotnet tool install <-h|--help>
```

## <a name="description"></a><span data-ttu-id="b6f94-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="b6f94-108">Description</span></span>

<span data-ttu-id="b6f94-109">O `dotnet tool install` comando fornece uma maneira de você instalar ferramentas .NET Core em sua máquina.</span><span class="sxs-lookup"><span data-stu-id="b6f94-109">The `dotnet tool install` command provides a way for you to install .NET Core tools on your machine.</span></span> <span data-ttu-id="b6f94-110">Para usar o comando, você especifica uma das seguintes opções de instalação:</span><span class="sxs-lookup"><span data-stu-id="b6f94-110">To use the command, you specify one of the following installation options:</span></span>

* <span data-ttu-id="b6f94-111">Para instalar uma ferramenta global no `--global` local padrão, use a opção.</span><span class="sxs-lookup"><span data-stu-id="b6f94-111">To install a global tool in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="b6f94-112">Para instalar uma ferramenta global em `--tool-path` um local personalizado, use a opção.</span><span class="sxs-lookup"><span data-stu-id="b6f94-112">To install a global tool in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="b6f94-113">Para instalar uma ferramenta local, `--global` `--tool-path` omita as opções e opções.</span><span class="sxs-lookup"><span data-stu-id="b6f94-113">To install a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="b6f94-114">**As ferramentas locais estão disponíveis a partir do .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="b6f94-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

<span data-ttu-id="b6f94-115">As ferramentas globais são instaladas nos seguintes `-g` `--global` diretórios por padrão quando você especifica a opção ou opção:</span><span class="sxs-lookup"><span data-stu-id="b6f94-115">Global tools are installed in the following directories by default when you specify the `-g` or `--global` option:</span></span>

| <span data-ttu-id="b6f94-116">Sistema operacional</span><span class="sxs-lookup"><span data-stu-id="b6f94-116">OS</span></span>          | <span data-ttu-id="b6f94-117">Caminho</span><span class="sxs-lookup"><span data-stu-id="b6f94-117">Path</span></span>                          |
|-------------|-------------------------------|
| <span data-ttu-id="b6f94-118">Linux/macOS</span><span class="sxs-lookup"><span data-stu-id="b6f94-118">Linux/macOS</span></span> | `$HOME/.dotnet/tools`         |
| <span data-ttu-id="b6f94-119">Windows</span><span class="sxs-lookup"><span data-stu-id="b6f94-119">Windows</span></span>     | `%USERPROFILE%\.dotnet\tools` |

<span data-ttu-id="b6f94-120">As ferramentas locais são adicionadas a um arquivo *tool-manifest.json* em um diretório *.config* o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="b6f94-120">Local tools are added to a *tool-manifest.json* file in a *.config* directory under the current directory.</span></span> <span data-ttu-id="b6f94-121">Se um arquivo manifesto ainda não existir, crie-o executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="b6f94-121">If a manifest file doesn't exist yet, create it by running the following command:</span></span>

```dotnetcli
dotnet new tool-manifest
```

<span data-ttu-id="b6f94-122">Para obter mais informações, consulte [Instalar uma ferramenta local](global-tools.md#install-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="b6f94-122">For more information, see [Install a local tool](global-tools.md#install-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="b6f94-123">Argumentos</span><span class="sxs-lookup"><span data-stu-id="b6f94-123">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="b6f94-124">Nome/ID do pacote NuGet que contém a ferramenta .NET Core a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="b6f94-124">Name/ID of the NuGet package that contains the .NET Core tool to install.</span></span>

## <a name="options"></a><span data-ttu-id="b6f94-125">Opções</span><span class="sxs-lookup"><span data-stu-id="b6f94-125">Options</span></span>

- **`add-source <SOURCE>`**

  <span data-ttu-id="b6f94-126">Adiciona outra origem do pacote NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="b6f94-126">Adds an additional NuGet package source to use during installation.</span></span>

- **`configfile <FILE>`**

  <span data-ttu-id="b6f94-127">O arquivo de configuração do NuGet (*nuget.config*) a ser usado.</span><span class="sxs-lookup"><span data-stu-id="b6f94-127">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`framework <FRAMEWORK>`**

  <span data-ttu-id="b6f94-128">Especifica a [estrutura de destino](../../standard/frameworks.md) para a qual instalar a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="b6f94-128">Specifies the [target framework](../../standard/frameworks.md) to install the tool for.</span></span> <span data-ttu-id="b6f94-129">Por padrão, o SDK do .NET Core tenta escolher a estrutura de destino mais apropriada.</span><span class="sxs-lookup"><span data-stu-id="b6f94-129">By default, the .NET Core SDK tries to choose the most appropriate target framework.</span></span>

- **`-g|--global`**

  <span data-ttu-id="b6f94-130">Especifica que a instalação é de todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="b6f94-130">Specifies that the installation is user wide.</span></span> <span data-ttu-id="b6f94-131">Não pode ser combinada com a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="b6f94-131">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="b6f94-132">Omitir ambos `--global` e `--tool-path` especificar uma instalação de ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="b6f94-132">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-h|--help`**

  <span data-ttu-id="b6f94-133">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="b6f94-133">Prints out a short help for the command.</span></span>

- **`tool-path <PATH>`**

  <span data-ttu-id="b6f94-134">Especifica o local do qual a Ferramenta Global será instalada.</span><span class="sxs-lookup"><span data-stu-id="b6f94-134">Specifies the location where to install the Global Tool.</span></span> <span data-ttu-id="b6f94-135">PATH pode ser absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="b6f94-135">PATH can be absolute or relative.</span></span> <span data-ttu-id="b6f94-136">Se PATH não existir, o comando tentará criá-lo.</span><span class="sxs-lookup"><span data-stu-id="b6f94-136">If PATH doesn't exist, the command tries to create it.</span></span> <span data-ttu-id="b6f94-137">Omitir ambos `--global` e `--tool-path` especificar uma instalação de ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="b6f94-137">Omitting both `--global` and `--tool-path` specifies a local tool installation.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="b6f94-138">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="b6f94-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b6f94-139">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b6f94-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version <VERSION_NUMBER>`**

  <span data-ttu-id="b6f94-140">A versão da ferramenta a ser instalada.</span><span class="sxs-lookup"><span data-stu-id="b6f94-140">The version of the tool to install.</span></span> <span data-ttu-id="b6f94-141">Por padrão, a última versão estável do pacote é instalada.</span><span class="sxs-lookup"><span data-stu-id="b6f94-141">By default, the latest stable package version is installed.</span></span> <span data-ttu-id="b6f94-142">Use essa opção para instalar a versão prévia ou versões mais antigas da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="b6f94-142">Use this option to install preview or older versions of the tool.</span></span>

## <a name="examples"></a><span data-ttu-id="b6f94-143">Exemplos</span><span class="sxs-lookup"><span data-stu-id="b6f94-143">Examples</span></span>

- **`dotnet tool install -g dotnetsay`**

  <span data-ttu-id="b6f94-144">Instala [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta global no local padrão.</span><span class="sxs-lookup"><span data-stu-id="b6f94-144">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in the default location.</span></span>

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="b6f94-145">Instala [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta global em um diretório específico do Windows.</span><span class="sxs-lookup"><span data-stu-id="b6f94-145">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Windows directory.</span></span>

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="b6f94-146">Instala [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta global em um diretório específico do Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="b6f94-146">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool in a specific Linux/macOS directory.</span></span>

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  <span data-ttu-id="b6f94-147">Instala a versão 2.0.0 do [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta global.</span><span class="sxs-lookup"><span data-stu-id="b6f94-147">Installs version 2.0.0 of [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a global tool.</span></span>

- **`dotnet tool install dotnetsay`**

  <span data-ttu-id="b6f94-148">Instala [dotnetsay](https://www.nuget.org/packages/dotnetsay/) como uma ferramenta local para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="b6f94-148">Installs [dotnetsay](https://www.nuget.org/packages/dotnetsay/) as a local tool for the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="b6f94-149">Confira também</span><span class="sxs-lookup"><span data-stu-id="b6f94-149">See also</span></span>

- [<span data-ttu-id="b6f94-150">.NET Core ferramentas</span><span class="sxs-lookup"><span data-stu-id="b6f94-150">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="b6f94-151">Tutorial: Instale e use uma ferramenta global .NET Core usando o .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="b6f94-151">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="b6f94-152">Tutorial: Instale e use uma ferramenta local .NET Core usando o .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="b6f94-152">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
