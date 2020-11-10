---
ms.openlocfilehash: f6e4c3d5c5fd020562e48515554136e0f8b6785c
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440413"
---
### <a name="data-protection-dataprotectionblobs-uses-new-azure-storage-apis"></a><span data-ttu-id="8aad9-101">Proteção de dados: dataprotegetion. BLOBs usa novas APIs de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="8aad9-101">Data Protection: DataProtection.Blobs uses new Azure Storage APIs</span></span>

<span data-ttu-id="8aad9-102">`Azure.Extensions.AspNetCore.DataProtection.Blobs` depende das [bibliotecas de armazenamento do Azure](https://github.com/Azure/azure-storage-net).</span><span class="sxs-lookup"><span data-stu-id="8aad9-102">`Azure.Extensions.AspNetCore.DataProtection.Blobs` depends on the [Azure Storage libraries](https://github.com/Azure/azure-storage-net).</span></span> <span data-ttu-id="8aad9-103">Essas bibliotecas renomeam seus assemblies, pacotes e namespaces.</span><span class="sxs-lookup"><span data-stu-id="8aad9-103">These libraries renamed their assemblies, packages, and namespaces.</span></span> <span data-ttu-id="8aad9-104">A partir do ASP.NET Core 3,0, `Azure.Extensions.AspNetCore.DataProtection.Blobs` o usa as `Azure.Storage.` APIs e os pacotes novos e prefixados.</span><span class="sxs-lookup"><span data-stu-id="8aad9-104">Starting in ASP.NET Core 3.0, `Azure.Extensions.AspNetCore.DataProtection.Blobs` uses the new `Azure.Storage.`-prefixed APIs and packages.</span></span>

<span data-ttu-id="8aad9-105">Para perguntas sobre as APIs de armazenamento do Azure, use <https://github.com/Azure/azure-storage-net> .</span><span class="sxs-lookup"><span data-stu-id="8aad9-105">For questions about the Azure Storage APIs, use <https://github.com/Azure/azure-storage-net>.</span></span> <span data-ttu-id="8aad9-106">Para obter uma discussão sobre esse problema, consulte [dotnet/aspnetcore # 19570](https://github.com/dotnet/aspnetcore/issues/19570).</span><span class="sxs-lookup"><span data-stu-id="8aad9-106">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8aad9-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8aad9-107">Version introduced</span></span>

<span data-ttu-id="8aad9-108">3.0</span><span class="sxs-lookup"><span data-stu-id="8aad9-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="8aad9-109">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="8aad9-109">Old behavior</span></span>

<span data-ttu-id="8aad9-110">O pacote referenciou o `WindowsAzure.Storage` pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="8aad9-110">The package referenced the `WindowsAzure.Storage` NuGet package.</span></span>
<span data-ttu-id="8aad9-111">O pacote faz referência ao `Microsoft.Azure.Storage.Blob` pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="8aad9-111">The package references the `Microsoft.Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="8aad9-112">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="8aad9-112">New behavior</span></span>

<span data-ttu-id="8aad9-113">O pacote faz referência ao `Azure.Storage.Blob` pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="8aad9-113">The package references the `Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8aad9-114">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="8aad9-114">Reason for change</span></span>

<span data-ttu-id="8aad9-115">Essa alteração permite `Azure.Extensions.AspNetCore.DataProtection.Blobs` migrar para os pacotes de armazenamento do Azure recomendados.</span><span class="sxs-lookup"><span data-stu-id="8aad9-115">This change allows `Azure.Extensions.AspNetCore.DataProtection.Blobs` to migrate to the recommended Azure Storage packages.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8aad9-116">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="8aad9-116">Recommended action</span></span>

<span data-ttu-id="8aad9-117">Se você ainda precisar usar as APIs mais antigas do armazenamento do Azure com o ASP.NET Core 3,0, adicione uma dependência direta ao pacote [WindowsAzure. Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) ou [Microsoft. Azure. Storage](https://www.nuget.org/packages/Microsoft.Azure.Storage.Blob/).</span><span class="sxs-lookup"><span data-stu-id="8aad9-117">If you still need to use the older Azure Storage APIs with ASP.NET Core 3.0, add a direct dependency to the package [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) or [Microsoft.Azure.Storage](https://www.nuget.org/packages/Microsoft.Azure.Storage.Blob/).</span></span> <span data-ttu-id="8aad9-118">Esse pacote pode ser instalado junto com as novas `Azure.Storage` APIs.</span><span class="sxs-lookup"><span data-stu-id="8aad9-118">This package can be installed alongside the new `Azure.Storage` APIs.</span></span>

<span data-ttu-id="8aad9-119">Em muitos casos, a atualização envolve apenas a alteração das `using` instruções para usar os novos namespaces:</span><span class="sxs-lookup"><span data-stu-id="8aad9-119">In many cases, the upgrade only involves changing the `using` statements to use the new namespaces:</span></span>

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
- using Microsoft.Azure.Storage;
- using Microsoft.Azure.Storage.Blob;
+ using Azure.Storage;
+ using Azure.Storage.Blobs;
```

#### <a name="category"></a><span data-ttu-id="8aad9-120">Categoria</span><span class="sxs-lookup"><span data-stu-id="8aad9-120">Category</span></span>

<span data-ttu-id="8aad9-121">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8aad9-121">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8aad9-122">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8aad9-122">Affected APIs</span></span>

<span data-ttu-id="8aad9-123">Nenhum</span><span class="sxs-lookup"><span data-stu-id="8aad9-123">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
