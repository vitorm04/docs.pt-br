---
title: comando de origem de lista de NuGet do dotnet
description: O comando dotnet do código-fonte do NuGet lista todas as fontes existentes dos arquivos de configuração do NuGet.
ms.date: 03/20/2020
ms.openlocfilehash: 071061e32aa1bf888e197ec6bf97f4e4f6859f0b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537881"
---
# <a name="dotnet-nuget-list-source"></a><span data-ttu-id="eeffc-103">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="eeffc-103">dotnet nuget list source</span></span>

<span data-ttu-id="eeffc-104">**Este artigo aplica-se a:** ✔️ SDK 3.1.200 do .NET Core e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="eeffc-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="eeffc-105">Name</span><span class="sxs-lookup"><span data-stu-id="eeffc-105">Name</span></span>

<span data-ttu-id="eeffc-106">`dotnet nuget list source` -Lista todas as fontes do NuGet configuradas.</span><span class="sxs-lookup"><span data-stu-id="eeffc-106">`dotnet nuget list source` - Lists all configured NuGet sources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="eeffc-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="eeffc-107">Synopsis</span></span>

```dotnetcli
dotnet nuget list source [--format [Detailed|Short]] [--configfile <FILE>]

dotnet nuget list source -h|--help
```

## <a name="description"></a><span data-ttu-id="eeffc-108">Description</span><span class="sxs-lookup"><span data-stu-id="eeffc-108">Description</span></span>

<span data-ttu-id="eeffc-109">O `dotnet nuget list source` comando lista todas as fontes existentes dos arquivos de configuração do NuGet.</span><span class="sxs-lookup"><span data-stu-id="eeffc-109">The `dotnet nuget list source` command lists all existing sources from your NuGet configuration files.</span></span>

## <a name="options"></a><span data-ttu-id="eeffc-110">Opções</span><span class="sxs-lookup"><span data-stu-id="eeffc-110">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="eeffc-111">O arquivo de configuração do NuGet.</span><span class="sxs-lookup"><span data-stu-id="eeffc-111">The NuGet configuration file.</span></span> <span data-ttu-id="eeffc-112">Se especificado, somente as configurações desse arquivo serão usadas.</span><span class="sxs-lookup"><span data-stu-id="eeffc-112">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="eeffc-113">Se não for especificado, a hierarquia de arquivos de configuração do diretório atual será usada.</span><span class="sxs-lookup"><span data-stu-id="eeffc-113">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="eeffc-114">Para obter mais informações, consulte [configurações comuns do NuGet](/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="eeffc-114">For more information, see [Common NuGet Configurations](/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`--format [Detailed|Short]`**

  <span data-ttu-id="eeffc-115">O formato da saída do comando de lista: `Detailed` (o padrão) e `Short` .</span><span class="sxs-lookup"><span data-stu-id="eeffc-115">The format of the list command output: `Detailed` (the default) and `Short`.</span></span>

## <a name="examples"></a><span data-ttu-id="eeffc-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="eeffc-116">Examples</span></span>

- <span data-ttu-id="eeffc-117">Listar fontes configuradas do diretório atual:</span><span class="sxs-lookup"><span data-stu-id="eeffc-117">List configured sources from the current directory:</span></span>

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a><span data-ttu-id="eeffc-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="eeffc-118">See also</span></span>

- [<span data-ttu-id="eeffc-119">Seções de origem do pacote em arquivos NuGet.config</span><span class="sxs-lookup"><span data-stu-id="eeffc-119">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="eeffc-120">comando Sources (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="eeffc-120">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
