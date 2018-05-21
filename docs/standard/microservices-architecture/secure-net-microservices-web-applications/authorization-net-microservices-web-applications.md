---
title: Sobre a autorização em aplicativos Web e em microsserviços .NET
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Sobre a autorização em aplicativos Web e em microsserviços .NET
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 2ea56f5a28d115fc5d91a98604b82565c8bf5c78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a><span data-ttu-id="455bb-103">Sobre a autorização em aplicativos Web e em microsserviços .NET</span><span class="sxs-lookup"><span data-stu-id="455bb-103">About authorization in .NET microservices and web applications</span></span>

<span data-ttu-id="455bb-104">Após a autenticação, as APIs Web do ASP.NET Core precisam autorizar o acesso.</span><span class="sxs-lookup"><span data-stu-id="455bb-104">After authentication, ASP.NET Core Web APIs need to authorize access.</span></span> <span data-ttu-id="455bb-105">Esse processo permite que um serviço disponibilize APIs para alguns usuários autenticados, mas não para todos.</span><span class="sxs-lookup"><span data-stu-id="455bb-105">This process allows a service to make APIs available to some authenticated users, but not to all.</span></span> <span data-ttu-id="455bb-106">A [autorização](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) pode ser dada com base em funções de usuários ou em política personalizada, que pode incluir inspeção de declarações ou outros fatores.</span><span class="sxs-lookup"><span data-stu-id="455bb-106">[Authorization](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) can be done based on users’ roles or based on custom policy, which might include inspecting claims or other heuristics.</span></span>

<span data-ttu-id="455bb-107">Restringir o acesso a uma rota do ASP.NET Core MVC é tão fácil quanto a aplicação de um atributo Authorize ao método de ação (ou à classe do controlador todas as ações dele exigirem autorização), como mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="455bb-107">Restricting access to an ASP.NET Core MVC route is as easy as applying an Authorize attribute to the action method (or to the controller’s class if all the controller’s actions require authorization), as shown in following example:</span></span>

```csharp
public class AccountController : Controller
{
    public ActionResult Login()
    {
    }

    [Authorize]
    public ActionResult Logout()
    {
    }
}
```

<span data-ttu-id="455bb-108">Por padrão, adicionar um atributo Authorize sem parâmetros limitará o acesso aos usuários autenticados do controlador ou ação.</span><span class="sxs-lookup"><span data-stu-id="455bb-108">By default, adding an Authorize attribute without parameters will limit access to authenticated users for that controller or action.</span></span> <span data-ttu-id="455bb-109">Para restringir a disponibilidade de uma API apenas para usuários específicos, o atributo pode ser expandido para especificar funções necessárias ou políticas que os usuários devem atender.</span><span class="sxs-lookup"><span data-stu-id="455bb-109">To further restrict an API to be available for only specific users, the attribute can be expanded to specify required roles or policies that users must satisfy.</span></span>

## <a name="implementing-role-based-authorization"></a><span data-ttu-id="455bb-110">Implementar a autorização baseada em função</span><span class="sxs-lookup"><span data-stu-id="455bb-110">Implementing role-based authorization</span></span>

<span data-ttu-id="455bb-111">A identidade do ASP.NET Core tem um conceito interno de funções.</span><span class="sxs-lookup"><span data-stu-id="455bb-111">ASP.NET Core Identity has a built-in concept of roles.</span></span> <span data-ttu-id="455bb-112">Além dos usuários, a identidade do ASP.NET Core armazena informações sobre as diferentes funções usadas pelo aplicativo e controla quais usuários são atribuídos a quais funções.</span><span class="sxs-lookup"><span data-stu-id="455bb-112">In addition to users, ASP.NET Core Identity stores information about different roles used by the application and keeps track of which users are assigned to which roles.</span></span> <span data-ttu-id="455bb-113">Essas atribuições podem ser alteradas programaticamente com o tipo RoleManager (que atualiza as funções no armazenamento persistente) e o tipo UserManager (que pode atribuir ou cancelar a atribuição às funções dos usuários).</span><span class="sxs-lookup"><span data-stu-id="455bb-113">These assignments can be changed programmatically with the RoleManager type (which updates roles in persisted storage) and UserManager type (which can assign or unassign users from roles).</span></span>

