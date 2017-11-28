---
title: "Comando dotnet msbuild – CLI do .NET Core"
description: "O comando dotnet msbuild fornece acesso à linha de comando MSBuild."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 96e4eac528abad2b336a979a98c9be2bee5d17ee
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="55e57-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="55e57-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="55e57-104">Nome</span><span class="sxs-lookup"><span data-stu-id="55e57-104">Name</span></span>

<span data-ttu-id="55e57-105">`dotnet msbuild` – Compila um projeto e todas as suas dependências.</span><span class="sxs-lookup"><span data-stu-id="55e57-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="55e57-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="55e57-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="55e57-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="55e57-107">Description</span></span>

<span data-ttu-id="55e57-108">O comando `dotnet msbuild` permite o acesso a um MSBuild totalmente funcional.</span><span class="sxs-lookup"><span data-stu-id="55e57-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="55e57-109">O comando tem exatamente os mesmos recursos do cliente de linha de comando existente do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="55e57-109">The command has the exact same capabilities as existing MSBuild command-line client.</span></span> <span data-ttu-id="55e57-110">As opções são todas iguais.</span><span class="sxs-lookup"><span data-stu-id="55e57-110">The options are all the same.</span></span> <span data-ttu-id="55e57-111">Use a [Referência de linha de comando do MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) para obter informações sobre as opções disponíveis.</span><span class="sxs-lookup"><span data-stu-id="55e57-111">Use the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) to obtain information on the available options.</span></span> 

## <a name="examples"></a><span data-ttu-id="55e57-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="55e57-112">Examples</span></span>

<span data-ttu-id="55e57-113">Compile um projeto e suas dependências:</span><span class="sxs-lookup"><span data-stu-id="55e57-113">Build a project and its dependencies:</span></span>

`dotnet msbuild`

<span data-ttu-id="55e57-114">Compile um projeto e suas dependências usando a configuração da Versão:</span><span class="sxs-lookup"><span data-stu-id="55e57-114">Build a project and its dependencies using Release configuration:</span></span>

`dotnet msbuild /p:Configuration=Release`

<span data-ttu-id="55e57-115">Execute o destino de publicação e publique para o RID `osx.10.11-x64`:</span><span class="sxs-lookup"><span data-stu-id="55e57-115">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

<span data-ttu-id="55e57-116">Confira o projeto inteiro com todos os destinos incluídos pelo SDK:</span><span class="sxs-lookup"><span data-stu-id="55e57-116">See the whole project with all targets included by the SDK:</span></span>

`dotnet msbuild /pp`
