---
title: comando de execução da ferramenta dotnet
description: O comando dotnet ferramenta de execução invoca uma ferramenta local.
ms.date: 02/14/2020
ms.openlocfilehash: 76830b8a8088fbf21f14ab0722b9547eabde7ba4
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156953"
---
# <a name="dotnet-tool-run"></a><span data-ttu-id="a2d0f-103">dotnet tool run</span><span class="sxs-lookup"><span data-stu-id="a2d0f-103">dotnet tool run</span></span>

<span data-ttu-id="a2d0f-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 3,0 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="a2d0f-104">**This article applies to:** ✔️ .NET Core 3.0 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="a2d0f-105">Nome</span><span class="sxs-lookup"><span data-stu-id="a2d0f-105">Name</span></span>

<span data-ttu-id="a2d0f-106">`dotnet tool run`-invoca uma ferramenta local.</span><span class="sxs-lookup"><span data-stu-id="a2d0f-106">`dotnet tool run` - Invokes a local tool.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a2d0f-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="a2d0f-107">Synopsis</span></span>

```dotnetcli
dotnet tool run <COMMAND NAME>
dotnet tool run <-h|--help>
```

## <a name="description"></a><span data-ttu-id="a2d0f-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="a2d0f-108">Description</span></span>

<span data-ttu-id="a2d0f-109">O comando `dotnet tool run` pesquisa os arquivos de manifesto da ferramenta que estão no escopo do diretório atual.</span><span class="sxs-lookup"><span data-stu-id="a2d0f-109">The `dotnet tool run` command searches tool manifest files that are in scope for the current directory.</span></span> <span data-ttu-id="a2d0f-110">Quando ele encontra uma referência à ferramenta especificada, ele executa a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="a2d0f-110">When it finds a reference to the specified tool, it runs the tool.</span></span> <span data-ttu-id="a2d0f-111">Para obter mais informações, consulte [invocar uma ferramenta local](global-tools.md#invoke-a-local-tool).</span><span class="sxs-lookup"><span data-stu-id="a2d0f-111">For more information, see [Invoke a local tool](global-tools.md#invoke-a-local-tool).</span></span>

## <a name="arguments"></a><span data-ttu-id="a2d0f-112">Argumentos</span><span class="sxs-lookup"><span data-stu-id="a2d0f-112">Arguments</span></span>

- **`COMMAND_NAME`**

  <span data-ttu-id="a2d0f-113">O nome do comando da ferramenta a ser executada.</span><span class="sxs-lookup"><span data-stu-id="a2d0f-113">The command name of the tool to run.</span></span>

## <a name="options"></a><span data-ttu-id="a2d0f-114">Opções</span><span class="sxs-lookup"><span data-stu-id="a2d0f-114">Options</span></span>

- **`-h|--help`**

  <span data-ttu-id="a2d0f-115">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="a2d0f-115">Prints out a short help for the command.</span></span>

## <a name="example"></a><span data-ttu-id="a2d0f-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a2d0f-116">Example</span></span>

- **`dotnet tool run dotnetsay`**

  <span data-ttu-id="a2d0f-117">Executa a ferramenta local `dotnetsay`.</span><span class="sxs-lookup"><span data-stu-id="a2d0f-117">Runs the `dotnetsay` local tool.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2d0f-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="a2d0f-118">See also</span></span>

- [<span data-ttu-id="a2d0f-119">Ferramentas do .NET Core</span><span class="sxs-lookup"><span data-stu-id="a2d0f-119">.NET Core tools</span></span>](global-tools.md)
