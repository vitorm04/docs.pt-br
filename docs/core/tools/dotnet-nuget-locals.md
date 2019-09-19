---
title: Comando dotnet nuget locals
description: O comando nuget dotnet locals limpa ou lista os recursos locais do NuGet, como cache de solicitação http-, cache temporário ou pasta de pacotes globais em todo o computador.
author: karann-msft
ms.date: 06/26/2019
ms.openlocfilehash: 482e841d3b402084eb8c7f2456779f1600a5dd19
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117623"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="f76c8-103">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="f76c8-103">dotnet nuget locals</span></span>

<span data-ttu-id="f76c8-104">**Este tópico aplica-se a: ✓** SDK do .NET Core 1.x e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="f76c8-104">**This topic applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="f76c8-105">Nome</span><span class="sxs-lookup"><span data-stu-id="f76c8-105">Name</span></span>

<span data-ttu-id="f76c8-106">`dotnet nuget locals`-Limpa ou lista os recursos locais do NuGet.</span><span class="sxs-lookup"><span data-stu-id="f76c8-106">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f76c8-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="f76c8-107">Synopsis</span></span>

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]
dotnet nuget locals [-h|--help]
```

## <a name="description"></a><span data-ttu-id="f76c8-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="f76c8-108">Description</span></span>

<span data-ttu-id="f76c8-109">O comando `dotnet nuget locals` limpa ou lista os recursos locais do NuGet no cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.</span><span class="sxs-lookup"><span data-stu-id="f76c8-109">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="f76c8-110">Arguments</span><span class="sxs-lookup"><span data-stu-id="f76c8-110">Arguments</span></span>

* **`CACHE_LOCATION`**

  <span data-ttu-id="f76c8-111">O local do cache a ser listado ou limpo.</span><span class="sxs-lookup"><span data-stu-id="f76c8-111">The cache location to list or clear.</span></span> <span data-ttu-id="f76c8-112">Aceita um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="f76c8-112">It accepts one of the following values:</span></span>

  * <span data-ttu-id="f76c8-113">`all` – Indica que a operação especificada aplica-se a todos os tipos cache: o cache de solicitação http, cache de pacotes globais e o cache temporário.</span><span class="sxs-lookup"><span data-stu-id="f76c8-113">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
  * <span data-ttu-id="f76c8-114">`http-cache` – Indica que a operação especificada aplica-se apenas ao cache de solicitação http.</span><span class="sxs-lookup"><span data-stu-id="f76c8-114">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="f76c8-115">Os outros locais do cache não são afetados.</span><span class="sxs-lookup"><span data-stu-id="f76c8-115">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="f76c8-116">`global-packages` – Indica que a operação especificada aplica-se apenas ao cache de pacotes globais.</span><span class="sxs-lookup"><span data-stu-id="f76c8-116">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="f76c8-117">Os outros locais do cache não são afetados.</span><span class="sxs-lookup"><span data-stu-id="f76c8-117">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="f76c8-118">`temp` – Indica que a operação especificada aplica-se apenas ao cache temporário.</span><span class="sxs-lookup"><span data-stu-id="f76c8-118">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="f76c8-119">Os outros locais do cache não são afetados.</span><span class="sxs-lookup"><span data-stu-id="f76c8-119">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="f76c8-120">Opções</span><span class="sxs-lookup"><span data-stu-id="f76c8-120">Options</span></span>

* **`--force-english-output`**

  <span data-ttu-id="f76c8-121">Força a execução do aplicativo usando uma cultura invariável com base em inglês.</span><span class="sxs-lookup"><span data-stu-id="f76c8-121">Forces the application to run using an invariant, English-based culture.</span></span>

* **`-h|--help`**

  <span data-ttu-id="f76c8-122">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="f76c8-122">Prints out a short help for the command.</span></span>

* **`-c|--clear`**

  <span data-ttu-id="f76c8-123">A opção clear executa uma operação de limpeza no tipo de cache especificado.</span><span class="sxs-lookup"><span data-stu-id="f76c8-123">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="f76c8-124">O conteúdo dos diretórios de cache é excluído recursivamente.</span><span class="sxs-lookup"><span data-stu-id="f76c8-124">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="f76c8-125">O usuário/grupo executor deve ter permissão nos arquivos nos diretórios de cache.</span><span class="sxs-lookup"><span data-stu-id="f76c8-125">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="f76c8-126">Caso contrário, um erro é exibido, indicando as pastas/os arquivos que não foram limpos.</span><span class="sxs-lookup"><span data-stu-id="f76c8-126">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

* **`-l|--list`**

  <span data-ttu-id="f76c8-127">A opção de lista é usada para exibir a localização do tipo de cache especificado.</span><span class="sxs-lookup"><span data-stu-id="f76c8-127">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="f76c8-128">Exemplos</span><span class="sxs-lookup"><span data-stu-id="f76c8-128">Examples</span></span>

* <span data-ttu-id="f76c8-129">Exibe os caminhos de todos os diretórios de cache local (diretório de cache de http, o diretório de cache de pacotes globais e diretório de cache temporário):</span><span class="sxs-lookup"><span data-stu-id="f76c8-129">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```dotnetcli
  dotnet nuget locals –l all
  ```

* <span data-ttu-id="f76c8-130">Exibe o caminho para o diretório local do cache de http:</span><span class="sxs-lookup"><span data-stu-id="f76c8-130">Displays the path for the local http-cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals --list http-cache
  ```

* <span data-ttu-id="f76c8-131">Limpa todos os arquivos dos diretórios de cache local (diretório de cache de http, o diretório de cache de pacotes globais e diretório de cache temporário):</span><span class="sxs-lookup"><span data-stu-id="f76c8-131">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```dotnetcli
  dotnet nuget locals --clear all
  ```

* <span data-ttu-id="f76c8-132">Limpa todos os arquivos no diretório local de cache de pacotes globais:</span><span class="sxs-lookup"><span data-stu-id="f76c8-132">Clears all files in local global-packages cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals -c global-packages
  ```

* <span data-ttu-id="f76c8-133">Limpa todos os arquivos no diretório local de cache temporário:</span><span class="sxs-lookup"><span data-stu-id="f76c8-133">Clears all files in local temporary cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals -c temp
  ```

## <a name="troubleshooting"></a><span data-ttu-id="f76c8-134">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="f76c8-134">Troubleshooting</span></span>

<span data-ttu-id="f76c8-135">Para saber mais sobre os problemas e erros mais comuns ao usar o comando `dotnet nuget locals`, veja [Gerenciamento do cache do NuGet](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="f76c8-135">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>
