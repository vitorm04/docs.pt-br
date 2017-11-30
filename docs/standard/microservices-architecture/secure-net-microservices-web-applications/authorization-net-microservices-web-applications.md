---
title: "Sobre a autorização em aplicativos da web e microservices do .NET"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Sobre a autorização em aplicativos da web e microservices do .NET"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 51adda4f5bdb28154f17b9a988ee2d887bf1d461
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a><span data-ttu-id="638bd-104">Sobre a autorização em aplicativos da web e microservices do .NET</span><span class="sxs-lookup"><span data-stu-id="638bd-104">About authorization in .NET microservices and web applications</span></span>

<span data-ttu-id="638bd-105">Após a autenticação, as APIs da Web do ASP.NET Core necessário autorizar o acesso.</span><span class="sxs-lookup"><span data-stu-id="638bd-105">After authentication, ASP.NET Core Web APIs need to authorize access.</span></span> <span data-ttu-id="638bd-106">Esse processo permite que um serviço de APIs disponíveis para alguns usuários autenticados, mas não para todos.</span><span class="sxs-lookup"><span data-stu-id="638bd-106">This process allows a service to make APIs available to some authenticated users, but not to all.</span></span> <span data-ttu-id="638bd-107">[Autorização](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) pode ser feita com base em funções de usuários ou com base em política personalizada, que pode incluir inspecionando declarações ou outros fatores.</span><span class="sxs-lookup"><span data-stu-id="638bd-107">[Authorization](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) can be done based on users’ roles or based on custom policy, which might include inspecting claims or other heuristics.</span></span>

<span data-ttu-id="638bd-108">Restringir o acesso a uma rota do MVC do ASP.NET Core é tão fácil quanto a aplicação de um atributo de autorização para o método de ação (ou a classe do controlador se ações de todos os do controlador exigem autorização), como mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="638bd-108">Restricting access to an ASP.NET Core MVC route is as easy as applying an Authorize attribute to the action method (or to the controller’s class if all the controller’s actions require authorization), as shown in following example:</span></span>

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

<span data-ttu-id="638bd-109">Por padrão, adicionando um atributo de autorizar sem parâmetros limitará o acesso aos usuários autenticados do controlador ou ação.</span><span class="sxs-lookup"><span data-stu-id="638bd-109">By default, adding an Authorize attribute without parameters will limit access to authenticated users for that controller or action.</span></span> <span data-ttu-id="638bd-110">Para restringir uma API para estar disponível para apenas usuários específicos, o atributo pode ser expandido para especificar funções necessárias ou políticas que os usuários devem atender.</span><span class="sxs-lookup"><span data-stu-id="638bd-110">To further restrict an API to be available for only specific users, the attribute can be expanded to specify required roles or policies that users must satisfy.</span></span>

## <a name="implementing-role-based-authorization"></a><span data-ttu-id="638bd-111">Implementar a autorização baseada em função</span><span class="sxs-lookup"><span data-stu-id="638bd-111">Implementing role-based authorization</span></span>

<span data-ttu-id="638bd-112">Identidade do ASP.NET Core tem um conceito interno de funções.</span><span class="sxs-lookup"><span data-stu-id="638bd-112">ASP.NET Core Identity has a built-in concept of roles.</span></span> <span data-ttu-id="638bd-113">Além dos usuários, a identidade do ASP.NET Core armazena informações sobre as diferentes funções usadas pelo aplicativo e controla quais usuários são atribuídos a quais funções.</span><span class="sxs-lookup"><span data-stu-id="638bd-113">In addition to users, ASP.NET Core Identity stores information about different roles used by the application and keeps track of which users are assigned to which roles.</span></span> <span data-ttu-id="638bd-114">Essas atribuições podem ser alteradas por meio de programação com o tipo de RoleManager (que atualiza as funções no armazenamento persistente) e o tipo de UserManager (que pode atribuir ou remover usuários das funções).</span><span class="sxs-lookup"><span data-stu-id="638bd-114">These assignments can be changed programmatically with the RoleManager type (which updates roles in persisted storage) and UserManager type (which can assign or unassign users from roles).</span></span>

