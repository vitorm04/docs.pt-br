---
title: Comando dotnet msbuild
description: O comando dotnet msbuild fornece acesso à linha de comando MSBuild.
ms.date: 02/14/2020
ms.openlocfilehash: 88e85868e2d7de564b2e4c90ce6e78bde4cb350e
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463622"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="734eb-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="734eb-103">dotnet msbuild</span></span>

<span data-ttu-id="734eb-104">**Este artigo se aplica a:** ✔️ .NET Core 2.x SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="734eb-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="734eb-105">Nome</span><span class="sxs-lookup"><span data-stu-id="734eb-105">Name</span></span>

<span data-ttu-id="734eb-106">`dotnet msbuild` – Compila um projeto e todas as suas dependências.</span><span class="sxs-lookup"><span data-stu-id="734eb-106">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="734eb-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="734eb-107">Synopsis</span></span>

```dotnetcli
dotnet msbuild <MSBUILD_ARGUMENTS>

dotnet msbuild -h
```

## <a name="description"></a><span data-ttu-id="734eb-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="734eb-108">Description</span></span>

<span data-ttu-id="734eb-109">O comando `dotnet msbuild` permite o acesso a um MSBuild totalmente funcional.</span><span class="sxs-lookup"><span data-stu-id="734eb-109">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="734eb-110">O comando tem exatamente os mesmos recursos que o cliente de linha de comando MSBuild existente apenas para projetos no estilo SDK.</span><span class="sxs-lookup"><span data-stu-id="734eb-110">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="734eb-111">As opções são todas iguais.</span><span class="sxs-lookup"><span data-stu-id="734eb-111">The options are all the same.</span></span> <span data-ttu-id="734eb-112">Para obter mais informações sobre as opções disponíveis, consulte a [referência de linha de comando MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="734eb-112">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="734eb-113">O comando [dotnet build](dotnet-build.md) é equivalente ao comando `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="734eb-113">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="734eb-114">[a compilação dotnet](dotnet-build.md) é mais comumente usada para projetos de construção, `dotnet msbuild` mas como ela sempre executa o alvo de construção, você pode usar quando não quiser construir o projeto.</span><span class="sxs-lookup"><span data-stu-id="734eb-114">[dotnet build](dotnet-build.md) is more commonly used for building projects, but because it always runs the build target, you can use `dotnet msbuild` when you don't want to build the project.</span></span> <span data-ttu-id="734eb-115">Por exemplo, se você tiver um alvo específico, você `dotnet msbuild` deseja executar sem construir o projeto, use e especifique o destino.</span><span class="sxs-lookup"><span data-stu-id="734eb-115">For example, if you have a specific target you want to run without building the project, use `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="734eb-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="734eb-116">Examples</span></span>

- <span data-ttu-id="734eb-117">Compile um projeto e suas dependências:</span><span class="sxs-lookup"><span data-stu-id="734eb-117">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

- <span data-ttu-id="734eb-118">Compile um projeto e suas dependências usando a configuração da Versão:</span><span class="sxs-lookup"><span data-stu-id="734eb-118">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- <span data-ttu-id="734eb-119">Execute o destino de publicação e publique para o RID `osx.10.11-x64`:</span><span class="sxs-lookup"><span data-stu-id="734eb-119">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- <span data-ttu-id="734eb-120">Confira o projeto inteiro com todos os destinos incluídos pelo SDK:</span><span class="sxs-lookup"><span data-stu-id="734eb-120">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
