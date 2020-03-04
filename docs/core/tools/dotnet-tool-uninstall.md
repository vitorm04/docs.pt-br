---
title: Comando dotnet tool uninstall
description: O comando dotnet ferramenta de desinstalação desinstala a ferramenta .NET Core especificada do seu computador.
ms.date: 02/14/2020
ms.openlocfilehash: 7a15c169c73cf5a743e0fa6f47645d6bccedbde3
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157039"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="bd604-103">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="bd604-103">dotnet tool uninstall</span></span>

<span data-ttu-id="bd604-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="bd604-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="bd604-105">Nome</span><span class="sxs-lookup"><span data-stu-id="bd604-105">Name</span></span>

<span data-ttu-id="bd604-106">`dotnet tool uninstall`-desinstala a [ferramenta .NET Core](global-tools.md) especificada do seu computador.</span><span class="sxs-lookup"><span data-stu-id="bd604-106">`dotnet tool uninstall` - Uninstalls the specified [.NET Core tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bd604-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="bd604-107">Synopsis</span></span>

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <PACKAGE_NAME>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a><span data-ttu-id="bd604-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="bd604-108">Description</span></span>

<span data-ttu-id="bd604-109">O comando `dotnet tool uninstall` fornece uma maneira de desinstalar as ferramentas do .NET Core do seu computador.</span><span class="sxs-lookup"><span data-stu-id="bd604-109">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core tools from your machine.</span></span> <span data-ttu-id="bd604-110">Para usar o comando, especifique uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="bd604-110">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="bd604-111">Para desinstalar uma ferramenta global que foi instalada no local padrão, use a opção `--global`.</span><span class="sxs-lookup"><span data-stu-id="bd604-111">To uninstall a global tool that was installed in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="bd604-112">Para desinstalar uma ferramenta global que foi instalada em um local personalizado, use a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="bd604-112">To uninstall a global tool that was installed in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="bd604-113">Para desinstalar uma ferramenta local, omita as opções `--global` e `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="bd604-113">To uninstall a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="bd604-114">**As ferramentas locais estão disponíveis a partir do SDK do .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="bd604-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="bd604-115">Argumentos</span><span class="sxs-lookup"><span data-stu-id="bd604-115">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="bd604-116">Nome/ID do pacote NuGet que contém a ferramenta .NET Core a ser desinstalada.</span><span class="sxs-lookup"><span data-stu-id="bd604-116">Name/ID of the NuGet package that contains the .NET Core tool to uninstall.</span></span> <span data-ttu-id="bd604-117">Encontre o nome do pacote usando o comando [dotnet tool list](dotnet-tool-list.md).</span><span class="sxs-lookup"><span data-stu-id="bd604-117">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="bd604-118">Opções</span><span class="sxs-lookup"><span data-stu-id="bd604-118">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="bd604-119">Especifica que a ferramenta a ser removida pertence a uma instalação de todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="bd604-119">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="bd604-120">Não pode ser combinada com a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="bd604-120">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="bd604-121">Omitir `--global` e `--tool-path` especifica que a ferramenta a ser removida é uma ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="bd604-121">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="bd604-122">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="bd604-122">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="bd604-123">Especifica o local onde a ferramenta será desinstalada.</span><span class="sxs-lookup"><span data-stu-id="bd604-123">Specifies the location where to uninstall the tool.</span></span> <span data-ttu-id="bd604-124">PATH pode ser absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="bd604-124">PATH can be absolute or relative.</span></span> <span data-ttu-id="bd604-125">Não pode ser combinada com a opção `--global`.</span><span class="sxs-lookup"><span data-stu-id="bd604-125">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="bd604-126">Omitir `--global` e `--tool-path` especifica que a ferramenta a ser removida é uma ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="bd604-126">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

## <a name="examples"></a><span data-ttu-id="bd604-127">Exemplos</span><span class="sxs-lookup"><span data-stu-id="bd604-127">Examples</span></span>

- **`dotnet tool uninstall -g dotnetsay`**

  <span data-ttu-id="bd604-128">Desinstala a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) .</span><span class="sxs-lookup"><span data-stu-id="bd604-128">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="bd604-129">Desinstala a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) de um diretório específico do Windows.</span><span class="sxs-lookup"><span data-stu-id="bd604-129">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Windows directory.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="bd604-130">Desinstala a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) de um diretório específico do linux/MacOS.</span><span class="sxs-lookup"><span data-stu-id="bd604-130">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Linux/macOS directory.</span></span>

- **`dotnet tool uninstall dotnetsay`**

  <span data-ttu-id="bd604-131">Desinstala a ferramenta local [dotnetsay](https://www.nuget.org/packages/dotnetsay/) do diretório atual.</span><span class="sxs-lookup"><span data-stu-id="bd604-131">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool from the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="bd604-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="bd604-132">See also</span></span>

- [<span data-ttu-id="bd604-133">Ferramentas do .NET Core</span><span class="sxs-lookup"><span data-stu-id="bd604-133">.NET Core tools</span></span>](global-tools.md)
