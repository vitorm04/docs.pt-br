---
ms.openlocfilehash: c8f44ae1a500ed240dbff7d9a2c1479af368b7f1
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394000"
---
### <a name="identity-default-bootstrap-version-of-ui-changed"></a><span data-ttu-id="dd74c-101">Identidade: versão de inicialização padrão da interface do usuário alterada</span><span class="sxs-lookup"><span data-stu-id="dd74c-101">Identity: Default Bootstrap version of UI changed</span></span>

<span data-ttu-id="dd74c-102">A partir do ASP.NET Core 3,0, a interface do usuário de identidade usa como padrão a versão 4 da inicialização.</span><span class="sxs-lookup"><span data-stu-id="dd74c-102">Starting in ASP.NET Core 3.0, Identity UI defaults to using version 4 of Bootstrap.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="dd74c-103">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="dd74c-103">Version introduced</span></span>

<span data-ttu-id="dd74c-104">3.0</span><span class="sxs-lookup"><span data-stu-id="dd74c-104">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="dd74c-105">Comportamento antigo</span><span class="sxs-lookup"><span data-stu-id="dd74c-105">Old behavior</span></span>

<span data-ttu-id="dd74c-106">A chamada do método `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` era a mesma que `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span><span class="sxs-lookup"><span data-stu-id="dd74c-106">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call was the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);`</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="dd74c-107">Novo comportamento</span><span class="sxs-lookup"><span data-stu-id="dd74c-107">New behavior</span></span>

<span data-ttu-id="dd74c-108">A chamada do método `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` é a mesma que `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span><span class="sxs-lookup"><span data-stu-id="dd74c-108">The `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();` method call is the same as `services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap4);`</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="dd74c-109">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="dd74c-109">Reason for change</span></span>

<span data-ttu-id="dd74c-110">A inicialização 4 foi lançada durante ASP.NET Core período de tempo de 3,0.</span><span class="sxs-lookup"><span data-stu-id="dd74c-110">Bootstrap 4 was released during ASP.NET Core 3.0 timeframe.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="dd74c-111">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="dd74c-111">Recommended action</span></span>

<span data-ttu-id="dd74c-112">Você será afetado por essa alteração se usar a interface do usuário de identidade padrão e a tiver adicionado em `Startup.ConfigureServices`, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="dd74c-112">You're impacted by this change if you use the default Identity UI and have added it in `Startup.ConfigureServices` as shown in the following example:</span></span>

```csharp
services.AddDefaultIdentity<IdentityUser>().AddDefaultUI();
```

<span data-ttu-id="dd74c-113">Execute uma das seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="dd74c-113">Take one of the following actions:</span></span>

- <span data-ttu-id="dd74c-114">Migre seu aplicativo para usar a inicialização 4 usando o [Guia de migração](https://getbootstrap.com/docs/4.0/migration).</span><span class="sxs-lookup"><span data-stu-id="dd74c-114">Migrate your app to use Bootstrap 4 using their [migration guide](https://getbootstrap.com/docs/4.0/migration).</span></span>
- <span data-ttu-id="dd74c-115">Atualize `Startup.ConfigureServices` para impor o uso da inicialização 3.</span><span class="sxs-lookup"><span data-stu-id="dd74c-115">Update `Startup.ConfigureServices` to enforce usage of Bootstrap 3.</span></span> <span data-ttu-id="dd74c-116">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="dd74c-116">For example:</span></span>

    ```csharp
    services.AddDefaultIdentity<IdentityUser>().AddDefaultUI(UIFramework.Bootstrap3);
    ```

#### <a name="category"></a><span data-ttu-id="dd74c-117">Categoria</span><span class="sxs-lookup"><span data-stu-id="dd74c-117">Category</span></span>

<span data-ttu-id="dd74c-118">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dd74c-118">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="dd74c-119">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="dd74c-119">Affected APIs</span></span>

<span data-ttu-id="dd74c-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="dd74c-120">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
