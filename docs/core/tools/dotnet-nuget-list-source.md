---
title: dotnet nuget comando fonte de lista
description: O comando dotnet nuget list list all existing sources from your NuGet configuration files.
ms.date: 03/20/2020
ms.openlocfilehash: 8b14413949bd60ddeed977d19eec9bb99982da70
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463548"
---
# <a name="dotnet-nuget-list-source"></a><span data-ttu-id="2af3a-103">dotnet nuget list source</span><span class="sxs-lookup"><span data-stu-id="2af3a-103">dotnet nuget list source</span></span>

<span data-ttu-id="2af3a-104">**Este artigo se aplica a:** ✔️ .NET Core 3.1.200 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="2af3a-104">**This article applies to:** ✔️ .NET Core 3.1.200 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="2af3a-105">Nome</span><span class="sxs-lookup"><span data-stu-id="2af3a-105">Name</span></span>

<span data-ttu-id="2af3a-106">`dotnet nuget list source`- Lista todas as fontes nuget configuradas.</span><span class="sxs-lookup"><span data-stu-id="2af3a-106">`dotnet nuget list source` - Lists all configured NuGet sources.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2af3a-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="2af3a-107">Synopsis</span></span>

```dotnetcli
dotnet nuget list source [--format [Detailed|Short]] [--configfile <FILE>]

dotnet nuget list source -h|--help
```

## <a name="description"></a><span data-ttu-id="2af3a-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="2af3a-108">Description</span></span>

<span data-ttu-id="2af3a-109">O `dotnet nuget list source` comando lista todas as fontes existentes dos arquivos de configuração do NuGet.</span><span class="sxs-lookup"><span data-stu-id="2af3a-109">The `dotnet nuget list source` command lists all existing sources from your NuGet configuration files.</span></span>

## <a name="options"></a><span data-ttu-id="2af3a-110">Opções</span><span class="sxs-lookup"><span data-stu-id="2af3a-110">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="2af3a-111">O arquivo de configuração NuGet.</span><span class="sxs-lookup"><span data-stu-id="2af3a-111">The NuGet configuration file.</span></span> <span data-ttu-id="2af3a-112">Se especificado, apenas as configurações deste arquivo serão usadas.</span><span class="sxs-lookup"><span data-stu-id="2af3a-112">If specified, only the settings from this file will be used.</span></span> <span data-ttu-id="2af3a-113">Se não for especificado, a hierarquia dos arquivos de configuração do diretório atual será usada.</span><span class="sxs-lookup"><span data-stu-id="2af3a-113">If not specified, the hierarchy of configuration files from the current directory will be used.</span></span> <span data-ttu-id="2af3a-114">Para obter mais informações, consulte [Configurações comuns de NuGet](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span><span class="sxs-lookup"><span data-stu-id="2af3a-114">For more information, see [Common NuGet Configurations](https://docs.microsoft.com/nuget/consume-packages/configuring-nuget-behavior).</span></span>

- **`--format [Detailed|Short]`**

  <span data-ttu-id="2af3a-115">O formato da saída `Detailed` de comando da `Short`lista: (o padrão) e .</span><span class="sxs-lookup"><span data-stu-id="2af3a-115">The format of the list command output: `Detailed` (the default) and `Short`.</span></span>

## <a name="examples"></a><span data-ttu-id="2af3a-116">Exemplos</span><span class="sxs-lookup"><span data-stu-id="2af3a-116">Examples</span></span>

- <span data-ttu-id="2af3a-117">Listar fontes configuradas do diretório atual:</span><span class="sxs-lookup"><span data-stu-id="2af3a-117">List configured sources from the current directory:</span></span>

  ```dotnetcli
  dotnet nuget list source
  ```

## <a name="see-also"></a><span data-ttu-id="2af3a-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="2af3a-118">See also</span></span>

- [<span data-ttu-id="2af3a-119">Seções de origem do pacote em arquivos NuGet.config</span><span class="sxs-lookup"><span data-stu-id="2af3a-119">Package source sections in NuGet.config files</span></span>](/nuget/reference/nuget-config-file#package-source-sections)

- [<span data-ttu-id="2af3a-120">comando fontes (nuget.exe)</span><span class="sxs-lookup"><span data-stu-id="2af3a-120">sources command (nuget.exe)</span></span>](/nuget/reference/cli-reference/cli-ref-sources)
