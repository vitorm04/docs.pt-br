---
title: Comando dotnet tool list
description: O comando dotnet da lista de ferramentas lista as ferramentas do .NET Core que estão instaladas em seu computador.
ms.date: 02/14/2020
ms.openlocfilehash: 7ca894ab0f5daf0118ff92fb39e0118b952b3d83
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768268"
---
# <a name="dotnet-tool-list"></a><span data-ttu-id="3b534-103">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="3b534-103">dotnet tool list</span></span>

<span data-ttu-id="3b534-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="3b534-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="3b534-105">Name</span><span class="sxs-lookup"><span data-stu-id="3b534-105">Name</span></span>

<span data-ttu-id="3b534-106">`dotnet tool list`-Lista todas as [Ferramentas do .NET Core](global-tools.md) do tipo especificado atualmente instalado no seu computador.</span><span class="sxs-lookup"><span data-stu-id="3b534-106">`dotnet tool list` - Lists all [.NET Core tools](global-tools.md) of the specified type currently installed on your machine.</span></span>

## <a name="synopsis"></a><span data-ttu-id="3b534-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="3b534-107">Synopsis</span></span>

```dotnetcli
dotnet tool list -g|--global

dotnet tool list --tool-path <PATH>

dotnet tool list --local

dotnet tool list

dotnet tool list -h|--help
```

## <a name="description"></a><span data-ttu-id="3b534-108">Description</span><span class="sxs-lookup"><span data-stu-id="3b534-108">Description</span></span>

<span data-ttu-id="3b534-109">O `dotnet tool list` comando fornece uma maneira de listar todas as ferramentas globais, de caminho de ferramenta ou locais do .NET Core instaladas em seu computador.</span><span class="sxs-lookup"><span data-stu-id="3b534-109">The `dotnet tool list` command provides a way for you to list all .NET Core global, tool-path, or local tools installed on your machine.</span></span> <span data-ttu-id="3b534-110">O comando lista o nome do pacote, a versão instalada e o comando da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="3b534-110">The command lists the package name, version installed, and the tool command.</span></span>  <span data-ttu-id="3b534-111">Para usar o comando, especifique um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="3b534-111">To use the command, you specify one of the following:</span></span>

* <span data-ttu-id="3b534-112">Para listar as ferramentas globais instaladas no local padrão, use a `--global` opção</span><span class="sxs-lookup"><span data-stu-id="3b534-112">To list global tools installed in the default location, use the `--global` option</span></span>
* <span data-ttu-id="3b534-113">Para listar as ferramentas globais instaladas em um local personalizado, use a `--tool-path` opção.</span><span class="sxs-lookup"><span data-stu-id="3b534-113">To list global tools installed in a custom location, use the `--tool-path` option.</span></span>
* <span data-ttu-id="3b534-114">Para listar as ferramentas locais, uma ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="3b534-114">To list local tools, A local tool.</span></span> <span data-ttu-id="3b534-115">Use a `--local` opção ou omita as `--global` `--tool-path` Opções, e `--local` .</span><span class="sxs-lookup"><span data-stu-id="3b534-115">use the `--local` option or omit the `--global`, `--tool-path`, and `--local` options.</span></span>

<span data-ttu-id="3b534-116">**As ferramentas locais estão disponíveis a partir do SDK do .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="3b534-116">**Local tools are available starting with .NET Core SDK 3.0.**</span></span>

## <a name="options"></a><span data-ttu-id="3b534-117">Opções</span><span class="sxs-lookup"><span data-stu-id="3b534-117">Options</span></span>

- **`-g|--global`**

  <span data-ttu-id="3b534-118">Lista as ferramentas globais em todo o usuário.</span><span class="sxs-lookup"><span data-stu-id="3b534-118">Lists user-wide global tools.</span></span> <span data-ttu-id="3b534-119">Não pode ser combinada com a opção `--tool-path`.</span><span class="sxs-lookup"><span data-stu-id="3b534-119">Can't be combined with the `--tool-path` option.</span></span> <span data-ttu-id="3b534-120">Omitir `--global` e `--tool-path` listar as ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="3b534-120">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

