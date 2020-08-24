---
ms.openlocfilehash: 474f039cf00cb48761bfe7b7c4a0a9c6300cd820
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2020
ms.locfileid: "81637191"
---
### <a name="identity-adddefaultui-method-overload-removed"></a><span data-ttu-id="09ada-101">Identidade: sobrecarga do método AddDefaultUI removida</span><span class="sxs-lookup"><span data-stu-id="09ada-101">Identity: AddDefaultUI method overload removed</span></span>

<span data-ttu-id="09ada-102">A partir do ASP.NET Core 3,0, a sobrecarga do método [IdentityBuilderUIExtensions. AddDefaultUI (IdentityBuilder, UIFramework)](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_) não existe mais.</span><span class="sxs-lookup"><span data-stu-id="09ada-102">Starting with ASP.NET Core 3.0, the [IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_) method overload no longer exists.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="09ada-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="09ada-103">Version introduced</span></span>

<span data-ttu-id="09ada-104">3,0</span><span class="sxs-lookup"><span data-stu-id="09ada-104">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="09ada-105">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="09ada-105">Reason for change</span></span>

<span data-ttu-id="09ada-106">Essa alteração foi resultado da adoção do recurso de ativos da Web estáticos.</span><span class="sxs-lookup"><span data-stu-id="09ada-106">This change was a result of adoption of the static web assets feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="09ada-107">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="09ada-107">Recommended action</span></span>

<span data-ttu-id="09ada-108">Chame <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> em vez da sobrecarga que usa dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="09ada-108">Call <xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType> instead of the overload that takes two arguments.</span></span> <span data-ttu-id="09ada-109">Se você estiver usando a inicialização 3, adicione também a seguinte linha a um `<PropertyGroup>` elemento em seu arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="09ada-109">If you're using Bootstrap 3, also add the following line to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="09ada-110">Categoria</span><span class="sxs-lookup"><span data-stu-id="09ada-110">Category</span></span>

<span data-ttu-id="09ada-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="09ada-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="09ada-112">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="09ada-112">Affected APIs</span></span>

[<span data-ttu-id="09ada-113">IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)</span><span class="sxs-lookup"><span data-stu-id="09ada-113">IdentityBuilderUIExtensions.AddDefaultUI(IdentityBuilder,UIFramework)</span></span>](https://docs.microsoft.com/dotnet/api/microsoft.aspnetcore.identity.identitybuilderuiextensions.adddefaultui?view=aspnetcore-2.2#Microsoft_AspNetCore_Identity_IdentityBuilderUIExtensions_AddDefaultUI_Microsoft_AspNetCore_Identity_IdentityBuilder_Microsoft_AspNetCore_Identity_UI_UIFramework_)

<!--

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
