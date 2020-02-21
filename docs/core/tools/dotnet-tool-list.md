---
title: Comando dotnet tool list
description: O comando dotnet da lista de ferramentas lista as ferramentas do .NET Core que estão instaladas em seu computador.
ms.date: 02/14/2020
ms.openlocfilehash: bb74cfeaf441cf8a1a030d97d16655f85d8267d1
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543450"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="e50c9-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="e50c9-103">dotnet tool list</span></span>

<span data-ttu-id="e50c9-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="e50c9-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="e50c9-105">Nome</span><span class="sxs-lookup"><span data-stu-id="e50c9-105">Name</span></span>

<span data-ttu-id="e50c9-106">`dotnet tool list`-lista todas as [Ferramentas do .NET Core](global-tools.md) do tipo especificado atualmente instalado em seu computador.</span><span class="sxs-lookup"><span data-stu-id="e50c9-106">`dotnet tool list` - Lists all [.NET Core tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e50c9-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="e50c9-107">Synopsis</span></span>

```dotnetcli
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list
dotnet tool list <-h|--help>
```

## <a name="description"></a><span data-ttu-id="e50c9-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="e50c9-108">Description</span></span>

<span data-ttu-id="e50c9-109">O comando `dotnet tool list` fornece uma maneira de listar todas as ferramentas globais, caminho-ferramenta ou local do .NET Core instaladas em seu computador.</span><span class="sxs-lookup"><span data-stu-id="e50c9-109">The `dotnet tool list` command provides a way for you to list all .NET Core global, tool-path, or local Tools installed on your machine.</span></span> <span data-ttu-id="e50c9-110">O comando lista o nome do pacote, a versão instalada e o comando da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="e50c9-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="e50c9-111">Para usar o comando, especifique um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="e50c9-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="e50c9-112">Uma ferramenta global instalada no local padrão.</span><span class="sxs-lookup"><span data-stu-id="e50c9-112">A global tool installed in the default location.</span></span> <span data-ttu-id="e50c9-113">Usar a opção `--global`</span><span class="sxs-lookup"><span data-stu-id="e50c9-113">Use the `--global` option</span></span>
* <span data-ttu-id="e50c9-114">Uma ferramenta global instalada em um local personalizado.</span><span class="sxs-lookup"><span data-stu-id="e50c9-114">A global tool installed in a custom location.</span></span> <span data-ttu-id="e50c9-115">Use a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="e50c9-115">Use the `--tool-path` option.</span></span>
* <span data-ttu-id="e50c9-116">Uma ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="e50c9-116">A local tool.</span></span> <span data-ttu-id="e50c9-117">Omita as opções `--global` e `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="e50c9-117">Omit the `--global` and `--tool-path` options.</span></span>

<span data-ttu-id="e50c9-118">**As ferramentas locais estão disponíveis a partir do SDK do .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="e50c9-118">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="e50c9-119">Opções</span><span class="sxs-lookup"><span data-stu-id="e50c9-119">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="e50c9-120">Lista as ferramentas globais em todo o usuário.</span><span class="sxs-lookup"><span data-stu-id="e50c9-120">Lists user-wide global tools.</span></span> <span data-ttu-id="e50c9-121">Não pode ser combinada com a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="e50c9-121">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="e50c9-122">Omitir `--global` e `--tool-path` lista as ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="e50c9-122">Omitting both `--global` and `--tool-path` lists local tools.</span></span> 

- **`-h|--help`**

  <span data-ttu-id="e50c9-123">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="e50c9-123">Prints out a short help for the command.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="e50c9-124">Especifica um local personalizado onde encontrar ferramentas globais.</span><span class="sxs-lookup"><span data-stu-id="e50c9-124">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="e50c9-125">PATH pode ser absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="e50c9-125">PATH can be absolute or relative.</span></span> <span data-ttu-id="e50c9-126">Não pode ser combinada com a opção `--global`.</span><span class="sxs-lookup"><span data-stu-id="e50c9-126">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="e50c9-127">Omitir `--global` e `--tool-path` lista as ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="e50c9-127">Omitting both `--global` and `--tool-path` lists local tools.</span></span> 

## <a name="examples"></a><span data-ttu-id="e50c9-128">Exemplos</span><span class="sxs-lookup"><span data-stu-id="e50c9-128">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="e50c9-129">Lista todas as ferramentas globais instaladas por todo o usuário em seu computador (perfil de usuário atual).</span><span class="sxs-lookup"><span data-stu-id="e50c9-129">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="e50c9-130">Lista as ferramentas globais de um diretório específico do Windows.</span><span class="sxs-lookup"><span data-stu-id="e50c9-130">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="e50c9-131">Lista as ferramentas globais de um diretório específico do Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="e50c9-131">Lists the global tools from a specific Linux/macOS directory.</span></span>

- **`dotnet tool list`**

  <span data-ttu-id="e50c9-132">Lista todas as ferramentas locais disponíveis no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="e50c9-132">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="e50c9-133">Confira também</span><span class="sxs-lookup"><span data-stu-id="e50c9-133">See also</span></span>

- [<span data-ttu-id="e50c9-134">Ferramentas do .NET Core</span><span class="sxs-lookup"><span data-stu-id="e50c9-134">.NET Core tools</span></span>](global-tools.md)
