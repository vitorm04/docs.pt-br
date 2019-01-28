---
title: Comando dotnet tool uninstall
description: O comando dotnet tool uninstall desinstala do computador a Ferramenta Global do .NET Core especificada.
ms.date: 05/29/2018
ms.openlocfilehash: 4d53d305131e3399ab5d9c19f9319f3ba3544c19
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680917"
---
# <a name="dotnet-tool-uninstall"></a><span data-ttu-id="42d01-103">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="42d01-103">dotnet tool uninstall</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="42d01-104">Nome</span><span class="sxs-lookup"><span data-stu-id="42d01-104">Name</span></span>

<span data-ttu-id="42d01-105">`dotnet tool uninstall` – desinstala do computador a [Ferramenta Global do .NET Core](global-tools.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="42d01-105">`dotnet tool uninstall` - Uninstalls the specified [.NET Core Global Tool](global-tools.md) from your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="42d01-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="42d01-106">Synopsis</span></span>

```console
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a><span data-ttu-id="42d01-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="42d01-107">Description</span></span>

<span data-ttu-id="42d01-108">O comando `dotnet tool uninstall` fornece uma maneira de desinstalar do computador as Ferramentas Globais do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="42d01-108">The `dotnet tool uninstall` command provides a way for you to uninstall .NET Core Global Tools from your machine.</span></span> <span data-ttu-id="42d01-109">Para usar o comando, você precisa especificar que deseja remover uma ferramenta de todos os usuários usando a opção `--global` ou especificar um caminho para o local em que a ferramenta está instalada usando a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="42d01-109">To use the command, you either have to specify that you want to remove a user-wide tool using the `--global` option or specify a path to where the tool is installed using the `--tool-path` option.</span></span>

## <a name="arguments"></a><span data-ttu-id="42d01-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="42d01-110">Arguments</span></span>

`PACKAGE_NAME`

<span data-ttu-id="42d01-111">Nome/ID do pacote NuGet que contém a Ferramenta Global do .NET Core a ser desinstalada.</span><span class="sxs-lookup"><span data-stu-id="42d01-111">Name/ID of the NuGet package that contains the .NET Core Global Tool to uninstall.</span></span> <span data-ttu-id="42d01-112">Encontre o nome do pacote usando o comando [dotnet tool list](dotnet-tool-list.md).</span><span class="sxs-lookup"><span data-stu-id="42d01-112">You can find the package name using the [dotnet tool list](dotnet-tool-list.md) command.</span></span>

## <a name="options"></a><span data-ttu-id="42d01-113">Opções</span><span class="sxs-lookup"><span data-stu-id="42d01-113">Options</span></span>

`-g|--global`

<span data-ttu-id="42d01-114">Especifica que a ferramenta a ser removida pertence a uma instalação de todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="42d01-114">Specifies that the tool to be removed is from a user-wide installation.</span></span> <span data-ttu-id="42d01-115">Não pode ser combinada com a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="42d01-115">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="42d01-116">Se você não especificar essa opção, especifique a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="42d01-116">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="42d01-117">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="42d01-117">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="42d01-118">Especifica o local do qual a Ferramenta Global será desinstalada.</span><span class="sxs-lookup"><span data-stu-id="42d01-118">Specifies the location where to uninstall the Global Tool.</span></span> <span data-ttu-id="42d01-119">PATH pode ser absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="42d01-119">PATH can be absolute or relative.</span></span> <span data-ttu-id="42d01-120">Não pode ser combinada com a opção `--global`.</span><span class="sxs-lookup"><span data-stu-id="42d01-120">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="42d01-121">Se você não especificar essa opção, especifique a opção `--global`.</span><span class="sxs-lookup"><span data-stu-id="42d01-121">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="42d01-122">Exemplos</span><span class="sxs-lookup"><span data-stu-id="42d01-122">Examples</span></span>

<span data-ttu-id="42d01-123">Desinstala a Ferramenta Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/):</span><span class="sxs-lookup"><span data-stu-id="42d01-123">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool:</span></span>

`dotnet tool uninstall -g dotnetsay`

<span data-ttu-id="42d01-124">Desinstala a Ferramenta Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) de uma pasta específica do Windows:</span><span class="sxs-lookup"><span data-stu-id="42d01-124">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool from a specific Windows folder:</span></span>

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

<span data-ttu-id="42d01-125">Desinstala a Ferramenta Global [dotnetsay](https://www.nuget.org/packages/dotnetsay/) de uma pasta específica do Linux/macOS:</span><span class="sxs-lookup"><span data-stu-id="42d01-125">Uninstalls the [dotnetsay](https://www.nuget.org/packages/dotnetsay/) Global Tool from a specific Linux/macOS folder:</span></span>

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="42d01-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="42d01-126">See also</span></span>

- [<span data-ttu-id="42d01-127">Ferramentas Globais do .NET Core</span><span class="sxs-lookup"><span data-stu-id="42d01-127">.NET Core Global Tools</span></span>](global-tools.md)
