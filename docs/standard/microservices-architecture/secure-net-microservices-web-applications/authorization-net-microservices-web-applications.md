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
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>Sobre a autorização em aplicativos da web e microservices do .NET

Após a autenticação, as APIs da Web do ASP.NET Core necessário autorizar o acesso. Esse processo permite que um serviço de APIs disponíveis para alguns usuários autenticados, mas não para todos. [Autorização](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) pode ser feita com base em funções de usuários ou com base em política personalizada, que pode incluir inspecionando declarações ou outros fatores.

Restringir o acesso a uma rota do MVC do ASP.NET Core é tão fácil quanto a aplicação de um atributo de autorização para o método de ação (ou a classe do controlador se ações de todos os do controlador exigem autorização), como mostrado no exemplo a seguir:

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

Por padrão, adicionando um atributo de autorizar sem parâmetros limitará o acesso aos usuários autenticados do controlador ou ação. Para restringir uma API para estar disponível para apenas usuários específicos, o atributo pode ser expandido para especificar funções necessárias ou políticas que os usuários devem atender.

## <a name="implementing-role-based-authorization"></a>Implementar a autorização baseada em função

Identidade do ASP.NET Core tem um conceito interno de funções. Além dos usuários, a identidade do ASP.NET Core armazena informações sobre as diferentes funções usadas pelo aplicativo e controla quais usuários são atribuídos a quais funções. Essas atribuições podem ser alteradas por meio de programação com o tipo de RoleManager (que atualiza as funções no armazenamento persistente) e o tipo de UserManager (que pode atribuir ou remover usuários das funções).

Se você estiver autenticando com tokens de portador JWT, o middleware de autenticação do portador de JWT do ASP.NET Core populará funções de usuário com base em declarações de função encontradas no token. Para limitar o acesso a uma ação do MVC ou o controlador para usuários em funções específicas, você pode incluir um parâmetro de funções no cabeçalho de autorização, conforme mostrado no exemplo a seguir:

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

Neste exemplo, apenas os usuários em funções de administrador ou PowerUser podem acessar APIs no controlador ControlPanel (como executar a ação SetTime). A API de desligamento é mais restrito para permitir o acesso somente aos usuários na função de administrador.

Para exigir que um usuário estar em várias funções, você usar vários atributos de autorização, conforme mostrado no exemplo a seguir:

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

Neste exemplo, para chamar API1, um usuário deve:

-   Em que o administrador *ou* função PowerUser, *e*

-   Ter a função RemoteEmployee, *e*

-   Satisfazer um manipulador personalizado para autorização CustomPolicy.

## <a name="implementing-policy-based-authorization"></a>Implementar a autorização baseada em políticas

Regras de autorização personalizada também podem ser escritas usando [diretivas de autorização](https://docs.asp.net/en/latest/security/authorization/policies.html). Nesta seção, fornecemos uma visão geral. Mais detalhes estão disponíveis no online [Workshop de autorização de ASP.NET](https://github.com/blowdart/AspNetAuthorizationWorkshop).

Diretivas de autorização personalizada são registradas no método Startup.ConfigureServices usando o serviço. Método AddAuthorization. Esse método usa um delegado que configura um argumento AuthorizationOptions.

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

Conforme mostrado no exemplo, políticas podem ser associadas a diferentes tipos de requisitos. Depois que as políticas são registradas, eles podem ser aplicados a um controlador ou ação, passando o nome da política como o argumento de política de autorizar atributo (por exemplo, \[Authorize(Policy="EmployeesOnly")\]) podem ter políticas vários requisitos, não apenas um (conforme mostrado nestes exemplos).

No exemplo anterior, a primeira chamada AddPolicy é apenas uma maneira alternativa de autorização de função. Se \[Authorize(Policy="AdministratorsOnly")\] é aplicado a uma API, apenas os usuários na função de administrador poderão acessá-lo.

A segunda chamada AddPolicy demonstra uma maneira fácil para exigir que um determinado declaração deve estar presente para o usuário. O método de RequireClaim também usa valores esperados para a declaração. Se os valores são especificados, o requisito é atendido somente se o usuário tem uma declaração do tipo correto tanto um dos valores especificados. Se você estiver usando o middleware de autenticação do portador JWT, todas as propriedades JWT estarão disponíveis como declarações de usuário.

A política mais interessante mostrada aqui é o terceiro método AddPolicy, porque ele usa um requisito de autorização personalizada. Usando os requisitos de autorização personalizada, você pode ter um grande controle sobre como a autorização é executada. Para que isso funcione, você deve implementar esses tipos:

-   Um tipo de requisitos que deriva de IAuthorizationRequirement e que contém campos para especificar os detalhes da solicitação. No exemplo, este é um campo de idade para o tipo de MinimumAgeRequirement de exemplo.

-   Um manipulador que implementa AuthorizationHandler&lt;T&gt;, onde T é o tipo de IAuthorizationRequirement o manipulador pode atender. O manipulador deve implementar o método HandleRequirementAsync, que verifica se um contexto especificado que contém informações sobre o usuário atende o requisito.

Se o usuário atende ao requisito, uma chamada para o contexto. Êxito será indicar que o usuário está autorizado. Se houver várias maneiras que um usuário pode satisfazer um requisito de autorização, vários manipuladores podem ser criados.

Além de registrar os requisitos de política personalizada com chamadas AddPolicy, você também precisa registrar manipuladores de requisito personalizado por meio de injeção de dependência (services. AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).

Um exemplo de um requisito de autorização personalizada e o manipulador para verificar a idade do usuário (com base em uma declaração de data de nascimento) está disponível no ASP.NET Core [documentação de autorização](https://docs.asp.net/en/latest/security/authorization/policies.html).

## <a name="additional-resources"></a>Recursos adicionais

-   **Autenticação do ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)

-   **Autorização de ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)

-   **Autorização baseada em função**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)

-   **Autorização personalizada com base na política**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)




>[!div class="step-by-step"]
[Anterior] (index.md) [Avançar] (desenvolvedor-aplicativo-segredos-storage.md)
