---
ms.openlocfilehash: db70596552ffd699156e1b7a55cb1e944596f077
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901970"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a><span data-ttu-id="dfb3d-101">Proteção de dados: dataprotection. AzureStorage usa novas APIs de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="dfb3d-101">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>

<span data-ttu-id="dfb3d-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> depende das [bibliotecas de armazenamento do Azure](https://github.com/Azure/azure-storage-net).</span><span class="sxs-lookup"><span data-stu-id="dfb3d-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> depends on the [Azure Storage libraries](https://github.com/Azure/azure-storage-net).</span></span> <span data-ttu-id="dfb3d-103">Essas bibliotecas renomeam seus assemblies, pacotes e namespaces.</span><span class="sxs-lookup"><span data-stu-id="dfb3d-103">These libraries renamed their assemblies, packages, and namespaces.</span></span> <span data-ttu-id="dfb3d-104">A partir do ASP.NET Core 3,0, `Microsoft.AspNetCore.DataProtection.AzureStorage` usa os novos pacotes e APIs prefixados `Microsoft.Azure.Storage.`.</span><span class="sxs-lookup"><span data-stu-id="dfb3d-104">Starting in ASP.NET Core 3.0, `Microsoft.AspNetCore.DataProtection.AzureStorage` uses the new `Microsoft.Azure.Storage.`-prefixed APIs and packages.</span></span>

<span data-ttu-id="dfb3d-105">Para perguntas sobre as APIs de armazenamento do Azure, use <https://github.com/Azure/azure-storage-net>.</span><span class="sxs-lookup"><span data-stu-id="dfb3d-105">For questions about the Azure Storage APIs, use <https://github.com/Azure/azure-storage-net>.</span></span> <span data-ttu-id="dfb3d-106">Para obter uma discussão sobre esse problema, consulte [dotnet/aspnetcore # 8472](https://github.com/dotnet/aspnetcore/issues/8472).</span><span class="sxs-lookup"><span data-stu-id="dfb3d-106">For discussion on this issue, see [dotnet/aspnetcore#8472](https://github.com/dotnet/aspnetcore/issues/8472).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="dfb3d-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="dfb3d-107">Version introduced</span></span>

<span data-ttu-id="dfb3d-108">3.0</span><span class="sxs-lookup"><span data-stu-id="dfb3d-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="dfb3d-109">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="dfb3d-109">Old behavior</span></span>

<span data-ttu-id="dfb3d-110">O pacote referenciou o `WindowsAzure.Storage` pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="dfb3d-110">The package referenced the `WindowsAzure.Storage` NuGet package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="dfb3d-111">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="dfb3d-111">New behavior</span></span>

<span data-ttu-id="dfb3d-112">O pacote faz referência ao pacote NuGet `Microsoft.Azure.Storage.Blob`.</span><span class="sxs-lookup"><span data-stu-id="dfb3d-112">The package references the `Microsoft.Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="dfb3d-113">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="dfb3d-113">Reason for change</span></span>

<span data-ttu-id="dfb3d-114">Essa alteração permite que `Microsoft.AspNetCore.DataProtection.AzureStorage` migrem para os pacotes de armazenamento do Azure recomendados.</span><span class="sxs-lookup"><span data-stu-id="dfb3d-114">This change allows `Microsoft.AspNetCore.DataProtection.AzureStorage` to migrate to the recommended Azure Storage packages.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="dfb3d-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="dfb3d-115">Recommended action</span></span>

<span data-ttu-id="dfb3d-116">Se você ainda precisar usar as APIs mais antigas do armazenamento do Azure com o ASP.NET Core 3,0, adicione uma dependência direta ao pacote [WindowsAzure. Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) .</span><span class="sxs-lookup"><span data-stu-id="dfb3d-116">If you still need to use the older Azure Storage APIs with ASP.NET Core 3.0, add a direct dependency to the [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) package.</span></span> <span data-ttu-id="dfb3d-117">Esse pacote pode ser instalado junto com as novas APIs de `Microsoft.Azure.Storage`.</span><span class="sxs-lookup"><span data-stu-id="dfb3d-117">This package can be installed alongside the new `Microsoft.Azure.Storage` APIs.</span></span>

<span data-ttu-id="dfb3d-118">Em muitos casos, a atualização envolve apenas a alteração das instruções `using` para usar os novos namespaces:</span><span class="sxs-lookup"><span data-stu-id="dfb3d-118">In many cases, the upgrade only involves changing the `using` statements to use the new namespaces:</span></span>

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a><span data-ttu-id="dfb3d-119">Categoria</span><span class="sxs-lookup"><span data-stu-id="dfb3d-119">Category</span></span>

<span data-ttu-id="dfb3d-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dfb3d-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="dfb3d-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="dfb3d-121">Affected APIs</span></span>

<span data-ttu-id="dfb3d-122">{1&gt;Nenhum&lt;1}</span><span class="sxs-lookup"><span data-stu-id="dfb3d-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