<span data-ttu-id="455bb-114">Se você estiver autenticando com tokens de portador JWT, o middleware de autenticação do portador de JWT do ASP.NET Core preencherá funções de usuário com base em declarações de função encontradas no token.</span><span class="sxs-lookup"><span data-stu-id="455bb-114">If you are authenticating with JWT bearer tokens, the ASP.NET Core JWT bearer authentication middleware will populate a user’s roles based on role claims found in the token.</span></span> <span data-ttu-id="455bb-115">Para limitar o acesso a uma ação ou controlador MVC para usuários em funções específicas, você pode incluir um parâmetro Roles no cabeçalho Authorize, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="455bb-115">To limit access to an MVC action or controller to users in specific roles, you can include a Roles parameter in the Authorize header, as shown in the following example:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
public class ControlPanelController : Controller
{
    public ActionResult SetTime()
    {
    }

    [Authorize(Roles = "Administrator")]
    public ActionResult ShutDown()
    {
    }
}
```

<span data-ttu-id="455bb-116">Neste exemplo, apenas os usuários nas funções Administrator ou PowerUser podem acessar APIs no controlador ControlPanel (como executar a ação SetTime).</span><span class="sxs-lookup"><span data-stu-id="455bb-116">In this example, only users in the Administrator or PowerUser roles can access APIs in the ControlPanel controller (such as executing the SetTime action).</span></span> <span data-ttu-id="455bb-117">A API ShutDown é mais restrita para permitir o acesso somente aos usuários na função Administrator.</span><span class="sxs-lookup"><span data-stu-id="455bb-117">The ShutDown API is further restricted to allow access only to users in the Administrator role.</span></span>

<span data-ttu-id="455bb-118">Para exigir que um usuário esteja em várias funções, use vários atributos Authorize, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="455bb-118">To require a user be in multiple roles, you use multiple Authorize attributes, as shown in the following example:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

<span data-ttu-id="455bb-119">Neste exemplo, para chamar API1, um usuário deve:</span><span class="sxs-lookup"><span data-stu-id="455bb-119">In this example, to call API1, a user must:</span></span>

-   <span data-ttu-id="455bb-120">estar na função Adminstrator *ou* PowerUser *;*</span><span class="sxs-lookup"><span data-stu-id="455bb-120">Be in the Adminstrator *or* PowerUser role, *and*</span></span>

-   <span data-ttu-id="455bb-121">estar na função RemoteEmployee *e*</span><span class="sxs-lookup"><span data-stu-id="455bb-121">Be in the RemoteEmployee role, *and*</span></span>

-   <span data-ttu-id="455bb-122">satisfazer a um manipulador personalizado da autorização CustomPolicy.</span><span class="sxs-lookup"><span data-stu-id="455bb-122">Satisfy a custom handler for CustomPolicy authorization.</span></span>

## <a name="implementing-policy-based-authorization"></a><span data-ttu-id="455bb-123">Implementar a autorização baseada em política</span><span class="sxs-lookup"><span data-stu-id="455bb-123">Implementing policy-based authorization</span></span>

<span data-ttu-id="455bb-124">Regras de autorização personalizadas também podem ser gravadas usando [políticas de autorização](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="455bb-124">Custom authorization rules can also be written using [authorization policies](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span> <span data-ttu-id="455bb-125">Nesta seção, fornecemos uma visão geral.</span><span class="sxs-lookup"><span data-stu-id="455bb-125">In this section we provide an overview.</span></span> <span data-ttu-id="455bb-126">Mais detalhes estão disponíveis online em [Workshop de Autorização no ASP.NET](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span><span class="sxs-lookup"><span data-stu-id="455bb-126">More detail is available in the online [ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span></span>

<span data-ttu-id="455bb-127">Políticas de autorização personalizadas são registradas no método Startup.ConfigureServices usando o método service.AddAuthorization.</span><span class="sxs-lookup"><span data-stu-id="455bb-127">Custom authorization policies are registered in the Startup.ConfigureServices method using the service.AddAuthorization method.</span></span> <span data-ttu-id="455bb-128">Esse método usa um delegado que configura um argumento AuthorizationOptions.</span><span class="sxs-lookup"><span data-stu-id="455bb-128">This method takes a delegate that configures an AuthorizationOptions argument.</span></span>

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("AdministratorsOnly", policy =>
        policy.RequireRole("Administrator"));
    options.AddPolicy("EmployeesOnly", policy =>
        policy.RequireClaim("EmployeeNumber"));
    options.AddPolicy("Over21", policy =>
        policy.Requirements.Add(new MinimumAgeRequirement(21)));
});
```

