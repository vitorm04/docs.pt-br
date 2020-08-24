---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901777"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a><span data-ttu-id="1dc23-101">Hospedagem: host genérico restringe injeção de construtor de inicialização</span><span class="sxs-lookup"><span data-stu-id="1dc23-101">Hosting: Generic host restricts Startup constructor injection</span></span>

<span data-ttu-id="1dc23-102">Os únicos tipos aos quais o host genérico dá suporte para `Startup` injeção de construtor de classe são `IHostEnvironment` , `IWebHostEnvironment` e `IConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="1dc23-102">The only types the generic host supports for `Startup` class constructor injection are `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration`.</span></span> <span data-ttu-id="1dc23-103">Aplicativos que usam não `WebHost` são afetados.</span><span class="sxs-lookup"><span data-stu-id="1dc23-103">Apps using `WebHost` are unaffected.</span></span>

#### <a name="change-description"></a><span data-ttu-id="1dc23-104">Descrição da alteração</span><span class="sxs-lookup"><span data-stu-id="1dc23-104">Change description</span></span>

<span data-ttu-id="1dc23-105">Antes do ASP.NET Core 3,0, a injeção de Construtor poderia ser usada para tipos arbitrários no `Startup` Construtor da classe.</span><span class="sxs-lookup"><span data-stu-id="1dc23-105">Prior to ASP.NET Core 3.0, constructor injection could be used for arbitrary types in the `Startup` class's constructor.</span></span> <span data-ttu-id="1dc23-106">No ASP.NET Core 3,0, a pilha da Web foi replataforma na biblioteca de hosts genérica.</span><span class="sxs-lookup"><span data-stu-id="1dc23-106">In ASP.NET Core 3.0, the web stack was replatformed onto the generic host library.</span></span> <span data-ttu-id="1dc23-107">Você pode ver a alteração no arquivo *Program.cs* dos modelos:</span><span class="sxs-lookup"><span data-stu-id="1dc23-107">You can see the change in the *Program.cs* file of the templates:</span></span>

<span data-ttu-id="1dc23-108">**ASP.NET Core 2. x:**</span><span class="sxs-lookup"><span data-stu-id="1dc23-108">**ASP.NET Core 2.x:**</span></span>

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

<span data-ttu-id="1dc23-109">**ASP.NET Core 3,0:**</span><span class="sxs-lookup"><span data-stu-id="1dc23-109">**ASP.NET Core 3.0:**</span></span>

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

<span data-ttu-id="1dc23-110">`Host` usa um contêiner de injeção de dependência (DI) para compilar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1dc23-110">`Host` uses one dependency injection (DI) container to build the app.</span></span> <span data-ttu-id="1dc23-111">`WebHost` usa dois contêineres: um para o host e outro para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1dc23-111">`WebHost` uses two containers: one for the host and one for the app.</span></span> <span data-ttu-id="1dc23-112">Como resultado, o `Startup` Construtor não dá mais suporte à injeção de serviço personalizado.</span><span class="sxs-lookup"><span data-stu-id="1dc23-112">As a result, the `Startup` constructor no longer supports custom service injection.</span></span> <span data-ttu-id="1dc23-113">Somente `IHostEnvironment` , `IWebHostEnvironment` e `IConfiguration` podem ser injetados.</span><span class="sxs-lookup"><span data-stu-id="1dc23-113">Only `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration` can be injected.</span></span> <span data-ttu-id="1dc23-114">Essa alteração impede problemas de DI como a criação duplicada de um serviço singleton.</span><span class="sxs-lookup"><span data-stu-id="1dc23-114">This change prevents DI issues such as the duplicate creation of a singleton service.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1dc23-115">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="1dc23-115">Version introduced</span></span>

<span data-ttu-id="1dc23-116">3,0</span><span class="sxs-lookup"><span data-stu-id="1dc23-116">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1dc23-117">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="1dc23-117">Reason for change</span></span>

<span data-ttu-id="1dc23-118">Essa alteração é uma consequência da replataforma da pilha da Web na biblioteca de hosts genérica.</span><span class="sxs-lookup"><span data-stu-id="1dc23-118">This change is a consequence of replatforming the web stack onto the generic host library.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1dc23-119">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="1dc23-119">Recommended action</span></span>

<span data-ttu-id="1dc23-120">Injetar serviços na `Startup.Configure` assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="1dc23-120">Inject services into the `Startup.Configure` method signature.</span></span> <span data-ttu-id="1dc23-121">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="1dc23-121">For example:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a><span data-ttu-id="1dc23-122">Categoria</span><span class="sxs-lookup"><span data-stu-id="1dc23-122">Category</span></span>

<span data-ttu-id="1dc23-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1dc23-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1dc23-124">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="1dc23-124">Affected APIs</span></span>

<span data-ttu-id="1dc23-125">Nenhum</span><span class="sxs-lookup"><span data-stu-id="1dc23-125">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
