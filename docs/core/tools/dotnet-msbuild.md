---
title: Comando dotnet msbuild – CLI do .NET Core
description: O comando dotnet msbuild fornece acesso à linha de comando MSBuild.
ms.date: 12/03/2018
ms.openlocfilehash: 93471ded9614502ab89d5afb19dd9992f068ef80
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53128041"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="2fac3-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="2fac3-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="2fac3-104">Nome</span><span class="sxs-lookup"><span data-stu-id="2fac3-104">Name</span></span>

<span data-ttu-id="2fac3-105">`dotnet msbuild` – Compila um projeto e todas as suas dependências.</span><span class="sxs-lookup"><span data-stu-id="2fac3-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2fac3-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="2fac3-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="2fac3-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2fac3-107">Description</span></span>

<span data-ttu-id="2fac3-108">O comando `dotnet msbuild` permite o acesso a um MSBuild totalmente funcional.</span><span class="sxs-lookup"><span data-stu-id="2fac3-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="2fac3-109">O comando tem exatamente os mesmos recursos do cliente de linha de comando existente do MSBuild somente para projetos no estilo SDK.</span><span class="sxs-lookup"><span data-stu-id="2fac3-109">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style project only.</span></span> <span data-ttu-id="2fac3-110">As opções são todas iguais.</span><span class="sxs-lookup"><span data-stu-id="2fac3-110">The options are all the same.</span></span> <span data-ttu-id="2fac3-111">Para obter mais informações sobre as opções disponíveis, confira a [Referência de linha de comando do MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="2fac3-111">For more information about the available options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="2fac3-112">O comando [dotnet build](dotnet-build.md) é equivalente ao comando `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="2fac3-112">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore -target:Build`.</span></span> <span data-ttu-id="2fac3-113">`dotnet build` é mais comumente usado na criação de projetos, mas `dotnet msbuild` oferece mais controle.</span><span class="sxs-lookup"><span data-stu-id="2fac3-113">`dotnet build` is more commonly used for building projects, but `dotnet msbuild` gives you more control.</span></span> <span data-ttu-id="2fac3-114">Por exemplo, se houver um destino específico que você deseja executar (sem executar o destino do build), convém usar `dotnet msbuild`.</span><span class="sxs-lookup"><span data-stu-id="2fac3-114">For example, if you have a specific target you want to run (without running the build target), you probably want to use `dotnet msbuild`.</span></span>

## <a name="examples"></a><span data-ttu-id="2fac3-115">Exemplos</span><span class="sxs-lookup"><span data-stu-id="2fac3-115">Examples</span></span>

* <span data-ttu-id="2fac3-116">Compile um projeto e suas dependências:</span><span class="sxs-lookup"><span data-stu-id="2fac3-116">Build a project and its dependencies:</span></span>

  ```console
  dotnet msbuild
  ```

* <span data-ttu-id="2fac3-117">Compile um projeto e suas dependências usando a configuração da Versão:</span><span class="sxs-lookup"><span data-stu-id="2fac3-117">Build a project and its dependencies using Release configuration:</span></span>

  ```console
  dotnet msbuild -p:Configuration=Release
  ```

* <span data-ttu-id="2fac3-118">Execute o destino de publicação e publique para o RID `osx.10.11-x64`:</span><span class="sxs-lookup"><span data-stu-id="2fac3-118">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```console
  dotnet msbuild -t:Publish -p:RuntimeIdentifiers=osx.10.11-x64
  ```

* <span data-ttu-id="2fac3-119">Confira o projeto inteiro com todos os destinos incluídos pelo SDK:</span><span class="sxs-lookup"><span data-stu-id="2fac3-119">See the whole project with all targets included by the SDK:</span></span>

  ```console
  dotnet msbuild -pp
  ```