---
ms.openlocfilehash: 7723892a33bf7dd8e475b2f696db5d9ab287e182
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602988"
---

<span data-ttu-id="bc156-101">Os pacotes adicionados aos feeds do Gerenciador de pacotes são nomeados em um formato hackable: `{product}-{type}-{version}` .</span><span class="sxs-lookup"><span data-stu-id="bc156-101">The packages added to package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="bc156-102">**remessa**</span><span class="sxs-lookup"><span data-stu-id="bc156-102">**product**</span></span>\
<span data-ttu-id="bc156-103">O tipo de produto .NET a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="bc156-103">The type of .NET product to install.</span></span> <span data-ttu-id="bc156-104">As opções válidas são:</span><span class="sxs-lookup"><span data-stu-id="bc156-104">Valid options are:</span></span>

  - <span data-ttu-id="bc156-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="bc156-105">dotnet</span></span>
  - <span data-ttu-id="bc156-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="bc156-106">aspnetcore</span></span>

- <span data-ttu-id="bc156-107">**Escreva**</span><span class="sxs-lookup"><span data-stu-id="bc156-107">**type**</span></span>\
<span data-ttu-id="bc156-108">Escolhe o SDK ou o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bc156-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="bc156-109">As opções válidas são:</span><span class="sxs-lookup"><span data-stu-id="bc156-109">Valid options are:</span></span>

  - <span data-ttu-id="bc156-110">sdk</span><span class="sxs-lookup"><span data-stu-id="bc156-110">sdk</span></span>
  - <span data-ttu-id="bc156-111">runtime</span><span class="sxs-lookup"><span data-stu-id="bc156-111">runtime</span></span>

- <span data-ttu-id="bc156-112">**Versão**</span><span class="sxs-lookup"><span data-stu-id="bc156-112">**version**</span></span>\
<span data-ttu-id="bc156-113">A versão do SDK ou do tempo de execução a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="bc156-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="bc156-114">Este artigo sempre fornecerá as instruções para a versão mais recente com suporte.</span><span class="sxs-lookup"><span data-stu-id="bc156-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="bc156-115">As opções válidas são qualquer versão lançada, como:</span><span class="sxs-lookup"><span data-stu-id="bc156-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="bc156-116">3.1</span><span class="sxs-lookup"><span data-stu-id="bc156-116">3.1</span></span>
  - <span data-ttu-id="bc156-117">3.0</span><span class="sxs-lookup"><span data-stu-id="bc156-117">3.0</span></span>
  - <span data-ttu-id="bc156-118">2.1</span><span class="sxs-lookup"><span data-stu-id="bc156-118">2.1</span></span>

  <span data-ttu-id="bc156-119">É possível que o SDK/tempo de execução que você está tentando baixar não esteja disponível para sua distribuição do Linux.</span><span class="sxs-lookup"><span data-stu-id="bc156-119">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="bc156-120">Para obter uma lista de distribuições com suporte, consulte [dependências e requisitos do .NET Core](../linux.md).</span><span class="sxs-lookup"><span data-stu-id="bc156-120">For a list of supported distributions, see [.NET Core dependencies and requirements](../linux.md).</span></span>

### <a name="examples"></a><span data-ttu-id="bc156-121">Exemplos</span><span class="sxs-lookup"><span data-stu-id="bc156-121">Examples</span></span>

- <span data-ttu-id="bc156-122">Instale o tempo de execução do ASP.NET Core 3,1:`aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="bc156-122">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="bc156-123">Instale o tempo de execução do .NET Core 2,1:`dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="bc156-123">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="bc156-124">Instale o SDK do .NET Core 3,1:`dotnet-sdk-3.1`</span><span class="sxs-lookup"><span data-stu-id="bc156-124">Install the .NET Core 3.1 SDK: `dotnet-sdk-3.1`</span></span>

### <a name="package-missing"></a><span data-ttu-id="bc156-125">Pacote ausente</span><span class="sxs-lookup"><span data-stu-id="bc156-125">Package missing</span></span>

<span data-ttu-id="bc156-126">Se a combinação de versão do pacote não funcionar, ela não estará disponível.</span><span class="sxs-lookup"><span data-stu-id="bc156-126">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="bc156-127">Por exemplo, não há um SDK ASP.NET Core, os componentes do SDK estão incluídos no SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bc156-127">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="bc156-128">O valor `aspnetcore-sdk-2.2` está incorreto e deve ser `dotnet-sdk-2.2` .</span><span class="sxs-lookup"><span data-stu-id="bc156-128">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="bc156-129">Para obter uma lista de distribuições do Linux com suporte no .NET Core, confira [dependências e requisitos do .NET Core](../linux.md).</span><span class="sxs-lookup"><span data-stu-id="bc156-129">For a list of Linux distributions supported by .NET Core, see [.NET Core dependencies and requirements](../linux.md).</span></span>
