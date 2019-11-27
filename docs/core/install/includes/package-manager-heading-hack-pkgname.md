---
ms.openlocfilehash: 7a55641b3673dc4d8d9b328f0de99b7247ca51d4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450880"
---

<span data-ttu-id="b07cc-101">Os pacotes adicionados aos feeds do Gerenciador de pacotes são nomeados em um formato hackable: `{product}-{type}-{version}`.</span><span class="sxs-lookup"><span data-stu-id="b07cc-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="b07cc-102">\ do **produto**</span><span class="sxs-lookup"><span data-stu-id="b07cc-102">**product**\</span></span>
<span data-ttu-id="b07cc-103">O tipo de produto .NET a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="b07cc-103">The type of .NET product to install.</span></span> <span data-ttu-id="b07cc-104">As opções válidas são:</span><span class="sxs-lookup"><span data-stu-id="b07cc-104">Valid options are:</span></span>

  - <span data-ttu-id="b07cc-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="b07cc-105">dotnet</span></span>
  - <span data-ttu-id="b07cc-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="b07cc-106">aspnetcore</span></span>

- <span data-ttu-id="b07cc-107">**tipo**</span><span class="sxs-lookup"><span data-stu-id="b07cc-107">**type**</span></span>\
<span data-ttu-id="b07cc-108">Escolhe o SDK ou o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b07cc-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="b07cc-109">As opções válidas são:</span><span class="sxs-lookup"><span data-stu-id="b07cc-109">Valid options are:</span></span>

  - <span data-ttu-id="b07cc-110">sdk</span><span class="sxs-lookup"><span data-stu-id="b07cc-110">sdk</span></span>
  - <span data-ttu-id="b07cc-111">runtime</span><span class="sxs-lookup"><span data-stu-id="b07cc-111">runtime</span></span>

- <span data-ttu-id="b07cc-112">**versão**</span><span class="sxs-lookup"><span data-stu-id="b07cc-112">**version**</span></span>\
<span data-ttu-id="b07cc-113">A versão do SDK ou do tempo de execução a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="b07cc-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="b07cc-114">Este artigo sempre fornecerá as instruções para a versão mais recente com suporte.</span><span class="sxs-lookup"><span data-stu-id="b07cc-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="b07cc-115">As opções válidas são qualquer versão lançada, como:</span><span class="sxs-lookup"><span data-stu-id="b07cc-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="b07cc-116">3.0</span><span class="sxs-lookup"><span data-stu-id="b07cc-116">3.0</span></span>
  - <span data-ttu-id="b07cc-117">2.2</span><span class="sxs-lookup"><span data-stu-id="b07cc-117">2.2</span></span>
  - <span data-ttu-id="b07cc-118">2.1</span><span class="sxs-lookup"><span data-stu-id="b07cc-118">2.1</span></span>

### <a name="examples"></a><span data-ttu-id="b07cc-119">Exemplos</span><span class="sxs-lookup"><span data-stu-id="b07cc-119">Examples</span></span>

- <span data-ttu-id="b07cc-120">Instale o SDK do .NET Core 2,2: `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="b07cc-120">Install the .NET Core 2.2 SDK: `dotnet-sdk-2.2`</span></span>
- <span data-ttu-id="b07cc-121">Instale o tempo de execução do ASP.NET Core 3,0: `aspnetcore-runtime-3.0`</span><span class="sxs-lookup"><span data-stu-id="b07cc-121">Install the ASP.NET Core 3.0 runtime: `aspnetcore-runtime-3.0`</span></span>
- <span data-ttu-id="b07cc-122">Instale o tempo de execução do .NET Core 2,1: `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="b07cc-122">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>

### <a name="troubleshoot"></a><span data-ttu-id="b07cc-123">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="b07cc-123">Troubleshoot</span></span>

<span data-ttu-id="b07cc-124">Se a combinação de pacote não funcionar, ela não estará disponível.</span><span class="sxs-lookup"><span data-stu-id="b07cc-124">If the package combination doesn't work, it's not available.</span></span> <span data-ttu-id="b07cc-125">Por exemplo, não há um SDK ASP.NET Core, os componentes do SDK estão incluídos no SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b07cc-125">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="b07cc-126">O valor `aspnetcore-sdk-2.2` está incorreto e deve ser `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="b07cc-126">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`</span></span>
