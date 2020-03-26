---
ms.openlocfilehash: 4340ed7444681b4601dea50c93926b0ee0c07eec
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134097"
---

<span data-ttu-id="47664-101">Os pacotes adicionados aos feeds do gerenciador `{product}-{type}-{version}`de pacotes são nomeados em um formato hackeável: .</span><span class="sxs-lookup"><span data-stu-id="47664-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="47664-102">**Produto**</span><span class="sxs-lookup"><span data-stu-id="47664-102">**product**</span></span>\
<span data-ttu-id="47664-103">O tipo de produto .NET a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="47664-103">The type of .NET product to install.</span></span> <span data-ttu-id="47664-104">As opções válidas são:</span><span class="sxs-lookup"><span data-stu-id="47664-104">Valid options are:</span></span>

  - <span data-ttu-id="47664-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="47664-105">dotnet</span></span>
  - <span data-ttu-id="47664-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="47664-106">aspnetcore</span></span>

- <span data-ttu-id="47664-107">**Tipo**</span><span class="sxs-lookup"><span data-stu-id="47664-107">**type**</span></span>\
<span data-ttu-id="47664-108">Escolhe o SDK ou o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="47664-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="47664-109">As opções válidas são:</span><span class="sxs-lookup"><span data-stu-id="47664-109">Valid options are:</span></span>

  - <span data-ttu-id="47664-110">sdk</span><span class="sxs-lookup"><span data-stu-id="47664-110">sdk</span></span>
  - <span data-ttu-id="47664-111">runtime</span><span class="sxs-lookup"><span data-stu-id="47664-111">runtime</span></span>

- <span data-ttu-id="47664-112">**Versão**</span><span class="sxs-lookup"><span data-stu-id="47664-112">**version**</span></span>\
<span data-ttu-id="47664-113">A versão do SDK ou tempo de execução para instalar.</span><span class="sxs-lookup"><span data-stu-id="47664-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="47664-114">Este artigo sempre dará as instruções para a versão mais recente suportada.</span><span class="sxs-lookup"><span data-stu-id="47664-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="47664-115">Opções válidas são qualquer versão lançada, tais como:</span><span class="sxs-lookup"><span data-stu-id="47664-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="47664-116">3.1</span><span class="sxs-lookup"><span data-stu-id="47664-116">3.1</span></span>
  - <span data-ttu-id="47664-117">3.0</span><span class="sxs-lookup"><span data-stu-id="47664-117">3.0</span></span>
  - <span data-ttu-id="47664-118">2.1</span><span class="sxs-lookup"><span data-stu-id="47664-118">2.1</span></span>

  <span data-ttu-id="47664-119">É possível que o SDK/tempo de execução que você está tentando baixar não esteja disponível para sua distribuição Linux.</span><span class="sxs-lookup"><span data-stu-id="47664-119">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="47664-120">Para obter uma lista de distribuições suportadas, consulte [as dependências e os requisitos do .NET Core](../dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="47664-120">For a list of supported distributions, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>

### <a name="examples"></a><span data-ttu-id="47664-121">Exemplos</span><span class="sxs-lookup"><span data-stu-id="47664-121">Examples</span></span>

- <span data-ttu-id="47664-122">Instale o tempo de execução do ASP.NET Core 3.1:`aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="47664-122">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="47664-123">Instale o tempo de execução do .NET Core 2.1:`dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="47664-123">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="47664-124">Instale o .NET Core 3.1 SDK:`dotnet-sdk-3.1`</span><span class="sxs-lookup"><span data-stu-id="47664-124">Install the .NET Core 3.1 SDK: `dotnet-sdk-3.1`</span></span>

### <a name="package-missing"></a><span data-ttu-id="47664-125">Pacote ausente</span><span class="sxs-lookup"><span data-stu-id="47664-125">Package missing</span></span>

<span data-ttu-id="47664-126">Se a combinação de versão de pacote não funcionar, ela não está disponível.</span><span class="sxs-lookup"><span data-stu-id="47664-126">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="47664-127">Por exemplo, não há uma ASP.NET SDK Core, os componentes do SDK estão incluídos no .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="47664-127">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="47664-128">O `aspnetcore-sdk-2.2` valor está incorreto e deve ser `dotnet-sdk-2.2`.</span><span class="sxs-lookup"><span data-stu-id="47664-128">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="47664-129">Para obter uma lista de distribuições Linux suportadas pelo .NET Core, consulte [as dependências e requisitos do .NET Core](../dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="47664-129">For a list of Linux distributions supported by .NET Core, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>
