---
title: dotnet nuget desativar comando fonte
description: O comando dotnet nuget desabilita uma fonte existente em seus arquivos de configuração NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 54acb40b1944eaff347107e8f3439578ec8e0f3c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463575"
---
# <a name="dotnet-nuget-disable-source"></a><span data-ttu-id="7c6a4-103">dotnet nuget disable source</span><span class="sxs-lookup"><span data-stu-id="7c6a4-103">dotnet nuget disable source</span></span>

<span data-ttu-id="7c6a4-104">**Este artigo se aplica a:** ✔️ .NET Core 3.1.200 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="7c6a4-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="7c6a4-105">Nome</span><span class="sxs-lookup"><span data-stu-id="7c6a4-105">Name</span></span>

<span data-ttu-id="7c6a4-106">`dotnet nuget disable source`- Desabilite uma fonte NuGet.</span><span class="sxs-lookup"><span data-stu-id="7c6a4-106">`dotnet nuget disable source` - Disable a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="7c6a4-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="7c6a4-107">Synopsis</span></span>

```dotnetcli
dotnet nuget disable source <NAME> [--configfile <FILE>]

dotnet nuget disable source -h|--help
```

## <a name="description"></a><span data-ttu-id="7c6a4-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c6a4-108">Description</span></span>

<span data-ttu-id="7c6a4-109">O `dotnet nuget disable source` comando desativa uma fonte existente em seus arquivos de configuração NuGet.</span><span class="sxs-lookup"><span data-stu-id="7c6a4-109">The `dotnet nuget disable source` command disables an existing source in your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="7c6a4-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="7c6a4-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="7c6a4-111">Nome da fonte.</span><span class="sxs-lookup"><span data-stu-id="7c6a4-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="7c6a4-112">Opções</span><span class="sxs-lookup"><span data-stu-id="7c6a4-112">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="7c6a4-113">O arquivo de configuração NuGet.</span><span class="sxs-lookup"><span data-stu-id="7c6a4-113">The NuGet configuration file.</span></span> <span data-ttu-id="7c6a4-114">Se especificado, apenas as configurações deste arquivo serão usadas.</span><span class="sxs-lookup"><span data-stu-id="7c6a4-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="7c6a4-115">Se não for especificado, a hierarquia dos arquivos de configuração do diretório atual será usada.</span><span class="sxs-lookup"><span data-stu-id="7c6a4-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="7c6a4-116">Para obter mais informações, consulte [Configurações comuns de NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="7c6a4-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="7c6a4-117">Exemplos</span><span class="sxs-lookup"><span data-stu-id="7c6a4-117">Examples</span></span>

- <span data-ttu-id="7c6a4-118">Desativar uma fonte com `mySource`o nome de:</span><span class="sxs-lookup"><span data-stu-id="7c6a4-118">Disable a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget disable source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="7c6a4-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="7c6a4-119">See also</span></span>

- [<span data-ttu-id="7c6a4-120">Seções de origem do pacote em arquivos NuGet.config</span><span class="sxs-lookup"><span data-stu-id="7c6a4-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="7c6a4-121">comando fontes (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="7c6a4-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
