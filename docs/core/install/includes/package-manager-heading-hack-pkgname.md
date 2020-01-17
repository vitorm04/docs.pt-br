---
ms.openlocfilehash: 47e8e15a64236d8ade2febb1add81fa4e5c030d9
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116162"
---

<span data-ttu-id="74c19-101">Os pacotes adicionados aos feeds do Gerenciador de pacotes são nomeados em um formato hackable: `{product}-{type}-{version}`.</span><span class="sxs-lookup"><span data-stu-id="74c19-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="74c19-102">\ do **produto**</span><span class="sxs-lookup"><span data-stu-id="74c19-102">**product**\</span></span>
<span data-ttu-id="74c19-103">O tipo de produto .NET a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="74c19-103">The type of .NET product to install.</span></span> <span data-ttu-id="74c19-104">As opções válidas são:</span><span class="sxs-lookup"><span data-stu-id="74c19-104">Valid options are:</span></span>

  - <span data-ttu-id="74c19-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="74c19-105">dotnet</span></span>
  - <span data-ttu-id="74c19-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="74c19-106">aspnetcore</span></span>

- <span data-ttu-id="74c19-107">**tipo**</span><span class="sxs-lookup"><span data-stu-id="74c19-107">**type**</span></span>\
<span data-ttu-id="74c19-108">Escolhe o SDK ou o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="74c19-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="74c19-109">As opções válidas são:</span><span class="sxs-lookup"><span data-stu-id="74c19-109">Valid options are:</span></span>

  - <span data-ttu-id="74c19-110">sdk</span><span class="sxs-lookup"><span data-stu-id="74c19-110">sdk</span></span>
  - <span data-ttu-id="74c19-111">Tempo de execução do</span><span class="sxs-lookup"><span data-stu-id="74c19-111">runtime</span></span>

- <span data-ttu-id="74c19-112">**versão**</span><span class="sxs-lookup"><span data-stu-id="74c19-112">**version**</span></span>\
<span data-ttu-id="74c19-113">A versão do SDK ou do tempo de execução a ser instalado.</span><span class="sxs-lookup"><span data-stu-id="74c19-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="74c19-114">Este artigo sempre fornecerá as instruções para a versão mais recente com suporte.</span><span class="sxs-lookup"><span data-stu-id="74c19-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="74c19-115">As opções válidas são qualquer versão lançada, como:</span><span class="sxs-lookup"><span data-stu-id="74c19-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="74c19-116">3.0</span><span class="sxs-lookup"><span data-stu-id="74c19-116">3.0</span></span>
  - <span data-ttu-id="74c19-117">2.2</span><span class="sxs-lookup"><span data-stu-id="74c19-117">2.2</span></span>
  - <span data-ttu-id="74c19-118">2.1</span><span class="sxs-lookup"><span data-stu-id="74c19-118">2.1</span></span>

### <a name="examples"></a><span data-ttu-id="74c19-119">Exemplos</span><span class="sxs-lookup"><span data-stu-id="74c19-119">Examples</span></span>

- <span data-ttu-id="74c19-120">Instale o SDK do .NET Core 2,2: `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="74c19-120">Install the .NET Core 2.2 SDK: `dotnet-sdk-2.2`</span></span>
- <span data-ttu-id="74c19-121">Instale o tempo de execução do ASP.NET Core 3,1: `aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="74c19-121">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="74c19-122">Instale o tempo de execução do .NET Core 2,1: `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="74c19-122">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>

### <a name="troubleshoot"></a><span data-ttu-id="74c19-123">Solução de problemas</span><span class="sxs-lookup"><span data-stu-id="74c19-123">Troubleshoot</span></span>

<span data-ttu-id="74c19-124">Se a combinação de pacote não funcionar, ela não estará disponível.</span><span class="sxs-lookup"><span data-stu-id="74c19-124">If the package combination doesn't work, it's not available.</span></span> <span data-ttu-id="74c19-125">Por exemplo, não há um SDK ASP.NET Core, os componentes do SDK estão incluídos no SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74c19-125">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="74c19-126">O valor `aspnetcore-sdk-2.2` está incorreto e deve ser `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="74c19-126">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`</span></span>