<span data-ttu-id="638bd-115">Se você estiver autenticando com tokens de portador JWT, o middleware de autenticação do portador de JWT do ASP.NET Core populará funções de usuário com base em declarações de função encontradas no token.</span><span class="sxs-lookup"><span data-stu-id="638bd-115">If you are authenticating with JWT bearer tokens, the ASP.NET Core JWT bearer authentication middleware will populate a user’s roles based on role claims found in the token.</span></span> <span data-ttu-id="638bd-116">Para limitar o acesso a uma ação do MVC ou o controlador para usuários em funções específicas, você pode incluir um parâmetro de funções no cabeçalho de autorização, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="638bd-116">To limit access to an MVC action or controller to users in specific roles, you can include a Roles parameter in the Authorize header, as shown in the following example:</span></span>

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

<span data-ttu-id="638bd-117">Neste exemplo, apenas os usuários em funções de administrador ou PowerUser podem acessar APIs no controlador ControlPanel (como executar a ação SetTime).</span><span class="sxs-lookup"><span data-stu-id="638bd-117">In this example, only users in the Administrator or PowerUser roles can access APIs in the ControlPanel controller (such as executing the SetTime action).</span></span> <span data-ttu-id="638bd-118">A API de desligamento é mais restrito para permitir o acesso somente aos usuários na função de administrador.</span><span class="sxs-lookup"><span data-stu-id="638bd-118">The ShutDown API is further restricted to allow access only to users in the Administrator role.</span></span>

<span data-ttu-id="638bd-119">Para exigir que um usuário estar em várias funções, você usar vários atributos de autorização, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="638bd-119">To require a user be in multiple roles, you use multiple Authorize attributes, as shown in the following example:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

<span data-ttu-id="638bd-120">Neste exemplo, para chamar API1, um usuário deve:</span><span class="sxs-lookup"><span data-stu-id="638bd-120">In this example, to call API1, a user must:</span></span>

-   <span data-ttu-id="638bd-121">Em que o administrador *ou* função PowerUser, *e*</span><span class="sxs-lookup"><span data-stu-id="638bd-121">Be in the Adminstrator *or* PowerUser role, *and*</span></span>

-   <span data-ttu-id="638bd-122">Ter a função RemoteEmployee, *e*</span><span class="sxs-lookup"><span data-stu-id="638bd-122">Be in the RemoteEmployee role, *and*</span></span>

-   <span data-ttu-id="638bd-123">Satisfazer um manipulador personalizado para autorização CustomPolicy.</span><span class="sxs-lookup"><span data-stu-id="638bd-123">Satisfy a custom handler for CustomPolicy authorization.</span></span>

## <a name="implementing-policy-based-authorization"></a><span data-ttu-id="638bd-124">Implementar a autorização baseada em políticas</span><span class="sxs-lookup"><span data-stu-id="638bd-124">Implementing policy-based authorization</span></span>

