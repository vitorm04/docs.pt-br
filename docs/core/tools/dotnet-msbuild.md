---
title: Comando dotnet msbuild
description: O comando dotnet msbuild fornece acesso à linha de comando MSBuild.
ms.date: 12/03/2018
ms.openlocfilehash: dae1e9f0ca355166d41c11fbafb80c7c9fb29748
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76733201"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="c1630-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="c1630-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="c1630-104">{1&gt;Nome&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c1630-104">Name</span></span>

<span data-ttu-id="c1630-105">`dotnet msbuild` – Compila um projeto e todas as suas dependências.</span><span class="sxs-lookup"><span data-stu-id="c1630-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c1630-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="c1630-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="c1630-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="c1630-107">Description</span></span>

<span data-ttu-id="c1630-108">O comando `dotnet msbuild` permite o acesso a um MSBuild totalmente funcional.</span><span class="sxs-lookup"><span data-stu-id="c1630-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="c1630-109">O comando tem exatamente os mesmos recursos que o cliente de linha de comando do MSBuild existente apenas para projetos no estilo SDK.</span><span class="sxs-lookup"><span data-stu-id="c1630-109">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="c1630-110">As opções são todas iguais.</span><span class="sxs-lookup"><span data-stu-id="c1630-110">The options are all the same.</span></span> <span data-ttu-id="c1630-111">Para obter mais informações sobre as opções disponíveis, consulte a [referência de linha de comando do MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="c1630-111">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="c1630-112">O comando [dotnet build](dotnet-build.md) é equivalente ao comando `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="c1630-112">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="c1630-113">a [compilação dotnet](dotnet-build.md) é mais comumente usada para criar projetos, mas como ele sempre executa o destino da compilação, você pode usar `dotnet msbuild` quando não quiser compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="c1630-113">[dotnet build](dotnet-build.md) is more commonly used for building projects, but because it always runs the build target, you can use `dotnet msbuild` when you don't want to build the project.</span></span> <span data-ttu-id="c1630-114">Por exemplo, se você tiver um destino específico que deseja executar sem compilar o projeto, use `dotnet msbuild` e especifique o destino.</span><span class="sxs-lookup"><span data-stu-id="c1630-114">For example, if you have a specific target you want to run without building the project, use `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="c1630-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c1630-115">Examples</span></span>

* <span data-ttu-id="c1630-116">Compile um projeto e suas dependências:</span><span class="sxs-lookup"><span data-stu-id="c1630-116">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

* <span data-ttu-id="c1630-117">Compile um projeto e suas dependências usando a configuração da Versão:</span><span class="sxs-lookup"><span data-stu-id="c1630-117">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

* <span data-ttu-id="c1630-118">Execute o destino de publicação e publique para o RID `osx.10.11-x64`:</span><span class="sxs-lookup"><span data-stu-id="c1630-118">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

* <span data-ttu-id="c1630-119">Confira o projeto inteiro com todos os destinos incluídos pelo SDK:</span><span class="sxs-lookup"><span data-stu-id="c1630-119">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
