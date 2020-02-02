---
ms.openlocfilehash: ef3e4f9f8145677732b9d2e66d416be277697f55
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920657"
---

<span data-ttu-id="ac475-101">Os pacotes adicionados aos feeds do Gerenciador de pacotes são nomeados em um formato hackable: `{product}-{type}-{version}`.</span><span class="sxs-lookup"><span data-stu-id="ac475-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="ac475-102">\ do **produto**</span><span class="sxs-lookup"><span data-stu-id="ac475-102">**product**\</span></span>
<span data-ttu-id="ac475-103">O tipo de produto .NET a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="ac475-103">The type of .NET product to install.</span></span> <span data-ttu-id="ac475-104">As opções válidas são:</span><span class="sxs-lookup"><span data-stu-id="ac475-104">Valid options are:</span></span>

  - <span data-ttu-id="ac475-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="ac475-105">dotnet</span></span>
  - <span data-ttu-id="ac475-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="ac475-106">aspnetcore</span></span>

- <span data-ttu-id="ac475-107">**tipo**</span><span class="sxs-lookup"><span data-stu-id="ac475-107">**type**</span></span>\
<span data-ttu-id="ac475-108">Escolhe o SDK ou o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ac475-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="ac475-109">As opções válidas são:</span><span class="sxs-lookup"><span data-stu-id="ac475-109">Valid options are:</span></span>

  - <span data-ttu-id="ac475-110">sdk</span><span class="sxs-lookup"><span data-stu-id="ac475-110">sdk</span></span>
  - <span data-ttu-id="ac475-111">Tempo de execução do</span><span class="sxs-lookup"><span data-stu-id="ac475-111">runtime</span></span>

- <span data-ttu-id="ac475-112">**versão**</span><span class="sxs-lookup"><span data-stu-id="ac475-112">**version**</span></span>\
<span data-ttu-id="ac475-113">A versão do SDK ou do tempo de execução a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="ac475-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="ac475-114">Este artigo sempre fornecerá as instruções para a versão mais recente com suporte.</span><span class="sxs-lookup"><span data-stu-id="ac475-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="ac475-115">As opções válidas são qualquer versão lançada, como:</span><span class="sxs-lookup"><span data-stu-id="ac475-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="ac475-116">3.0</span><span class="sxs-lookup"><span data-stu-id="ac475-116">3.0</span></span>
  - <span data-ttu-id="ac475-117">2.2</span><span class="sxs-lookup"><span data-stu-id="ac475-117">2.2</span></span>
  - <span data-ttu-id="ac475-118">2.1</span><span class="sxs-lookup"><span data-stu-id="ac475-118">2.1</span></span>

### <a name="examples"></a><span data-ttu-id="ac475-119">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ac475-119">Examples</span></span>

- <span data-ttu-id="ac475-120">Instale o SDK do .NET Core 2,2: `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="ac475-120">Install the .NET Core 2.2 SDK: `dotnet-sdk-2.2`</span></span>
- <span data-ttu-id="ac475-121">Instale o tempo de execução do ASP.NET Core 3,1: `aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="ac475-121">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="ac475-122">Instale o tempo de execução do .NET Core 2,1: `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="ac475-122">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>

### <a name="package-missing"></a><span data-ttu-id="ac475-123">Pacote ausente</span><span class="sxs-lookup"><span data-stu-id="ac475-123">Package missing</span></span>

<span data-ttu-id="ac475-124">Se a combinação de versão do pacote não funcionar, ela não estará disponível.</span><span class="sxs-lookup"><span data-stu-id="ac475-124">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="ac475-125">Por exemplo, não há um SDK ASP.NET Core, os componentes do SDK estão incluídos no SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ac475-125">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="ac475-126">O valor `aspnetcore-sdk-2.2` está incorreto e deve ser `dotnet-sdk-2.2`.</span><span class="sxs-lookup"><span data-stu-id="ac475-126">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span>
