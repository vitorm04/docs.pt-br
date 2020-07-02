---
ms.openlocfilehash: c5a061dffa1deb66e1769d6ec70dfa2155ac6a31
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85615597"
---
### <a name="calling-createdefaultauthorizationcontext-with-a-null-argument-has-changed"></a><span data-ttu-id="16e50-101">Chamada para CreateDefaultAuthorizationContext com um argumento nulo foi alterada</span><span class="sxs-lookup"><span data-stu-id="16e50-101">Calling CreateDefaultAuthorizationContext with a null argument has changed</span></span>

#### <a name="details"></a><span data-ttu-id="16e50-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="16e50-102">Details</span></span>

<span data-ttu-id="16e50-103">A implementação de <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=fullName> retornado por uma chamada a <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=fullName> com um argumento authorizationPolicies nulo mudou sua implementação no .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="16e50-103">The implementation of the <xref:System.IdentityModel.Policy.AuthorizationContext?displayProperty=fullName> returned by a call to the <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=fullName> with a null authorizationPolicies argument has changed its implementation in the .NET Framework 4.6.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="16e50-104">Sugestão</span><span class="sxs-lookup"><span data-stu-id="16e50-104">Suggestion</span></span>

<span data-ttu-id="16e50-105">Em casos raros, os aplicativos WCF que usam a autenticação personalizada podem ver diferenças de comportamento.</span><span class="sxs-lookup"><span data-stu-id="16e50-105">In rare cases, WCF apps that use custom authentication may see behavioral differences.</span></span> <span data-ttu-id="16e50-106">Nesses casos, o comportamento anterior pode ser restaurado de uma destas duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="16e50-106">In such cases, the previous behavior can be restored in either of two ways:</span></span>

- <span data-ttu-id="16e50-107">Recompile o aplicativo para se destinar a uma versão anterior ao .NET Framework 4.6.</span><span class="sxs-lookup"><span data-stu-id="16e50-107">Recompile your app to target an earlier version of the .NET Framework than 4.6.</span></span> <span data-ttu-id="16e50-108">Para serviços hospedados pelo IIS, use o elemento `<httpRuntime targetFramework="x.x">` para direcionar a uma versão anterior do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16e50-108">For IIS-hosted services, use the `<httpRuntime targetFramework="x.x">` element to target an earlier version of the .NET Framework.</span></span>
- <span data-ttu-id="16e50-109">Adicione a seguinte linha à seção `<appSettings>` de seu arquivo app.config:</span><span class="sxs-lookup"><span data-stu-id="16e50-109">Add the following line to the `<appSettings>` section of your app.config file:</span></span>

    ```xml
    <add key="appContext.SetSwitch:Switch.System.IdentityModel.EnableCachedEmptyDefaultAuthorizationContext" value="true" />
    ```

| <span data-ttu-id="16e50-110">Name</span><span class="sxs-lookup"><span data-stu-id="16e50-110">Name</span></span>    | <span data-ttu-id="16e50-111">Valor</span><span class="sxs-lookup"><span data-stu-id="16e50-111">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="16e50-112">Escopo</span><span class="sxs-lookup"><span data-stu-id="16e50-112">Scope</span></span>   | <span data-ttu-id="16e50-113">Secundária</span><span class="sxs-lookup"><span data-stu-id="16e50-113">Minor</span></span>       |
| <span data-ttu-id="16e50-114">Versão</span><span class="sxs-lookup"><span data-stu-id="16e50-114">Version</span></span> | <span data-ttu-id="16e50-115">4.6</span><span class="sxs-lookup"><span data-stu-id="16e50-115">4.6</span></span>         |
| <span data-ttu-id="16e50-116">Type</span><span class="sxs-lookup"><span data-stu-id="16e50-116">Type</span></span>    | <span data-ttu-id="16e50-117">Redirecionando</span><span class="sxs-lookup"><span data-stu-id="16e50-117">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="16e50-118">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="16e50-118">Affected APIs</span></span>

- <xref:System.IdentityModel.Policy.AuthorizationContext.CreateDefaultAuthorizationContext(System.Collections.Generic.IList{System.IdentityModel.Policy.IAuthorizationPolicy})?displayProperty=nameWithType>
