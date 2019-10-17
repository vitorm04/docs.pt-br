---
ms.openlocfilehash: f103c96588bae167216d09a82973a4a7abfb5cc3
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394019"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a><span data-ttu-id="12772-101">Proteção de dados: dataprotection. AzureStorage usa novas APIs de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="12772-101">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>

<span data-ttu-id="12772-102">o <xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> depende das [bibliotecas de armazenamento do Azure](https://github.com/Azure/azure-storage-net).</span><span class="sxs-lookup"><span data-stu-id="12772-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> depends on the [Azure Storage libraries](https://github.com/Azure/azure-storage-net).</span></span> <span data-ttu-id="12772-103">Essas bibliotecas renomeam seus assemblies, pacotes e namespaces.</span><span class="sxs-lookup"><span data-stu-id="12772-103">These libraries renamed their assemblies, packages, and namespaces.</span></span> <span data-ttu-id="12772-104">A partir do ASP.NET Core 3,0, o `Microsoft.AspNetCore.DataProtection.AzureStorage` usa as novas APIs e pacotes prefixados do `Microsoft.Azure.Storage.`.</span><span class="sxs-lookup"><span data-stu-id="12772-104">Starting in ASP.NET Core 3.0, `Microsoft.AspNetCore.DataProtection.AzureStorage` uses the new `Microsoft.Azure.Storage.`-prefixed APIs and packages.</span></span>

<span data-ttu-id="12772-105">Para perguntas sobre as APIs de armazenamento do Azure, use <https://github.com/Azure/azure-storage-net>.</span><span class="sxs-lookup"><span data-stu-id="12772-105">For questions about the Azure Storage APIs, use <https://github.com/Azure/azure-storage-net>.</span></span> <span data-ttu-id="12772-106">Para obter uma discussão sobre esse problema, consulte [ASPNET/AspNetCore # 8472](https://github.com/aspnet/AspNetCore/issues/8472).</span><span class="sxs-lookup"><span data-stu-id="12772-106">For discussion on this issue, see [aspnet/AspNetCore#8472](https://github.com/aspnet/AspNetCore/issues/8472).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="12772-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="12772-107">Version introduced</span></span>

<span data-ttu-id="12772-108">3.0</span><span class="sxs-lookup"><span data-stu-id="12772-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="12772-109">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="12772-109">Old behavior</span></span>

<span data-ttu-id="12772-110">O pacote referenciou o pacote NuGet `WindowsAzure.Storage`.</span><span class="sxs-lookup"><span data-stu-id="12772-110">The package referenced the `WindowsAzure.Storage` NuGet package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="12772-111">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="12772-111">New behavior</span></span>

<span data-ttu-id="12772-112">O pacote faz referência ao pacote NuGet `Microsoft.Azure.Storage.Blob`.</span><span class="sxs-lookup"><span data-stu-id="12772-112">The package references the `Microsoft.Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="12772-113">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="12772-113">Reason for change</span></span>

<span data-ttu-id="12772-114">Essa alteração permite que `Microsoft.AspNetCore.DataProtection.AzureStorage` migre para os pacotes de armazenamento do Azure recomendados.</span><span class="sxs-lookup"><span data-stu-id="12772-114">This change allows `Microsoft.AspNetCore.DataProtection.AzureStorage` to migrate to the recommended Azure Storage packages.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="12772-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="12772-115">Recommended action</span></span>

<span data-ttu-id="12772-116">Se você ainda precisar usar as APIs mais antigas do armazenamento do Azure com o ASP.NET Core 3,0, adicione uma dependência direta ao pacote [WindowsAzure. Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) .</span><span class="sxs-lookup"><span data-stu-id="12772-116">If you still need to use the older Azure Storage APIs with ASP.NET Core 3.0, add a direct dependency to the [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) package.</span></span> <span data-ttu-id="12772-117">Esse pacote pode ser instalado juntamente com as novas APIs `Microsoft.Azure.Storage`.</span><span class="sxs-lookup"><span data-stu-id="12772-117">This package can be installed alongside the new `Microsoft.Azure.Storage` APIs.</span></span>

<span data-ttu-id="12772-118">Em muitos casos, a atualização envolve apenas a alteração das instruções `using` para usar os novos namespaces:</span><span class="sxs-lookup"><span data-stu-id="12772-118">In many cases, the upgrade only involves changing the `using` statements to use the new namespaces:</span></span>

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a><span data-ttu-id="12772-119">Categoria</span><span class="sxs-lookup"><span data-stu-id="12772-119">Category</span></span>

<span data-ttu-id="12772-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="12772-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="12772-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="12772-121">Affected APIs</span></span>

<span data-ttu-id="12772-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="12772-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
