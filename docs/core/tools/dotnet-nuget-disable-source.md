---
title: dotnet nuget desativar comando fonte
description: O comando dotnet nuget desabilita uma fonte existente em seus arquivos de configuração NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 5aa16c842bcddeead180fdeec3d9dcdda33f7ed9
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80148550"
---
# <a name="dotnet-nuget-disable-source"></a><span data-ttu-id="5ffe5-103">dotnet nuget desativar fonte</span><span class="sxs-lookup"><span data-stu-id="5ffe5-103">dotnet nuget disable source</span></span>

<span data-ttu-id="5ffe5-104">**Este artigo se aplica a:** ✔️ .NET Core 3.1.200 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="5ffe5-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="5ffe5-105">Nome</span><span class="sxs-lookup"><span data-stu-id="5ffe5-105">Name</span></span>

<span data-ttu-id="5ffe5-106">`dotnet nuget disable source`- Desabilite uma fonte NuGet.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-106">`dotnet nuget disable source` - Disable a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="5ffe5-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="5ffe5-107">Synopsis</span></span>

```dotnetcli
dotnet nuget disable source <NAME> [--configfile]
dotnet nuget disable source [-h|--help]
```

## <a name="description"></a><span data-ttu-id="5ffe5-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ffe5-108">Description</span></span>

<span data-ttu-id="5ffe5-109">O `dotnet nuget disable source` comando desativa uma fonte existente em seus arquivos de configuração NuGet.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-109">The `dotnet nuget disable source` command disables an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="5ffe5-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="5ffe5-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="5ffe5-111">Nome da fonte.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="5ffe5-112">Opções</span><span class="sxs-lookup"><span data-stu-id="5ffe5-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="5ffe5-113">O arquivo de configuração NuGet.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-113">The NuGet configuration file.</span></span> <span data-ttu-id="5ffe5-114">Se especificado, apenas as configurações deste arquivo serão usadas.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="5ffe5-115">Se não for especificado, a hierarquia dos arquivos de configuração do diretório atual será usada.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="5ffe5-116">Para obter mais informações, consulte [Configurações comuns de NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="5ffe5-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="5ffe5-117">Exemplos</span><span class="sxs-lookup"><span data-stu-id="5ffe5-117">Examples</span></span>

- <span data-ttu-id="5ffe5-118">Desativar uma fonte com `mySource`o nome de:</span><span class="sxs-lookup"><span data-stu-id="5ffe5-118">Disable a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget disable source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="5ffe5-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="5ffe5-119">See also</span></span>

- [<span data-ttu-id="5ffe5-120">Seções de origem do pacote em arquivos NuGet.config</span><span class="sxs-lookup"><span data-stu-id="5ffe5-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="5ffe5-121">comando fontes (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="5ffe5-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
