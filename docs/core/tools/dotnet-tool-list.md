---
title: Comando dotnet tool list
description: O comando dotnet tool list lists the .NET Core ferramentas que estão instaladas na sua máquina.
ms.date: 02/14/2020
ms.openlocfilehash: def3c345a775e5a65ec3d37718d207c80ca7ceee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847866"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="be194-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="be194-103">dotnet tool list</span></span>

<span data-ttu-id="be194-104">**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="be194-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="be194-105">Nome</span><span class="sxs-lookup"><span data-stu-id="be194-105">Name</span></span>

<span data-ttu-id="be194-106">`dotnet tool list`- Lista todas as [ferramentas .NET Core](global-tools.md) do tipo especificado atualmente instalados em sua máquina.</span><span class="sxs-lookup"><span data-stu-id="be194-106">`dotnet tool list` - Lists all [.NET Core tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="be194-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="be194-107">Synopsis</span></span>

```dotnetcli
dotnet tool list <-g|--global>

dotnet tool list <--tool-path>

dotnet tool list

dotnet tool list <-h|--help>
```

## <a name="description"></a><span data-ttu-id="be194-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="be194-108">Description</span></span>

<span data-ttu-id="be194-109">O `dotnet tool list` comando fornece uma maneira de você listar todas as Ferramentas globais, de caminho de ferramentas ou locais do .NET Core instaladas na máquina.</span><span class="sxs-lookup"><span data-stu-id="be194-109">The `dotnet tool list` command provides a way for you to list all .NET Core global, tool-path, or local Tools installed on your machine.</span></span> <span data-ttu-id="be194-110">O comando lista o nome do pacote, a versão instalada e o comando da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="be194-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="be194-111">Para usar o comando, você especifica um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="be194-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="be194-112">Uma ferramenta global instalada no local padrão.</span><span class="sxs-lookup"><span data-stu-id="be194-112">A global tool installed in the default location.</span></span> <span data-ttu-id="be194-113">Use `--global` a opção</span><span class="sxs-lookup"><span data-stu-id="be194-113">Use the `--global` option</span></span>
* <span data-ttu-id="be194-114">Uma ferramenta global instalada em um local personalizado.</span><span class="sxs-lookup"><span data-stu-id="be194-114">A global tool installed in a custom location.</span></span> <span data-ttu-id="be194-115">Use a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="be194-115">Use the `--tool-path` option.</span></span>
* <span data-ttu-id="be194-116">Uma ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="be194-116">A local tool.</span></span> <span data-ttu-id="be194-117">Omita `--global` `--tool-path` as opções.</span><span class="sxs-lookup"><span data-stu-id="be194-117">Omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="be194-118">**As ferramentas locais estão disponíveis a partir do .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="be194-118">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="be194-119">Opções</span><span class="sxs-lookup"><span data-stu-id="be194-119">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="be194-120">Lista ferramentas globais de todo o usuário.</span><span class="sxs-lookup"><span data-stu-id="be194-120">Lists user-wide global tools.</span></span> <span data-ttu-id="be194-121">Não pode ser combinada com a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="be194-121">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="be194-122">Omitindo ambos `--global` e `--tool-path` lista ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="be194-122">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="be194-123">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="be194-123">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="be194-124">Especifica um local personalizado onde encontrar ferramentas globais.</span><span class="sxs-lookup"><span data-stu-id="be194-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="be194-125">PATH pode ser absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="be194-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="be194-126">Não pode ser combinada com a opção `--global`.</span><span class="sxs-lookup"><span data-stu-id="be194-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="be194-127">Omitindo ambos `--global` e `--tool-path` lista ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="be194-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="be194-128">Exemplos</span><span class="sxs-lookup"><span data-stu-id="be194-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="be194-129">Lista todas as ferramentas globais instaladas em todo o usuário em sua máquina (perfil de usuário atual).</span><span class="sxs-lookup"><span data-stu-id="be194-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="be194-130">Lista as ferramentas globais de um diretório específico do Windows.</span><span class="sxs-lookup"><span data-stu-id="be194-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="be194-131">Lista as ferramentas globais de um diretório específico do Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="be194-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- **`dotnet tool list`**

  <span data-ttu-id="be194-132">Lista todas as ferramentas locais disponíveis no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="be194-132">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="be194-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="be194-133">See also</span></span>

- [<span data-ttu-id="be194-134">.NET Core ferramentas</span><span class="sxs-lookup"><span data-stu-id="be194-134">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="be194-135">Tutorial: Instale e use uma ferramenta global .NET Core usando o .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="be194-135">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="be194-136">Tutorial: Instale e use uma ferramenta local .NET Core usando o .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="be194-136">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
