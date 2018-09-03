---
title: Comando dotnet tool list – CLI do .NET Core
description: O comando dotnet tool list lista a Ferramenta Global do .NET Core especificada no computador.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: e2bea974207d3098ed67b69ed16a72a03c44cd8b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467050"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="7e083-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="7e083-103">dotnet tool list</span></span>

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a><span data-ttu-id="7e083-104">Nome</span><span class="sxs-lookup"><span data-stu-id="7e083-104">Name</span></span>

<span data-ttu-id="7e083-105">`dotnet tool list` – lista todas as [Ferramentas Globais do .NET Core](global-tools.md) atualmente instaladas no diretório padrão do computador ou no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="7e083-105">`dotnet tool list` - Lists all [.NET Core Global Tools](global-tools.md) currently installed in the default directory on your machine or in the specified path.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7e083-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="7e083-106">Synopsis</span></span>

```console
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a><span data-ttu-id="7e083-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e083-107">Description</span></span>

<span data-ttu-id="7e083-108">O comando `dotnet tool list` fornece uma maneira de listar todas as Ferramentas Globais do .NET Core instaladas de todos os usuários no computador (perfil do usuário atual) ou no caminho especificado.</span><span class="sxs-lookup"><span data-stu-id="7e083-108">The `dotnet tool list` command provides a way for you to list all .NET Core Global Tools installed user-wide on your machine (current user profile) or in the specified path.</span></span> <span data-ttu-id="7e083-109">O comando lista o nome do pacote, a versão instalada e o comando da Ferramenta Global.</span><span class="sxs-lookup"><span data-stu-id="7e083-109">The command lists the package name, version installed, and the Global Tool command.</span></span> <span data-ttu-id="7e083-110">Para usar o comando list, você precisa especificar que deseja ver todas as ferramentas de todos os usuários usando a opção `--global` ou especificar um caminho personalizado usando a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="7e083-110">To use the list command, you either have to specify that you want to see all user-wide tools using the `--global` option or specify a custom path using the `--tool-path` option.</span></span>

## <a name="options"></a><span data-ttu-id="7e083-111">Opções</span><span class="sxs-lookup"><span data-stu-id="7e083-111">Options</span></span>

`-g|--global`

<span data-ttu-id="7e083-112">Lista as Ferramentas Globais de todos os usuários.</span><span class="sxs-lookup"><span data-stu-id="7e083-112">Lists user-wide Global Tools.</span></span> <span data-ttu-id="7e083-113">Não pode ser combinada com a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="7e083-113">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="7e083-114">Se você não especificar essa opção, especifique a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="7e083-114">If you don't specify this option, you must specify the `--tool-path` option.</span></span>

`-h|--help`

<span data-ttu-id="7e083-115">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="7e083-115">Prints out a short help for the command.</span></span>

`--tool-path <PATH>`

<span data-ttu-id="7e083-116">Especifica um local personalizado no qual encontrar as Ferramentas Globais.</span><span class="sxs-lookup"><span data-stu-id="7e083-116">Specifies a custom location where to find Global Tools.</span></span> <span data-ttu-id="7e083-117">PATH pode ser absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="7e083-117">PATH can be absolute or relative.</span></span> <span data-ttu-id="7e083-118">Não pode ser combinada com a opção `--global`.</span><span class="sxs-lookup"><span data-stu-id="7e083-118">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="7e083-119">Se você não especificar essa opção, especifique a opção `--global`.</span><span class="sxs-lookup"><span data-stu-id="7e083-119">If you don't specify this option, you must specify the `--global` option.</span></span>

## <a name="examples"></a><span data-ttu-id="7e083-120">Exemplos</span><span class="sxs-lookup"><span data-stu-id="7e083-120">Examples</span></span>

<span data-ttu-id="7e083-121">Lista todas as Ferramentas Globais instaladas de todos os usuários no computador (perfil do usuário atual):</span><span class="sxs-lookup"><span data-stu-id="7e083-121">Lists all Global Tools installed user-wide on your machine (current user profile):</span></span>

`dotnet tool list -g`

<span data-ttu-id="7e083-122">Lista as Ferramentas Globais de uma pasta específica do Windows:</span><span class="sxs-lookup"><span data-stu-id="7e083-122">Lists the Global Tools from a specific Windows folder:</span></span>

`dotnet tool list --tool-path c:\global-tools`

<span data-ttu-id="7e083-123">Lista as Ferramentas Globais de uma pasta específica do Linux/macOS:</span><span class="sxs-lookup"><span data-stu-id="7e083-123">Lists the Global Tools from a specific Linux/macOS folder:</span></span>

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a><span data-ttu-id="7e083-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e083-124">See also</span></span>

* [<span data-ttu-id="7e083-125">Ferramentas Globais do .NET Core</span><span class="sxs-lookup"><span data-stu-id="7e083-125">.NET Core Global Tools</span></span>](global-tools.md)