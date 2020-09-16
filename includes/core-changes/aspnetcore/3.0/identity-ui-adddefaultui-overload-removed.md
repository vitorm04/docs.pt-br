---
ms.openlocfilehash: e77312605ee367c159171e305d8f69429f9ac58b
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539563"
---
### <a name="identity-adddefaultui-method-overload-removed"></a><span data-ttu-id="73aa0-101">Identidade: sobrecarga do método AddDefaultUI removida</span><span class="sxs-lookup"><span data-stu-id="73aa0-101">Identity: AddDefaultUI method overload removed</span></span>

<span data-ttu-id="73aa0-102">A partir do ASP.NET Core 3,0, a sobrecarga do método [IdentityBuilderUIExtensions. AddDefaultUI (IdentityBuilder, UIFramework)](/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_) não existe mais.</span><span class="sxs-lookup"><span data-stu-id="73aa0-102">Starting with ASP.NET Core 3.0, the [IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)](/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_) method overload no longer exists.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="73aa0-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="73aa0-103">Version introduced</span></span>

<span data-ttu-id="73aa0-104">3.0</span><span class="sxs-lookup"><span data-stu-id="73aa0-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="73aa0-105">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="73aa0-105">Reason for change</span></span>

<span data-ttu-id="73aa0-106">Essa alteração foi resultado da adoção do recurso de ativos da Web estáticos.</span><span class="sxs-lookup"><span data-stu-id="73aa0-106">This change was a result of adoption of the static web assets feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="73aa0-107">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="73aa0-107">Recommended action</span></span>

<span data-ttu-id="73aa0-108">Chame <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> em vez da sobrecarga que usa dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="73aa0-108">Call <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> instead of the overload that takes two arguments.</span></span> <span data-ttu-id="73aa0-109">Se você estiver usando a inicialização 3, adicione também a seguinte linha a um `<PropertyGroup>` elemento em seu arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="73aa0-109">If you're using Bootstrap 3, also add the following line to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="73aa0-110">Categoria</span><span class="sxs-lookup"><span data-stu-id="73aa0-110">Category</span></span>

<span data-ttu-id="73aa0-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="73aa0-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="73aa0-112">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="73aa0-112">Affected APIs</span></span>

[<span data-ttu-id="73aa0-113">IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)</span><span class="sxs-lookup"><span data-stu-id="73aa0-113">IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)</span></span>](/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
