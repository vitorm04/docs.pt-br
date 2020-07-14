---
title: Comando dotnet tool update
description: O comando dotnet ferramenta de atualização atualiza a ferramenta .NET Core especificada em seu computador.
ms.date: 07/08/2020
ms.openlocfilehash: 7c4bde44ac9964828074baeb1a697ba64ed17887
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226615"
---
# <a name="dotnet-tool-update"></a><span data-ttu-id="6ba5b-103">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="6ba5b-103">dotnet tool update</span></span>

<span data-ttu-id="6ba5b-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="6ba5b-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="6ba5b-105">Nome</span><span class="sxs-lookup"><span data-stu-id="6ba5b-105">Name</span></span>

<span data-ttu-id="6ba5b-106">`dotnet tool update`-Atualiza a [ferramenta .NET Core](global-tools.md) especificada em seu computador.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-106">`dotnet tool update` - Updates the specified [.NET Core tool](global-tools.md) on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6ba5b-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="6ba5b-107">Synopsis</span></span>

```dotnetcli
dotnet tool update <PACKAGE_ID> -g|--global
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [--add-source <SOURCE>] [--disable-parallel]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --tool-path <PATH>
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [--add-source <SOURCE>] [--disable-parallel]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --local
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [--add-source <SOURCE>] [--disable-parallel]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [--tool-manifest <PATH>]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update -h|--help
```

## <a name="description"></a><span data-ttu-id="6ba5b-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="6ba5b-108">Description</span></span>

<span data-ttu-id="6ba5b-109">O `dotnet tool update` comando fornece uma maneira de atualizar as ferramentas do .NET Core em seu computador para a versão estável mais recente do pacote.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-109">The `dotnet tool update` command provides a way for you to update .NET Core tools on your machine to the latest stable version of the package.</span></span> <span data-ttu-id="6ba5b-110">O comando desinstala e reinstala uma ferramenta, atualizando-a efetivamente.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-110">The command uninstalls and reinstalls a tool, effectively updating it.</span></span> <span data-ttu-id="6ba5b-111">Para usar o comando, especifique uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="6ba5b-111">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="6ba5b-112">Para atualizar uma ferramenta global que foi instalada no local padrão, use a `--global` opção</span><span class="sxs-lookup"><span data-stu-id="6ba5b-112">To update a global tool that was installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="6ba5b-113">Para atualizar uma ferramenta global que foi instalada em um local personalizado, use a `--tool-path` opção.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-113">To update a global tool that was installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="6ba5b-114">Para atualizar uma ferramenta local, use a `--local` opção.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-114">To update a local tool, use the `--local` option.</span></span>

<span data-ttu-id="6ba5b-115">**As ferramentas locais estão disponíveis a partir do SDK do .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="6ba5b-115">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="6ba5b-116">Argumentos</span><span class="sxs-lookup"><span data-stu-id="6ba5b-116">Arguments</span></span>

- **`PACKAGE_ID`**

  <span data-ttu-id="6ba5b-117">Nome/ID do pacote NuGet que contém a ferramenta global .NET Core a ser atualizada.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-117">Name/ID of the NuGet package that contains the .NET Core global tool to update.</span></span> <span data-ttu-id="6ba5b-118">Encontre o nome do pacote usando o comando [dotnet tool list](dotnet-tool-list.md).</span><span class="sxs-lookup"><span data-stu-id="6ba5b-118">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="6ba5b-119">Opções</span><span class="sxs-lookup"><span data-stu-id="6ba5b-119">Options</span></span>

- **`--add-source <SOURCE>`**

  <span data-ttu-id="6ba5b-120">Adiciona outra origem do pacote NuGet a ser usada durante a instalação.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-120">Adds an additional NuGet package source to use during installation.</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="6ba5b-121">O arquivo de configuração do NuGet (*nuget.config*) a ser usado.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-121">The NuGet configuration (*nuget.config*) file to use.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="6ba5b-122">Impedir a restauração de vários projetos em paralelo.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-122">Prevent restoring multiple projects in parallel.</span></span>

- **`--framework <FRAMEWORK>`**

  <span data-ttu-id="6ba5b-123">Especifica a [estrutura de destino](../../standard/frameworks.md) para a qual atualizar a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-123">Specifies the [target framework](../../standard/frameworks.md) to update the tool for.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="6ba5b-124">Tratar falhas de origem do pacote como avisos.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-124">Treat package source failures as warnings.</span></span>

- **`--interactive`**

  <span data-ttu-id="6ba5b-125">Permite que o comando pare e aguarde a entrada ou uma ação do usuário (por exemplo, para concluir a autenticação).</span><span class="sxs-lookup"><span data-stu-id="6ba5b-125">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span>

- **`--local`**

  <span data-ttu-id="6ba5b-126">Atualize a ferramenta e o manifesto da ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-126">Update the tool and the local tool manifest.</span></span> <span data-ttu-id="6ba5b-127">Não pode ser combinada com a opção `--global`.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-127">Can't be combined with the `--global` option.</span></span>

