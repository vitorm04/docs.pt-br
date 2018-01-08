---
title: "Comando dotnet nuget locals – CLI do .NET Core"
description: "O comando nuget dotnet locals limpa ou lista os recursos locais do NuGet, como cache de solicitação http-, cache temporário ou pasta de pacotes globais em todo o computador."
author: karann-msft
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: 9c8df8e457a9883b86abd0505c0c682d849bc7b1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="dea5a-103">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="dea5a-103">dotnet nuget locals</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="dea5a-104">Nome</span><span class="sxs-lookup"><span data-stu-id="dea5a-104">Name</span></span>

<span data-ttu-id="dea5a-105">`dotnet nuget locals`-Limpa ou lista os recursos locais do NuGet.</span><span class="sxs-lookup"><span data-stu-id="dea5a-105">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="dea5a-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="dea5a-106">Synopsis</span></span>

`dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output] [-h|--help]`

## <a name="description"></a><span data-ttu-id="dea5a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="dea5a-107">Description</span></span>

<span data-ttu-id="dea5a-108">O comando `dotnet nuget locals` limpa ou lista os recursos locais do NuGet no cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.</span><span class="sxs-lookup"><span data-stu-id="dea5a-108">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="dea5a-109">Arguments</span><span class="sxs-lookup"><span data-stu-id="dea5a-109">Arguments</span></span>

`CACHE_LOCATION`

<span data-ttu-id="dea5a-110">Um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="dea5a-110">One of the following values:</span></span>

* <span data-ttu-id="dea5a-111">`all` – Indica que a operação especificada aplica-se a todos os tipos cache: o cache de solicitação http, cache de pacotes globais e o cache temporário.</span><span class="sxs-lookup"><span data-stu-id="dea5a-111">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
* <span data-ttu-id="dea5a-112">`http-cache` – Indica que a operação especificada aplica-se apenas ao cache de solicitação http.</span><span class="sxs-lookup"><span data-stu-id="dea5a-112">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="dea5a-113">Outros locais de cache não são afetados.</span><span class="sxs-lookup"><span data-stu-id="dea5a-113">The other cache locations are not affected.</span></span>
* <span data-ttu-id="dea5a-114">`global-packages` – Indica que a operação especificada aplica-se apenas ao cache de pacotes globais.</span><span class="sxs-lookup"><span data-stu-id="dea5a-114">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="dea5a-115">Outros locais de cache não são afetados.</span><span class="sxs-lookup"><span data-stu-id="dea5a-115">The other cache locations are not affected.</span></span>
* <span data-ttu-id="dea5a-116">`temp` – Indica que a operação especificada aplica-se apenas ao cache temporário.</span><span class="sxs-lookup"><span data-stu-id="dea5a-116">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="dea5a-117">Outros locais de cache não são afetados.</span><span class="sxs-lookup"><span data-stu-id="dea5a-117">The other cache locations are not affected.</span></span>

## <a name="options"></a><span data-ttu-id="dea5a-118">Opções</span><span class="sxs-lookup"><span data-stu-id="dea5a-118">Options</span></span>

`-h|--help`

<span data-ttu-id="dea5a-119">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="dea5a-119">Prints out a short help for the command.</span></span>

`-c|--clear`

<span data-ttu-id="dea5a-120">A opção clear executa uma operação de limpeza no tipo de cache especificado.</span><span class="sxs-lookup"><span data-stu-id="dea5a-120">The clear option performs a clear operation on the specified cache type.</span></span> <span data-ttu-id="dea5a-121">O conteúdo dos diretórios de cache é excluído recursivamente.</span><span class="sxs-lookup"><span data-stu-id="dea5a-121">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="dea5a-122">O usuário/grupo executor deve ter permissão nos arquivos nos diretórios de cache.</span><span class="sxs-lookup"><span data-stu-id="dea5a-122">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="dea5a-123">Se não tiver, um erro será exibido indicando que os arquivos/pastas que não foram limpos.</span><span class="sxs-lookup"><span data-stu-id="dea5a-123">If not, an error is displayed indicating the files/folders which were not cleared.</span></span>

`-l|--list`

<span data-ttu-id="dea5a-124">A opção de lista é usada para exibir a localização do tipo de cache especificado.</span><span class="sxs-lookup"><span data-stu-id="dea5a-124">The list option is used to display the location of the specified cache type.</span></span> 

`--force-english-output`

<span data-ttu-id="dea5a-125">Força a saída da linha de comando em inglês.</span><span class="sxs-lookup"><span data-stu-id="dea5a-125">Forces command-line output in English.</span></span>

## <a name="examples"></a><span data-ttu-id="dea5a-126">Exemplos</span><span class="sxs-lookup"><span data-stu-id="dea5a-126">Examples</span></span>

<span data-ttu-id="dea5a-127">Exibe os caminhos de todos os diretórios de cache local (diretório de cache de http, o diretório de cache de pacotes globais e diretório de cache temporário):</span><span class="sxs-lookup"><span data-stu-id="dea5a-127">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals –l all`

<span data-ttu-id="dea5a-128">Exibe o caminho para o diretório local do cache de http:</span><span class="sxs-lookup"><span data-stu-id="dea5a-128">Displays the path for the local http-cache directory:</span></span>

`dotnet nuget locals --list http-cache`

<span data-ttu-id="dea5a-129">Limpa todos os arquivos dos diretórios de cache local (diretório de cache de http, o diretório de cache de pacotes globais e diretório de cache temporário):</span><span class="sxs-lookup"><span data-stu-id="dea5a-129">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

`dotnet nuget locals --clear all`

<span data-ttu-id="dea5a-130">Limpa todos os arquivos no diretório local de cache de pacotes globais:</span><span class="sxs-lookup"><span data-stu-id="dea5a-130">Clears all files in local global-packages cache directory:</span></span>

`dotnet nuget locals -c global-packages`

<span data-ttu-id="dea5a-131">Limpa todos os arquivos no diretório local de cache temporário:</span><span class="sxs-lookup"><span data-stu-id="dea5a-131">Clears all files in local temporary cache directory:</span></span>

`dotnet nuget locals -c temp`

## <a name="troubleshooting"></a><span data-ttu-id="dea5a-132">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="dea5a-132">Troubleshooting</span></span>

<span data-ttu-id="dea5a-133">Para saber mais sobre os problemas e erros mais comuns ao usar o comando `dotnet nuget locals`, veja [Gerenciamento do cache do NuGet](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="dea5a-133">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>