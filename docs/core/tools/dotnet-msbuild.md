---
title: Comando dotnet msbuild
description: O comando dotnet msbuild fornece acesso à linha de comando MSBuild.
ms.date: 12/03/2018
ms.openlocfilehash: b83f1272cdd4c5fcdb6b1e34aef7692e9acc01cd
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117706"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="902df-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="902df-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="902df-104">Nome</span><span class="sxs-lookup"><span data-stu-id="902df-104">Name</span></span>

<span data-ttu-id="902df-105">`dotnet msbuild` – Compila um projeto e todas as suas dependências.</span><span class="sxs-lookup"><span data-stu-id="902df-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="902df-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="902df-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="902df-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="902df-107">Description</span></span>

<span data-ttu-id="902df-108">O comando `dotnet msbuild` permite o acesso a um MSBuild totalmente funcional.</span><span class="sxs-lookup"><span data-stu-id="902df-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="902df-109">O comando tem exatamente os mesmos recursos do cliente de linha de comando existente do MSBuild somente para projetos no estilo SDK.</span><span class="sxs-lookup"><span data-stu-id="902df-109">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style project only.</span></span> <span data-ttu-id="902df-110">As opções são todas iguais.</span><span class="sxs-lookup"><span data-stu-id="902df-110">The options are all the same.</span></span> <span data-ttu-id="902df-111">Para obter mais informações sobre as opções disponíveis, confira a [Referência de linha de comando do MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="902df-111">For more information about the available options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="902df-112">O comando [dotnet build](dotnet-build.md) é equivalente ao comando `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="902df-112">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="902df-113">`dotnet build` é mais comumente usado na criação de projetos, mas `dotnet msbuild` oferece mais controle.</span><span class="sxs-lookup"><span data-stu-id="902df-113">`dotnet build` is more commonly used for building projects, but `dotnet msbuild` gives you more control.</span></span> <span data-ttu-id="902df-114">Por exemplo, se houver um destino específico que você deseja executar (sem executar o destino do build), convém usar `dotnet msbuild`.</span><span class="sxs-lookup"><span data-stu-id="902df-114">For example, if you have a specific target you want to run (without running the build target), you probably want to use `dotnet msbuild`.</span></span>

## <a name="examples"></a><span data-ttu-id="902df-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="902df-115">Examples</span></span>

* <span data-ttu-id="902df-116">Compile um projeto e suas dependências:</span><span class="sxs-lookup"><span data-stu-id="902df-116">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

* <span data-ttu-id="902df-117">Compile um projeto e suas dependências usando a configuração da Versão:</span><span class="sxs-lookup"><span data-stu-id="902df-117">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -p:Configuration=Release
  ```

* <span data-ttu-id="902df-118">Execute o destino de publicação e publique para o RID `osx.10.11-x64`:</span><span class="sxs-lookup"><span data-stu-id="902df-118">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64
  ```

* <span data-ttu-id="902df-119">Confira o projeto inteiro com todos os destinos incluídos pelo SDK:</span><span class="sxs-lookup"><span data-stu-id="902df-119">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -pp
  ```