- **`--no-cache`**

  <span data-ttu-id="6ba5b-128">Não armazene em cache pacotes e solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-128">Do not cache packages and HTTP requests.</span></span>

- **`--tool-manifest <PATH>`**

  <span data-ttu-id="6ba5b-129">Caminho para o arquivo de manifesto.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-129">Path to the manifest file.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="6ba5b-130">Especifica o local onde a ferramenta global está instalada.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-130">Specifies the location where the global tool is installed.</span></span> <span data-ttu-id="6ba5b-131">PATH pode ser absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-131">PATH can be absolute or relative.</span></span> <span data-ttu-id="6ba5b-132">Não pode ser combinada com a opção `--global`.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-132">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="6ba5b-133">Omitir ambos `--global` e `--tool-path` especifica que a ferramenta a ser atualizada é uma ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-133">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`--version <VERSION>`**

  <span data-ttu-id="6ba5b-134">O intervalo de versão do pacote de ferramentas para o qual atualizar.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-134">The version range of the tool package to update to.</span></span> <span data-ttu-id="6ba5b-135">Isso não pode ser usado para fazer downgrade de versões. primeiro, você deve obter `uninstall` versões mais recentes.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-135">This cannot be used to downgrade versions, you must `uninstall` newer versions first.</span></span>

- **`-g|--global`**

  <span data-ttu-id="6ba5b-136">Especifica que a atualização destina-se a uma ferramenta de todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-136">Specifies that the update is for a user-wide tool.</span></span> <span data-ttu-id="6ba5b-137">Não pode ser combinada com a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-137">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="6ba5b-138">Omitir ambos `--global` e `--tool-path` especifica que a ferramenta a ser atualizada é uma ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-138">Omitting both `--global` and `--tool-path` specifies that the tool to be updated is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="6ba5b-139">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-139">Prints out a short help for the command.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="6ba5b-140">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-140">Sets the verbosity level of the command.</span></span> <span data-ttu-id="6ba5b-141">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-141">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="6ba5b-142">Exemplos</span><span class="sxs-lookup"><span data-stu-id="6ba5b-142">Examples</span></span>

- **`dotnet tool update -g dotnetsay`**

  <span data-ttu-id="6ba5b-143">Atualiza a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) .</span><span class="sxs-lookup"><span data-stu-id="6ba5b-143">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="6ba5b-144">Atualiza a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) localizada em um diretório específico do Windows.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-144">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Windows directory.</span></span>

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="6ba5b-145">Atualiza a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) localizada em um diretório específico do linux/MacOS.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-145">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool located in a specific Linux/macOS directory.</span></span>

- **`dotnet tool update dotnetsay`**

  <span data-ttu-id="6ba5b-146">Atualiza a ferramenta local [dotnetsay](https://www.nuget.org/packages/dotnetsay/) instalada para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-146">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool installed for the current directory.</span></span>

- **`dotnet tool update -g dotnetsay --version 2.0.*`**

  <span data-ttu-id="6ba5b-147">Atualiza a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) para a versão mais recente do patch, com uma versão principal do `2` e uma versão secundária do `0` .</span><span class="sxs-lookup"><span data-stu-id="6ba5b-147">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool to the latest patch version, with a major version of `2`, and a minor version of `0`.</span></span>

- **`dotnet tool update -g dotnetsay --version (2.0.*,2.1.4)`**

  <span data-ttu-id="6ba5b-148">Atualiza a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) para a versão mais baixa dentro do intervalo especificado `(> 2.0.0 && < 2.1.4)` , a versão `2.1.0` deve ser instalada.</span><span class="sxs-lookup"><span data-stu-id="6ba5b-148">Updates the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool to the lowest version within the specified range `(> 2.0.0 && < 2.1.4)`, version `2.1.0` would be installed.</span></span> <span data-ttu-id="6ba5b-149">Para obter mais informações sobre intervalos de controle de versão semântico, consulte [intervalos de versão de empacotamento NuGet](/nuget/concepts/package-versioning#version-ranges).</span><span class="sxs-lookup"><span data-stu-id="6ba5b-149">For more information on semantic versioning ranges, see [NuGet packaging version ranges](/nuget/concepts/package-versioning#version-ranges).</span></span>

## <a name="see-also"></a><span data-ttu-id="6ba5b-150">Confira também</span><span class="sxs-lookup"><span data-stu-id="6ba5b-150">See also</span></span>

- [<span data-ttu-id="6ba5b-151">Ferramentas do .NET Core</span><span class="sxs-lookup"><span data-stu-id="6ba5b-151">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="6ba5b-152">Controle de versão semântico</span><span class="sxs-lookup"><span data-stu-id="6ba5b-152">Semantic versioning</span></span>](https://semver.org)
- [<span data-ttu-id="6ba5b-153">Tutorial: instalar e usar uma ferramenta global do .NET Core usando o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="6ba5b-153">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="6ba5b-154">Tutorial: instalar e usar uma ferramenta local do .NET Core usando o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="6ba5b-154">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
