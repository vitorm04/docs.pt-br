---
ms.openlocfilehash: 51b3c1b3e3d61b23a0511ca807afef0269ac9ee4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77466109"
---

<span data-ttu-id="b5848-101">Os pacotes adicionados aos feeds do gerenciador `{product}-{type}-{version}`de pacotes são nomeados em um formato hackeável: .</span><span class="sxs-lookup"><span data-stu-id="b5848-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="b5848-102">**Produto**</span><span class="sxs-lookup"><span data-stu-id="b5848-102">**product**</span></span>\
<span data-ttu-id="b5848-103">O tipo de produto .NET a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="b5848-103">The type of .NET product to install.</span></span> <span data-ttu-id="b5848-104">As opções válidas são:</span><span class="sxs-lookup"><span data-stu-id="b5848-104">Valid options are:</span></span>

  - <span data-ttu-id="b5848-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="b5848-105">dotnet</span></span>
  - <span data-ttu-id="b5848-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="b5848-106">aspnetcore</span></span>

- <span data-ttu-id="b5848-107">**Tipo**</span><span class="sxs-lookup"><span data-stu-id="b5848-107">**type**</span></span>\
<span data-ttu-id="b5848-108">Escolhe o SDK ou o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b5848-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="b5848-109">As opções válidas são:</span><span class="sxs-lookup"><span data-stu-id="b5848-109">Valid options are:</span></span>

  - <span data-ttu-id="b5848-110">sdk</span><span class="sxs-lookup"><span data-stu-id="b5848-110">sdk</span></span>
  - <span data-ttu-id="b5848-111">runtime</span><span class="sxs-lookup"><span data-stu-id="b5848-111">runtime</span></span>

- <span data-ttu-id="b5848-112">**Versão**</span><span class="sxs-lookup"><span data-stu-id="b5848-112">**version**</span></span>\
<span data-ttu-id="b5848-113">A versão do SDK ou tempo de execução para instalar.</span><span class="sxs-lookup"><span data-stu-id="b5848-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="b5848-114">Este artigo sempre dará as instruções para a versão mais recente suportada.</span><span class="sxs-lookup"><span data-stu-id="b5848-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="b5848-115">Opções válidas são qualquer versão lançada, tais como:</span><span class="sxs-lookup"><span data-stu-id="b5848-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="b5848-116">3.1</span><span class="sxs-lookup"><span data-stu-id="b5848-116">3.1</span></span>
  - <span data-ttu-id="b5848-117">3.0</span><span class="sxs-lookup"><span data-stu-id="b5848-117">3.0</span></span>
  - <span data-ttu-id="b5848-118">2.1</span><span class="sxs-lookup"><span data-stu-id="b5848-118">2.1</span></span>

  <span data-ttu-id="b5848-119">É possível que o SDK/tempo de execução que você está tentando baixar não esteja disponível para sua distribuição Linux.</span><span class="sxs-lookup"><span data-stu-id="b5848-119">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="b5848-120">Para obter uma lista de distribuições suportadas, consulte [as dependências e os requisitos do .NET Core](../dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="b5848-120">For a list of supported distributions, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>

### <a name="examples"></a><span data-ttu-id="b5848-121">Exemplos</span><span class="sxs-lookup"><span data-stu-id="b5848-121">Examples</span></span>

- <span data-ttu-id="b5848-122">Instale o tempo de execução do ASP.NET Core 3.1:`aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="b5848-122">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="b5848-123">Instale o tempo de execução do .NET Core 2.1:`dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="b5848-123">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="b5848-124">Instale o .NET Core 3.0 SDK:`dotnet-sdk-3.0`</span><span class="sxs-lookup"><span data-stu-id="b5848-124">Install the .NET Core 3.0 SDK: `dotnet-sdk-3.0`</span></span>

### <a name="package-missing"></a><span data-ttu-id="b5848-125">Pacote ausente</span><span class="sxs-lookup"><span data-stu-id="b5848-125">Package missing</span></span>

<span data-ttu-id="b5848-126">Se a combinação de versão de pacote não funcionar, ela não está disponível.</span><span class="sxs-lookup"><span data-stu-id="b5848-126">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="b5848-127">Por exemplo, não há uma ASP.NET SDK Core, os componentes do SDK estão incluídos no .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="b5848-127">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="b5848-128">O `aspnetcore-sdk-2.2` valor está incorreto e deve ser `dotnet-sdk-2.2`.</span><span class="sxs-lookup"><span data-stu-id="b5848-128">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="b5848-129">Para obter uma lista de distribuições Linux suportadas pelo .NET Core, consulte [as dependências e requisitos do .NET Core](../dependencies.md?pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="b5848-129">For a list of Linux distributions supported by .NET Core, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>