- **`-h|--help`**

  <span data-ttu-id="3b534-121">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="3b534-121">Prints out a short help for the command.</span></span>

- **`--local`**

  <span data-ttu-id="3b534-122">Lista as ferramentas locais para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="3b534-122">Lists local tools for the current directory.</span></span> <span data-ttu-id="3b534-123">Não pode ser combinado com `--global` as `--tool-path` Opções ou.</span><span class="sxs-lookup"><span data-stu-id="3b534-123">Can't be combined with the `--global` or `--tool-path` options.</span></span> <span data-ttu-id="3b534-124">Omitir `--global` e `--tool-path` listar as ferramentas locais, mesmo se `--local` não for especificado.</span><span class="sxs-lookup"><span data-stu-id="3b534-124">Omitting both `--global` and `--tool-path` lists local tools even if `--local` is not specified.</span></span>

- **`--tool-path <PATH>`**

  <span data-ttu-id="3b534-125">Especifica um local personalizado onde encontrar ferramentas globais.</span><span class="sxs-lookup"><span data-stu-id="3b534-125">Specifies a custom location where to find global tools.</span></span> <span data-ttu-id="3b534-126">PATH pode ser absoluto ou relativo.</span><span class="sxs-lookup"><span data-stu-id="3b534-126">PATH can be absolute or relative.</span></span> <span data-ttu-id="3b534-127">Não pode ser combinada com a opção `--global`.</span><span class="sxs-lookup"><span data-stu-id="3b534-127">Can't be combined with the `--global` option.</span></span> <span data-ttu-id="3b534-128">Omitir `--global` e `--tool-path` listar as ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="3b534-128">Omitting both `--global` and `--tool-path` lists local tools.</span></span>

## <a name="examples"></a><span data-ttu-id="3b534-129">Exemplos</span><span class="sxs-lookup"><span data-stu-id="3b534-129">Examples</span></span>

- **`dotnet tool list -g`**

  <span data-ttu-id="3b534-130">Lista todas as ferramentas globais instaladas por todo o usuário em seu computador (perfil de usuário atual).</span><span class="sxs-lookup"><span data-stu-id="3b534-130">Lists all global tools installed user-wide on your machine (current user profile).</span></span>

- **`dotnet tool list --tool-path c:\global-tools`**

  <span data-ttu-id="3b534-131">Lista as ferramentas globais de um diretório específico do Windows.</span><span class="sxs-lookup"><span data-stu-id="3b534-131">Lists the global tools from a specific Windows directory.</span></span>

- **`dotnet tool list --tool-path ~/bin`**

  <span data-ttu-id="3b534-132">Lista as ferramentas globais de um diretório específico do Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="3b534-132">Lists the global tools from a specific Linux/macOS directory.</span></span>

- <span data-ttu-id="3b534-133">**`dotnet tool list`** or**`dotnet tool list --local`**</span><span class="sxs-lookup"><span data-stu-id="3b534-133">**`dotnet tool list`** or **`dotnet tool list --local`**</span></span>

  <span data-ttu-id="3b534-134">Lista todas as ferramentas locais disponíveis no diretório atual.</span><span class="sxs-lookup"><span data-stu-id="3b534-134">Lists all local tools available in the current directory.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b534-135">Veja também</span><span class="sxs-lookup"><span data-stu-id="3b534-135">See also</span></span>

- [<span data-ttu-id="3b534-136">Ferramentas do .NET Core</span><span class="sxs-lookup"><span data-stu-id="3b534-136">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="3b534-137">Tutorial: instalar e usar uma ferramenta global do .NET Core usando o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="3b534-137">Tutorial: Install and use a .NET Core global tool using the .NET Core CLI</span></span>](global-tools-how-to-use.md)
- [<span data-ttu-id="3b534-138">Tutorial: instalar e usar uma ferramenta local do .NET Core usando o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="3b534-138">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
