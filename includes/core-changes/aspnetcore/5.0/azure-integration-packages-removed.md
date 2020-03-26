---
ms.openlocfilehash: d8506893f5b3eefa6f46dc9f773e43b125ee5210
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291669"
---
### <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a><span data-ttu-id="50567-101">Azure: pacotes de integração azure prefixados pela Microsoft removidos</span><span class="sxs-lookup"><span data-stu-id="50567-101">Azure: Microsoft-prefixed Azure integration packages removed</span></span>

<span data-ttu-id="50567-102">Os `Microsoft.*` seguintes pacotes que fornecem integração entre ASP.NET SDKs Core e Azure não estão incluídos no ASP.NET Core 5.0:</span><span class="sxs-lookup"><span data-stu-id="50567-102">The following `Microsoft.*` packages that provide integration between ASP.NET Core and Azure SDKs aren't included in ASP.NET Core 5.0:</span></span>

* <span data-ttu-id="50567-103">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), que integra [o Azure Key Vault](/azure/key-vault/) no sistema de [configuração](/aspnet/core/fundamentals/configuration/).</span><span class="sxs-lookup"><span data-stu-id="50567-103">[Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), which integrates [Azure Key Vault](/azure/key-vault/) into the [Configuration system](/aspnet/core/fundamentals/configuration/).</span></span>
* <span data-ttu-id="50567-104">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), que integra o Azure Key Vault no [sistema de proteção de dados ASP.NET.](/aspnet/core/security/data-protection/introduction)</span><span class="sxs-lookup"><span data-stu-id="50567-104">[Microsoft.AspNetCore.DataProtection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), which integrates Azure Key Vault into the [ASP.NET Core Data Protection system](/aspnet/core/security/data-protection/introduction).</span></span>
* <span data-ttu-id="50567-105">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), que integra o [Azure Blob Storage](/azure/storage/blobs/) ao sistema de proteção de dados ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="50567-105">[Microsoft.AspNetCore.DataProtection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), which integrates [Azure Blob Storage](/azure/storage/blobs/) into the ASP.NET Core Data Protection system.</span></span>

