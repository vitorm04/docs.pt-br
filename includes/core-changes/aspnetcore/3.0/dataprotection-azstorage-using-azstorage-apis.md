---
ms.openlocfilehash: db70596552ffd699156e1b7a55cb1e944596f077
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901970"
---
### <a name="data-protection-dataprotectionazurestorage-uses-new-azure-storage-apis"></a><span data-ttu-id="19658-101">Proteção de dados: DataProtection.AzureStorage usa novas APIs de armazenamento do Azure</span><span class="sxs-lookup"><span data-stu-id="19658-101">Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs</span></span>

<span data-ttu-id="19658-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName>depende das [bibliotecas de armazenamento Azure.](https://github.com/Azure/azure-storage-net)</span><span class="sxs-lookup"><span data-stu-id="19658-102"><xref:Microsoft.AspNetCore.DataProtection.AzureStorage?displayProperty=fullName> depends on the [Azure Storage libraries](https://github.com/Azure/azure-storage-net).</span></span> <span data-ttu-id="19658-103">Essas bibliotecas renomearam seus conjuntos, pacotes e espaços de nome.</span><span class="sxs-lookup"><span data-stu-id="19658-103">These libraries renamed their assemblies, packages, and namespaces.</span></span> <span data-ttu-id="19658-104">A partir de ASP.NET `Microsoft.AspNetCore.DataProtection.AzureStorage` Core 3.0, usa as novas `Microsoft.Azure.Storage.`APIs e pacotes prefixados.</span><span class="sxs-lookup"><span data-stu-id="19658-104">Starting in ASP.NET Core 3.0, `Microsoft.AspNetCore.DataProtection.AzureStorage` uses the new `Microsoft.Azure.Storage.`-prefixed APIs and packages.</span></span>

<span data-ttu-id="19658-105">Para dúvidas sobre as APIs <https://github.com/Azure/azure-storage-net>de armazenamento do Azure, use .</span><span class="sxs-lookup"><span data-stu-id="19658-105">For questions about the Azure Storage APIs, use <https://github.com/Azure/azure-storage-net>.</span></span> <span data-ttu-id="19658-106">Para discussão sobre este assunto, consulte [dotnet/aspnetcore#8472](https://github.com/dotnet/aspnetcore/issues/8472).</span><span class="sxs-lookup"><span data-stu-id="19658-106">For discussion on this issue, see [dotnet/aspnetcore#8472](https://github.com/dotnet/aspnetcore/issues/8472).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="19658-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="19658-107">Version introduced</span></span>

<span data-ttu-id="19658-108">3.0</span><span class="sxs-lookup"><span data-stu-id="19658-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="19658-109">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="19658-109">Old behavior</span></span>

<span data-ttu-id="19658-110">O pacote fazia `WindowsAzure.Storage` referência ao pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="19658-110">The package referenced the `WindowsAzure.Storage` NuGet package.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="19658-111">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="19658-111">New behavior</span></span>

<span data-ttu-id="19658-112">O pacote faz `Microsoft.Azure.Storage.Blob` referência ao pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="19658-112">The package references the `Microsoft.Azure.Storage.Blob` NuGet package.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="19658-113">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="19658-113">Reason for change</span></span>

<span data-ttu-id="19658-114">Essa alteração `Microsoft.AspNetCore.DataProtection.AzureStorage` permite migrar para os pacotes recomendados do Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="19658-114">This change allows `Microsoft.AspNetCore.DataProtection.AzureStorage` to migrate to the recommended Azure Storage packages.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="19658-115">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="19658-115">Recommended action</span></span>

<span data-ttu-id="19658-116">Se você ainda precisar usar as APIs de armazenamento azure mais antigas com ASP.NET Core 3.0, adicione uma dependência direta ao pacote [WindowsAzure.Storage.](https://www.nuget.org/packages/WindowsAzure.Storage/)</span><span class="sxs-lookup"><span data-stu-id="19658-116">If you still need to use the older Azure Storage APIs with ASP.NET Core 3.0, add a direct dependency to the [WindowsAzure.Storage](https://www.nuget.org/packages/WindowsAzure.Storage/) package.</span></span> <span data-ttu-id="19658-117">Este pacote pode ser instalado `Microsoft.Azure.Storage` junto com as novas APIs.</span><span class="sxs-lookup"><span data-stu-id="19658-117">This package can be installed alongside the new `Microsoft.Azure.Storage` APIs.</span></span>

<span data-ttu-id="19658-118">Em muitos casos, a atualização `using` envolve apenas alterar as instruções para usar os novos namespaces:</span><span class="sxs-lookup"><span data-stu-id="19658-118">In many cases, the upgrade only involves changing the `using` statements to use the new namespaces:</span></span>

```diff
- using Microsoft.WindowsAzure.Storage;
- using Microsoft.WindowsAzure.Storage.Blob;
+ using Microsoft.Azure.Storage;
+ using Microsoft.Azure.Storage.Blob;
```

#### <a name="category"></a><span data-ttu-id="19658-119">Categoria</span><span class="sxs-lookup"><span data-stu-id="19658-119">Category</span></span>

<span data-ttu-id="19658-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="19658-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="19658-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="19658-121">Affected APIs</span></span>

<span data-ttu-id="19658-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="19658-122">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
