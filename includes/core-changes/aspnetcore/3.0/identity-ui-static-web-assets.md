---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73041653"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a><span data-ttu-id="0c9e5-101">Identidade: A ui usa o recurso de ativos web estáticos</span><span class="sxs-lookup"><span data-stu-id="0c9e5-101">Identity: UI uses static web assets feature</span></span>

<span data-ttu-id="0c9e5-102">ASP.NET Core 3.0 introduziu um recurso de ativos web estáticos, e a II de identidade o adotou.</span><span class="sxs-lookup"><span data-stu-id="0c9e5-102">ASP.NET Core 3.0 introduced a static web assets feature, and Identity UI has adopted it.</span></span>

#### <a name="change-description"></a><span data-ttu-id="0c9e5-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="0c9e5-103">Change description</span></span>

<span data-ttu-id="0c9e5-104">Como resultado da iu de identidade adotando o recurso de ativos web estáticos:</span><span class="sxs-lookup"><span data-stu-id="0c9e5-104">As a result of Identity UI adopting the static web assets feature:</span></span>

- <span data-ttu-id="0c9e5-105">A seleção do `IdentityUIFrameworkVersion` framework é realizada usando a propriedade em seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="0c9e5-105">Framework selection is accomplished by using the `IdentityUIFrameworkVersion` property in your project file.</span></span>
- <span data-ttu-id="0c9e5-106">Bootstrap 4 é a estrutura de interface do iu padrão para interface do iu de identidade.</span><span class="sxs-lookup"><span data-stu-id="0c9e5-106">Bootstrap 4 is the default UI framework for Identity UI.</span></span> <span data-ttu-id="0c9e5-107">Bootstrap 3 chegou ao fim da vida útil, e você deve considerar migrar para uma versão suportada.</span><span class="sxs-lookup"><span data-stu-id="0c9e5-107">Bootstrap 3 has reached end of life, and you should consider migrating to a supported version.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="0c9e5-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="0c9e5-108">Version introduced</span></span>

<span data-ttu-id="0c9e5-109">3.0</span><span class="sxs-lookup"><span data-stu-id="0c9e5-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="0c9e5-110">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="0c9e5-110">Old behavior</span></span>

<span data-ttu-id="0c9e5-111">A estrutura de interface do ui padrão para iu de identidade era **Bootstrap 3**.</span><span class="sxs-lookup"><span data-stu-id="0c9e5-111">The default UI framework for Identity UI was **Bootstrap 3**.</span></span> <span data-ttu-id="0c9e5-112">A estrutura de IA pode ser configurada usando um parâmetro para a chamada do `AddDefaultUI` método `Startup.ConfigureServices`.</span><span class="sxs-lookup"><span data-stu-id="0c9e5-112">The UI framework could be configured using a parameter to the `AddDefaultUI` method call in `Startup.ConfigureServices`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="0c9e5-113">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="0c9e5-113">New behavior</span></span>

<span data-ttu-id="0c9e5-114">A estrutura de interface do rei padrão para interface do iu de identidade é **Bootstrap 4**.</span><span class="sxs-lookup"><span data-stu-id="0c9e5-114">The default UI framework for Identity UI is **Bootstrap 4**.</span></span> <span data-ttu-id="0c9e5-115">A estrutura de IA deve ser configurada no `AddDefaultUI` arquivo do projeto, em vez de na chamada do método.</span><span class="sxs-lookup"><span data-stu-id="0c9e5-115">The UI framework must be configured in your project file, instead of in the `AddDefaultUI` method call.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="0c9e5-116">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="0c9e5-116">Reason for change</span></span>

<span data-ttu-id="0c9e5-117">A adoção do recurso de ativos web estáticos exigiu que a configuração da estrutura de ida e qualquer outra seja para o MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0c9e5-117">Adoption of the static web assets feature required that the UI framework configuration move to MSBuild.</span></span> <span data-ttu-id="0c9e5-118">A decisão sobre qual quadro incorporar é uma decisão de tempo de construção, não uma decisão em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0c9e5-118">The decision on which framework to embed is a build-time decision, not a runtime decision.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="0c9e5-119">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="0c9e5-119">Recommended action</span></span>

<span data-ttu-id="0c9e5-120">Revise a interface do site para garantir que os novos componentes bootstrap 4 sejam compatíveis.</span><span class="sxs-lookup"><span data-stu-id="0c9e5-120">Review your site UI to ensure the new Bootstrap 4 components are compatible.</span></span> <span data-ttu-id="0c9e5-121">Se necessário, `IdentityUIFrameworkVersion` use a propriedade MSBuild para reverter para Bootstrap 3.</span><span class="sxs-lookup"><span data-stu-id="0c9e5-121">If necessary, use the `IdentityUIFrameworkVersion` MSBuild property to revert to Bootstrap 3.</span></span> <span data-ttu-id="0c9e5-122">Adicione a propriedade `<PropertyGroup>` a um elemento no arquivo do projeto:</span><span class="sxs-lookup"><span data-stu-id="0c9e5-122">Add the property to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="0c9e5-123">Categoria</span><span class="sxs-lookup"><span data-stu-id="0c9e5-123">Category</span></span>

<span data-ttu-id="0c9e5-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0c9e5-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="0c9e5-125">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="0c9e5-125">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
