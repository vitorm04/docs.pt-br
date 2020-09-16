---
title: comando de remoção de origem do NuGet do dotnet
description: O comando dotnet NuGet remove Source remove uma fonte existente dos arquivos de configuração do NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: b5575c31c0008d6e3e5a2e52906a076614217dd0
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537880"
---
# <a name="dotnet-nuget-remove-source"></a><span data-ttu-id="c9b5b-103">dotnet nuget remove source</span><span class="sxs-lookup"><span data-stu-id="c9b5b-103">dotnet nuget remove source</span></span>

<span data-ttu-id="c9b5b-104">**Este artigo aplica-se a:** ✔️ SDK 3.1.200 do .NET Core e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="c9b5b-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="c9b5b-105">Name</span><span class="sxs-lookup"><span data-stu-id="c9b5b-105">Name</span></span>

<span data-ttu-id="c9b5b-106">`dotnet nuget remove source` -Remover uma origem do NuGet.</span><span class="sxs-lookup"><span data-stu-id="c9b5b-106">`dotnet nuget remove source` - Remove a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="c9b5b-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="c9b5b-107">Synopsis</span></span>

```dotnetcli
dotnet nuget remove source <NAME> [--configfile <FILE>]

dotnet nuget remove source -h|--help
```

## <a name="description"></a><span data-ttu-id="c9b5b-108">Description</span><span class="sxs-lookup"><span data-stu-id="c9b5b-108">Description</span></span>

<span data-ttu-id="c9b5b-109">O `dotnet nuget remove source` comando Remove uma fonte existente dos arquivos de configuração do NuGet.</span><span class="sxs-lookup"><span data-stu-id="c9b5b-109">The `dotnet nuget remove source` command removes an existing source from your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="c9b5b-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="c9b5b-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="c9b5b-111">Nome da origem.</span><span class="sxs-lookup"><span data-stu-id="c9b5b-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="c9b5b-112">Opções</span><span class="sxs-lookup"><span data-stu-id="c9b5b-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="c9b5b-113">O arquivo de configuração do NuGet.</span><span class="sxs-lookup"><span data-stu-id="c9b5b-113">The NuGet configuration file.</span></span> <span data-ttu-id="c9b5b-114">Se especificado, somente as configurações desse arquivo serão usadas.</span><span class="sxs-lookup"><span data-stu-id="c9b5b-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="c9b5b-115">Se não for especificado, a hierarquia de arquivos de configuração do diretório atual será usada.</span><span class="sxs-lookup"><span data-stu-id="c9b5b-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="c9b5b-116">Para obter mais informações, consulte [configurações comuns do NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="c9b5b-116">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="c9b5b-117">Exemplos</span><span class="sxs-lookup"><span data-stu-id="c9b5b-117">Examples</span></span>

- <span data-ttu-id="c9b5b-118">Remova uma fonte com o nome de `mySource` :</span><span class="sxs-lookup"><span data-stu-id="c9b5b-118">Remove a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget remove source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="c9b5b-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="c9b5b-119">See also</span></span>

- [<span data-ttu-id="c9b5b-120">Seções de origem do pacote em arquivos NuGet.config</span><span class="sxs-lookup"><span data-stu-id="c9b5b-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="c9b5b-121">comando Sources (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="c9b5b-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
