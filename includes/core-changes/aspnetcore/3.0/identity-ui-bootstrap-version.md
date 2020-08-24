---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394000"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a><span data-ttu-id="14cbf-101">Identidade: versão de inicialização padrão da interface do usuário alterada</span><span class="sxs-lookup"><span data-stu-id="14cbf-101">Identity: Default Bootstrap version of UI changed</span></span>

<span data-ttu-id="14cbf-102">A partir do ASP.NET Core 3,0, a interface do usuário de identidade usa como padrão a versão 4 da inicialização.</span><span class="sxs-lookup"><span data-stu-id="14cbf-102">Starting in ASP.NET Core 3.0, Identity UI defaults to using version 4 of Bootstrap.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="14cbf-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="14cbf-103">Version introduced</span></span>

<span data-ttu-id="14cbf-104">3,0</span><span class="sxs-lookup"><span data-stu-id="14cbf-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="14cbf-105">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="14cbf-105">Old behavior</span></span>

<span data-ttu-id="14cbf-106">A `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` chamada do método era igual a `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span><span class="sxs-lookup"><span data-stu-id="14cbf-106">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call was the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="14cbf-107">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="14cbf-107">New behavior</span></span>

<span data-ttu-id="14cbf-108">A `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` chamada do método é igual a `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span><span class="sxs-lookup"><span data-stu-id="14cbf-108">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call is the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="14cbf-109">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="14cbf-109">Reason for change</span></span>

<span data-ttu-id="14cbf-110">A inicialização 4 foi lançada durante ASP.NET Core período de tempo de 3,0.</span><span class="sxs-lookup"><span data-stu-id="14cbf-110">Bootstrap 4 was released during ASP.NET Core 3.0 timeframe.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="14cbf-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="14cbf-111">Recommended action</span></span>

<span data-ttu-id="14cbf-112">Você será afetado por essa alteração se usar a interface do usuário de identidade padrão e a tiver adicionado no `Startup.ConfigureServices` , conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="14cbf-112">You're impacted by this change if you use the default Identity UI and have added it in `Startup.ConfigureServices` as shown in the following example:</span></span>

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

<span data-ttu-id="14cbf-113">Execute uma das seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="14cbf-113">Take one of the following actions:</span></span>

- <span data-ttu-id="14cbf-114">Migre seu aplicativo para usar a inicialização 4 usando o [Guia de migração](https://getbootstrap.com/docs/4.0/migration).</span><span class="sxs-lookup"><span data-stu-id="14cbf-114">Migrate your app to use Bootstrap 4 using their [migration guide](https://getbootstrap.com/docs/4.0/migration).</span></span>
- <span data-ttu-id="14cbf-115">Atualize `Startup.ConfigureServices` para impor o uso da inicialização 3.</span><span class="sxs-lookup"><span data-stu-id="14cbf-115">Update `Startup.ConfigureServices` to enforce usage of Bootstrap 3.</span></span> <span data-ttu-id="14cbf-116">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="14cbf-116">For example:</span></span>

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a><span data-ttu-id="14cbf-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="14cbf-117">Category</span></span>

<span data-ttu-id="14cbf-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="14cbf-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="14cbf-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="14cbf-119">Affected APIs</span></span>

<span data-ttu-id="14cbf-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="14cbf-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
