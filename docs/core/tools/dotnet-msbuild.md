---
title: Comando dotnet msbuild
description: O comando dotnet msbuild fornece acesso à linha de comando MSBuild.
ms.date: 02/14/2020
ms.openlocfilehash: 9739fe782e17db3955db087ca1781ad4280cd491
ms.sourcegitcommit: 1eae045421d9ea2bfc82aaccfa5b1ff1b8c9e0e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/16/2020
ms.locfileid: "84803171"
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="b7431-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="b7431-103">dotnet msbuild</span></span>

<span data-ttu-id="b7431-104">**Este artigo aplica-se a:** ✔️ SDK do .NET Core 2. x e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="b7431-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="b7431-105">Nome</span><span class="sxs-lookup"><span data-stu-id="b7431-105">Name</span></span>

<span data-ttu-id="b7431-106">`dotnet msbuild` – Compila um projeto e todas as suas dependências.</span><span class="sxs-lookup"><span data-stu-id="b7431-106">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span> <span data-ttu-id="b7431-107">Observação: um arquivo de solução ou de projeto pode precisar ser especificado se houver vários.</span><span class="sxs-lookup"><span data-stu-id="b7431-107">Note: A solution or project file may need to be specified if there are multiple.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b7431-108">Sinopse</span><span class="sxs-lookup"><span data-stu-id="b7431-108">Synopsis</span></span>

```dotnetcli
dotnet msbuild <MSBUILD_ARGUMENTS>

dotnet msbuild -h
```

## <a name="description"></a><span data-ttu-id="b7431-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="b7431-109">Description</span></span>

<span data-ttu-id="b7431-110">O comando `dotnet msbuild` permite o acesso a um MSBuild totalmente funcional.</span><span class="sxs-lookup"><span data-stu-id="b7431-110">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="b7431-111">O comando tem exatamente os mesmos recursos que o cliente de linha de comando do MSBuild existente apenas para projetos no estilo SDK.</span><span class="sxs-lookup"><span data-stu-id="b7431-111">The command has the exact same capabilities as the existing MSBuild command-line client for SDK-style projects only.</span></span> <span data-ttu-id="b7431-112">As opções são todas iguais.</span><span class="sxs-lookup"><span data-stu-id="b7431-112">The options are all the same.</span></span> <span data-ttu-id="b7431-113">Para obter mais informações sobre as opções disponíveis, consulte a [referência de linha de comando do MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="b7431-113">For more information about the available options, see the [MSBuild command-line reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="b7431-114">O comando [dotnet build](dotnet-build.md) é equivalente ao comando `dotnet msbuild -restore`.</span><span class="sxs-lookup"><span data-stu-id="b7431-114">The [dotnet build](dotnet-build.md) command is equivalent to `dotnet msbuild -restore`.</span></span> <span data-ttu-id="b7431-115">Quando você não quiser compilar o projeto e tiver um destino específico que deseja executar, use `dotnet build` ou `dotnet msbuild` e especifique o destino.</span><span class="sxs-lookup"><span data-stu-id="b7431-115">When you don't want to build the project and you have a specific target you want to run, use `dotnet build` or `dotnet msbuild` and specify the target.</span></span>

## <a name="examples"></a><span data-ttu-id="b7431-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="b7431-116">Examples</span></span>

- <span data-ttu-id="b7431-117">Compile um projeto e suas dependências:</span><span class="sxs-lookup"><span data-stu-id="b7431-117">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet msbuild
  ```

- <span data-ttu-id="b7431-118">Compile um projeto e suas dependências usando a configuração da Versão:</span><span class="sxs-lookup"><span data-stu-id="b7431-118">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet msbuild -property:Configuration=Release
  ```

- <span data-ttu-id="b7431-119">Execute o destino de publicação e publique para o RID `osx.10.11-x64`:</span><span class="sxs-lookup"><span data-stu-id="b7431-119">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

  ```dotnetcli
  dotnet msbuild -target:Publish -property:RuntimeIdentifiers=osx.10.11-x64
  ```

- <span data-ttu-id="b7431-120">Confira o projeto inteiro com todos os destinos incluídos pelo SDK:</span><span class="sxs-lookup"><span data-stu-id="b7431-120">See the whole project with all targets included by the SDK:</span></span>

  ```dotnetcli
  dotnet msbuild -preprocess
  dotnet msbuild -preprocess:<fileName>.xml
  ```
