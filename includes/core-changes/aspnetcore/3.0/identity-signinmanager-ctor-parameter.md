---
ms.openlocfilehash: ed5a90063b8963d79f412ec1c5c0b9030f980f83
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275164"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="b2fd9-101">Identidade: O construtor SignInManager aceita novo parâmetro</span><span class="sxs-lookup"><span data-stu-id="b2fd9-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="b2fd9-102">Começando com ASP.NET Núcleo 3.0, um `IUserConfirmation<TUser>` novo `SignInManager` parâmetro foi adicionado ao construtor.</span><span class="sxs-lookup"><span data-stu-id="b2fd9-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="b2fd9-103">Para obter mais informações, consulte [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span><span class="sxs-lookup"><span data-stu-id="b2fd9-103">For more information, see [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b2fd9-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="b2fd9-104">Version introduced</span></span>

<span data-ttu-id="b2fd9-105">3.0</span><span class="sxs-lookup"><span data-stu-id="b2fd9-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b2fd9-106">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="b2fd9-106">Reason for change</span></span>

<span data-ttu-id="b2fd9-107">A motivação para a mudança foi adicionar suporte para novos fluxos de e-mail/confirmação em Identidade.</span><span class="sxs-lookup"><span data-stu-id="b2fd9-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b2fd9-108">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="b2fd9-108">Recommended action</span></span>

<span data-ttu-id="b2fd9-109">Se construir manualmente `SignInManager`um , `IUserConfirmation` forneça uma implementação ou pegue uma da injeção de dependência para fornecer.</span><span class="sxs-lookup"><span data-stu-id="b2fd9-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="b2fd9-110">Categoria</span><span class="sxs-lookup"><span data-stu-id="b2fd9-110">Category</span></span>

<span data-ttu-id="b2fd9-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b2fd9-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b2fd9-112">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="b2fd9-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
