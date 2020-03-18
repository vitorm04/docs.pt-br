---
ms.openlocfilehash: 6f8e6d2786d20e055c9bef63891db4d6f88bc64b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901851"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a><span data-ttu-id="8aac7-101">Identidade: O construtor SignInManager aceita novo parâmetro</span><span class="sxs-lookup"><span data-stu-id="8aac7-101">Identity: SignInManager constructor accepts new parameter</span></span>

<span data-ttu-id="8aac7-102">Começando com ASP.NET Núcleo 3.0, um `IUserConfirmation<TUser>` novo `SignInManager` parâmetro foi adicionado ao construtor.</span><span class="sxs-lookup"><span data-stu-id="8aac7-102">Starting with ASP.NET Core 3.0, a new `IUserConfirmation<TUser>` parameter was added to the `SignInManager` constructor.</span></span> <span data-ttu-id="8aac7-103">Para obter mais informações, consulte [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span><span class="sxs-lookup"><span data-stu-id="8aac7-103">For more information, see [dotnet/aspnetcore#8356](https://github.com/dotnet/aspnetcore/issues/8356).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8aac7-104">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="8aac7-104">Version introduced</span></span>

<span data-ttu-id="8aac7-105">3.0</span><span class="sxs-lookup"><span data-stu-id="8aac7-105">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="8aac7-106">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="8aac7-106">Reason for change</span></span>

<span data-ttu-id="8aac7-107">A motivação para a mudança foi adicionar suporte para novos fluxos de e-mail/confirmação em Identidade.</span><span class="sxs-lookup"><span data-stu-id="8aac7-107">The motivation for the change was to add support for new email / confirmation flows in Identity.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8aac7-108">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="8aac7-108">Recommended action</span></span>

<span data-ttu-id="8aac7-109">Se construir manualmente `SignInManager`um , `IUserConfirmation` forneça uma implementação ou pegue uma da injeção de dependência para fornecer.</span><span class="sxs-lookup"><span data-stu-id="8aac7-109">If manually constructing a `SignInManager`, provide an implementation of `IUserConfirmation` or grab one from dependency injection to provide.</span></span>

#### <a name="category"></a><span data-ttu-id="8aac7-110">Categoria</span><span class="sxs-lookup"><span data-stu-id="8aac7-110">Category</span></span>

<span data-ttu-id="8aac7-111">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8aac7-111">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8aac7-112">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="8aac7-112">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
