---
title: Comando dotnet msbuild – CLI do .NET Core
description: O comando dotnet msbuild fornece acesso à linha de comando MSBuild.
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 9e6f8b3063b4cd2a3a36cae8839d6f83e0466e03
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-msbuild"></a><span data-ttu-id="ecadb-103">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="ecadb-103">dotnet msbuild</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="ecadb-104">Nome</span><span class="sxs-lookup"><span data-stu-id="ecadb-104">Name</span></span>

<span data-ttu-id="ecadb-105">`dotnet msbuild` – Compila um projeto e todas as suas dependências.</span><span class="sxs-lookup"><span data-stu-id="ecadb-105">`dotnet msbuild` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ecadb-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="ecadb-106">Synopsis</span></span>

`dotnet msbuild <msbuild_arguments> [-h]`

## <a name="description"></a><span data-ttu-id="ecadb-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="ecadb-107">Description</span></span>

<span data-ttu-id="ecadb-108">O comando `dotnet msbuild` permite o acesso a um MSBuild totalmente funcional.</span><span class="sxs-lookup"><span data-stu-id="ecadb-108">The `dotnet msbuild` command allows access to a fully functional MSBuild.</span></span>

<span data-ttu-id="ecadb-109">O comando tem exatamente os mesmos recursos do cliente de linha de comando existente do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="ecadb-109">The command has the exact same capabilities as existing MSBuild command-line client.</span></span> <span data-ttu-id="ecadb-110">As opções são todas iguais.</span><span class="sxs-lookup"><span data-stu-id="ecadb-110">The options are all the same.</span></span> <span data-ttu-id="ecadb-111">Use a [Referência de linha de comando do MSBuild](/visualstudio/msbuild/msbuild-command-line-reference) para obter informações sobre as opções disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ecadb-111">Use the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference) to obtain information on the available options.</span></span> 

## <a name="examples"></a><span data-ttu-id="ecadb-112">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ecadb-112">Examples</span></span>

<span data-ttu-id="ecadb-113">Compile um projeto e suas dependências:</span><span class="sxs-lookup"><span data-stu-id="ecadb-113">Build a project and its dependencies:</span></span>

`dotnet msbuild`

<span data-ttu-id="ecadb-114">Compile um projeto e suas dependências usando a configuração da Versão:</span><span class="sxs-lookup"><span data-stu-id="ecadb-114">Build a project and its dependencies using Release configuration:</span></span>

`dotnet msbuild /p:Configuration=Release`

<span data-ttu-id="ecadb-115">Execute o destino de publicação e publique para o RID `osx.10.11-x64`:</span><span class="sxs-lookup"><span data-stu-id="ecadb-115">Run the publish target and publish for the `osx.10.11-x64` RID:</span></span>

`dotnet msbuild /t:Publish /p:RuntimeIdentifiers=osx.10.11-x64`

<span data-ttu-id="ecadb-116">Confira o projeto inteiro com todos os destinos incluídos pelo SDK:</span><span class="sxs-lookup"><span data-stu-id="ecadb-116">See the whole project with all targets included by the SDK:</span></span>

`dotnet msbuild /pp`