<span data-ttu-id="455bb-129">Conforme mostrado no exemplo, políticas podem ser associadas a diferentes tipos de requisitos.</span><span class="sxs-lookup"><span data-stu-id="455bb-129">As shown in the example, policies can be associated with different types of requirements.</span></span> <span data-ttu-id="455bb-130">Depois que as políticas são registradas, elas podem ser aplicadas a um controlador ou ação, passando o nome da política como o argumento Policy do atributo Authorize (por exemplo, \[Authorize(Policy="EmployeesOnly")\]). As políticas podem ter vários requisitos, e não apenas um (conforme mostrado nestes exemplos).</span><span class="sxs-lookup"><span data-stu-id="455bb-130">After the policies are registered, they can be applied to an action or controller by passing the policy’s name as the Policy argument of the Authorize attribute (for example, \[Authorize(Policy="EmployeesOnly")\]) Policies can have multiple requirements, not just one (as shown in these examples).</span></span>

<span data-ttu-id="455bb-131">No exemplo anterior, a primeira chamada AddPolicy é apenas uma maneira alternativa de autorizar pela função.</span><span class="sxs-lookup"><span data-stu-id="455bb-131">In the previous example, the first AddPolicy call is just an alternative way of authorizing by role.</span></span> <span data-ttu-id="455bb-132">Se \[Authorize(Policy="AdministratorsOnly")\] for aplicado a uma API, apenas os usuários na função Administrator poderão acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="455bb-132">If \[Authorize(Policy="AdministratorsOnly")\] is applied to an API, only users in the Administrator role will be able to access it.</span></span>

<span data-ttu-id="455bb-133">A segunda chamada AddPolicy demonstra uma maneira fácil de exigir que uma determinada declaração esteja presente para o usuário.</span><span class="sxs-lookup"><span data-stu-id="455bb-133">The second AddPolicy call demonstrates an easy way to require that a particular claim should be present for the user.</span></span> <span data-ttu-id="455bb-134">O método RequireClaim também usa valores esperados para a declaração opcionalmente.</span><span class="sxs-lookup"><span data-stu-id="455bb-134">The RequireClaim method also optionally takes expected values for the claim.</span></span> <span data-ttu-id="455bb-135">Se os valores são especificados, o requisito é atendido somente se o usuário tem uma declaração do tipo correto e um dos valores especificados.</span><span class="sxs-lookup"><span data-stu-id="455bb-135">If values are specified, the requirement is met only if the user has both a claim of the correct type and one of the specified values.</span></span> <span data-ttu-id="455bb-136">Se você estiver usando o middleware de autenticação do portador de JWT, todas as propriedades do JWT estarão disponíveis como declarações de usuário.</span><span class="sxs-lookup"><span data-stu-id="455bb-136">If you are using the JWT bearer authentication middleware, all JWT properties will be available as user claims.</span></span>

<span data-ttu-id="455bb-137">A política mais interessante mostrada aqui é o terceiro método AddPolicy, porque ele usa um requisito de autorização personalizado.</span><span class="sxs-lookup"><span data-stu-id="455bb-137">The most interesting policy shown here is in the third AddPolicy method, because it uses a custom authorization requirement.</span></span> <span data-ttu-id="455bb-138">Usando os requisitos de autorização personalizados, você pode ter grande controle sobre como a autorização é realizada.</span><span class="sxs-lookup"><span data-stu-id="455bb-138">By using custom authorization requirements, you can have a great deal of control over how authorization is performed.</span></span> <span data-ttu-id="455bb-139">Para que isso funcione, você deve implementar esses tipos:</span><span class="sxs-lookup"><span data-stu-id="455bb-139">For this to work, you must implement these types:</span></span>