<span data-ttu-id="638bd-125">Regras de autorização personalizada também podem ser escritas usando [diretivas de autorização](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="638bd-125">Custom authorization rules can also be written using [authorization policies](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span> <span data-ttu-id="638bd-126">Nesta seção, fornecemos uma visão geral.</span><span class="sxs-lookup"><span data-stu-id="638bd-126">In this section we provide an overview.</span></span> <span data-ttu-id="638bd-127">Mais detalhes estão disponíveis no online [Workshop de autorização de ASP.NET](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span><span class="sxs-lookup"><span data-stu-id="638bd-127">More detail is available in the online [ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span></span>

<span data-ttu-id="638bd-128">Diretivas de autorização personalizada são registradas no método Startup.ConfigureServices usando o serviço. Método AddAuthorization.</span><span class="sxs-lookup"><span data-stu-id="638bd-128">Custom authorization policies are registered in the Startup.ConfigureServices method using the service.AddAuthorization method.</span></span> <span data-ttu-id="638bd-129">Esse método usa um delegado que configura um argumento AuthorizationOptions.</span><span class="sxs-lookup"><span data-stu-id="638bd-129">This method takes a delegate that configures an AuthorizationOptions argument.</span></span>

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

<span data-ttu-id="638bd-130">Conforme mostrado no exemplo, políticas podem ser associadas a diferentes tipos de requisitos.</span><span class="sxs-lookup"><span data-stu-id="638bd-130">As shown in the example, policies can be associated with different types of requirements.</span></span> <span data-ttu-id="638bd-131">Depois que as políticas são registradas, eles podem ser aplicados a um controlador ou ação, passando o nome da política como o argumento de política de autorizar atributo (por exemplo, \[Authorize(Policy="EmployeesOnly")\]) podem ter políticas vários requisitos, não apenas um (conforme mostrado nestes exemplos).</span><span class="sxs-lookup"><span data-stu-id="638bd-131">After the policies are registered, they can be applied to an action or controller by passing the policy’s name as the Policy argument of the Authorize attribute (for example, \[Authorize(Policy="EmployeesOnly")\]) Policies can have multiple requirements, not just one (as shown in these examples).</span></span>

<span data-ttu-id="638bd-132">No exemplo anterior, a primeira chamada AddPolicy é apenas uma maneira alternativa de autorização de função.</span><span class="sxs-lookup"><span data-stu-id="638bd-132">In the previous example, the first AddPolicy call is just an alternative way of authorizing by role.</span></span> <span data-ttu-id="638bd-133">Se \[Authorize(Policy="AdministratorsOnly")\] é aplicado a uma API, apenas os usuários na função de administrador poderão acessá-lo.</span><span class="sxs-lookup"><span data-stu-id="638bd-133">If \[Authorize(Policy="AdministratorsOnly")\] is applied to an API, only users in the Administrator role will be able to access it.</span></span>

<span data-ttu-id="638bd-134">A segunda chamada AddPolicy demonstra uma maneira fácil para exigir que um determinado declaração deve estar presente para o usuário.</span><span class="sxs-lookup"><span data-stu-id="638bd-134">The second AddPolicy call demonstrates an easy way to require that a particular claim should be present for the user.</span></span> <span data-ttu-id="638bd-135">O método de RequireClaim também usa valores esperados para a declaração.</span><span class="sxs-lookup"><span data-stu-id="638bd-135">The RequireClaim method also optionally takes expected values for the claim.</span></span> <span data-ttu-id="638bd-136">Se os valores são especificados, o requisito é atendido somente se o usuário tem uma declaração do tipo correto tanto um dos valores especificados.</span><span class="sxs-lookup"><span data-stu-id="638bd-136">If values are specified, the requirement is met only if the user has both a claim of the correct type and one of the specified values.</span></span> <span data-ttu-id="638bd-137">Se você estiver usando o middleware de autenticação do portador JWT, todas as propriedades JWT estarão disponíveis como declarações de usuário.</span><span class="sxs-lookup"><span data-stu-id="638bd-137">If you are using the JWT bearer authentication middleware, all JWT properties will be available as user claims.</span></span>

<span data-ttu-id="638bd-138">A política mais interessante mostrada aqui é o terceiro método AddPolicy, porque ele usa um requisito de autorização personalizada.</span><span class="sxs-lookup"><span data-stu-id="638bd-138">The most interesting policy shown here is in the third AddPolicy method, because it uses a custom authorization requirement.</span></span> <span data-ttu-id="638bd-139">Usando os requisitos de autorização personalizada, você pode ter um grande controle sobre como a autorização é executada.</span><span class="sxs-lookup"><span data-stu-id="638bd-139">By using custom authorization requirements, you can have a great deal of control over how authorization is performed.</span></span> <span data-ttu-id="638bd-140">Para que isso funcione, você deve implementar esses tipos:</span><span class="sxs-lookup"><span data-stu-id="638bd-140">For this to work, you must implement these types:</span></span>

-   <span data-ttu-id="638bd-141">Um tipo de requisitos que deriva de IAuthorizationRequirement e que contém campos para especificar os detalhes da solicitação.</span><span class="sxs-lookup"><span data-stu-id="638bd-141">A Requirements type that derives from IAuthorizationRequirement and that contains fields specifying the details of the requirement.</span></span> <span data-ttu-id="638bd-142">No exemplo, este é um campo de idade para o tipo de MinimumAgeRequirement de exemplo.</span><span class="sxs-lookup"><span data-stu-id="638bd-142">In the example, this is an age field for the sample MinimumAgeRequirement type.</span></span>

-   <span data-ttu-id="638bd-143">Um manipulador que implementa AuthorizationHandler&lt;T&gt;, onde T é o tipo de IAuthorizationRequirement o manipulador pode atender.</span><span class="sxs-lookup"><span data-stu-id="638bd-143">A handler that implements AuthorizationHandler&lt;T&gt;, where T is the type of IAuthorizationRequirement that the handler can satisfy.</span></span> <span data-ttu-id="638bd-144">O manipulador deve implementar o método HandleRequirementAsync, que verifica se um contexto especificado que contém informações sobre o usuário atende o requisito.</span><span class="sxs-lookup"><span data-stu-id="638bd-144">The handler must implement the HandleRequirementAsync method, which checks whether a specified context that contains information about the user satisfies the requirement.</span></span>

<span data-ttu-id="638bd-145">Se o usuário atende ao requisito, uma chamada para o contexto. Êxito será indicar que o usuário está autorizado.</span><span class="sxs-lookup"><span data-stu-id="638bd-145">If the user meets the requirement, a call to context.Succeed will indicate that the user is authorized.</span></span> <span data-ttu-id="638bd-146">Se houver várias maneiras que um usuário pode satisfazer um requisito de autorização, vários manipuladores podem ser criados.</span><span class="sxs-lookup"><span data-stu-id="638bd-146">If there are multiple ways that a user might satisfy an authorization requirement, multiple handlers can be created.</span></span>

<span data-ttu-id="638bd-147">Além de registrar os requisitos de política personalizada com chamadas AddPolicy, você também precisa registrar manipuladores de requisito personalizado por meio de injeção de dependência (services. AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).</span><span class="sxs-lookup"><span data-stu-id="638bd-147">In addition to registering custom policy requirements with AddPolicy calls, you also need to register custom requirement handlers via Dependency Injection (services.AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).</span></span>

<span data-ttu-id="638bd-148">Um exemplo de um requisito de autorização personalizada e o manipulador para verificar a idade do usuário (com base em uma declaração de data de nascimento) está disponível no ASP.NET Core [documentação de autorização](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="638bd-148">An example of a custom authorization requirement and handler for checking a user’s age (based on a DateOfBirth claim) is available in the ASP.NET Core [authorization documentation](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="638bd-149">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="638bd-149">Additional resources</span></span>

-   <span data-ttu-id="638bd-150">**Autenticação do ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span><span class="sxs-lookup"><span data-stu-id="638bd-150">**ASP.NET Core Authentication**
[*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span></span>

-   <span data-ttu-id="638bd-151">**Autorização de ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)</span><span class="sxs-lookup"><span data-stu-id="638bd-151">**ASP.NET Core Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)</span></span>

-   <span data-ttu-id="638bd-152">**Autorização baseada em função**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)</span><span class="sxs-lookup"><span data-stu-id="638bd-152">**Role based Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)</span></span>

-   <span data-ttu-id="638bd-153">**Autorização personalizada com base na política**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)</span><span class="sxs-lookup"><span data-stu-id="638bd-153">**Custom Policy-Based Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="638bd-154">[Anterior] (index.md) [Avançar] (desenvolvedor-aplicativo-segredos-storage.md)</span><span class="sxs-lookup"><span data-stu-id="638bd-154">[Previous] (index.md) [Next] (developer-app-secrets-storage.md)</span></span>
