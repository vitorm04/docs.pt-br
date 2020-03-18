---
title: Comando dotnet tool uninstall
description: O comando dotnet desinstalar a ferramenta .NET Core especificada da sua máquina.
ms.date: 02/14/2020
ms.openlocfilehash: 82799404c40baa3a39f4e2a5fdb414fb745ef448
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847827"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="5893e-103">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="5893e-103">dotnet tool uninstall</span></span>

<span data-ttu-id="5893e-104">**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="5893e-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5893e-105">Nome</span><span class="sxs-lookup"><span data-stu-id="5893e-105">Name</span></span>

<span data-ttu-id="5893e-106">`dotnet tool uninstall`- Desinstala a [ferramenta .NET Core](global-tools.md) especificada da sua máquina.</span><span class="sxs-lookup"><span data-stu-id="5893e-106">`dotnet tool uninstall` - Uninstalls the specified [.NET Core tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5893e-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="5893e-107">Synopsis</span></span>

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>

dotnet tool uninstall <PACKAGE_NAME> <--tool-path>

dotnet tool uninstall <PACKAGE_NAME>

dotnet tool uninstall <-h|--help>
```

## <a name="description"></a><span data-ttu-id="5893e-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="5893e-108">Description</span></span>

<span data-ttu-id="5893e-109">O `dotnet tool uninstall` comando fornece uma maneira de você desinstalar ferramentas .NET Core da sua máquina.</span><span class="sxs-lookup"><span data-stu-id="5893e-109">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core tools from your machine.</span></span> <span data-ttu-id="5893e-110">Para usar o comando, você especifica uma das seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="5893e-110">To use the command, you specify one of the following options:</span></span>

* <span data-ttu-id="5893e-111">Para desinstalar uma ferramenta global instalada no local `--global` padrão, use a opção.</span><span class="sxs-lookup"><span data-stu-id="5893e-111">To uninstall a global tool that was installed in the default location, use the `--global` option.</span></span>
* <span data-ttu-id="5893e-112">Para desinstalar uma ferramenta global instalada em um `--tool-path` local personalizado, use a opção.</span><span class="sxs-lookup"><span data-stu-id="5893e-112">To uninstall a global tool that was installed in a custom location,  use the `--tool-path` option.</span></span>
* <span data-ttu-id="5893e-113">Para desinstalar uma ferramenta local, omita as `--global` opções e `--tool-path` opções.</span><span class="sxs-lookup"><span data-stu-id="5893e-113">To uninstall a local tool, omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="5893e-114">**As ferramentas locais estão disponíveis a partir do .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="5893e-114">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="arguments"></a><span data-ttu-id="5893e-115">Argumentos</span><span class="sxs-lookup"><span data-stu-id="5893e-115">Arguments</span></span>

- **`PACKAGE_NAME`**

  <span data-ttu-id="5893e-116">Nome/ID do pacote NuGet que contém a ferramenta .NET Core para desinstalar.</span><span class="sxs-lookup"><span data-stu-id="5893e-116">Name/ID of the NuGet package that contains the .NET Core tool to uninstall.</span></span> <span data-ttu-id="5893e-117">Encontre o nome do pacote usando o comando [dotnet tool list](dotnet-tool-list.md).</span><span class="sxs-lookup"><span data-stu-id="5893e-117">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="5893e-118">Opções</span><span class="sxs-lookup"><span data-stu-id="5893e-118">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="5893e-119">Especifica que a ferramenta a ser removida pertence a uma instalação de todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="5893e-119">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="5893e-120">Não pode ser combinada com a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="5893e-120">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="5893e-121">Omitir ambos `--global` e `--tool-path` especificar que a ferramenta a ser removida é uma ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="5893e-121">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

- **`-h|--help`**

  <span data-ttu-id="5893e-122">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="5893e-122">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="5893e-123">Especifica o local onde desinstalar a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="5893e-123">Specifies the location where to uninstall the tool.</span></span> <span data-ttu-id="5893e-124">PATH pode ser absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="5893e-124">PATH can be absolute or relative.</span></span> <span data-ttu-id="5893e-125">Não pode ser combinada com a opção `--global`.</span><span class="sxs-lookup"><span data-stu-id="5893e-125">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="5893e-126">Omitir ambos `--global` e `--tool-path` especificar que a ferramenta a ser removida é uma ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="5893e-126">Omitting both `--global` and `--tool-path` specifies that the tool to be removed is a local tool.</span></span>

## <a name="examples"></a><span data-ttu-id="5893e-127">Exemplos</span><span class="sxs-lookup"><span data-stu-id="5893e-127">Examples</span></span>

- **`dotnet tool uninstall -g dotnetsay`**

  <span data-ttu-id="5893e-128">Desinstala a ferramenta global [dotnetsay.](https://www.nuget.org/packages/dotnetsay/)</span><span class="sxs-lookup"><span data-stu-id="5893e-128">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  <span data-ttu-id="5893e-129">Desinstala a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) de um diretório específico do Windows.</span><span class="sxs-lookup"><span data-stu-id="5893e-129">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Windows directory.</span></span>

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  <span data-ttu-id="5893e-130">Desinstala a ferramenta global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) a partir de um diretório específico do Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="5893e-130">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) global tool from a specific Linux/macOS directory.</span></span>

- **`dotnet tool uninstall dotnetsay`**

  <span data-ttu-id="5893e-131">Desinstala a ferramenta local [dotnetsay](https://www.nuget.org/packages/dotnetsay/) do diretório atual.</span><span class="sxs-lookup"><span data-stu-id="5893e-131">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) local tool from the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="5893e-132">Confira também</span><span class="sxs-lookup"><span data-stu-id="5893e-132">See also</span></span>

- [<span data-ttu-id="5893e-133">.NET Core ferramentas</span><span class="sxs-lookup"><span data-stu-id="5893e-133">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="5893e-134">Tutorial: Instale e use uma ferramenta global .NET Core usando o .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="5893e-134">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="5893e-135">Tutorial: Instale e use uma ferramenta local .NET Core usando o .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="5893e-135">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