-   <span data-ttu-id="455bb-140">Um tipo Requirements que deriva de IAuthorizationRequirement e contém campos para especificar os detalhes do requisito.</span><span class="sxs-lookup"><span data-stu-id="455bb-140">A Requirements type that derives from IAuthorizationRequirement and that contains fields specifying the details of the requirement.</span></span> <span data-ttu-id="455bb-141">No exemplo, esse é um campo de idade para o tipo MinimumAgeRequirement de exemplo.</span><span class="sxs-lookup"><span data-stu-id="455bb-141">In the example, this is an age field for the sample MinimumAgeRequirement type.</span></span>

-   <span data-ttu-id="455bb-142">Um manipulador que implementa AuthorizationHandler&lt;T&gt;, em que T é o tipo de IAuthorizationRequirement que o manipulador pode atender.</span><span class="sxs-lookup"><span data-stu-id="455bb-142">A handler that implements AuthorizationHandler&lt;T&gt;, where T is the type of IAuthorizationRequirement that the handler can satisfy.</span></span> <span data-ttu-id="455bb-143">O manipulador deve implementar o método HandleRequirementAsync, que verifica se um contexto especificado que contém informações sobre o usuário atende ao requisito.</span><span class="sxs-lookup"><span data-stu-id="455bb-143">The handler must implement the HandleRequirementAsync method, which checks whether a specified context that contains information about the user satisfies the requirement.</span></span>

<span data-ttu-id="455bb-144">Se o usuário atender ao requisito, uma chamada para context.Succeed indicará que o usuário está autorizado.</span><span class="sxs-lookup"><span data-stu-id="455bb-144">If the user meets the requirement, a call to context.Succeed will indicate that the user is authorized.</span></span> <span data-ttu-id="455bb-145">Se houver várias maneiras pelas quais um usuário pode satisfazer a um requisito de autorização, vários manipuladores poderão ser criados.</span><span class="sxs-lookup"><span data-stu-id="455bb-145">If there are multiple ways that a user might satisfy an authorization requirement, multiple handlers can be created.</span></span>

<span data-ttu-id="455bb-146">Além de registrar requisitos de política personalizados com chamadas AddPolicy, também é necessário registrar manipuladores de requisito personalizados por meio da Injeção de Dependência (services.AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).</span><span class="sxs-lookup"><span data-stu-id="455bb-146">In addition to registering custom policy requirements with AddPolicy calls, you also need to register custom requirement handlers via Dependency Injection (services.AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).</span></span>

<span data-ttu-id="455bb-147">Um exemplo de requisito de autorização personalizado e manipulador para verificar a idade do usuário (com base em uma declaração DateOfBirth) está disponível na [documentação de autorização](https://docs.asp.net/en/latest/security/authorization/policies.html) do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="455bb-147">An example of a custom authorization requirement and handler for checking a user’s age (based on a DateOfBirth claim) is available in the ASP.NET Core [authorization documentation](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="455bb-148">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="455bb-148">Additional resources</span></span>

-   <span data-ttu-id="455bb-149">**Autenticação do ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span><span class="sxs-lookup"><span data-stu-id="455bb-149">**ASP.NET Core Authentication**
[*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span></span>

-   <span data-ttu-id="455bb-150">**Autorização do ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)</span><span class="sxs-lookup"><span data-stu-id="455bb-150">**ASP.NET Core Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)</span></span>

-   <span data-ttu-id="455bb-151">**Autorização baseada em função**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)</span><span class="sxs-lookup"><span data-stu-id="455bb-151">**Role based Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)</span></span>

-   <span data-ttu-id="455bb-152">**Autorização baseada em política personalizada**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)</span><span class="sxs-lookup"><span data-stu-id="455bb-152">**Custom Policy-Based Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="455bb-153">[Anterior] (index.md) [Próximo] (developer-app-secrets-storage.md)</span><span class="sxs-lookup"><span data-stu-id="455bb-153">[Previous] (index.md) [Next] (developer-app-secrets-storage.md)</span></span>
