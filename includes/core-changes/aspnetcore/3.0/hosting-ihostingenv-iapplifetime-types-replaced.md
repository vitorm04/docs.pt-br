---
ms.openlocfilehash: be1fad236dd3eed047b010e93285aec8bc607b61
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394334"
---
### <a name="hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced"></a><span data-ttu-id="ee23f-101">Hospedagem: tipos IHostingEnvironment e IApplicationLifetime marcados como obsoletos e substituídos</span><span class="sxs-lookup"><span data-stu-id="ee23f-101">Hosting: IHostingEnvironment and IApplicationLifetime types marked obsolete and replaced</span></span>

<span data-ttu-id="ee23f-102">Novos tipos foram introduzidos para substituir os tipos existentes `IHostingEnvironment` e `IApplicationLifetime`.</span><span class="sxs-lookup"><span data-stu-id="ee23f-102">New types have been introduced to replace existing `IHostingEnvironment` and `IApplicationLifetime` types.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ee23f-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="ee23f-103">Version introduced</span></span>

<span data-ttu-id="ee23f-104">3.0</span><span class="sxs-lookup"><span data-stu-id="ee23f-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ee23f-105">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="ee23f-105">Old behavior</span></span>

<span data-ttu-id="ee23f-106">Havia dois tipos diferentes `IHostingEnvironment` e `IApplicationLifetime` de `Microsoft.Extensions.Hosting` e `Microsoft.AspNetCore.Hosting`.</span><span class="sxs-lookup"><span data-stu-id="ee23f-106">There were two different `IHostingEnvironment` and `IApplicationLifetime` types from `Microsoft.Extensions.Hosting` and `Microsoft.AspNetCore.Hosting`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ee23f-107">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="ee23f-107">New behavior</span></span>

<span data-ttu-id="ee23f-108">Os tipos antigos foram marcados como obsoletos e substituídos por novos tipos.</span><span class="sxs-lookup"><span data-stu-id="ee23f-108">The old types have been marked as obsolete and replaced with new types.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ee23f-109">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="ee23f-109">Reason for change</span></span>

<span data-ttu-id="ee23f-110">Quando `Microsoft.Extensions.Hosting` foi introduzido no ASP.NET Core 2,1, alguns tipos, como `IHostingEnvironment` e `IApplicationLifetime`, foram copiados de `Microsoft.AspNetCore.Hosting`.</span><span class="sxs-lookup"><span data-stu-id="ee23f-110">When `Microsoft.Extensions.Hosting` was introduced in ASP.NET Core 2.1, some types like `IHostingEnvironment` and `IApplicationLifetime` were copied from `Microsoft.AspNetCore.Hosting`.</span></span> <span data-ttu-id="ee23f-111">Algumas alterações ASP.NET Core 3,0 fazem com que os aplicativos incluam os namespaces `Microsoft.Extensions.Hosting` e `Microsoft.AspNetCore.Hosting`.</span><span class="sxs-lookup"><span data-stu-id="ee23f-111">Some ASP.NET Core 3.0 changes cause apps to include both the `Microsoft.Extensions.Hosting` and `Microsoft.AspNetCore.Hosting` namespaces.</span></span> <span data-ttu-id="ee23f-112">Qualquer uso desses tipos duplicados causa um erro de compilador "referência ambígua" quando ambos os namespaces são referenciados.</span><span class="sxs-lookup"><span data-stu-id="ee23f-112">Any use of those duplicate types causes an "ambiguous reference" compiler error when both namespaces are referenced.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ee23f-113">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="ee23f-113">Recommended action</span></span>

<span data-ttu-id="ee23f-114">Substituídos os usos dos tipos antigos pelos tipos introduzidos recentemente, como abaixo:</span><span class="sxs-lookup"><span data-stu-id="ee23f-114">Replaced any usages of the old types with the newly introduced types as below:</span></span>

<span data-ttu-id="ee23f-115">**Tipos obsoletos (aviso):**</span><span class="sxs-lookup"><span data-stu-id="ee23f-115">**Obsolete types (warning):**</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>

<span data-ttu-id="ee23f-116">**Novos tipos:**</span><span class="sxs-lookup"><span data-stu-id="ee23f-116">**New types:**</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment?displayProperty=nameWithType>
- `Microsoft.AspNetCore.Hosting.IWebHostEnvironment : IHostEnvironment`
- <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.Environments?displayProperty=nameWithType>

<span data-ttu-id="ee23f-117">Os novos métodos de extensão `IHostEnvironment` `IsDevelopment` e `IsProduction` estão no namespace `Microsoft.Extensions.Hosting`.</span><span class="sxs-lookup"><span data-stu-id="ee23f-117">The new `IHostEnvironment` `IsDevelopment` and `IsProduction` extension methods are in the `Microsoft.Extensions.Hosting` namespace.</span></span> <span data-ttu-id="ee23f-118">Esse namespace pode precisar ser adicionado ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="ee23f-118">That namespace may need to be added to your project.</span></span>

#### <a name="category"></a><span data-ttu-id="ee23f-119">Categoria</span><span class="sxs-lookup"><span data-stu-id="ee23f-119">Category</span></span>

<span data-ttu-id="ee23f-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ee23f-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ee23f-121">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="ee23f-121">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Hosting.IHostingEnvironment?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.EnvironmentName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IApplicationLifetime?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostingEnvironment?displayProperty=nameWithType>

<!-- 

#### Affected APIs

- `T:Microsoft.AspNetCore.Hosting.EnvironmentName`
- `T:Microsoft.AspNetCore.Hosting.IApplicationLifetime`
- `T:Microsoft.AspNetCore.Hosting.IHostingEnvironment`
- `T:Microsoft.Extensions.Hosting.EnvironmentName`
- `T:Microsoft.Extensions.Hosting.IApplicationLifetime`
- `T:Microsoft.Extensions.Hosting.IHostingEnvironment`

-->