<span data-ttu-id="50567-106">Para discussão sobre este assunto, consulte [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span><span class="sxs-lookup"><span data-stu-id="50567-106">For discussion on this issue, see [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="50567-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="50567-107">Version introduced</span></span>

<span data-ttu-id="50567-108">5.0 Visualização 1</span><span class="sxs-lookup"><span data-stu-id="50567-108">5.0 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="50567-109">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="50567-109">Old behavior</span></span>

<span data-ttu-id="50567-110">Os `Microsoft.*` pacotes integraram os serviços do Azure com as APIs de Configuração e Proteção de Dados.</span><span class="sxs-lookup"><span data-stu-id="50567-110">The `Microsoft.*` packages integrated Azure services with the Configuration and Data Protection APIs.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="50567-111">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="50567-111">New behavior</span></span>

<span data-ttu-id="50567-112">Novos `Azure.*` pacotes integram os serviços do Azure com as APIs de Configuração e Proteção de Dados.</span><span class="sxs-lookup"><span data-stu-id="50567-112">New `Azure.*` packages integrate Azure services with the Configuration and Data Protection APIs.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="50567-113">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="50567-113">Reason for change</span></span>

<span data-ttu-id="50567-114">A mudança foi `Microsoft.*` feita porque os pacotes eram:</span><span class="sxs-lookup"><span data-stu-id="50567-114">The change was made because the `Microsoft.*` packages were:</span></span>

* <span data-ttu-id="50567-115">Usando versões desatualizadas do Azure SDK.</span><span class="sxs-lookup"><span data-stu-id="50567-115">Using outdated versions of the Azure SDK.</span></span> <span data-ttu-id="50567-116">Atualizações simples não foram possíveis porque as novas versões do Azure SDK incluíam mudanças de ruptura.</span><span class="sxs-lookup"><span data-stu-id="50567-116">Simple updates weren't possible because the new versions of the Azure SDK included breaking changes.</span></span>
* <span data-ttu-id="50567-117">Vinculado ao cronograma de lançamento do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="50567-117">Tied to the .NET Core release schedule.</span></span> <span data-ttu-id="50567-118">Transferir a propriedade dos pacotes para a equipe do Azure SDK permite atualizações de pacotes à medida que o SDK do Azure é atualizado.</span><span class="sxs-lookup"><span data-stu-id="50567-118">Transferring ownership of the packages to the Azure SDK team enables package updates as the Azure SDK is updated.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="50567-119">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="50567-119">Recommended action</span></span>

<span data-ttu-id="50567-120">Em ASP.NET projetos Core 2.1 ou `Microsoft.*` posteriores, substitua o antigo pelos novos `Azure.*` pacotes.</span><span class="sxs-lookup"><span data-stu-id="50567-120">In ASP.NET Core 2.1 or later projects, replace the old `Microsoft.*` with the new `Azure.*` packages.</span></span>

| <span data-ttu-id="50567-121">Velho</span><span class="sxs-lookup"><span data-stu-id="50567-121">Old</span></span> | <span data-ttu-id="50567-122">Novo</span><span class="sxs-lookup"><span data-stu-id="50567-122">New</span></span> |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [<span data-ttu-id="50567-123">Azure.AspNetCore.DataProtection.Keys</span><span class="sxs-lookup"><span data-stu-id="50567-123">Azure.AspNetCore.DataProtection.Keys</span></span>](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [<span data-ttu-id="50567-124">Azure.AspNetCore.DataProtection.Blobs</span><span class="sxs-lookup"><span data-stu-id="50567-124">Azure.AspNetCore.DataProtection.Blobs</span></span>](https://www.nuget.org/packages/Azure.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [<span data-ttu-id="50567-125">Azure.Extensions.Configuration.Secrets</span><span class="sxs-lookup"><span data-stu-id="50567-125">Azure.Extensions.Configuration.Secrets</span></span>](https://www.nuget.org/packages/Azure.Extensions.Configuration.Secrets) |

<span data-ttu-id="50567-126">Os novos pacotes usam uma nova versão do Azure SDK que inclui mudanças de quebra.</span><span class="sxs-lookup"><span data-stu-id="50567-126">The new packages use a new version of the Azure SDK that includes breaking changes.</span></span> <span data-ttu-id="50567-127">Os padrões de uso geral são inalterados.</span><span class="sxs-lookup"><span data-stu-id="50567-127">The general usage patterns are unchanged.</span></span> <span data-ttu-id="50567-128">Algumas sobrecargas e opções podem diferir para se adaptar às alterações nas APIs SDK subjacentes.</span><span class="sxs-lookup"><span data-stu-id="50567-128">Some overloads and options may differ to adapt to changes in the underlying Azure SDK APIs.</span></span>

<span data-ttu-id="50567-129">Os pacotes antigos:</span><span class="sxs-lookup"><span data-stu-id="50567-129">The old packages will:</span></span>

* <span data-ttu-id="50567-130">Seja apoiado pela equipe ASP.NET Core durante toda a vida do .NET Core 2.1 e 3.1.</span><span class="sxs-lookup"><span data-stu-id="50567-130">Be supported by the ASP.NET Core team for the lifetime of .NET Core 2.1 and 3.1.</span></span>
* <span data-ttu-id="50567-131">Não ser incluído em .NET 5.</span><span class="sxs-lookup"><span data-stu-id="50567-131">Not be included in .NET 5.</span></span>

<span data-ttu-id="50567-132">Ao atualizar seu projeto para .NET `Azure.*` 5, transicione para os pacotes para manter o suporte.</span><span class="sxs-lookup"><span data-stu-id="50567-132">When upgrading your project to .NET 5, transition to the `Azure.*` packages to maintain support.</span></span>

#### <a name="category"></a><span data-ttu-id="50567-133">Categoria</span><span class="sxs-lookup"><span data-stu-id="50567-133">Category</span></span>

<span data-ttu-id="50567-134">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="50567-134">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="50567-135">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="50567-135">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
