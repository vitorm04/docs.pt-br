---
title: Comando dotnet nuget locals
description: O comando nuget dotnet locals limpa ou lista os recursos locais do NuGet, como cache de solicitação http-, cache temporário ou pasta de pacotes globais em todo o computador.
author: karann-msft
ms.date: 02/14/2020
ms.openlocfilehash: 5b421b5058528a93c7be58eef2932937cc9cc12d
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463526"
---
# <a name="dotnet-nuget-locals"></a><span data-ttu-id="7d738-103">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="7d738-103">dotnet nuget locals</span></span>

<span data-ttu-id="7d738-104">**Este artigo se aplica a:** ✔️ .NET Core 2.x SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="7d738-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="7d738-105">Nome</span><span class="sxs-lookup"><span data-stu-id="7d738-105">Name</span></span>

<span data-ttu-id="7d738-106">`dotnet nuget locals`-Limpa ou lista os recursos locais do NuGet.</span><span class="sxs-lookup"><span data-stu-id="7d738-106">`dotnet nuget locals` - Clears or lists local NuGet resources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7d738-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="7d738-107">Synopsis</span></span>

```dotnetcli
dotnet nuget locals <CACHE_LOCATION> [(-c|--clear)|(-l|--list)] [--force-english-output]

dotnet nuget locals -h|--help
```

## <a name="description"></a><span data-ttu-id="7d738-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="7d738-108">Description</span></span>

<span data-ttu-id="7d738-109">O comando `dotnet nuget locals` limpa ou lista os recursos locais do NuGet no cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.</span><span class="sxs-lookup"><span data-stu-id="7d738-109">The `dotnet nuget locals` command clears or lists local NuGet resources in the http-request cache, temporary cache, or machine-wide global packages folder.</span></span>

## <a name="arguments"></a><span data-ttu-id="7d738-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="7d738-110">Arguments</span></span>

- **`CACHE_LOCATION`**

  <span data-ttu-id="7d738-111">O local do cache a ser listado ou limpo.</span><span class="sxs-lookup"><span data-stu-id="7d738-111">The cache location to list or clear.</span></span> <span data-ttu-id="7d738-112">Aceita um dos seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="7d738-112">It accepts one of the following values:</span></span>

  * <span data-ttu-id="7d738-113">`all` – Indica que a operação especificada aplica-se a todos os tipos cache: o cache de solicitação http, cache de pacotes globais e o cache temporário.</span><span class="sxs-lookup"><span data-stu-id="7d738-113">`all` - Indicates that the specified operation is applied to all cache types: http-request cache, global packages cache, and the temporary cache.</span></span>
  * <span data-ttu-id="7d738-114">`http-cache` – Indica que a operação especificada aplica-se apenas ao cache de solicitação http.</span><span class="sxs-lookup"><span data-stu-id="7d738-114">`http-cache` - Indicates that the specified operation is applied only to the http-request cache.</span></span> <span data-ttu-id="7d738-115">Os outros locais do cache não são afetados.</span><span class="sxs-lookup"><span data-stu-id="7d738-115">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="7d738-116">`global-packages` – Indica que a operação especificada aplica-se apenas ao cache de pacotes globais.</span><span class="sxs-lookup"><span data-stu-id="7d738-116">`global-packages` - Indicates that the specified operation is applied only to the global packages cache.</span></span> <span data-ttu-id="7d738-117">Os outros locais do cache não são afetados.</span><span class="sxs-lookup"><span data-stu-id="7d738-117">The other cache locations aren't affected.</span></span>
  * <span data-ttu-id="7d738-118">`temp` – Indica que a operação especificada aplica-se apenas ao cache temporário.</span><span class="sxs-lookup"><span data-stu-id="7d738-118">`temp` - Indicates that the specified operation is applied only to the temporary cache.</span></span> <span data-ttu-id="7d738-119">Os outros locais do cache não são afetados.</span><span class="sxs-lookup"><span data-stu-id="7d738-119">The other cache locations aren't affected.</span></span>

## <a name="options"></a><span data-ttu-id="7d738-120">Opções</span><span class="sxs-lookup"><span data-stu-id="7d738-120">Options</span></span>

