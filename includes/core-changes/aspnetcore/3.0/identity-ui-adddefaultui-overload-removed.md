---
ms.openlocfilehash: 806722ea9aec1c828786525e3155b7f624159ac1
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72522682"
---
### <a name="identity-adddefaultui-method-overload-removed"></a><span data-ttu-id="24132-101">Identidade: sobrecarga do método AddDefaultUI removida</span><span class="sxs-lookup"><span data-stu-id="24132-101">Identity: AddDefaultUI method overload removed</span></span>

<span data-ttu-id="24132-102">A partir do ASP.NET Core 3,0, a sobrecarga do método <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> não existe mais.</span><span class="sxs-lookup"><span data-stu-id="24132-102">Starting with ASP.NET Core 3.0, the <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType> method overload no longer exists.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="24132-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="24132-103">Version introduced</span></span>

<span data-ttu-id="24132-104">3.0</span><span class="sxs-lookup"><span data-stu-id="24132-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="24132-105">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="24132-105">Reason for change</span></span>

<span data-ttu-id="24132-106">Essa alteração foi resultado da adoção do recurso de ativos da Web estáticos.</span><span class="sxs-lookup"><span data-stu-id="24132-106">This change was a result of adoption of the static web assets feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="24132-107">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="24132-107">Recommended action</span></span>

<span data-ttu-id="24132-108">Chame <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> em vez da sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="24132-108">Call <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> instead of the overload.</span></span> <span data-ttu-id="24132-109">Se você estiver usando a inicialização 3, adicione também a seguinte linha a um elemento `<PropertyGroup>` em seu arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="24132-109">If you're using Bootstrap 3, also add the following line to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="24132-110">Categoria</span><span class="sxs-lookup"><span data-stu-id="24132-110">Category</span></span>

<span data-ttu-id="24132-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="24132-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="24132-112">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="24132-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
