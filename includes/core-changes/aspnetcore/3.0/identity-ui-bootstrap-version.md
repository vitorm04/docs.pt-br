---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394000"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a><span data-ttu-id="64dc3-101">Identidade: Versão padrão do Bootstrap da interface do ui alterada</span><span class="sxs-lookup"><span data-stu-id="64dc3-101">Identity: Default Bootstrap version of UI changed</span></span>

<span data-ttu-id="64dc3-102">A partir de ASP.NET Core 3.0, a Interface do Usuário de Identidade não usa a versão 4 do Bootstrap.</span><span class="sxs-lookup"><span data-stu-id="64dc3-102">Starting in ASP.NET Core 3.0, Identity UI defaults to using version 4 of Bootstrap.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="64dc3-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="64dc3-103">Version introduced</span></span>

<span data-ttu-id="64dc3-104">3.0</span><span class="sxs-lookup"><span data-stu-id="64dc3-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="64dc3-105">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="64dc3-105">Old behavior</span></span>

<span data-ttu-id="64dc3-106">A `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` chamada do método era a mesma que`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span><span class="sxs-lookup"><span data-stu-id="64dc3-106">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call was the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="64dc3-107">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="64dc3-107">New behavior</span></span>

<span data-ttu-id="64dc3-108">A `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` chamada do método é a mesma que`services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span><span class="sxs-lookup"><span data-stu-id="64dc3-108">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call is the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="64dc3-109">Motivo da mudança</span><span class="sxs-lookup"><span data-stu-id="64dc3-109">Reason for change</span></span>

<span data-ttu-id="64dc3-110">Bootstrap 4 foi lançado durante ASP.NET período de tempo do Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="64dc3-110">Bootstrap 4 was released during ASP.NET Core 3.0 timeframe.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="64dc3-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="64dc3-111">Recommended action</span></span>

<span data-ttu-id="64dc3-112">Você será impactado por essa alteração se usar a ui `Startup.ConfigureServices` de identidade padrão e adicioná-la como mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="64dc3-112">You're impacted by this change if you use the default Identity UI and have added it in `Startup.ConfigureServices` as shown in the following example:</span></span>

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

<span data-ttu-id="64dc3-113">Execute uma das seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="64dc3-113">Take one of the following actions:</span></span>

- <span data-ttu-id="64dc3-114">Migre seu aplicativo para usar o Bootstrap 4 usando seu [guia de migração](https://getbootstrap.com/docs/4.0/migration).</span><span class="sxs-lookup"><span data-stu-id="64dc3-114">Migrate your app to use Bootstrap 4 using their [migration guide](https://getbootstrap.com/docs/4.0/migration).</span></span>
- <span data-ttu-id="64dc3-115">Atualização `Startup.ConfigureServices` para reforçar o uso do Bootstrap 3.</span><span class="sxs-lookup"><span data-stu-id="64dc3-115">Update `Startup.ConfigureServices` to enforce usage of Bootstrap 3.</span></span> <span data-ttu-id="64dc3-116">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="64dc3-116">For example:</span></span>

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a><span data-ttu-id="64dc3-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="64dc3-117">Category</span></span>

<span data-ttu-id="64dc3-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="64dc3-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="64dc3-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="64dc3-119">Affected APIs</span></span>

<span data-ttu-id="64dc3-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="64dc3-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