- **`--force-english-output`**

  <span data-ttu-id="7d738-121">Força a execução do aplicativo usando uma cultura invariável com base em inglês.</span><span class="sxs-lookup"><span data-stu-id="7d738-121">Forces the application to run using an invariant, English-based culture.</span></span>

- **`-h|--help`**

  <span data-ttu-id="7d738-122">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="7d738-122">Prints out a short help for the command.</span></span>

- **`-c|--clear`**

  <span data-ttu-id="7d738-123">A opção clear executa uma operação de limpeza no tipo de cache especificado.</span><span class="sxs-lookup"><span data-stu-id="7d738-123">The clear option executes a clear operation on the specified cache type.</span></span> <span data-ttu-id="7d738-124">O conteúdo dos diretórios de cache é excluído recursivamente.</span><span class="sxs-lookup"><span data-stu-id="7d738-124">The contents of the cache directories are deleted recursively.</span></span> <span data-ttu-id="7d738-125">O usuário/grupo executor deve ter permissão nos arquivos nos diretórios de cache.</span><span class="sxs-lookup"><span data-stu-id="7d738-125">The executing user/group must have permission to the files in the cache directories.</span></span> <span data-ttu-id="7d738-126">Caso contrário, um erro é exibido, indicando as pastas/os arquivos que não foram limpos.</span><span class="sxs-lookup"><span data-stu-id="7d738-126">If not, an error is displayed indicating the files/folders that weren't cleared.</span></span>

- **`-l|--list`**

  <span data-ttu-id="7d738-127">A opção de lista é usada para exibir a localização do tipo de cache especificado.</span><span class="sxs-lookup"><span data-stu-id="7d738-127">The list option is used to display the location of the specified cache type.</span></span>

## <a name="examples"></a><span data-ttu-id="7d738-128">Exemplos</span><span class="sxs-lookup"><span data-stu-id="7d738-128">Examples</span></span>

- <span data-ttu-id="7d738-129">Exibe os caminhos de todos os diretórios de cache local (diretório de cache de http, o diretório de cache de pacotes globais e diretório de cache temporário):</span><span class="sxs-lookup"><span data-stu-id="7d738-129">Displays the paths of all the local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```dotnetcli
  dotnet nuget locals all –l
  ```

- <span data-ttu-id="7d738-130">Exibe o caminho para o diretório local do cache de http:</span><span class="sxs-lookup"><span data-stu-id="7d738-130">Displays the path for the local http-cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals http-cache --list
  ```

- <span data-ttu-id="7d738-131">Limpa todos os arquivos dos diretórios de cache local (diretório de cache de http, o diretório de cache de pacotes globais e diretório de cache temporário):</span><span class="sxs-lookup"><span data-stu-id="7d738-131">Clears all files from all local cache directories (http-cache directory, global-packages cache directory, and temporary cache directory):</span></span>

  ```dotnetcli
  dotnet nuget locals all --clear
  ```

- <span data-ttu-id="7d738-132">Limpa todos os arquivos no diretório local de cache de pacotes globais:</span><span class="sxs-lookup"><span data-stu-id="7d738-132">Clears all files in local global-packages cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals global-packages -c
  ```

- <span data-ttu-id="7d738-133">Limpa todos os arquivos no diretório local de cache temporário:</span><span class="sxs-lookup"><span data-stu-id="7d738-133">Clears all files in local temporary cache directory:</span></span>

  ```dotnetcli
  dotnet nuget locals temp -c
  ```

## <a name="troubleshooting"></a><span data-ttu-id="7d738-134">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="7d738-134">Troubleshooting</span></span>

<span data-ttu-id="7d738-135">Para saber mais sobre os problemas e erros mais comuns ao usar o comando `dotnet nuget locals`, veja [Gerenciamento do cache do NuGet](/nuget/consume-packages/managing-the-nuget-cache).</span><span class="sxs-lookup"><span data-stu-id="7d738-135">For information on common problems and errors while using the `dotnet nuget locals` command, see [Managing the NuGet cache](/nuget/consume-packages/managing-the-nuget-cache).</span></span>
