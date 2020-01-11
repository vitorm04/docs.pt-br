---
ms.openlocfilehash: d1ddba72ce25c5e01025d916d52f785b5a1a9e71
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901777"
---
### <a name="hosting-generic-host-restricts-startup-constructor-injection"></a><span data-ttu-id="00163-101">Hospedagem: host genérico restringe injeção de construtor de inicialização</span><span class="sxs-lookup"><span data-stu-id="00163-101">Hosting: Generic host restricts Startup constructor injection</span></span>

<span data-ttu-id="00163-102">Os únicos tipos aos quais o host genérico dá suporte para injeção de construtor de classe `Startup` são `IHostEnvironment`, `IWebHostEnvironment`e `IConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="00163-102">The only types the generic host supports for `Startup` class constructor injection are `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration`.</span></span> <span data-ttu-id="00163-103">Os aplicativos que usam `WebHost` não são afetados.</span><span class="sxs-lookup"><span data-stu-id="00163-103">Apps using `WebHost` are unaffected.</span></span>

#### <a name="change-description"></a><span data-ttu-id="00163-104">Descrição das alterações</span><span class="sxs-lookup"><span data-stu-id="00163-104">Change description</span></span>

<span data-ttu-id="00163-105">Antes do ASP.NET Core 3,0, a injeção de Construtor poderia ser usada para tipos arbitrários no construtor da classe `Startup`.</span><span class="sxs-lookup"><span data-stu-id="00163-105">Prior to ASP.NET Core 3.0, constructor injection could be used for arbitrary types in the `Startup` class's constructor.</span></span> <span data-ttu-id="00163-106">No ASP.NET Core 3,0, a pilha da Web foi replataforma na biblioteca de hosts genérica.</span><span class="sxs-lookup"><span data-stu-id="00163-106">In ASP.NET Core 3.0, the web stack was replatformed onto the generic host library.</span></span> <span data-ttu-id="00163-107">Você pode ver a alteração no arquivo *Program.cs* dos modelos:</span><span class="sxs-lookup"><span data-stu-id="00163-107">You can see the change in the *Program.cs* file of the templates:</span></span>

<span data-ttu-id="00163-108">**ASP.NET Core 2. x:**</span><span class="sxs-lookup"><span data-stu-id="00163-108">**ASP.NET Core 2.x:**</span></span>

<https://github.com/dotnet/aspnetcore/blob/5cb615fcbe8559e49042e93394008077e30454c0/src/Templating/src/Microsoft.DotNet.Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L20-L22>

<span data-ttu-id="00163-109">**ASP.NET Core 3,0:**</span><span class="sxs-lookup"><span data-stu-id="00163-109">**ASP.NET Core 3.0:**</span></span>

<https://github.com/dotnet/aspnetcore/blob/b1ca2c1155da3920f0df5108b9fedbe82efaa11c/src/ProjectTemplates/Web.ProjectTemplates/content/EmptyWeb-CSharp/Program.cs#L19-L24>

<span data-ttu-id="00163-110">`Host` usa um contêiner de injeção de dependência (DI) para compilar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00163-110">`Host` uses one dependency injection (DI) container to build the app.</span></span> <span data-ttu-id="00163-111">`WebHost` usa dois contêineres: um para o host e outro para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="00163-111">`WebHost` uses two containers: one for the host and one for the app.</span></span> <span data-ttu-id="00163-112">Como resultado, o Construtor `Startup` não oferece mais suporte à injeção de serviço personalizado.</span><span class="sxs-lookup"><span data-stu-id="00163-112">As a result, the `Startup` constructor no longer supports custom service injection.</span></span> <span data-ttu-id="00163-113">Somente `IHostEnvironment`, `IWebHostEnvironment`e `IConfiguration` podem ser injetados.</span><span class="sxs-lookup"><span data-stu-id="00163-113">Only `IHostEnvironment`, `IWebHostEnvironment`, and `IConfiguration` can be injected.</span></span> <span data-ttu-id="00163-114">Essa alteração impede problemas de DI como a criação duplicada de um serviço singleton.</span><span class="sxs-lookup"><span data-stu-id="00163-114">This change prevents DI issues such as the duplicate creation of a singleton service.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="00163-115">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="00163-115">Version introduced</span></span>

<span data-ttu-id="00163-116">3.0</span><span class="sxs-lookup"><span data-stu-id="00163-116">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="00163-117">Motivo da alteração</span><span class="sxs-lookup"><span data-stu-id="00163-117">Reason for change</span></span>

<span data-ttu-id="00163-118">Essa alteração é uma consequência da replataforma da pilha da Web na biblioteca de hosts genérica.</span><span class="sxs-lookup"><span data-stu-id="00163-118">This change is a consequence of replatforming the web stack onto the generic host library.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="00163-119">Ação recomendada</span><span class="sxs-lookup"><span data-stu-id="00163-119">Recommended action</span></span>

<span data-ttu-id="00163-120">Injetar serviços na assinatura do método de `Startup.Configure`.</span><span class="sxs-lookup"><span data-stu-id="00163-120">Inject services into the `Startup.Configure` method signature.</span></span> <span data-ttu-id="00163-121">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="00163-121">For example:</span></span>

```csharp
public void Configure(IApplicationBuilder app, IOptions<MyOptions> options)
```

#### <a name="category"></a><span data-ttu-id="00163-122">Categoria</span><span class="sxs-lookup"><span data-stu-id="00163-122">Category</span></span>

<span data-ttu-id="00163-123">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="00163-123">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="00163-124">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="00163-124">Affected APIs</span></span>

<span data-ttu-id="00163-125">{1&gt;Nenhum&lt;1}</span><span class="sxs-lookup"><span data-stu-id="00163-125">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
