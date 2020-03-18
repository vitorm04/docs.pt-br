---
ms.openlocfilehash: 806722ea9aec1c828786525e3155b7f624159ac1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522682"
---
### <a name="identity-adddefaultui-method-overload-removed"></a><span data-ttu-id="a48e7-101">Identidade: Sobrecarga de método AddDefaultUI removida</span><span class="sxs-lookup"><span data-stu-id="a48e7-101">Identity: AddDefaultUI method overload removed</span></span>

<span data-ttu-id="a48e7-102">Começando com ASP.NET Núcleo 3.0, a sobrecarga do <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> método não existe mais.</span><span class="sxs-lookup"><span data-stu-id="a48e7-102">Starting with ASP.NET Core 3.0, the <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> method overload no longer exists.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a48e7-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="a48e7-103">Version introduced</span></span>

<span data-ttu-id="a48e7-104">3.0</span><span class="sxs-lookup"><span data-stu-id="a48e7-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a48e7-105">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="a48e7-105">Reason for change</span></span>

<span data-ttu-id="a48e7-106">Essa mudança foi resultado da adoção do recurso de ativos web estáticos.</span><span class="sxs-lookup"><span data-stu-id="a48e7-106">This change was a result of adoption of the static web assets feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a48e7-107">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="a48e7-107">Recommended action</span></span>

<span data-ttu-id="a48e7-108">Ligue <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> em vez da sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="a48e7-108">Call <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> instead of the overload.</span></span> <span data-ttu-id="a48e7-109">Se você estiver usando bootstrap 3, adicione `<PropertyGroup>` também a seguinte linha a um elemento no arquivo do projeto:</span><span class="sxs-lookup"><span data-stu-id="a48e7-109">If you're using Bootstrap 3, also add the following line to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="a48e7-110">Categoria</span><span class="sxs-lookup"><span data-stu-id="a48e7-110">Category</span></span>

<span data-ttu-id="a48e7-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a48e7-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a48e7-112">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="a48e7-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
