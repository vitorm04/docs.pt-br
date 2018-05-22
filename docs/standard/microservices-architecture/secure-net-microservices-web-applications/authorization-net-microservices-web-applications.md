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
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>Sobre a autorização em aplicativos Web e em microsserviços .NET

Após a autenticação, as APIs Web do ASP.NET Core precisam autorizar o acesso. Esse processo permite que um serviço disponibilize APIs para alguns usuários autenticados, mas não para todos. A [autorização](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) pode ser dada com base em funções de usuários ou em política personalizada, que pode incluir inspeção de declarações ou outros fatores.

Restringir o acesso a uma rota do ASP.NET Core MVC é tão fácil quanto a aplicação de um atributo Authorize ao método de ação (ou à classe do controlador todas as ações dele exigirem autorização), como mostrado no exemplo a seguir:

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

Por padrão, adicionar um atributo Authorize sem parâmetros limitará o acesso aos usuários autenticados do controlador ou ação. Para restringir a disponibilidade de uma API apenas para usuários específicos, o atributo pode ser expandido para especificar funções necessárias ou políticas que os usuários devem atender.

## <a name="implementing-role-based-authorization"></a>Implementar a autorização baseada em função

A identidade do ASP.NET Core tem um conceito interno de funções. Além dos usuários, a identidade do ASP.NET Core armazena informações sobre as diferentes funções usadas pelo aplicativo e controla quais usuários são atribuídos a quais funções. Essas atribuições podem ser alteradas programaticamente com o tipo RoleManager (que atualiza as funções no armazenamento persistente) e o tipo UserManager (que pode atribuir ou cancelar a atribuição às funções dos usuários).

Se você estiver autenticando com tokens de portador JWT, o middleware de autenticação do portador de JWT do ASP.NET Core preencherá funções de usuário com base em declarações de função encontradas no token. Para limitar o acesso a uma ação ou controlador MVC para usuários em funções específicas, você pode incluir um parâmetro Roles no cabeçalho Authorize, conforme mostrado no exemplo a seguir:

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

Neste exemplo, apenas os usuários nas funções Administrator ou PowerUser podem acessar APIs no controlador ControlPanel (como executar a ação SetTime). A API ShutDown é mais restrita para permitir o acesso somente aos usuários na função Administrator.

Para exigir que um usuário esteja em várias funções, use vários atributos Authorize, conforme mostrado no exemplo a seguir:

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

Neste exemplo, para chamar API1, um usuário deve:

-   estar na função Adminstrator *ou* PowerUser *;*

-   estar na função RemoteEmployee *e*

-   satisfazer a um manipulador personalizado da autorização CustomPolicy.

## <a name="implementing-policy-based-authorization"></a>Implementar a autorização baseada em política

Regras de autorização personalizadas também podem ser gravadas usando [políticas de autorização](https://docs.asp.net/en/latest/security/authorization/policies.html). Nesta seção, fornecemos uma visão geral. Mais detalhes estão disponíveis online em [Workshop de Autorização no ASP.NET](https://github.com/blowdart/AspNetAuthorizationWorkshop).

Políticas de autorização personalizadas são registradas no método Startup.ConfigureServices usando o método service.AddAuthorization. Esse método usa um delegado que configura um argumento AuthorizationOptions.

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

Conforme mostrado no exemplo, políticas podem ser associadas a diferentes tipos de requisitos. Depois que as políticas são registradas, elas podem ser aplicadas a um controlador ou ação, passando o nome da política como o argumento Policy do atributo Authorize (por exemplo, \[Authorize(Policy="EmployeesOnly")\]). As políticas podem ter vários requisitos, e não apenas um (conforme mostrado nestes exemplos).

No exemplo anterior, a primeira chamada AddPolicy é apenas uma maneira alternativa de autorizar pela função. Se \[Authorize(Policy="AdministratorsOnly")\] for aplicado a uma API, apenas os usuários na função Administrator poderão acessá-lo.

A segunda chamada AddPolicy demonstra uma maneira fácil de exigir que uma determinada declaração esteja presente para o usuário. O método RequireClaim também usa valores esperados para a declaração opcionalmente. Se os valores são especificados, o requisito é atendido somente se o usuário tem uma declaração do tipo correto e um dos valores especificados. Se você estiver usando o middleware de autenticação do portador de JWT, todas as propriedades do JWT estarão disponíveis como declarações de usuário.

A política mais interessante mostrada aqui é o terceiro método AddPolicy, porque ele usa um requisito de autorização personalizado. Usando os requisitos de autorização personalizados, você pode ter grande controle sobre como a autorização é realizada. Para que isso funcione, você deve implementar esses tipos:

-   Um tipo Requirements que deriva de IAuthorizationRequirement e contém campos para especificar os detalhes do requisito. No exemplo, esse é um campo de idade para o tipo MinimumAgeRequirement de exemplo.

-   Um manipulador que implementa AuthorizationHandler&lt;T&gt;, em que T é o tipo de IAuthorizationRequirement que o manipulador pode atender. O manipulador deve implementar o método HandleRequirementAsync, que verifica se um contexto especificado que contém informações sobre o usuário atende ao requisito.

Se o usuário atender ao requisito, uma chamada para context.Succeed indicará que o usuário está autorizado. Se houver várias maneiras pelas quais um usuário pode satisfazer a um requisito de autorização, vários manipuladores poderão ser criados.

Além de registrar requisitos de política personalizados com chamadas AddPolicy, também é necessário registrar manipuladores de requisito personalizados por meio da Injeção de Dependência (services.AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).

Um exemplo de requisito de autorização personalizado e manipulador para verificar a idade do usuário (com base em uma declaração DateOfBirth) está disponível na [documentação de autorização](https://docs.asp.net/en/latest/security/authorization/policies.html) do ASP.NET Core.

## <a name="additional-resources"></a>Recursos adicionais

-   **Autenticação do ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)

-   **Autorização do ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)

-   **Autorização baseada em função**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)

-   **Autorização baseada em política personalizada**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)




>[!div class="step-by-step"]
[Anterior] (index.md) [Próximo] (developer-app-secrets-storage.md)
