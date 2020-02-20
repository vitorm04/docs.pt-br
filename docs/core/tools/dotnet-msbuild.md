---
title: Comando dotnet msbuild
description: O comando dotnet msbuild fornece acesso à linha de comando MSBuild.
ms.date: 02/14/2020
ms.openlocfilehash: 28a32a460d644d3e22f16b5dd9416222ae466e2e
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503671"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="cb35f-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="cb35f-103">dotnet msbuild</span></span>

<span data-ttu-id="cb35f-104">**Este artigo aplica-se a:** ✔️ SDK do .NET Core 2. x e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="cb35f-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="cb35f-105">Nome</span><span class="sxs-lookup"><span data-stu-id="cb35f-105">Name</span></span>

<span data-ttu-id="cb35f-106">`dotnet msbuild` – Compila um projeto e todas as suas dependências.</span><span class="sxs-lookup"><span data-stu-id="cb35f-106">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="cb35f-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="cb35f-107">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="cb35f-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="cb35f-108">Description</span></span>

<span data-ttu-id="cb35f-109">O comando `dotnet msbuild` permite o acesso a um MSBuild totalmente funcional.</span><span class="sxs-lookup"><span data-stu-id="cb35f-109">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="cb35f-110">O comando tem exatamente os mesmos recursos que o cliente de linha de comando do MSBuild existente apenas para projetos no estilo SDK.</span><span class="sxs-lookup"><span data-stu-id="cb35f-110">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="cb35f-111">As opções são todas iguais.</span><span class="sxs-lookup"><span data-stu-id="cb35f-111">The options are all the same.</span></span> <span data-ttu-id="cb35f-112">Para obter mais informações sobre as opções disponíveis, consulte a [referência de linha de comando do MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="cb35f-112">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="cb35f-113">O comando [dotnet build](dotnet-build.md) é equivalente ao comando `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="cb35f-113">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="cb35f-114">a [compilação dotnet](dotnet-build.md) é mais comumente usada para criar projetos, mas como ele sempre executa o destino da compilação, você pode usar `dotnet msbuild` quando não quiser compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="cb35f-114">[dotnet build](dotnet-build.md) is more commonly used for building projects, but because it always runs the build target, you can use `dotnet msbuild` when you don't want to build the project.</span></span> <span data-ttu-id="cb35f-115">Por exemplo, se você tiver um destino específico que deseja executar sem compilar o projeto, use `dotnet msbuild` e especifique o destino.</span><span class="sxs-lookup"><span data-stu-id="cb35f-115">For example, if you have a specific target you want to run without building the project, use `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="cb35f-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="cb35f-116">Examples</span></span>

- <span data-ttu-id="cb35f-117">Compile um projeto e suas dependências:</span><span class="sxs-lookup"><span data-stu-id="cb35f-117">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

- <span data-ttu-id="cb35f-118">Compile um projeto e suas dependências usando a configuração da Versão:</span><span class="sxs-lookup"><span data-stu-id="cb35f-118">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- <span data-ttu-id="cb35f-119">Execute o destino de publicação e publique para o RID `osx.10.11-x64`:</span><span class="sxs-lookup"><span data-stu-id="cb35f-119">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- <span data-ttu-id="cb35f-120">Confira o projeto inteiro com todos os destinos incluídos pelo SDK:</span><span class="sxs-lookup"><span data-stu-id="cb35f-120">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  ```
