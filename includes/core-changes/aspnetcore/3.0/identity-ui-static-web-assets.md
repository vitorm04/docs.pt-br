---
ms.openlocfilehash: 8d7942ef6c36c01a9ae7ae2a9739f26dfcda5813
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394082"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a><span data-ttu-id="fabaa-101">Identidade: a interface do usuário usa o recurso de ativos da Web estáticos</span><span class="sxs-lookup"><span data-stu-id="fabaa-101">Identity: UI uses static web assets feature</span></span>

<span data-ttu-id="fabaa-102">O ASP.NET Core 3,0 introduziu um recurso de ativos da Web estático e a interface do usuário da identidade o adotou.</span><span class="sxs-lookup"><span data-stu-id="fabaa-102">ASP.NET Core 3.0 introduced a static web assets feature, and Identity UI has adopted it.</span></span>

#### <a name="change-description"></a><span data-ttu-id="fabaa-103">Alterar descrição</span><span class="sxs-lookup"><span data-stu-id="fabaa-103">Change description</span></span>

<span data-ttu-id="fabaa-104">Como resultado da interface do usuário de identidade adotando o recurso de ativos da Web estáticos:</span><span class="sxs-lookup"><span data-stu-id="fabaa-104">As a result of Identity UI adopting the static web assets feature:</span></span>

- <span data-ttu-id="fabaa-105">A seleção de estrutura é realizada usando a propriedade `IdentityUIFrameworkVersion` em seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="fabaa-105">Framework selection is accomplished by using the `IdentityUIFrameworkVersion` property in your project file.</span></span>
- <span data-ttu-id="fabaa-106">A inicialização 4 é a estrutura de interface do usuário padrão para a interface do usuário de identidade.</span><span class="sxs-lookup"><span data-stu-id="fabaa-106">Bootstrap 4 is the default UI framework for Identity UI.</span></span> <span data-ttu-id="fabaa-107">A inicialização 3 atingiu o fim da vida útil e você deve considerar a migração para uma versão com suporte.</span><span class="sxs-lookup"><span data-stu-id="fabaa-107">Bootstrap 3 has reached end of life, and you should consider migrating to a supported version.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="fabaa-108">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="fabaa-108">Version introduced</span></span>

<span data-ttu-id="fabaa-109">3.0</span><span class="sxs-lookup"><span data-stu-id="fabaa-109">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="fabaa-110">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="fabaa-110">Old behavior</span></span>

<span data-ttu-id="fabaa-111">A estrutura de interface do usuário padrão da interface do usuário de identidade foi a **inicialização 3**.</span><span class="sxs-lookup"><span data-stu-id="fabaa-111">The default UI framework for Identity UI was **Bootstrap 3**.</span></span> <span data-ttu-id="fabaa-112">A estrutura da interface do usuário pode ser configurada usando um parâmetro para a chamada do método `AddIdentityUI` em `Startup.ConfigureServices`.</span><span class="sxs-lookup"><span data-stu-id="fabaa-112">The UI framework could be configured using a parameter to the `AddIdentityUI` method call in `Startup.ConfigureServices`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="fabaa-113">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="fabaa-113">New behavior</span></span>

<span data-ttu-id="fabaa-114">A estrutura de interface do usuário padrão para identidade de interface do usuário é **Bootstrap 4**.</span><span class="sxs-lookup"><span data-stu-id="fabaa-114">The default UI framework for Identity UI is **Bootstrap 4**.</span></span> <span data-ttu-id="fabaa-115">A estrutura da interface do usuário deve ser configurada em seu arquivo de projeto, em vez de na chamada do método `AddIdentityUI`.</span><span class="sxs-lookup"><span data-stu-id="fabaa-115">The UI framework must be configured in your project file, instead of in the `AddIdentityUI` method call.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="fabaa-116">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="fabaa-116">Reason for change</span></span>

<span data-ttu-id="fabaa-117">A adoção do recurso de ativos da Web estáticos exigia que a configuração da estrutura da interface do usuário se mova para o MSBuild.</span><span class="sxs-lookup"><span data-stu-id="fabaa-117">Adoption of the static web assets feature required that the UI framework configuration move to MSBuild.</span></span> <span data-ttu-id="fabaa-118">A decisão sobre qual estrutura deve ser inserida é uma decisão em tempo de compilação, não uma decisão de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="fabaa-118">The decision on which framework to embed is a build-time decision, not a runtime decision.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="fabaa-119">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="fabaa-119">Recommended action</span></span>

<span data-ttu-id="fabaa-120">Examine a interface do usuário do site para garantir que os novos componentes Bootstrap 4 sejam compatíveis.</span><span class="sxs-lookup"><span data-stu-id="fabaa-120">Review your site UI to ensure the new Bootstrap 4 components are compatible.</span></span> <span data-ttu-id="fabaa-121">Se necessário, use a propriedade do MSBuild `IdentityUIFrameworkVersion` para reverter para a inicialização 3.</span><span class="sxs-lookup"><span data-stu-id="fabaa-121">If necessary, use the `IdentityUIFrameworkVersion` MSBuild property to revert to Bootstrap 3.</span></span> <span data-ttu-id="fabaa-122">Adicione a propriedade a um elemento `<PropertyGroup>` em seu arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="fabaa-122">Add the property to a `<PropertyGroup>` element in your project file:</span></span>

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a><span data-ttu-id="fabaa-123">Categoria</span><span class="sxs-lookup"><span data-stu-id="fabaa-123">Category</span></span>

<span data-ttu-id="fabaa-124">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="fabaa-124">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="fabaa-125">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="fabaa-125">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder)`

-->
