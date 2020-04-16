---
title: dotnet nuget remover comando fonte
description: O comando dotnet nuget remove source remove uma fonte existente de seus arquivos de configuração NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: b259873e1885644b272136fa31414410bdfd9f27
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463487"
---
# <a name="dotnet-nuget-remove-source"></a><span data-ttu-id="b0220-103">dotnet nuget remove source</span><span class="sxs-lookup"><span data-stu-id="b0220-103">dotnet nuget remove source</span></span>

<span data-ttu-id="b0220-104">**Este artigo se aplica a:** ✔️ .NET Core 3.1.200 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="b0220-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="b0220-105">Nome</span><span class="sxs-lookup"><span data-stu-id="b0220-105">Name</span></span>

<span data-ttu-id="b0220-106">`dotnet nuget remove source`- Remova uma fonte NuGet.</span><span class="sxs-lookup"><span data-stu-id="b0220-106">`dotnet nuget remove source` - Remove a NuGet source.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b0220-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="b0220-107">Synopsis</span></span>

```dotnetcli
dotnet nuget remove source <NAME> [--configfile <FILE>]

dotnet nuget remove source -h|--help
```

## <a name="description"></a><span data-ttu-id="b0220-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="b0220-108">Description</span></span>

<span data-ttu-id="b0220-109">O `dotnet nuget remove source` comando remove uma fonte existente dos arquivos de configuração nuGet.</span><span class="sxs-lookup"><span data-stu-id="b0220-109">The `dotnet nuget remove source` command removes an existing source from your NuGet configuration files.</span></span>

## <a name="arguments"></a><span data-ttu-id="b0220-110">Argumentos</span><span class="sxs-lookup"><span data-stu-id="b0220-110">Arguments</span></span>

- **`NAME`**

  <span data-ttu-id="b0220-111">Nome da fonte.</span><span class="sxs-lookup"><span data-stu-id="b0220-111">Name of the source.</span></span>

## <a name="options"></a><span data-ttu-id="b0220-112">Opções</span><span class="sxs-lookup"><span data-stu-id="b0220-112">Options</span></span>

- **`--configfile`**

  <span data-ttu-id="b0220-113">O arquivo de configuração NuGet.</span><span class="sxs-lookup"><span data-stu-id="b0220-113">The NuGet configuration file.</span></span> <span data-ttu-id="b0220-114">Se especificado, apenas as configurações deste arquivo serão usadas.</span><span class="sxs-lookup"><span data-stu-id="b0220-114">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="b0220-115">Se não for especificado, a hierarquia dos arquivos de configuração do diretório atual será usada.</span><span class="sxs-lookup"><span data-stu-id="b0220-115">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="b0220-116">Para obter mais informações, consulte [Configurações comuns de NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="b0220-116">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

## <a name="examples"></a><span data-ttu-id="b0220-117">Exemplos</span><span class="sxs-lookup"><span data-stu-id="b0220-117">Examples</span></span>

- <span data-ttu-id="b0220-118">Remover uma fonte `mySource`com o nome de:</span><span class="sxs-lookup"><span data-stu-id="b0220-118">Remove a source with name of `mySource`:</span></span>

  ```dotnetcli
  dotnet nuget remove source mySource
  ```

## <a name="see-also"></a><span data-ttu-id="b0220-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="b0220-119">See also</span></span>

- [<span data-ttu-id="b0220-120">Seções de origem do pacote em arquivos NuGet.config</span><span class="sxs-lookup"><span data-stu-id="b0220-120">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="b0220-121">comando fontes (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="b0220-121">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
