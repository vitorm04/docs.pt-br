---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73041653"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a><span data-ttu-id="d070a-101">Identidade: a interface do usuário usa o recurso de ativos da Web estáticos</span><span class="sxs-lookup"><span data-stu-id="d070a-101">Identity: UI uses static web assets feature</span></span>

<span data-ttu-id="d070a-102">O ASP.NET Core 3,0 introduziu um recurso de ativos da Web estático e a interface do usuário da identidade o adotou.</span><span class="sxs-lookup"><span data-stu-id="d070a-102">ASP.NET Core 3.0 introduced a static web assets feature, and Identity UI has adopted it.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d070a-103">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="d070a-103">Change description</span></span>

<span data-ttu-id="d070a-104">Como resultado da interface do usuário de identidade adotando o recurso de ativos da Web estáticos:</span><span class="sxs-lookup"><span data-stu-id="d070a-104">As a result of Identity UI adopting the static web assets feature:</span></span>

- <span data-ttu-id="d070a-105">A seleção de estrutura é realizada usando a `IdentityUIFrameworkVersion` propriedade em seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="d070a-105">Framework selection is accomplished by using the `IdentityUIFrameworkVersion` property in your project file.</span></span>
- <span data-ttu-id="d070a-106">A inicialização 4 é a estrutura de interface do usuário padrão para a interface do usuário de identidade.</span><span class="sxs-lookup"><span data-stu-id="d070a-106">Bootstrap 4 is the default UI framework for Identity UI.</span></span> <span data-ttu-id="d070a-107">A inicialização 3 atingiu o fim da vida útil e você deve considerar a migração para uma versão com suporte.</span><span class="sxs-lookup"><span data-stu-id="d070a-107">Bootstrap 3 has reached end of life, and you should consider migrating to a supported version.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d070a-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="d070a-108">Version introduced</span></span>

<span data-ttu-id="d070a-109">3,0</span><span class="sxs-lookup"><span data-stu-id="d070a-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="d070a-110">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="d070a-110">Old behavior</span></span>

<span data-ttu-id="d070a-111">A estrutura de interface do usuário padrão da interface do usuário de identidade foi a **inicialização 3**.</span><span class="sxs-lookup"><span data-stu-id="d070a-111">The default UI framework for Identity UI was **Bootstrap 3**.</span></span> <span data-ttu-id="d070a-112">A estrutura da interface do usuário pode ser configurada usando um parâmetro para a `AddDefaultUI` chamada do método no `Startup.ConfigureServices` .</span><span class="sxs-lookup"><span data-stu-id="d070a-112">The UI framework could be configured using a parameter to the `AddDefaultUI` method call in `Startup.ConfigureServices`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="d070a-113">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="d070a-113">New behavior</span></span>

<span data-ttu-id="d070a-114">A estrutura de interface do usuário padrão para identidade de interface do usuário é **Bootstrap 4**.</span><span class="sxs-lookup"><span data-stu-id="d070a-114">The default UI framework for Identity UI is **Bootstrap 4**.</span></span> <span data-ttu-id="d070a-115">A estrutura da interface do usuário deve ser configurada em seu arquivo de projeto, em vez de na `AddDefaultUI` chamada do método.</span><span class="sxs-lookup"><span data-stu-id="d070a-115">The UI framework must be configured in your project file, instead of in the `AddDefaultUI` method call.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="d070a-116">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="d070a-116">Reason for change</span></span>

<span data-ttu-id="d070a-117">A adoção do recurso de ativos da Web estáticos exigia que a configuração da estrutura da interface do usuário se mova para o MSBuild.</span><span class="sxs-lookup"><span data-stu-id="d070a-117">Adoption of the static web assets feature required that the UI framework configuration move to MSBuild.</span></span> <span data-ttu-id="d070a-118">A decisão sobre qual estrutura deve ser inserida é uma decisão em tempo de compilação, não uma decisão de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d070a-118">The decision on which framework to embed is a build-time decision, not a runtime decision.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d070a-119">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="d070a-119">Recommended action</span></span>

<span data-ttu-id="d070a-120">Examine a interface do usuário do site para garantir que os novos componentes Bootstrap 4 sejam compatíveis.</span><span class="sxs-lookup"><span data-stu-id="d070a-120">Review your site UI to ensure the new Bootstrap 4 components are compatible.</span></span> <span data-ttu-id="d070a-121">Se necessário, use a `IdentityUIFrameworkVersion` Propriedade MSBuild para reverter para a inicialização 3.</span><span class="sxs-lookup"><span data-stu-id="d070a-121">If necessary, use the `IdentityUIFrameworkVersion` MSBuild property to revert to Bootstrap 3.</span></span> <span data-ttu-id="d070a-122">Adicione a propriedade a um `<PropertyGroup>` elemento em seu arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="d070a-122">Add the property to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="d070a-123">Categoria</span><span class="sxs-lookup"><span data-stu-id="d070a-123">Category</span></span>

<span data-ttu-id="d070a-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d070a-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d070a-125">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="d070a-125">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
