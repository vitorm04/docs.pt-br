---
title: comando de execução de ferramenta dotnet
description: O comando dotnet tool run invoca uma ferramenta local.
ms.date: 02/14/2020
ms.openlocfilehash: a088cd0b7f4bba014234a8189a42a63aa6d88f4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847840"
---
# <a name="dotnet-tool-run"></a><span data-ttu-id="95245-103">dotnet ferramenta executar</span><span class="sxs-lookup"><span data-stu-id="95245-103">dotnet tool run</span></span>

<span data-ttu-id="95245-104">**Este artigo se aplica a:** ✔️ .NET Core 3.0 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="95245-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="95245-105">Nome</span><span class="sxs-lookup"><span data-stu-id="95245-105">Name</span></span>

<span data-ttu-id="95245-106">`dotnet tool run`- Invoca uma ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="95245-106">`dotnet tool run` - Invokes a local tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="95245-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="95245-107">Synopsis</span></span>

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run <-h|--help>
```

## <a name="description"></a><span data-ttu-id="95245-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="95245-108">Description</span></span>

<span data-ttu-id="95245-109">O `dotnet tool run` comando pesquisa arquivos manifestos de ferramenta que estão no escopo para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="95245-109">The `dotnet tool run` command searches tool manifest files that are in scope for the current directory.</span></span> <span data-ttu-id="95245-110">Quando encontra uma referência à ferramenta especificada, ela executa a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="95245-110">When it finds a reference to the specified tool, it runs the tool.</span></span> <span data-ttu-id="95245-111">Para obter mais informações, consulte [Invocar uma ferramenta local](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="95245-111">For more information, see [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="95245-112">Argumentos</span><span class="sxs-lookup"><span data-stu-id="95245-112">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="95245-113">O nome de comando da ferramenta para executar.</span><span class="sxs-lookup"><span data-stu-id="95245-113">The command name of the tool to run.</span></span>

## <a name="options"></a><span data-ttu-id="95245-114">Opções</span><span class="sxs-lookup"><span data-stu-id="95245-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="95245-115">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="95245-115">Prints out a short help for the command.</span></span>

## <a name="example"></a><span data-ttu-id="95245-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95245-116">Example</span></span>

- **`dotnet tool run dotnetsay`**

  <span data-ttu-id="95245-117">Executa `dotnetsay` a ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="95245-117">Runs the `dotnetsay` local tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="95245-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="95245-118">See also</span></span>

- [<span data-ttu-id="95245-119">.NET Core ferramentas</span><span class="sxs-lookup"><span data-stu-id="95245-119">.NET Core tools</span></span>](global-tools.md)
- [<span data-ttu-id="95245-120">Tutorial: Instale e use uma ferramenta local .NET Core usando o .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="95245-120">Tutorial: Install and use a .NET Core local tool using the .NET Core CLI</span></span>](local-tools-how-to-use.md)
