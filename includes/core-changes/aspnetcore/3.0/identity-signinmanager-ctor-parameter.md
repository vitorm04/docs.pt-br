---
ms.openlocfilehash: 6f8e6d2786d20e055c9bef63891db4d6f88bc64b
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901851"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="be5e4-101">Identity: o Construtor SignInManager aceita o novo parâmetro</span><span class="sxs-lookup"><span data-stu-id="be5e4-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="be5e4-102">A partir do ASP.NET Core 3,0, um novo parâmetro `IUserConfirmation<TUser>` foi adicionado ao Construtor `SignInManager`.</span><span class="sxs-lookup"><span data-stu-id="be5e4-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="be5e4-103">Para obter mais informações, consulte [dotnet/aspnetcore # 8356](https://github.com/dotnet/aspnetcore/issues/8356).</span><span class="sxs-lookup"><span data-stu-id="be5e4-103">For more information, see [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="be5e4-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="be5e4-104">Version introduced</span></span>

<span data-ttu-id="be5e4-105">3.0</span><span class="sxs-lookup"><span data-stu-id="be5e4-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="be5e4-106">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="be5e4-106">Reason for change</span></span>

<span data-ttu-id="be5e4-107">A motivação para a alteração foi adicionar suporte a novos fluxos de email/confirmação em identidade.</span><span class="sxs-lookup"><span data-stu-id="be5e4-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="be5e4-108">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="be5e4-108">Recommended action</span></span>

<span data-ttu-id="be5e4-109">Se você construir manualmente uma `SignInManager`, forneça uma implementação de `IUserConfirmation` ou pegue uma da injeção de dependência a ser fornecida.</span><span class="sxs-lookup"><span data-stu-id="be5e4-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="be5e4-110">Categoria</span><span class="sxs-lookup"><span data-stu-id="be5e4-110">Category</span></span>

<span data-ttu-id="be5e4-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="be5e4-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="be5e4-112">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="be5e4-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
