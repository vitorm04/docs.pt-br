---
title: comando dotnet habilitar origem do NuGet
description: O comando dotnet habilitar origem do NuGet habilita uma origem existente em seus arquivos de configuração do NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: b727844dd7d7cc82476e94a3f0ec4ecc6559d5ed
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537928"
---
# <a name="dotnet-nuget-enable-source"></a><span data-ttu-id="afb05-103">dotnet nuget enable source</span><span class="sxs-lookup"><span data-stu-id="afb05-103">dotnet nuget enable source</span></span>

<span data-ttu-id="afb05-104">**Este artigo aplica-se a:** ✔️ SDK 3.1.200 do .NET Core e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="afb05-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="afb05-105">Name</span><span class="sxs-lookup"><span data-stu-id="afb05-105">Name</span></span>

<span data-ttu-id="afb05-106">`dotnet nuget enable source` -Habilitar uma origem do NuGet.</span><span class="sxs-lookup"><span data-stu-id="afb05-106">`dotnet nuget enable source` - Enable a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="afb05-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="afb05-107">Synopsis</span></span>

```dotnetcli
dotnet nuget enable source <NAME> [--configfile <FILE>]

dotnet nuget enable source -h|--help
```

## <a name="description"></a><span data-ttu-id="afb05-108">Description</span><span class="sxs-lookup"><span data-stu-id="afb05-108">Description</span></span>

<span data-ttu-id="afb05-109">O `dotnet nuget enable source` comando habilita uma fonte existente em seus arquivos de configuração do NuGet.</span><span class="sxs-lookup"><span data-stu-id="afb05-109">The `dotnet nuget enable source` command enables an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="afb05-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="afb05-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="afb05-111">Nome da origem.</span><span class="sxs-lookup"><span data-stu-id="afb05-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="afb05-112">Opções</span><span class="sxs-lookup"><span data-stu-id="afb05-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="afb05-113">O arquivo de configuração do NuGet.</span><span class="sxs-lookup"><span data-stu-id="afb05-113">The NuGet configuration file.</span></span> <span data-ttu-id="afb05-114">Se especificado, somente as configurações desse arquivo serão usadas.</span><span class="sxs-lookup"><span data-stu-id="afb05-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="afb05-115">Se não for especificado, a hierarquia de arquivos de configuração do diretório atual será usada.</span><span class="sxs-lookup"><span data-stu-id="afb05-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="afb05-116">Para obter mais informações, consulte [configurações comuns do NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="afb05-116">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="afb05-117">Exemplos</span><span class="sxs-lookup"><span data-stu-id="afb05-117">Examples</span></span>

- <span data-ttu-id="afb05-118">Habilite uma fonte com o nome de `mySource` :</span><span class="sxs-lookup"><span data-stu-id="afb05-118">Enable a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget enable source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="afb05-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="afb05-119">See also</span></span>

- [<span data-ttu-id="afb05-120">Seções de origem do pacote em arquivos NuGet.config</span><span class="sxs-lookup"><span data-stu-id="afb05-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="afb05-121">comando Sources (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="afb05-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
