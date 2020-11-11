---
ms.openlocfilehash: ab1006f706439bcf5129854da3d14538e5b690a2
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506840"
---

<span data-ttu-id="9282f-101">Os pacotes adicionados aos feeds do Gerenciador de pacotes são nomeados em um formato hackable: `{product}-{type}-{version}` .</span><span class="sxs-lookup"><span data-stu-id="9282f-101">The packages added to package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="9282f-102">**remessa**</span><span class="sxs-lookup"><span data-stu-id="9282f-102">**product**</span></span>\
<span data-ttu-id="9282f-103">O tipo de produto .NET a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="9282f-103">The type of .NET product to install.</span></span> <span data-ttu-id="9282f-104">As opções válidas são:</span><span class="sxs-lookup"><span data-stu-id="9282f-104">Valid options are:</span></span>

  - <span data-ttu-id="9282f-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="9282f-105">dotnet</span></span>
  - <span data-ttu-id="9282f-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="9282f-106">aspnetcore</span></span>

- <span data-ttu-id="9282f-107">**Escreva**</span><span class="sxs-lookup"><span data-stu-id="9282f-107">**type**</span></span>\
<span data-ttu-id="9282f-108">Escolhe o SDK ou o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="9282f-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="9282f-109">As opções válidas são:</span><span class="sxs-lookup"><span data-stu-id="9282f-109">Valid options are:</span></span>

  - <span data-ttu-id="9282f-110">sdk</span><span class="sxs-lookup"><span data-stu-id="9282f-110">sdk</span></span>
  - <span data-ttu-id="9282f-111">runtime</span><span class="sxs-lookup"><span data-stu-id="9282f-111">runtime</span></span>

- <span data-ttu-id="9282f-112">**Versão**</span><span class="sxs-lookup"><span data-stu-id="9282f-112">**version**</span></span>\
<span data-ttu-id="9282f-113">A versão do SDK ou do tempo de execução a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="9282f-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="9282f-114">Este artigo sempre fornecerá as instruções para a versão mais recente com suporte.</span><span class="sxs-lookup"><span data-stu-id="9282f-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="9282f-115">As opções válidas são qualquer versão lançada, como:</span><span class="sxs-lookup"><span data-stu-id="9282f-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="9282f-116">5.0</span><span class="sxs-lookup"><span data-stu-id="9282f-116">5.0</span></span>
  - <span data-ttu-id="9282f-117">3.1</span><span class="sxs-lookup"><span data-stu-id="9282f-117">3.1</span></span>
  - <span data-ttu-id="9282f-118">3.0</span><span class="sxs-lookup"><span data-stu-id="9282f-118">3.0</span></span>
  - <span data-ttu-id="9282f-119">2.1</span><span class="sxs-lookup"><span data-stu-id="9282f-119">2.1</span></span>

  <span data-ttu-id="9282f-120">É possível que o SDK/tempo de execução que você está tentando baixar não esteja disponível para sua distribuição do Linux.</span><span class="sxs-lookup"><span data-stu-id="9282f-120">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="9282f-121">Para obter uma lista de distribuições com suporte, consulte [dependências e requisitos do .NET Core](../linux.md).</span><span class="sxs-lookup"><span data-stu-id="9282f-121">For a list of supported distributions, see [.NET Core dependencies and requirements](../linux.md).</span></span>

### <a name="examples"></a><span data-ttu-id="9282f-122">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9282f-122">Examples</span></span>

- <span data-ttu-id="9282f-123">Instale o tempo de execução do ASP.NET Core 5,0: `aspnetcore-runtime-5.0`</span><span class="sxs-lookup"><span data-stu-id="9282f-123">Install the ASP.NET Core 5.0 runtime: `aspnetcore-runtime-5.0`</span></span>
- <span data-ttu-id="9282f-124">Instale o tempo de execução do .NET Core 2,1: `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="9282f-124">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="9282f-125">Instale o SDK do .NET 5,0: `dotnet-sdk-5.0`</span><span class="sxs-lookup"><span data-stu-id="9282f-125">Install the .NET 5.0 SDK: `dotnet-sdk-5.0`</span></span>
- <span data-ttu-id="9282f-126">Instale o SDK do .NET Core 3,1: `dotnet-sdk-3.1`</span><span class="sxs-lookup"><span data-stu-id="9282f-126">Install the .NET Core 3.1 SDK: `dotnet-sdk-3.1`</span></span>

### <a name="package-missing"></a><span data-ttu-id="9282f-127">Pacote ausente</span><span class="sxs-lookup"><span data-stu-id="9282f-127">Package missing</span></span>

<span data-ttu-id="9282f-128">Se a combinação de versão do pacote não funcionar, ela não estará disponível.</span><span class="sxs-lookup"><span data-stu-id="9282f-128">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="9282f-129">Por exemplo, não há um SDK ASP.NET Core, os componentes do SDK estão incluídos no SDK do .NET.</span><span class="sxs-lookup"><span data-stu-id="9282f-129">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET SDK.</span></span> <span data-ttu-id="9282f-130">O valor `aspnetcore-sdk-2.2` está incorreto e deve ser `dotnet-sdk-2.2` .</span><span class="sxs-lookup"><span data-stu-id="9282f-130">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="9282f-131">Para obter uma lista de distribuições do Linux com suporte no .NET Core, consulte [dependências e requisitos do .net](../linux.md).</span><span class="sxs-lookup"><span data-stu-id="9282f-131">For a list of Linux distributions supported by .NET Core, see [.NET dependencies and requirements](../linux.md).</span></span>
