---
title: Desenvolvendo aplicativos ASP.NET Core MVC
description: Projetar aplicativos Web modernos com o ASP.NET Core e o Azure | desenvolvendo aplicativos ASP.NET Core MVC
author: ardalis
ms.author: wiwagn
ms.date: 06/28/2018
ms.openlocfilehash: de6b2e6650d173d325b2a717f5ee47506c307de7
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/13/2018
ms.locfileid: "49308585"
---
# <a name="develop-aspnet-core-mvc-apps"></a><span data-ttu-id="95c99-103">Desenvolver aplicativos ASP.NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="95c99-103">Develop ASP.NET Core MVC apps</span></span>

> <span data-ttu-id="95c99-104">"Não é importante acertar na primeira vez.</span><span class="sxs-lookup"><span data-stu-id="95c99-104">"It's not important to get it right the first time.</span></span> <span data-ttu-id="95c99-105">É extremamente importante acertar na última vez."</span><span class="sxs-lookup"><span data-stu-id="95c99-105">It's vitally important to get it right the last time."</span></span>  
> <span data-ttu-id="95c99-106">_- Andrew Hunt e David Thomas_</span><span class="sxs-lookup"><span data-stu-id="95c99-106">_- Andrew Hunt and David Thomas_</span></span>

<span data-ttu-id="95c99-107">O ASP.NET Core é uma estrutura multiplataforma de software livre para a criação de aplicativos Web modernos otimizados para a nuvem.</span><span class="sxs-lookup"><span data-stu-id="95c99-107">ASP.NET Core is a cross-platform, open-source framework for building modern cloud-optimized web applications.</span></span> <span data-ttu-id="95c99-108">Os aplicativos ASP.NET Core são leves e modulares, com suporte interno para a injeção de dependência, o que aumenta a capacidade de teste e a facilidade de manutenção.</span><span class="sxs-lookup"><span data-stu-id="95c99-108">ASP.NET Core apps are lightweight and modular, with built-in support for dependency injection, enabling greater testability and maintainability.</span></span> <span data-ttu-id="95c99-109">Combinado com o MVC, que é compatível com a criação de APIs Web modernas, além de aplicativos baseados em exibição, o ASP.NET Core é uma estrutura avançada para a criação de aplicativos Web empresariais.</span><span class="sxs-lookup"><span data-stu-id="95c99-109">Combined with MVC, which supports building modern web APIs in addition to view-based apps, ASP.NET Core is a powerful framework with which to build enterprise web applications.</span></span>

## <a name="mapping-requests-to-responses"></a><span data-ttu-id="95c99-110">Mapeando solicitações para respostas</span><span class="sxs-lookup"><span data-stu-id="95c99-110">Mapping requests to responses</span></span>

<span data-ttu-id="95c99-111">Em sua essência, os aplicativos ASP.NET Core mapeiam as solicitações de entrada para as respostas de saída.</span><span class="sxs-lookup"><span data-stu-id="95c99-111">At its heart, ASP.NET Core apps map incoming requests to outgoing responses.</span></span> <span data-ttu-id="95c99-112">Em um nível inferior, isso é feito com um middleware, e aplicativos ASP.NET Core e microsserviços simples podem ser compostos apenas por um middleware personalizado.</span><span class="sxs-lookup"><span data-stu-id="95c99-112">At a low level, this is done with middleware, and simple ASP.NET Core apps and microservices may be comprised solely of custom middleware.</span></span> <span data-ttu-id="95c99-113">Ao usar o ASP.NET Core MVC, você pode trabalhar em um nível um pouco superior, pensando em termos de _rotas_, _controladores_ e _ações_.</span><span class="sxs-lookup"><span data-stu-id="95c99-113">When using ASP.NET Core MVC, you can work at a somewhat higher level, thinking in terms of _routes_, _controllers_, and _actions_.</span></span> <span data-ttu-id="95c99-114">Cada solicitação de entrada é comparada com a tabela de roteamento do aplicativo e se uma rota correspondente é encontrada, o método de ação associado (pertencente a um controlador) é chamado para manipular a solicitação.</span><span class="sxs-lookup"><span data-stu-id="95c99-114">Each incoming request is compared with the application's routing table, and if a matching route is found, the associated action method (belonging to a controller) is called to handle the request.</span></span> <span data-ttu-id="95c99-115">Se nenhuma rota correspondente é encontrada, um manipulador de erro (nesse caso, retornando um resultado NotFound) é chamado.</span><span class="sxs-lookup"><span data-stu-id="95c99-115">If no matching route is found, an error handler (in this case, returning a NotFound result) is called.</span></span>

<span data-ttu-id="95c99-116">Os aplicativos ASP.NET Core MVC podem usar rotas convencionais, rotas de atributo ou ambas.</span><span class="sxs-lookup"><span data-stu-id="95c99-116">ASP.NET Core MVC apps can use conventional routes, attribute routes, or both.</span></span> <span data-ttu-id="95c99-117">As rotas convencionais são definidas no código, especificando as _convenções_ de roteamento com uma sintaxe parecida com o exemplo abaixo:</span><span class="sxs-lookup"><span data-stu-id="95c99-117">Conventional routes are defined in code, specifying routing _conventions_ using syntax like in the example below:</span></span>

```csharp
app.UseMvc(routes =>;
{
    routes.MapRoute("default","{controller=Home}/{action=Index}/{id?}");
});
```

<span data-ttu-id="95c99-118">Nesse exemplo, uma rota chamada "default" foi adicionada à tabela de roteamento.</span><span class="sxs-lookup"><span data-stu-id="95c99-118">In this example, a route named "default" has been added to the routing table.</span></span> <span data-ttu-id="95c99-119">Ela define um modelo de rota com espaços reservados para o _controlador_, a _ação_ e a _ID_. Os espaços reservados do controlador e da ação têm um padrão especificado ("Home" e "Index", respectivamente) e o espaço reservado da ID é opcional (em virtude de um "?" aplicado a ele).</span><span class="sxs-lookup"><span data-stu-id="95c99-119">It defines a route template with placeholders for _controller_, _action_, and _id_. The controller and action placeholders have default specified ("Home" and "Index", respectively), and the id placeholder is optional (by virtue of a "?" applied to it).</span></span> <span data-ttu-id="95c99-120">A convenção definida aqui indica que a primeira parte de uma solicitação deve corresponder ao nome do controlador, a segunda parte à ação, e, em seguida, se for necessário, uma terceira parte representará um parâmetro de ID.</span><span class="sxs-lookup"><span data-stu-id="95c99-120">The convention defined here states that the first part of a request should correspond to the name of the controller, the second part to the action, and then if necessary a third part will represent an id parameter.</span></span> <span data-ttu-id="95c99-121">As rotas convencionais costumam ser definidas em um lugar para o aplicativo, como no método Configure na classe Startup.</span><span class="sxs-lookup"><span data-stu-id="95c99-121">Conventional routes are typically defined in one place for the application, such as in the Configure method in the Startup class.</span></span>

<span data-ttu-id="95c99-122">As rotas de atributo são aplicadas aos controladores e às ações diretamente, em vez de serem especificadas globalmente.</span><span class="sxs-lookup"><span data-stu-id="95c99-122">Attribute routes are applied to controllers and actions directly, rather than specified globally.</span></span> <span data-ttu-id="95c99-123">Isso oferece a vantagem de torná-las muito mais detectáveis quando você estiver procurando um método específico, mas significa que as informações de roteamento não são mantidas em um único lugar no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="95c99-123">This has the advantage of making them much more discoverable when you're looking at a particular method, but does mean that routing information is not kept in one place in the application.</span></span> <span data-ttu-id="95c99-124">Com as rotas de atributo, você pode especificar com facilidade várias rotas para determinada ação, além de combinar rotas entre controladores e ações.</span><span class="sxs-lookup"><span data-stu-id="95c99-124">With attribute routes, you can easily specify multiple routes for a given action, as well as combine routes between controllers and actions.</span></span> <span data-ttu-id="95c99-125">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="95c99-125">For example:</span></span>

```csharp
[Route("Home")]
public class HomeController : Controller
{
    [Route("")] // Combines to define the route template "Home"
    [Route("Index")] // Combines to define route template "Home/Index"
    [Route("/")] // Does not combine, defines the route template ""
    public IActionResult Index() {}
}
```

<span data-ttu-id="95c99-126">As rotas podem ser especificadas no [HttpGet] e em atributos semelhantes, evitando a necessidade de adicionar atributos [Route] separados.</span><span class="sxs-lookup"><span data-stu-id="95c99-126">Routes can be specified on [HttpGet] and similar attributes, avoiding the need to add separate [Route] attributes.</span></span> <span data-ttu-id="95c99-127">As rotas de atributo também podem usar tokens para reduzir a necessidade de repetir os nomes do controlador ou da ação, conforme mostrado abaixo:</span><span class="sxs-lookup"><span data-stu-id="95c99-127">Attribute routes can also use tokens to reduce the need to repeat controller or action names, as shown below:</span></span>

```csharp
[Route("[controller\]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index() {}
}
```

<span data-ttu-id="95c99-128">Depois que for feita a correspondência de uma solicitação específica a uma rota, mas antes da chamada do método de ação, o ASP.NET Core MVC executará o [model binding](/aspnet/core/mvc/models/model-binding) e a [validação de modelos](/aspnet/core/mvc/models/validation) na solicitação.</span><span class="sxs-lookup"><span data-stu-id="95c99-128">Once a given request has been matched to a route, but before the action method is called, ASP.NET Core MVC will perform [model binding](/aspnet/core/mvc/models/model-binding) and [model validation](/aspnet/core/mvc/models/validation) on the request.</span></span> <span data-ttu-id="95c99-129">O model binding é responsável por converter os dados HTTP de entrada nos tipos .NET especificados como parâmetros do método de ação a ser chamado.</span><span class="sxs-lookup"><span data-stu-id="95c99-129">Model binding is responsible for converting incoming HTTP data into the .NET types specified as parameters of the action method to be called.</span></span> <span data-ttu-id="95c99-130">Por exemplo, se o método de ação esperar um parâmetro de ID int, o model binding tentará fornecer esse parâmetro com base em um valor fornecido como parte da solicitação.</span><span class="sxs-lookup"><span data-stu-id="95c99-130">For example, if the action method expects an int id parameter, model binding will attempt to provide this parameter from a value provided as part of the request.</span></span> <span data-ttu-id="95c99-131">Para fazer isso, o model binding procurará valores em um formulário publicado, valores na própria rota e valores de cadeia de caracteres de consulta.</span><span class="sxs-lookup"><span data-stu-id="95c99-131">To do so, model binding looks for values in a posted form, values in the route itself, and query string values.</span></span> <span data-ttu-id="95c99-132">Supondo que um valor de ID seja encontrado, ele será convertido em um inteiro antes de ser passado para o método de ação.</span><span class="sxs-lookup"><span data-stu-id="95c99-132">Assuming an id value is found, it will be converted to an integer before being passed into the action method.</span></span>

<span data-ttu-id="95c99-133">Após a associação do modelo, mas antes da chamada do método de ação, ocorre a validação de modelos.</span><span class="sxs-lookup"><span data-stu-id="95c99-133">After binding the model but before calling the action method, model validation occurs.</span></span> <span data-ttu-id="95c99-134">A validação de modelos usa atributos opcionais no tipo de modelo e pode ajudar a garantir que o objeto de modelo fornecido está em conformidade com determinados requisitos de dados.</span><span class="sxs-lookup"><span data-stu-id="95c99-134">Model validation uses optional attributes on the model type, and can help ensure that the provided model object conforms to certain data requirements.</span></span> <span data-ttu-id="95c99-135">Alguns valores podem ser especificados, conforme necessário, ou limitados a determinado tamanho ou intervalo numérico, etc. Se os atributos de validação forem especificados, mas o modelo não estiver em conformidade com seus requisitos, a propriedade ModelState.IsValid será falsa e o conjunto de regras de validação com falha estará disponível para ser enviado ao cliente que faz a solicitação.</span><span class="sxs-lookup"><span data-stu-id="95c99-135">Certain values may be specified as required, or limited to a certain length or numeric range, etc. If validation attributes are specified but the model does not conform to their requirements, the property ModelState.IsValid will be false, and the set of failing validation rules will be available to send to the client making the request.</span></span>

<span data-ttu-id="95c99-136">Se você estiver usando a validação de modelos, sempre verifique se o modelo é válido antes de executar comandos de alteração do estado, para garantir que o aplicativo não seja corrompido por dados inválidos.</span><span class="sxs-lookup"><span data-stu-id="95c99-136">If you're using model validation, you should be sure to always check that the model is valid before performing any state-altering commands, to ensure your app is not corrupted by invalid data.</span></span> <span data-ttu-id="95c99-137">Você pode usar um [filtro](/aspnet/core/mvc/controllers/filters) para evitar a necessidade de adicionar um código para isso em cada ação.</span><span class="sxs-lookup"><span data-stu-id="95c99-137">You can use a [filter](/aspnet/core/mvc/controllers/filters) to avoid the need to add code for this in every action.</span></span> <span data-ttu-id="95c99-138">Os filtros do ASP.NET Core MVC oferecem uma maneira de interceptar grupos de solicitações, de modo que as políticas comuns e os interesses paralelos possam ser aplicados de forma direcionada.</span><span class="sxs-lookup"><span data-stu-id="95c99-138">ASP.NET Core MVC filters offer a way of intercepting groups of requests, so that common policies and cross-cutting concerns can be applied on a targeted basis.</span></span> <span data-ttu-id="95c99-139">Os filtros podem ser aplicados a ações individuais, a controladores inteiros ou globalmente a um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="95c99-139">Filters can be applied to individual actions, whole controllers, or globally for an application.</span></span>

<span data-ttu-id="95c99-140">Para APIs Web, o ASP.NET Core MVC é compatível com a [_negociação de conteúdo_](/aspnet/core/mvc/models/formatting), permitindo que as solicitações especifiquem como as respostas devem ser formatadas.</span><span class="sxs-lookup"><span data-stu-id="95c99-140">For web APIs, ASP.NET Core MVC supports [_content negotiation_](/aspnet/core/mvc/models/formatting), allowing requests to specify how responses should be formatted.</span></span> <span data-ttu-id="95c99-141">Com base nos cabeçalhos fornecidos na solicitação, as ações que retornam dados formatarão a resposta em XML, JSON ou outro formato compatível.</span><span class="sxs-lookup"><span data-stu-id="95c99-141">Based on headers provided in the request, actions returning data will format the response in XML, JSON, or another supported format.</span></span> <span data-ttu-id="95c99-142">Esse recurso permite que a mesma API seja usada por vários clientes com diferentes requisitos de formato de dados.</span><span class="sxs-lookup"><span data-stu-id="95c99-142">This feature enables the same API to be used by multiple clients with different data format requirements.</span></span>

> ### <a name="references--mapping-requests-to-responses"></a><span data-ttu-id="95c99-143">Referências – Mapeando solicitações para respostas</span><span class="sxs-lookup"><span data-stu-id="95c99-143">References – Mapping Requests to Responses</span></span>
>
> - <span data-ttu-id="95c99-144">**Ações de roteamento para o controlador**
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing></span><span class="sxs-lookup"><span data-stu-id="95c99-144">**Routing to Controller Actions**
<https://docs.microsoft.com/aspnet/core/mvc/controllers/routing></span></span>
> - <span data-ttu-id="95c99-145">**Model binding**
> <https://docs.microsoft.com/aspnet/core/mvc/models/model-binding></span><span class="sxs-lookup"><span data-stu-id="95c99-145">**Model Binding**
<https://docs.microsoft.com/aspnet/core/mvc/models/model-binding></span></span>
> - <span data-ttu-id="95c99-146">**Validação de modelo**
> <https://docs.microsoft.com/aspnet/core/mvc/models/validation></span><span class="sxs-lookup"><span data-stu-id="95c99-146">**Model Validation**
<https://docs.microsoft.com/aspnet/core/mvc/models/validation></span></span>
> - <span data-ttu-id="95c99-147">**Filtros**
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters></span><span class="sxs-lookup"><span data-stu-id="95c99-147">**Filters**
<https://docs.microsoft.com/aspnet/core/mvc/controllers/filters></span></span>

## <a name="working-with-dependencies"></a><span data-ttu-id="95c99-148">Trabalhando com dependências</span><span class="sxs-lookup"><span data-stu-id="95c99-148">Working with dependencies</span></span>

<span data-ttu-id="95c99-149">O ASP.NET Core tem suporte interno para uma técnica conhecida como [injeção de dependência](/aspnet/core/fundamentals/dependency-injection), além de fazer uso dela internamente.</span><span class="sxs-lookup"><span data-stu-id="95c99-149">ASP.NET Core has built-in support for and internally makes use of a technique known as [dependency injection](/aspnet/core/fundamentals/dependency-injection).</span></span> <span data-ttu-id="95c99-150">A injeção de dependência é uma técnica que permite um acoplamento flexível entre diferentes partes de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="95c99-150">Dependency injection is a technique that enables loose coupling between different parts of an application.</span></span> <span data-ttu-id="95c99-151">Um acoplamento mais flexível é desejável porque facilita o isolamento de partes do aplicativo, permitindo o teste ou a substituição.</span><span class="sxs-lookup"><span data-stu-id="95c99-151">Looser coupling is desirable because it makes it easier to isolate parts of the application, allowing for testing or replacement.</span></span> <span data-ttu-id="95c99-152">Ele também torna menos provável que uma alteração em uma parte do aplicativo tenha um impacto inesperado em outro lugar do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="95c99-152">It also makes it less likely that a change in one part of the application will have an unexpected impact somewhere else in the application.</span></span> <span data-ttu-id="95c99-153">A injeção de dependência baseia-se no princípio da inversão de dependência e costuma ser fundamental para alcançar o princípio do aberto/fechado.</span><span class="sxs-lookup"><span data-stu-id="95c99-153">Dependency injection is based on the dependency inversion principle, and is often key to achieving the open/closed principle.</span></span> <span data-ttu-id="95c99-154">Ao avaliar como o aplicativo funciona com suas dependências, tenha cuidado com o code smell [adesão estática](https://deviq.com/static-cling/) e lembre-se do aforismo "[new é associação](https://ardalis.com/new-is-glue)".</span><span class="sxs-lookup"><span data-stu-id="95c99-154">When evaluating how your application works with its dependencies, beware of the [static cling](https://deviq.com/static-cling/) code smell, and remember the aphorism "[new is glue](https://ardalis.com/new-is-glue)."</span></span>

<span data-ttu-id="95c99-155">A adesão estática ocorre quando as classes fazem chamadas a métodos estáticos ou acessam propriedades estáticas que têm efeitos colaterais ou dependências na infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="95c99-155">Static cling occurs when your classes make calls to static methods, or access static properties, which have side effects or dependencies on infrastructure.</span></span> <span data-ttu-id="95c99-156">Por exemplo, se você tiver um método que chama um método estático, que, por sua vez, grava em um banco de dados, o método terá um acoplamento rígido com o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="95c99-156">For example, if you have a method that calls a static method, which in turn writes to a database, your method is tightly coupled to the database.</span></span> <span data-ttu-id="95c99-157">Qualquer coisa que interrompa essa chamada de banco de dados interromperá o método.</span><span class="sxs-lookup"><span data-stu-id="95c99-157">Anything that breaks that database call will break your method.</span></span> <span data-ttu-id="95c99-158">O teste desses métodos é notoriamente difícil, pois testes desse tipo exigem bibliotecas fictícias comerciais para simular as chamadas estáticas ou podem ser testados somente com um banco de dados de teste em vigor.</span><span class="sxs-lookup"><span data-stu-id="95c99-158">Testing such methods is notoriously difficult, since such tests either require commercial mocking libraries to mock the static calls, or can only be tested with a test database in place.</span></span> <span data-ttu-id="95c99-159">As chamadas estáticas que não têm nenhuma dependência na infraestrutura, especialmente aquelas que estão completamente sem estado, têm a permissão de chamar e não têm nenhum impacto sobre o acoplamento ou a capacidade de teste (além do acoplamento do código com a própria chamada estática).</span><span class="sxs-lookup"><span data-stu-id="95c99-159">Static calls that don't have any dependence on infrastructure, especially those that are completely stateless, are fine to call and have no impact on coupling or testability (beyond coupling code to the static call itself).</span></span>

<span data-ttu-id="95c99-160">Muitos desenvolvedores entendem os riscos da adesão estática e do estado global, mas ainda acoplarão rigidamente o código com implementações específicas por meio da criação de instância direta.</span><span class="sxs-lookup"><span data-stu-id="95c99-160">Many developers understand the risks of static cling and global state, but will still tightly couple their code to specific implementations through direct instantiation.</span></span> <span data-ttu-id="95c99-161">A frase "new é associação" deve ser um lembrete desse acoplamento e não uma reprovação geral do uso da palavra-chave new.</span><span class="sxs-lookup"><span data-stu-id="95c99-161">"New is glue" is meant to be a reminder of this coupling, and not a general condemnation of the use of the new keyword.</span></span> <span data-ttu-id="95c99-162">Assim como ocorre com chamadas de método estático, novas instâncias de tipos que não têm nenhuma dependência externa normalmente não acoplam rigidamente o código com detalhes de implementação nem dificultam mais o teste.</span><span class="sxs-lookup"><span data-stu-id="95c99-162">Just as with static method calls, new instances of types that have no external dependencies typically do not tightly couple code to implementation details or make testing more difficult.</span></span> <span data-ttu-id="95c99-163">No entanto, sempre que for criada uma instância para uma classe, reserve um breve momento para considerar se faz sentido embutir essa instância específica em código em um local específico ou se é um melhor design solicitar essa instância como uma dependência.</span><span class="sxs-lookup"><span data-stu-id="95c99-163">But each time a class is instantiated, take just a brief moment to consider whether it makes sense to hard-code that specific instance in that particular location, or if it would be a better design to request that instance as a dependency.</span></span>

### <a name="declare-your-dependencies"></a><span data-ttu-id="95c99-164">Declarar as dependências</span><span class="sxs-lookup"><span data-stu-id="95c99-164">Declare your dependencies</span></span>

<span data-ttu-id="95c99-165">O ASP.NET Core foi criado com a ideia de que os métodos e as classes devem declarar suas dependências, solicitando-as como argumentos.</span><span class="sxs-lookup"><span data-stu-id="95c99-165">ASP.NET Core is built around having methods and classes declare their dependencies, requesting them as arguments.</span></span> <span data-ttu-id="95c99-166">Os aplicativos ASP.NET normalmente são definidos em uma classe Startup, que por si só é configurada para dar suporte à injeção de dependência em vários pontos.</span><span class="sxs-lookup"><span data-stu-id="95c99-166">ASP.NET applications are typically set up in a Startup class, which itself is configured to support dependency injection at several points.</span></span> <span data-ttu-id="95c99-167">Se a classe Startup tem um construtor, ela pode solicitar dependências por meio do construtor, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="95c99-167">If your Startup class has a constructor, it can request dependencies through the constructor, like so:</span></span>

```csharp
public class Startup
{
    public Startup(IHostingEnvironment env)
    {
        var builder = new ConfigurationBuilder()
        .SetBasePath(env.ContentRootPath)
        .AddJsonFile("appsettings.json", optional: false, reloadOnChange: true)
        .AddJsonFile(\$"appsettings.{env.EnvironmentName}.json", optional: true);
    }
}
```

<span data-ttu-id="95c99-168">A classe Startup é interessante, pois não há nenhum requisito de tipo explícito para ela.</span><span class="sxs-lookup"><span data-stu-id="95c99-168">The Startup class is interesting in that there are no explicit type requirements for it.</span></span> <span data-ttu-id="95c99-169">Ela não herda de uma classe base Startup especial nem implementa nenhuma interface específica.</span><span class="sxs-lookup"><span data-stu-id="95c99-169">It doesn't inherit from a special Startup base class, nor does it implement any particular interface.</span></span> <span data-ttu-id="95c99-170">Você pode atribuir um construtor a ela, ou não, e pode especificar quantos parâmetros no construtor desejar.</span><span class="sxs-lookup"><span data-stu-id="95c99-170">You can give it a constructor, or not, and you can specify as many parameters on the constructor as you want.</span></span> <span data-ttu-id="95c99-171">Quando o host da Web que você configurou para o aplicativo for iniciado, ele chamará a classe Startup que você o instruiu a usar e usará a injeção de dependência para popular todas as dependências exigidas pela classe Startup.</span><span class="sxs-lookup"><span data-stu-id="95c99-171">When the web host you've configured for your application starts, it will call the Startup class you've told it to use, and will use dependency injection to populate any dependencies the Startup class requires.</span></span> <span data-ttu-id="95c99-172">É claro que, se você solicitar parâmetros que não estiverem configurados no contêiner de serviços usado pelo ASP.NET Core, receberá uma exceção, mas desde que você continue usando as dependências reconhecidas pelo contêiner, poderá solicitar o que desejar.</span><span class="sxs-lookup"><span data-stu-id="95c99-172">Of course, if you request parameters that aren't configured in the services container used by ASP.NET Core, you'll get an exception, but as long as you stick to dependencies the container knows about, you can request anything you want.</span></span>

<span data-ttu-id="95c99-173">A injeção de dependência baseia-se nos aplicativos ASP.NET Core desde o início, quando a instância de Startup é criada.</span><span class="sxs-lookup"><span data-stu-id="95c99-173">Dependency injection is built into your ASP.NET Core apps right from the start, when you create the Startup instance.</span></span> <span data-ttu-id="95c99-174">Ela não para na classe Startup.</span><span class="sxs-lookup"><span data-stu-id="95c99-174">It doesn't stop there for the Startup class.</span></span> <span data-ttu-id="95c99-175">Você também pode solicitar dependências no método Configure:</span><span class="sxs-lookup"><span data-stu-id="95c99-175">You can also request dependencies in the Configure method:</span></span>

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

<span data-ttu-id="95c99-176">O método ConfigureServices é a exceção a esse comportamento; ele precisa ter apenas um parâmetro do tipo IServiceCollection.</span><span class="sxs-lookup"><span data-stu-id="95c99-176">The ConfigureServices method is the exception to this behavior; it must take just one parameter of type IServiceCollection.</span></span> <span data-ttu-id="95c99-177">Ele realmente não precisa dar suporte à injeção de dependência, pois, por um lado, é responsável por adicionar objetos ao contêiner de serviços e, por outro, tem acesso a todos os serviços atualmente configurados por meio do parâmetro IServiceCollection.</span><span class="sxs-lookup"><span data-stu-id="95c99-177">It doesn't really need to support dependency injection, since on the one hand it is responsible for adding objects to the services container, and on the other it has access to all currently configured services via the IServiceCollection parameter.</span></span> <span data-ttu-id="95c99-178">Portanto, você pode trabalhar com as dependências definidas na coleção de serviços do ASP.NET Core em todas as partes da classe Startup, solicitando o serviço necessário como um parâmetro ou trabalhando com a IServiceCollection em ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="95c99-178">Thus, you can work with dependencies defined in the ASP.NET Core services collection in every part of the Startup class, either by requesting the needed service as a parameter or by working with the IServiceCollection in ConfigureServices.</span></span>

> [!NOTE]
> <span data-ttu-id="95c99-179">Caso você precise garantir que determinados serviços estejam disponíveis para a classe Startup, configure-os usando WebHostBuilder e seu método ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="95c99-179">If you need to ensure certain services are available to your Startup class, you can configure them using WebHostBuilder and its ConfigureServices method.</span></span>

<span data-ttu-id="95c99-180">A classe Startup é um modelo de como você deve estruturar outras partes do aplicativo ASP.NET Core, de Controladores, Middleware, Filtros a seus próprios Serviços.</span><span class="sxs-lookup"><span data-stu-id="95c99-180">The Startup class is a model for how you should structure other parts of your ASP.NET Core application, from Controllers to Middleware to Filters to your own Services.</span></span> <span data-ttu-id="95c99-181">Em cada caso, você deve seguir o [Princípio das Dependências Explícitas](https://deviq.com/explicit-dependencies-principle/), solicitando as dependências em vez de criá-las diretamente e aproveitando a injeção de dependência em todo o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="95c99-181">In each case, you should follow the [Explicit Dependencies Principle](https://deviq.com/explicit-dependencies-principle/), requesting your dependencies rather than directly creating them, and leveraging dependency injection throughout your application.</span></span> <span data-ttu-id="95c99-182">Tenha cuidado com o local em que você cria instâncias de implementações diretamente e como você as cria, especialmente serviços e objetos que trabalham com a infraestrutura ou que têm efeitos colaterais.</span><span class="sxs-lookup"><span data-stu-id="95c99-182">Be careful of where and how you directly instantiate implementations, especially services and objects that work with infrastructure or have side effects.</span></span> <span data-ttu-id="95c99-183">Prefira trabalhar com as abstrações definidas no núcleo do aplicativo e passadas como argumentos para referências embutidas em código a tipos de implementação específicos.</span><span class="sxs-lookup"><span data-stu-id="95c99-183">Prefer working with abstractions defined in your application core and passed in as arguments to hardcoding references to specific implementation types.</span></span>

## <a name="structuring-the-application"></a><span data-ttu-id="95c99-184">Estruturando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="95c99-184">Structuring the application</span></span>

<span data-ttu-id="95c99-185">Normalmente, os aplicativos monolíticos têm um único ponto de entrada.</span><span class="sxs-lookup"><span data-stu-id="95c99-185">Monolithic applications typically have a single entry point.</span></span> <span data-ttu-id="95c99-186">No caso de um aplicativo Web ASP.NET Core, o ponto de entrada será o projeto Web ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="95c99-186">In the case of an ASP.NET Core web application, the entry point will be the ASP.NET Core web project.</span></span> <span data-ttu-id="95c99-187">No entanto, isso não significa que a solução precise consistir em apenas um único projeto.</span><span class="sxs-lookup"><span data-stu-id="95c99-187">However, that doesn't mean the solution should consist of just a single project.</span></span> <span data-ttu-id="95c99-188">É útil dividir o aplicativo em camadas diferentes para seguir a separação de interesses.</span><span class="sxs-lookup"><span data-stu-id="95c99-188">It's useful to break up the application into different layers in order to follow separation of concerns.</span></span> <span data-ttu-id="95c99-189">Depois de dividido em camadas, é útil ir além de pastas para projetos separados, que podem ajudar a obter o melhor encapsulamento.</span><span class="sxs-lookup"><span data-stu-id="95c99-189">Once broken up into layers, it's helpful to go beyond folders to separate projects, which can help achieve better encapsulation.</span></span> <span data-ttu-id="95c99-190">A melhor abordagem para atingir essas metas com um aplicativo ASP.NET Core é uma variação da Arquitetura Limpa abordada no capítulo 5.</span><span class="sxs-lookup"><span data-stu-id="95c99-190">The best approach to achieve these goals with an ASP.NET Core application is a variation of the Clean Architecture discussed in chapter 5.</span></span> <span data-ttu-id="95c99-191">Seguindo essa abordagem, a solução do aplicativo será composta por bibliotecas separadas para a interface do usuário, a Infraestrutura e o ApplicationCore.</span><span class="sxs-lookup"><span data-stu-id="95c99-191">Following this approach, the application's solution will be comprised of separate libraries for the UI, Infrastructure, and ApplicationCore.</span></span>

<span data-ttu-id="95c99-192">Além desses projetos, projetos de teste separados são incluídos também (o teste é abordado no capítulo 9).</span><span class="sxs-lookup"><span data-stu-id="95c99-192">In addition to these projects, separate test projects are included as well (Testing is discussed in Chapter 9).</span></span>

<span data-ttu-id="95c99-193">O modelo de objeto do aplicativo e as interfaces devem ser colocados no projeto de ApplicationCore.</span><span class="sxs-lookup"><span data-stu-id="95c99-193">The application's object model and interfaces should be placed in the ApplicationCore project.</span></span> <span data-ttu-id="95c99-194">Esse projeto terá o menor número possível de dependências e os outros projetos na solução o referenciarão.</span><span class="sxs-lookup"><span data-stu-id="95c99-194">This project will have as few dependencies as possible, and the other projects in the solution will reference it.</span></span> <span data-ttu-id="95c99-195">As entidades de negócios que precisam ser persistidas são definidas no projeto de ApplicationCore, assim como os serviços que não dependem diretamente da infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="95c99-195">Business entities that need to be persisted are defined in the ApplicationCore project, as are services that do not directly depend on infrastructure.</span></span>

<span data-ttu-id="95c99-196">Os detalhes de implementação, como a persistência é executada ou como as notificações podem ser enviadas a um usuário, são mantidos no projeto de Infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="95c99-196">Implementation details, such as how persistence is performed or how notifications might be sent to a user, are kept in the Infrastructure project.</span></span> <span data-ttu-id="95c99-197">Esse projeto referenciará pacotes específicos à implementação, como o Entity Framework Core, mas não deve expor os detalhes sobre essas implementações fora do projeto.</span><span class="sxs-lookup"><span data-stu-id="95c99-197">This project will reference implementation-specific packages such as Entity Framework Core, but should not expose details about these implementations outside of the project.</span></span> <span data-ttu-id="95c99-198">Os repositórios e serviços de infraestrutura devem implementar interfaces que são definidas no projeto de ApplicationCore e suas implementações de persistência são responsáveis por recuperar e armazenar entidades definidas no ApplicationCore.</span><span class="sxs-lookup"><span data-stu-id="95c99-198">Infrastructure services and repositories should implement interfaces that are defined in the ApplicationCore project, and its persistence implementations are responsible for retrieving and storing entities defined in ApplicationCore.</span></span>

<span data-ttu-id="95c99-199">O projeto de interface do usuário do ASP.NET Core é responsável pelas preocupações no nível da interface do usuário, mas não deve incluir detalhes da lógica de negócios ou infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="95c99-199">The ASP.NET Core UI project is responsible for any UI level concerns, but should not include business logic or infrastructure details.</span></span> <span data-ttu-id="95c99-200">Na verdade, o ideal é que ele não tenha nem mesmo uma dependência no projeto de Infraestrutura, o que ajudará a garantir que nenhuma dependência entre os dois projetos seja introduzida acidentalmente.</span><span class="sxs-lookup"><span data-stu-id="95c99-200">In fact, ideally it shouldn't even have a dependency on the Infrastructure project, which will help ensure no dependency between the two projects is introduced accidentally.</span></span> <span data-ttu-id="95c99-201">Isso pode ser feito com um contêiner de DI de terceiros como o StructureMap, que permite definir regras de DI em classes do Registro em cada projeto.</span><span class="sxs-lookup"><span data-stu-id="95c99-201">This can be achieved using a third-party DI container like StructureMap, which allows you to define DI rules in Registry classes in each project.</span></span>

<span data-ttu-id="95c99-202">Outra abordagem para desacoplar o aplicativo dos detalhes de implementação é fazer com que o aplicativo chame microsserviços, talvez implantados em contêineres individuais do Docker.</span><span class="sxs-lookup"><span data-stu-id="95c99-202">Another approach to decoupling the application from implementation details is to have the application call microservices, perhaps deployed in individual Docker containers.</span></span> <span data-ttu-id="95c99-203">Isso fornece uma separação de interesses e um desacoplamento ainda maiores do que a utilização da DI entre dois projetos, mas traz uma complexidade adicional.</span><span class="sxs-lookup"><span data-stu-id="95c99-203">This provides even greater separation of concerns and decoupling than leveraging DI between two projects, but has additional complexity.</span></span>

### <a name="feature-organization"></a><span data-ttu-id="95c99-204">Organização do recurso</span><span class="sxs-lookup"><span data-stu-id="95c99-204">Feature organization</span></span>

<span data-ttu-id="95c99-205">Por padrão, os aplicativos ASP.NET Core organizam sua estrutura de pastas para incluir Controladores e Exibições e, frequentemente, ViewModels.</span><span class="sxs-lookup"><span data-stu-id="95c99-205">By default, ASP.NET Core applications organize their folder structure to include Controllers and Views, and frequently ViewModels.</span></span> <span data-ttu-id="95c99-206">Em geral, o código do lado do cliente para dar suporte a essas estruturas do lado do servidor é armazenado separadamente na pasta wwwroot.</span><span class="sxs-lookup"><span data-stu-id="95c99-206">Client-side code to support these server-side structures is typically stored separately in the wwwroot folder.</span></span> <span data-ttu-id="95c99-207">No entanto, os aplicativos grandes podem enfrentar problemas com essa organização, pois o trabalho em um recurso específico geralmente exige o salto entre essas pastas.</span><span class="sxs-lookup"><span data-stu-id="95c99-207">However, large applications may encounter problems with this organization, since working on any given feature often requires jumping between these folders.</span></span> <span data-ttu-id="95c99-208">Isso fica cada vez mais difícil à medida que aumenta o número de arquivos e subpastas em cada pasta, resultando em uma grande quantidade de rolagem pelo Gerenciador de Soluções.</span><span class="sxs-lookup"><span data-stu-id="95c99-208">This gets more and more difficult as the number of files and subfolders in each folder grows, resulting in a great deal of scrolling through Solution Explorer.</span></span> <span data-ttu-id="95c99-209">Uma solução para esse problema é organizar o código do aplicativo por _recurso_, em vez de por tipo de arquivo.</span><span class="sxs-lookup"><span data-stu-id="95c99-209">One solution to this problem is to organize application code by _feature_ instead of by file type.</span></span> <span data-ttu-id="95c99-210">Esse estilo organizacional é normalmente conhecido como pastas de recurso ou fatias de recurso (consulte também [Fatias verticais](https://deviq.com/vertical-slices/)).</span><span class="sxs-lookup"><span data-stu-id="95c99-210">This organizational style is typically referred to as feature folders or feature slices (see also: [Vertical Slices](https://deviq.com/vertical-slices/)).</span></span>

<span data-ttu-id="95c99-211">O ASP.NET Core MVC é compatível com Áreas para essa finalidade.</span><span class="sxs-lookup"><span data-stu-id="95c99-211">ASP.NET Core MVC supports Areas for this purpose.</span></span> <span data-ttu-id="95c99-212">Usando áreas, você pode criar conjuntos separados de pastas de Controladores e Exibições (bem como os modelos associados) em cada pasta de Área.</span><span class="sxs-lookup"><span data-stu-id="95c99-212">Using areas, you can create separate sets of Controllers and Views folders (as well as any associated models) in each Area folder.</span></span> <span data-ttu-id="95c99-213">A Figura 7-1 mostra uma estrutura de pastas de exemplo, usando Áreas.</span><span class="sxs-lookup"><span data-stu-id="95c99-213">Figure 7-1 shows an example folder structure, using Areas.</span></span>

![](./media/image7-1.png)

<span data-ttu-id="95c99-214">Figura 7-1 Organização de área de exemplo</span><span class="sxs-lookup"><span data-stu-id="95c99-214">Figure 7-1 Sample Area Organization</span></span>

<span data-ttu-id="95c99-215">Ao usar Áreas, você precisa usar atributos para decorar os controladores com o nome da área à qual eles pertencem:</span><span class="sxs-lookup"><span data-stu-id="95c99-215">When using Areas, you must use attributes to decorate your controllers with the name of the area to which they belong:</span></span>

```csharp
[Area("Catalog")]
public class HomeController
{}
```

<span data-ttu-id="95c99-216">Você também precisa adicionar o suporte para área às rotas:</span><span class="sxs-lookup"><span data-stu-id="95c99-216">You also need to add area support to your routes:</span></span>

```csharp
app.UseMvc(routes =>
{
    // Areas support
    routes.MapRoute(
    name: "areaRoute",
    template: "{area:exists}/{controller=Home}/{action=Index}/{id?}");
    routes.MapRoute(
    name: "default",
    template: "{controller=Home}/{action=Index}/{id?}");
});
```

<span data-ttu-id="95c99-217">Além do suporte interno para Áreas, você também pode usar sua própria estrutura de pastas e convenções no lugar de atributos e rotas personalizadas.</span><span class="sxs-lookup"><span data-stu-id="95c99-217">In addition to the built-in support for Areas, you can also use your own folder structure, and conventions in place of attributes and custom routes.</span></span> <span data-ttu-id="95c99-218">Isso permite que você tenha pastas de recurso que não incluíam pastas separadas para Exibições, Controladores, etc., mantendo a hierarquia mais simples e facilitando a visualização de todos os arquivos relacionados em um único local para cada recurso.</span><span class="sxs-lookup"><span data-stu-id="95c99-218">This would allow you to have feature folders that didn't include separate folders for Views, Controllers, etc., keeping the hierarchy flatter and making it easier to see all related files in a single place for each feature.</span></span>

<span data-ttu-id="95c99-219">O ASP.NET Core usa tipos de convenção internos para controlar seu comportamento.</span><span class="sxs-lookup"><span data-stu-id="95c99-219">ASP.NET Core uses built-in convention types to control its behavior.</span></span> <span data-ttu-id="95c99-220">Você pode modificar ou substituir essas convenções.</span><span class="sxs-lookup"><span data-stu-id="95c99-220">You can modify or replace these conventions.</span></span> <span data-ttu-id="95c99-221">Por exemplo, você pode criar uma convenção que receberá automaticamente o nome de recurso para determinado controlador com base em seu namespace (que geralmente se correlaciona com a pasta na qual o controlador está localizado):</span><span class="sxs-lookup"><span data-stu-id="95c99-221">For example, you can create a convention that will automatically get the feature name for a given controller based on its namespace (which typically correlates to the folder in which the controller is located):</span></span>

```csharp
FeatureConvention : IControllerModelConvention
{
    public void Apply(ControllerModel controller)
    {
        controller.Properties.Add("feature",
        GetFeatureName(controller.ControllerType));
    }

    private string GetFeatureName(TypeInfo controllerType)
    {
        string[] tokens = controllerType.FullName.Split('.');
        if (!tokens.Any(t => t == "Features")) return "";
        string featureName = tokens
        .SkipWhile(t => !t.Equals("features",
        StringComparison.CurrentCultureIgnoreCase))
        .Skip(1)
        .Take(1)
        .FirstOrDefault();
        return featureName;
    }
}
```

<span data-ttu-id="95c99-222">Em seguida, especifique essa convenção como uma opção quando você adicionar suporte para o MVC ao seu aplicativo em ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="95c99-222">You then specify this convention as an option when you add support for MVC to your application in ConfigureServices:</span></span>

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

<span data-ttu-id="95c99-223">O ASP.NET Core MVC também usa uma convenção para localizar exibições.</span><span class="sxs-lookup"><span data-stu-id="95c99-223">ASP.NET Core MVC also uses a convention to locate views.</span></span> <span data-ttu-id="95c99-224">Você pode substituí-la por uma convenção personalizada, de modo que as exibições estejam localizadas nas pastas de recurso (usando o nome de recurso fornecido pela FeatureConvention, acima).</span><span class="sxs-lookup"><span data-stu-id="95c99-224">You can override it with a custom convention so that views will be located in your feature folders (using the feature name provided by the FeatureConvention, above).</span></span> <span data-ttu-id="95c99-225">Saiba mais sobre essa abordagem e baixe uma amostra funcional no artigo do MSDN [Fatias de recurso para o ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt763233.aspx).</span><span class="sxs-lookup"><span data-stu-id="95c99-225">You can learn more about this approach and download a working sample from the MSDN article, [Feature Slices for ASP.NET Core MVC](https://msdn.microsoft.com/magazine/mt763233.aspx).</span></span>

### <a name="cross-cutting-concerns"></a><span data-ttu-id="95c99-226">Interesses paralelos</span><span class="sxs-lookup"><span data-stu-id="95c99-226">Cross-cutting concerns</span></span>

<span data-ttu-id="95c99-227">Conforme os aplicativos crescem, fica cada vez mais importante excluir interesses paralelos para eliminar a duplicação e manter a consistência.</span><span class="sxs-lookup"><span data-stu-id="95c99-227">As applications grow, it becomes increasingly important to factor out cross-cutting concerns to eliminate duplication and maintain consistency.</span></span> <span data-ttu-id="95c99-228">Alguns exemplos de interesses paralelos em aplicativos ASP.NET Core são autenticação, regras de validação de modelos, cache de saída e tratamento de erro, embora haja muitos outros.</span><span class="sxs-lookup"><span data-stu-id="95c99-228">Some examples of cross-cutting concerns in ASP.NET Core applications are authentication, model validation rules, output caching, and error handling, though there are many others.</span></span> <span data-ttu-id="95c99-229">Os [filtros](/aspnet/core/mvc/controllers/filters) do ASP.NET Core MVC permitem executar o código antes ou depois de determinadas etapas do pipeline de processamento de solicitações.</span><span class="sxs-lookup"><span data-stu-id="95c99-229">ASP.NET Core MVC [filters](/aspnet/core/mvc/controllers/filters) allow you to run code before or after certain steps in the request processing pipeline.</span></span> <span data-ttu-id="95c99-230">Por exemplo, um filtro pode ser executado antes e após o model binding, antes e após uma ação ou antes e após o resultado de uma ação.</span><span class="sxs-lookup"><span data-stu-id="95c99-230">For instance, a filter can run before and after model binding, before and after an action, or before and after an action's result.</span></span> <span data-ttu-id="95c99-231">Você também pode usar um filtro de autorização para controlar o acesso ao restante do pipeline.</span><span class="sxs-lookup"><span data-stu-id="95c99-231">You can also use an authorization filter to control access to the rest of the pipeline.</span></span> <span data-ttu-id="95c99-232">A Figura 7-2 mostra como solicitar fluxos de execução por meio de filtros, caso eles estejam configurados.</span><span class="sxs-lookup"><span data-stu-id="95c99-232">Figures 7-2 shows how request execution flows through filters, if configured.</span></span>

![A solicitação é processada por meio de Filtros de autorização, Filtros de recurso, Model binding, Filtros de ação, Execução de ação e Conversão do resultado de ação, Filtros de exceção, Filtros de resultado e Execução de resultado.](./media/image7-2.png)

<span data-ttu-id="95c99-235">Figura 7-2 Solicitar a execução por meio de filtros e do pipeline de solicitação.</span><span class="sxs-lookup"><span data-stu-id="95c99-235">Figure 7-2 Request execution through filters and request pipeline.</span></span>

<span data-ttu-id="95c99-236">Normalmente, os filtros são implementados como atributos, de modo que você possa aplicá-los a controladores ou ações.</span><span class="sxs-lookup"><span data-stu-id="95c99-236">Filters are usually implemented as attributes, so you can apply them controllers or actions.</span></span> <span data-ttu-id="95c99-237">Quando adicionados dessa maneira, os filtros especificados no nível da ação substituem ou se baseiam nos filtros especificados no nível do controlador, que, por sua vez, substituem os filtros globais.</span><span class="sxs-lookup"><span data-stu-id="95c99-237">When added in this fashion, filters specified at the action level override or build upon filters specified at the controller level, which themselves override global filters.</span></span> <span data-ttu-id="95c99-238">Por exemplo, o atributo \[Route\] pode ser usado para criar rotas entre controladores e ações.</span><span class="sxs-lookup"><span data-stu-id="95c99-238">For example, the \[Route\] attribute can be used to build up routes between controllers and actions.</span></span> <span data-ttu-id="95c99-239">Da mesma forma, a autorização pode ser configurada no nível do controlador e, em seguida, substituída por ações individuais, como mostra o seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="95c99-239">Likewise, authorization can be configured at the controller level, and then overridden by individual actions, as the following sample demonstrates:</span></span>

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous]
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

<span data-ttu-id="95c99-240">O primeiro método, Login, usa o filtro AllowAnonymous (atributo) para substituir o filtro Authorize definido no nível do controlador.</span><span class="sxs-lookup"><span data-stu-id="95c99-240">The first method, Login, uses the AllowAnonymous filter (attribute) to override the Authorize filter set at the controller level.</span></span> <span data-ttu-id="95c99-241">A ação ForgotPassword (e qualquer outra ação na classe que não tem um atributo AllowAnonymous) exigirá uma solicitação autenticada.</span><span class="sxs-lookup"><span data-stu-id="95c99-241">The ForgotPassword action (and any other action in the class that doesn't have an AllowAnonymous attribute) will require an authenticated request.</span></span>

<span data-ttu-id="95c99-242">Os filtros podem ser usados para eliminar a duplicação na forma de tratamento de erro comum de políticas para APIs.</span><span class="sxs-lookup"><span data-stu-id="95c99-242">Filters can be used to eliminate duplication in the form of common error handling policies for APIs.</span></span> <span data-ttu-id="95c99-243">Por exemplo, uma política de API típica é retornar uma resposta NotFound para solicitações que referenciam chaves que não existem e uma resposta BadRequest se há falha na validação de modelos.</span><span class="sxs-lookup"><span data-stu-id="95c99-243">For example, a typical API policy is to return a NotFound response to requests referencing keys that do not exist, and a BadRequest response if model validation fails.</span></span> <span data-ttu-id="95c99-244">O seguinte exemplo demonstra essas duas políticas em ação:</span><span class="sxs-lookup"><span data-stu-id="95c99-244">The following example demonstrates these two policies in action:</span></span>

```csharp
[HttpPut("{id}")]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    if ((await _authorRepository.ListAsync()).All(a => a.Id != id))
    {
        return NotFound(id);
    }
    if (!ModelState.IsValid)
    {
        return BadRequest(ModelState);
    }
    author.Id = id;
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

<span data-ttu-id="95c99-245">Não permita que os métodos de ação fiquem desorganizados com um código condicional como este.</span><span class="sxs-lookup"><span data-stu-id="95c99-245">Don't allow your action methods to become cluttered with conditional code like this.</span></span> <span data-ttu-id="95c99-246">Em vez disso, coloque as políticas em filtros que podem ser aplicados conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="95c99-246">Instead, pull the policies into filters that can be applied on an as-needed basis.</span></span> <span data-ttu-id="95c99-247">Neste exemplo, a verificação da validação de modelos, que deve ocorrer a qualquer momento em que um comando é enviado para a API, pode ser substituída pelo seguinte atributo:</span><span class="sxs-lookup"><span data-stu-id="95c99-247">In this example, the model validation check, which should occur any time a command is sent to the API, can be replaced by the following attribute:</span></span>

```csharp
public class ValidateModelAttribute : ActionFilterAttribute
{
    public override void OnActionExecuting(ActionExecutingContext context)
    {
        if (!context.ModelState.IsValid)
        {
            context.Result = new BadRequestObjectResult(context.ModelState);
        }
    }
}
```

<span data-ttu-id="95c99-248">Da mesma forma, um filtro pode ser usado para verificar se um registro existe e retornar 404 antes que a ação seja executada, eliminando a necessidade de executar essas verificações na ação.</span><span class="sxs-lookup"><span data-stu-id="95c99-248">Likewise, a filter can be used to check if a record exists and return a 404 before the action is executed, eliminating the need to perform these checks in the action.</span></span> <span data-ttu-id="95c99-249">Depois de retirar as convenções comuns e organizar sua solução para separar a lógica de negócios e o código de infraestrutura da interface do usuário, os métodos de ação do MVC devem ser extremamente dinâmicos:</span><span class="sxs-lookup"><span data-stu-id="95c99-249">Once you've pulled out common conventions and organized your solution to separate infrastructure code and business logic from your UI, your MVC action methods should be extremely thin:</span></span>

```csharp
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

<span data-ttu-id="95c99-250">Leia mais sobre como implementar filtros e baixe uma amostra funcional no artigo do MSDN [Filtros do ASP.NET Core MVC do mundo real](https://msdn.microsoft.com/magazine/mt767699.aspx).</span><span class="sxs-lookup"><span data-stu-id="95c99-250">You can read more about implementing filters and download a working sample from the MSDN article, [Real World ASP.NET Core MVC Filters](https://msdn.microsoft.com/magazine/mt767699.aspx).</span></span>

> ### <a name="references--structuring-applications"></a><span data-ttu-id="95c99-251">Referências – estruturando aplicativos</span><span class="sxs-lookup"><span data-stu-id="95c99-251">References – Structuring applications</span></span>
>
> - <span data-ttu-id="95c99-252">**Áreas**</span><span class="sxs-lookup"><span data-stu-id="95c99-252">**Areas**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - <span data-ttu-id="95c99-253">**MSDN Magazine – fatias de recurso do ASP.NET Core MVC**</span><span class="sxs-lookup"><span data-stu-id="95c99-253">**MSDN Magazine – Feature Slices for ASP.NET Core MVC**</span></span>  
 > <https://msdn.microsoft.com/magazine/mt763233.aspx>
> - <span data-ttu-id="95c99-254">**Filtros**</span><span class="sxs-lookup"><span data-stu-id="95c99-254">**Filters**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - <span data-ttu-id="95c99-255">**MSDN – Filtros do ASP.NET Core MVC do mundo real**</span><span class="sxs-lookup"><span data-stu-id="95c99-255">**MSDN – Real World ASP.NET Core MVC Filters**</span></span>  
>   <https://msdn.microsoft.com/magazine/mt767699.aspx>

## <a name="security"></a><span data-ttu-id="95c99-256">Segurança</span><span class="sxs-lookup"><span data-stu-id="95c99-256">Security</span></span>

<span data-ttu-id="95c99-257">A proteção de aplicativos Web é um tópico extenso, com muitas considerações.</span><span class="sxs-lookup"><span data-stu-id="95c99-257">Securing web applications is a large topic, with many considerations.</span></span> <span data-ttu-id="95c99-258">Em seu nível mais básico, a segurança envolve a garantia de que você sabe de quem determinada solicitação é proveniente e, em seguida, a garantia de que essa solicitação tem acesso somente aos recursos que deveria.</span><span class="sxs-lookup"><span data-stu-id="95c99-258">At its most basic level, security involves ensuring you know who a given request is coming from, and then ensuring that the request only has access to resources it should.</span></span> <span data-ttu-id="95c99-259">Autenticação é o processo de comparar as credenciais fornecidas com uma solicitação com aquelas em um armazenamento de dados confiável, para verificar se a solicitação deve ser tratada como proveniente de uma entidade conhecida.</span><span class="sxs-lookup"><span data-stu-id="95c99-259">Authentication is the process of comparing credentials provided with a request to those in a trusted data store, to see if the request should be treated as coming from a known entity.</span></span> <span data-ttu-id="95c99-260">Autorização é o processo de restringir o acesso a determinados recursos com base na identidade do usuário.</span><span class="sxs-lookup"><span data-stu-id="95c99-260">Authorization is the process of restricting access to certain resources based on user identity.</span></span> <span data-ttu-id="95c99-261">Uma terceira preocupação de segurança é proteger as solicitações contra interceptação por terceiros, para o qual você deve, pelo menos, [garantir que o SSL é usado pelo aplicativo](/aspnet/core/security/enforcing-ssl).</span><span class="sxs-lookup"><span data-stu-id="95c99-261">A third security concern is protecting requests from eavesdropping by third parties, for which you should at least [ensure that SSL is used by your application](/aspnet/core/security/enforcing-ssl).</span></span>

### <a name="authentication"></a><span data-ttu-id="95c99-262">Autenticação</span><span class="sxs-lookup"><span data-stu-id="95c99-262">Authentication</span></span>

<span data-ttu-id="95c99-263">O ASP.NET Core Identity é um sistema de associação que pode ser usado para dar suporte à funcionalidade de logon para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="95c99-263">ASP.NET Core Identity is a membership system you can use to support login functionality for your application.</span></span> <span data-ttu-id="95c99-264">Ele tem suporte para contas de usuário local, bem como suporte para provedores de logon externo de provedores como a conta da Microsoft, Twitter, Facebook, Google e muito mais.</span><span class="sxs-lookup"><span data-stu-id="95c99-264">It has support for local user accounts as well as external login provider support from providers like Microsoft Account, Twitter, Facebook, Google, and more.</span></span> <span data-ttu-id="95c99-265">Além do ASP.NET Core Identity, o aplicativo pode usar a autenticação do Windows ou um provedor de identidade de terceiros, como o [Identity Server](https://github.com/IdentityServer/IdentityServer4).</span><span class="sxs-lookup"><span data-stu-id="95c99-265">In addition to ASP.NET Core Identity, your application can use windows authentication, or a third-party identity provider like [Identity Server](https://github.com/IdentityServer/IdentityServer4).</span></span>

<span data-ttu-id="95c99-266">O ASP.NET Core Identity é incluído em novos modelos de projeto se a opção Contas de Usuário Individuais é marcada.</span><span class="sxs-lookup"><span data-stu-id="95c99-266">ASP.NET Core Identity is included in new project templates if the Individual User Accounts option is selected.</span></span> <span data-ttu-id="95c99-267">Esse modelo inclui suporte para registro, logon, logons externos, senhas esquecidas e funcionalidade adicional.</span><span class="sxs-lookup"><span data-stu-id="95c99-267">This template includes support for registration, login, external logins, forgotten passwords, and additional functionality.</span></span>

![](./media/image7-3.png)

<span data-ttu-id="95c99-268">Figura 7-3 Selecionar Contas de Usuário Individuais para pré-configurar o Identity.</span><span class="sxs-lookup"><span data-stu-id="95c99-268">Figure 7-3 Select Individual User Accounts to have Identity preconfigured.</span></span>

<span data-ttu-id="95c99-269">O suporte para identidade é configurado em Startup, em ConfigureServices e Configure:</span><span class="sxs-lookup"><span data-stu-id="95c99-269">Identity support is configured in Startup, both in ConfigureServices and Configure:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddDbContext<ApplicationDbContext>(options =>
    options.UseSqlServer(Configuration.GetConnectionString("DefaultConnection")));
    services.AddIdentity<ApplicationUser, IdentityRole>()
    .AddEntityFrameworkStores<ApplicationDbContext>()
    .AddDefaultTokenProviders();
    services.AddMvc();
}

public void Configure(IApplicationBuilder app)
{
    app.UseStaticFiles();
    app.UseIdentity();
    app.UseMvc(routes =>
    {
        routes.MapRoute(
        name: "default",
        template: "{controller=Home}/{action=Index}/{id?}");
    });
}
```

<span data-ttu-id="95c99-270">É importante que UseIdentity apareça antes de UseMvc no método Configure.</span><span class="sxs-lookup"><span data-stu-id="95c99-270">It's important that UseIdentity appear before UseMvc in the Configure method.</span></span> <span data-ttu-id="95c99-271">Ao configurar o Identity em ConfigureServices, você observará uma chamada a AddDefaultTokenProviders.</span><span class="sxs-lookup"><span data-stu-id="95c99-271">When configuring Identity in ConfigureServices, you'll notice a call to AddDefaultTokenProviders.</span></span> <span data-ttu-id="95c99-272">Isso não tem nada a ver com tokens que podem ser usados para proteger comunicações da Web, mas refere-se a provedores que criam prompts que podem ser enviados aos usuários por SMS ou email para que eles confirmem sua identidade.</span><span class="sxs-lookup"><span data-stu-id="95c99-272">This has nothing to do with tokens that may be used to secure web communications, but instead refers to providers that create prompts that can be sent to users via SMS or email in order for them to confirm their identity.</span></span>

<span data-ttu-id="95c99-273">Saiba mais sobre como [configurar a autenticação de dois fatores](/aspnet/core/security/authentication/2fa) e [habilitar provedores de logon externo](/aspnet/core/security/authentication/social/) na documentação oficial do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="95c99-273">You can learn more about [configuring two-factor authentication](/aspnet/core/security/authentication/2fa) and [enabling external login providers](/aspnet/core/security/authentication/social/) from the official ASP.NET Core docs.</span></span>

### <a name="authorization"></a><span data-ttu-id="95c99-274">Autorização</span><span class="sxs-lookup"><span data-stu-id="95c99-274">Authorization</span></span>

<span data-ttu-id="95c99-275">A forma mais simples de autorização envolve a restrição do acesso a usuários anônimos.</span><span class="sxs-lookup"><span data-stu-id="95c99-275">The simplest form of authorization involves restricting access to anonymous users.</span></span> <span data-ttu-id="95c99-276">Para fazer isso, basta aplicar o atributo \[Authorize\] a determinados controladores ou ações.</span><span class="sxs-lookup"><span data-stu-id="95c99-276">This can be achieved by simply applying the \[Authorize\] attribute to certain controllers or actions.</span></span> <span data-ttu-id="95c99-277">Se funções estiverem sendo usadas, o atributo poderá ser estendido ainda mais para restringir o acesso a usuários que pertencem a determinadas funções, conforme mostrado:</span><span class="sxs-lookup"><span data-stu-id="95c99-277">If roles are being used, the attribute can be further extended to restrict access to users who belong to certain roles, as shown:</span></span>

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

<span data-ttu-id="95c99-278">Nesse caso, os usuários que pertencem as funções HRManager ou Finance (ou ambas) terão acesso ao SalaryController.</span><span class="sxs-lookup"><span data-stu-id="95c99-278">In this case, users belonging to either the HRManager or Finance roles (or both) would have access to the SalaryController.</span></span> <span data-ttu-id="95c99-279">Para exigir que um usuário pertença a várias funções (não apenas a uma de várias), aplique o atributo várias vezes, especificando uma função obrigatória por vez.</span><span class="sxs-lookup"><span data-stu-id="95c99-279">To require that a user belong to multiple roles (not just one of several), you can apply the attribute multiple times, specifying a required role each time.</span></span>

<span data-ttu-id="95c99-280">A especificação de determinados conjuntos de funções como cadeias de caracteres em muitos controladores e ações diferentes pode levar à repetição indesejável.</span><span class="sxs-lookup"><span data-stu-id="95c99-280">Specifying certain sets of roles as strings in many different controllers and actions can lead to undesirable repetition.</span></span> <span data-ttu-id="95c99-281">Você pode configurar políticas de autorização, que encapsulam regras de autorização e, em seguida, especificar a política, em vez de funções individuais ao aplicar o atributo \[Authorize\]:</span><span class="sxs-lookup"><span data-stu-id="95c99-281">You can configure authorization policies, which encapsulate authorization rules, and then specify the policy instead of individual roles when applying the \[Authorize\] attribute:</span></span>

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

<span data-ttu-id="95c99-282">Usando políticas dessa forma, você pode separar os tipos de ações que estão sendo restringidos das funções ou regras específicas que se aplicam a eles.</span><span class="sxs-lookup"><span data-stu-id="95c99-282">Using policies in this way, you can separate the kinds of actions being restricted from the specific roles or rules that apply to it.</span></span> <span data-ttu-id="95c99-283">Posteriormente, se você criar uma nova função que precisa ter acesso a determinados recursos, basta atualizar uma política, em vez de atualizar cada lista de funções em cada atributo \[Authorize\].</span><span class="sxs-lookup"><span data-stu-id="95c99-283">Later, if you create a new role that needs to have access to certain resources, you can just update a policy, rather than updating every list of roles on every \[Authorize\] attribute.</span></span>

#### <a name="claims"></a><span data-ttu-id="95c99-284">Declarações</span><span class="sxs-lookup"><span data-stu-id="95c99-284">Claims</span></span>

<span data-ttu-id="95c99-285">Declarações são pares de nome e valor que representam as propriedades de um usuário autenticado.</span><span class="sxs-lookup"><span data-stu-id="95c99-285">Claims are name value pairs that represent properties of an authenticated user.</span></span> <span data-ttu-id="95c99-286">Por exemplo, você pode armazenar o número de funcionário dos usuários como uma declaração.</span><span class="sxs-lookup"><span data-stu-id="95c99-286">For example, you might store users' employee number as a claim.</span></span> <span data-ttu-id="95c99-287">Em seguida, as declarações podem ser usadas como parte de políticas de autorização.</span><span class="sxs-lookup"><span data-stu-id="95c99-287">Claims can then be used as part of authorization policies.</span></span> <span data-ttu-id="95c99-288">Você pode criar uma política chamada "EmployeeOnly" que exige a existência de uma declaração chamada "EmployeeNumber", conforme mostrado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="95c99-288">You could create a policy called "EmployeeOnly" that requires the existence of a claim called "EmployeeNumber", as shown in this example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc();
    services.AddAuthorization(options =>
    {
        options.AddPolicy("EmployeeOnly", policy => policy.RequireClaim("EmployeeNumber"));
    });
}
```

<span data-ttu-id="95c99-289">Essa política pode então ser usada com o atributo \[Authorize\] para proteger qualquer controlador e/ou ação, conforme descrito acima.</span><span class="sxs-lookup"><span data-stu-id="95c99-289">This policy could then be used with the \[Authorize\] attribute to protect any controller and/or action, as described above.</span></span>

#### <a name="securing-web-apis"></a><span data-ttu-id="95c99-290">Proteger APIs Web</span><span class="sxs-lookup"><span data-stu-id="95c99-290">Securing web APIs</span></span>

<span data-ttu-id="95c99-291">A maioria das APIs Web deve implementar um sistema de autenticação baseada em token.</span><span class="sxs-lookup"><span data-stu-id="95c99-291">Most web APIs should implement a token-based authentication system.</span></span> <span data-ttu-id="95c99-292">A autenticação de token é sem estado e foi projetada para ser escalonável.</span><span class="sxs-lookup"><span data-stu-id="95c99-292">Token authentication is stateless and designed to be scalable.</span></span> <span data-ttu-id="95c99-293">Em um sistema de autenticação baseada em token, o cliente deve primeiro ser autenticado no provedor de autenticação.</span><span class="sxs-lookup"><span data-stu-id="95c99-293">In a token-based authentication system, the client must first authenticate with the authentication provider.</span></span> <span data-ttu-id="95c99-294">Se ele for bem-sucedido, o cliente receberá um token, que é apenas uma cadeia de caracteres criptograficamente significativa.</span><span class="sxs-lookup"><span data-stu-id="95c99-294">If successful, the client is issued a token, which is simply a cryptographically meaningful string of characters.</span></span> <span data-ttu-id="95c99-295">Em seguida, quando o cliente precisar emitir uma solicitação para uma API, ele adicionará esse token como um cabeçalho na solicitação.</span><span class="sxs-lookup"><span data-stu-id="95c99-295">When the client then needs to issue a request to an API, it adds this token as a header on the request.</span></span> <span data-ttu-id="95c99-296">O servidor então validará o token encontrado no cabeçalho da solicitação antes de concluir a solicitação.</span><span class="sxs-lookup"><span data-stu-id="95c99-296">The server then validates the token found in the request header before completing the request.</span></span> <span data-ttu-id="95c99-297">A Figura 7-4 demonstra esse processo.</span><span class="sxs-lookup"><span data-stu-id="95c99-297">Figure 7-4 demonstrates this process.</span></span>

![TokenAuth](./media/image7-4.png)

<span data-ttu-id="95c99-299">**Figura 7-4.**</span><span class="sxs-lookup"><span data-stu-id="95c99-299">**Figure 7-4.**</span></span> <span data-ttu-id="95c99-300">Autenticação baseada em token para APIs Web.</span><span class="sxs-lookup"><span data-stu-id="95c99-300">Token-based authentication for Web APIs.</span></span>

> ### <a name="references--security"></a><span data-ttu-id="95c99-301">Referências – Segurança</span><span class="sxs-lookup"><span data-stu-id="95c99-301">References – Security</span></span>
>
> - <span data-ttu-id="95c99-302">**Visão geral da documentação sobre segurança**</span><span class="sxs-lookup"><span data-stu-id="95c99-302">**Security Docs Overview**</span></span>  
>   https://docs.microsoft.com/aspnet/core/security/
> - <span data-ttu-id="95c99-303">**Impondo o SSL em um aplicativo ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="95c99-303">**Enforcing SSL in an ASP.NET Core App**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - <span data-ttu-id="95c99-304">**Introdução ao Identity**</span><span class="sxs-lookup"><span data-stu-id="95c99-304">**Introduction to Identity**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - <span data-ttu-id="95c99-305">**Introdução à autorização**</span><span class="sxs-lookup"><span data-stu-id="95c99-305">**Introduction to Authorization**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - <span data-ttu-id="95c99-306">**Autenticação e autorização para Aplicativos de API no Serviço de Aplicativo do Azure**</span><span class="sxs-lookup"><span data-stu-id="95c99-306">**Authentication and Authorization for API Apps in Azure App Service**</span></span>  
>   <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>

## <a name="client-communication"></a><span data-ttu-id="95c99-307">Comunicação com o cliente</span><span class="sxs-lookup"><span data-stu-id="95c99-307">Client communication</span></span>

<span data-ttu-id="95c99-308">Além de fornecer páginas e responder a solicitações de dados por meio de APIs Web, os aplicativos ASP.NET Core podem se comunicar diretamente com os clientes conectados.</span><span class="sxs-lookup"><span data-stu-id="95c99-308">In addition to serving pages and responding to requests for data via web APIs, ASP.NET Core apps can communicate directly with connected clients.</span></span> <span data-ttu-id="95c99-309">Essa comunicação de saída pode usar uma variedade de tecnologias de transporte, sendo a mais comum o WebSockets.</span><span class="sxs-lookup"><span data-stu-id="95c99-309">This outbound communication can use a variety of transport technologies, the most common being WebSockets.</span></span> <span data-ttu-id="95c99-310">O SignalR do ASP.NET Core é uma biblioteca que simplifica o acréscimo da funcionalidade de comunicação de servidor para cliente em tempo real aos aplicativos.</span><span class="sxs-lookup"><span data-stu-id="95c99-310">ASP.NET Core SignalR is a library that makes it simple to add real-time server-to-client communication functionality to your applications.</span></span> <span data-ttu-id="95c99-311">O SignalR é compatível com uma variedade de tecnologias de transporte, incluindo o WebSockets, e abstrai muitos dos detalhes de implementação do desenvolvedor.</span><span class="sxs-lookup"><span data-stu-id="95c99-311">SignalR supports a variety of transport technologies, including WebSockets, and abstracts away many of the implementation details from the developer.</span></span>

<span data-ttu-id="95c99-312">O SignalR do ASP.NET Core está disponível com o ASP.NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="95c99-312">ASP.NET Core SignalR is available with ASP.NET Core 2.1.</span></span>

<span data-ttu-id="95c99-313">A comunicação do cliente em tempo real, seja ela por meio do WebSockets diretamente ou por outras técnicas, é útil em uma variedade de cenários de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="95c99-313">Real-time client communication, whether using WebSockets directly or other techniques, are useful in a variety of application scenarios.</span></span> <span data-ttu-id="95c99-314">Eis alguns exemplos:</span><span class="sxs-lookup"><span data-stu-id="95c99-314">Some examples include:</span></span>

- <span data-ttu-id="95c99-315">Aplicativos de sala de chat ao vivo</span><span class="sxs-lookup"><span data-stu-id="95c99-315">Live chat room applications</span></span>

- <span data-ttu-id="95c99-316">Monitoramento de aplicativos</span><span class="sxs-lookup"><span data-stu-id="95c99-316">Monitoring applications</span></span>

- <span data-ttu-id="95c99-317">Atualizações de andamento do trabalho</span><span class="sxs-lookup"><span data-stu-id="95c99-317">Job progress updates</span></span>

- <span data-ttu-id="95c99-318">Notificações</span><span class="sxs-lookup"><span data-stu-id="95c99-318">Notifications</span></span>

- <span data-ttu-id="95c99-319">Aplicativos de formulários interativos</span><span class="sxs-lookup"><span data-stu-id="95c99-319">Interactive forms applications</span></span>

<span data-ttu-id="95c99-320">Ao desenvolver a comunicação do cliente nos aplicativos, normalmente, há dois componentes:</span><span class="sxs-lookup"><span data-stu-id="95c99-320">When building client communication into your applications, there are typically two components:</span></span>

- <span data-ttu-id="95c99-321">Gerenciador de conexões do lado do servidor (Hub do SignalR, WebSocketManager, WebSocketHandler)</span><span class="sxs-lookup"><span data-stu-id="95c99-321">Server-side connection manager (SignalR Hub, WebSocketManager WebSocketHandler)</span></span>

- <span data-ttu-id="95c99-322">Biblioteca do lado do cliente</span><span class="sxs-lookup"><span data-stu-id="95c99-322">Client-side library</span></span>

<span data-ttu-id="95c99-323">Os clientes não estão limitados aos navegadores – aplicativos móveis, aplicativos de console e outros aplicativos nativos também podem se comunicar por meio do SignalR/WebSockets.</span><span class="sxs-lookup"><span data-stu-id="95c99-323">Clients aren't limited to browsers – mobile apps, console apps, and other native apps can also communicate using SignalR/WebSockets.</span></span> <span data-ttu-id="95c99-324">O seguinte programa simples ecoa todo o conteúdo enviado a um aplicativo de chat para o console, como parte de um aplicativo de exemplo WebSocketManager:</span><span class="sxs-lookup"><span data-stu-id="95c99-324">The following simple program echoes all content sent to a chat application to the console, as part of a WebSocketManager sample application:</span></span>

```csharp
public class Program
{
    private static Connection _connection;
    public static void Main(string[] args)
    {
        StartConnectionAsync();
        _connection.On("receiveMessage", (arguments) =>;
        {
            Console.WriteLine(\$"{arguments\[0\]} said: {arguments\[1\]}");
        });
        Console.ReadLine();
        StopConnectionAsync();
    }

    public static async Task StartConnectionAsync()
    {
        _connection = new Connection();
        await _connection.StartConnectionAsync("ws://localhost:65110/chat");
    }

    public static async Task StopConnectionAsync()
    {
        await _connection.StopConnectionAsync();
    }
}
```

<span data-ttu-id="95c99-325">Considere maneiras pelas quais os aplicativos se comunicam diretamente com aplicativos cliente e considere se a comunicação em tempo real melhorará a experiência do usuário do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="95c99-325">Consider ways in which your applications communicate directly with client applications, and consider whether real-time communication would improve your app's user experience.</span></span>

> ### <a name="references--client-communication"></a><span data-ttu-id="95c99-326">Referências – Comunicação do cliente</span><span class="sxs-lookup"><span data-stu-id="95c99-326">References – Client Communication</span></span>
>
> - <span data-ttu-id="95c99-327">**SignalR do ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="95c99-327">**ASP.NET Core SignalR**</span></span>  
>   <https://github.com/aspnet/SignalR>
> - <span data-ttu-id="95c99-328">**WebSocket Manager**</span><span class="sxs-lookup"><span data-stu-id="95c99-328">**WebSocket Manager**</span></span>  
>   https://github.com/radu-matei/websocket-manager

## <a name="domain-driven-design--should-you-apply-it"></a><span data-ttu-id="95c99-329">Design controlado por domínio: você deve aplicá-lo?</span><span class="sxs-lookup"><span data-stu-id="95c99-329">Domain-driven design – Should you apply it?</span></span>

<span data-ttu-id="95c99-330">O DDD (Design Controlado por Domínio) é uma abordagem ágil para a criação de software que enfatiza o foco no _domínio de negócios_.</span><span class="sxs-lookup"><span data-stu-id="95c99-330">Domain-Driven Design (DDD) is an agile approach to building software that emphasizes focusing on the _business domain_.</span></span> <span data-ttu-id="95c99-331">Ele coloca uma grande ênfase na comunicação e interação com especialistas no domínio de negócios que podem relatar para os desenvolvedores como funciona o sistema do mundo real.</span><span class="sxs-lookup"><span data-stu-id="95c99-331">It places a heavy emphasis on communication and interaction with business domain expert(s) who can relate to the developers how the real-world system works.</span></span> <span data-ttu-id="95c99-332">Por exemplo, se você estiver criando um sistema que manipula mercados de ações, o especialista em domínio poderá ser um corretor de valores experiente.</span><span class="sxs-lookup"><span data-stu-id="95c99-332">For example, if you're building a system that handles stock trades, your domain expert might be an experienced stock broker.</span></span> <span data-ttu-id="95c99-333">O DDD foi projetado para resolver problemas de negócios grandes e complexos e, geralmente, não é adequado para aplicativos menores e mais simples, pois o investimento no entendimento e na modelagem do domínio não vale a pena.</span><span class="sxs-lookup"><span data-stu-id="95c99-333">DDD is designed to address large, complex business problems, and is often not appropriate for smaller, simpler applications, as the investment in understanding and modeling the domain is not worth it.</span></span>

<span data-ttu-id="95c99-334">Ao criar um software seguindo uma abordagem de DDD, sua equipe (incluindo stakeholders não técnicos e colaboradores) deve desenvolver uma _linguagem ubíqua_ para o espaço do problema.</span><span class="sxs-lookup"><span data-stu-id="95c99-334">When building software following a DDD approach, your team (including non-technical stakeholders and contributors) should develop a _ubiquitous language_ for the problem space.</span></span> <span data-ttu-id="95c99-335">Ou seja, a mesma terminologia deve ser usada para o conceito do mundo real que está sendo modelado, o software equivalente e as estruturas que podem existir para persistir o conceito (por exemplo, tabelas de banco de dados).</span><span class="sxs-lookup"><span data-stu-id="95c99-335">That is, the same terminology should be used for the real-world concept being modeled, the software equivalent, and any structures that might exist to persist the concept (for example, database tables).</span></span> <span data-ttu-id="95c99-336">Portanto, os conceitos descritos na linguagem ubíqua devem formar a base do _modelo de domínio_.</span><span class="sxs-lookup"><span data-stu-id="95c99-336">Thus, the concepts described in the ubiquitous language should form the basis for your _domain model_.</span></span>

<span data-ttu-id="95c99-337">O modelo de domínio é composto por objetos que interagem entre si para representar o comportamento do sistema.</span><span class="sxs-lookup"><span data-stu-id="95c99-337">Your domain model is comprised of objects that interact with one another to represent the behavior of the system.</span></span> <span data-ttu-id="95c99-338">Esses objetos podem se enquadrar nas seguintes categorias:</span><span class="sxs-lookup"><span data-stu-id="95c99-338">These objects may fall into the following categories:</span></span>

- <span data-ttu-id="95c99-339">[Entidades](https://deviq.com/entity/), que representam objetos com um thread de identidade.</span><span class="sxs-lookup"><span data-stu-id="95c99-339">[Entities](https://deviq.com/entity/), which represent objects with a thread of identity.</span></span> <span data-ttu-id="95c99-340">As entidades costumam ser armazenadas na persistência com uma chave pela qual elas podem ser recuperadas posteriormente.</span><span class="sxs-lookup"><span data-stu-id="95c99-340">Entities are typically stored in persistence with a key by which they can later be retrieved.</span></span>

- <span data-ttu-id="95c99-341">[Agregações](https://deviq.com/aggregate-pattern/), que representam grupos de objetos que devem ser persistidos como uma unidade.</span><span class="sxs-lookup"><span data-stu-id="95c99-341">[Aggregates](https://deviq.com/aggregate-pattern/), which represent groups of objects that should be persisted as a unit.</span></span>

- <span data-ttu-id="95c99-342">[Objetos de valor](https://deviq.com/value-object/), que representam conceitos que podem ser comparados com base na soma de seus valores de propriedade.</span><span class="sxs-lookup"><span data-stu-id="95c99-342">[Value objects](https://deviq.com/value-object/), which represent concepts that can be compared on the basis of the sum of their property values.</span></span> <span data-ttu-id="95c99-343">Por exemplo, DateRange consiste em uma data de início e término.</span><span class="sxs-lookup"><span data-stu-id="95c99-343">For example, DateRange consisting of a start and end date.</span></span>

- <span data-ttu-id="95c99-344">[Eventos de domínio](https://martinfowler.com/eaaDev/DomainEvent.html), que representam coisas que acontecem no sistema que são de interesse para outras partes do sistema.</span><span class="sxs-lookup"><span data-stu-id="95c99-344">[Domain events](https://martinfowler.com/eaaDev/DomainEvent.html), which represent things happening within the system that are of interest to other parts of the system.</span></span>

<span data-ttu-id="95c99-345">Observe que um modelo de domínio DDD deve encapsular um comportamento complexo dentro do modelo.</span><span class="sxs-lookup"><span data-stu-id="95c99-345">Note that a DDD domain model should encapsulate complex behavior within the model.</span></span> <span data-ttu-id="95c99-346">As entidades, em particular, não devem ser apenas coleções de propriedades.</span><span class="sxs-lookup"><span data-stu-id="95c99-346">Entities, in particular, should not merely be collections of properties.</span></span> <span data-ttu-id="95c99-347">Quando o modelo de domínio não tem um comportamento e representa apenas o estado do sistema, ele é chamado de [modelo anêmico](https://deviq.com/anemic-model/), o que é indesejável no DDD.</span><span class="sxs-lookup"><span data-stu-id="95c99-347">When the domain model lacks behavior and merely represents the state of the system, it is said to be an [anemic model](https://deviq.com/anemic-model/), which is undesirable in DDD.</span></span>

<span data-ttu-id="95c99-348">Além desses tipos de modelo, o DDD normalmente emprega uma variedade de padrões:</span><span class="sxs-lookup"><span data-stu-id="95c99-348">In addition to these model types, DDD typically employs a variety of patterns:</span></span>

- <span data-ttu-id="95c99-349">[Repositório](https://deviq.com/repository-pattern/), para abstrair os detalhes de persistência.</span><span class="sxs-lookup"><span data-stu-id="95c99-349">[Repository](https://deviq.com/repository-pattern/), for abstracting persistence details.</span></span>

- <span data-ttu-id="95c99-350">[Alocador](https://en.wikipedia.org/wiki/Factory_method_pattern), para encapsular a criação de objetos complexos.</span><span class="sxs-lookup"><span data-stu-id="95c99-350">[Factory](https://en.wikipedia.org/wiki/Factory_method_pattern), for encapsulating complex object creation.</span></span>

- <span data-ttu-id="95c99-351">Eventos de domínio, para desacoplar um comportamento dependente do comportamento de gatilho.</span><span class="sxs-lookup"><span data-stu-id="95c99-351">Domain events, for decoupling dependent behavior from triggering behavior.</span></span>

- <span data-ttu-id="95c99-352">[Serviços](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/), para encapsular um comportamento complexo e/ou detalhes de implementação de infraestrutura.</span><span class="sxs-lookup"><span data-stu-id="95c99-352">[Services](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/), for encapsulating complex behavior and/or infrastructure implementation details.</span></span>

- <span data-ttu-id="95c99-353">[Comando](https://en.wikipedia.org/wiki/Command_pattern), para desacoplar a emissão de comandos e executar o comando em si.</span><span class="sxs-lookup"><span data-stu-id="95c99-353">[Command](https://en.wikipedia.org/wiki/Command_pattern), for decoupling issuing commands and executing the command itself.</span></span>

- <span data-ttu-id="95c99-354">[Especificação](https://deviq.com/specification-pattern/), para encapsular os detalhes de consulta.</span><span class="sxs-lookup"><span data-stu-id="95c99-354">[Specification](https://deviq.com/specification-pattern/), for encapsulating query details.</span></span>

<span data-ttu-id="95c99-355">O DDD também recomenda o uso da Arquitetura Limpa abordada anteriormente, permitindo o acoplamento flexível, o encapsulamento e um código que pode ser verificado com facilidade por meio de testes de unidade.</span><span class="sxs-lookup"><span data-stu-id="95c99-355">DDD also recommends the use of the Clean Architecture discussed previously, allowing for loose coupling, encapsulation, and code that can easily be verified using unit tests.</span></span>

### <a name="when-should-you-apply-ddd"></a><span data-ttu-id="95c99-356">Quando você deve aplicar o DDD</span><span class="sxs-lookup"><span data-stu-id="95c99-356">When should you apply DDD</span></span>

<span data-ttu-id="95c99-357">O DDD é adequado para aplicativos grandes com complexidade significativa de negócios (não apenas técnica).</span><span class="sxs-lookup"><span data-stu-id="95c99-357">DDD is well-suited to large applications with significant business (not just technical) complexity.</span></span> <span data-ttu-id="95c99-358">O aplicativo deve exigir o conhecimento de especialistas no domínio.</span><span class="sxs-lookup"><span data-stu-id="95c99-358">The application should require the knowledge of domain experts.</span></span> <span data-ttu-id="95c99-359">Deve haver um comportamento significativo no próprio modelo de domínio, que representa as regras de negócio e as interações, além de simplesmente armazenar e recuperar o estado atual de vários registros de armazenamentos de dados.</span><span class="sxs-lookup"><span data-stu-id="95c99-359">There should be significant behavior in the domain model itself, representing business rules and interactions beyond simply storing and retrieving the current state of various records from data stores.</span></span>

### <a name="when-shouldnt-you-apply-ddd"></a><span data-ttu-id="95c99-360">Quando você não deve aplicar o DDD</span><span class="sxs-lookup"><span data-stu-id="95c99-360">When shouldn't you apply DDD</span></span>

<span data-ttu-id="95c99-361">O DDD envolve investimentos em modelagem, arquitetura e comunicação que não podem ser garantidos para aplicativos menores ou aplicativos que são essencialmente apenas CRUD (criar/ler/atualizar/excluir).</span><span class="sxs-lookup"><span data-stu-id="95c99-361">DDD involves investments in modeling, architecture, and communication that may not be warranted for smaller applications or applications that are essentially just CRUD (create/read/update/delete).</span></span> <span data-ttu-id="95c99-362">Caso você opte por abordar seu aplicativo seguindo o DDD, mas descubra que o domínio tem um modelo anêmico sem nenhum comportamento, talvez você precise repensar sua abordagem.</span><span class="sxs-lookup"><span data-stu-id="95c99-362">If you choose to approach your application following DDD, but find that your domain has an anemic model with no behavior, you may need to rethink your approach.</span></span> <span data-ttu-id="95c99-363">O aplicativo pode não precisar do DDD ou você pode precisar de assistência na refatoração do aplicativo para encapsular a lógica de negócios no modelo de domínio, em vez de na interface do usuário ou no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="95c99-363">Either your application may not need DDD, or you may need assistance refactoring your application to encapsulate business logic in the domain model, rather than in your database or user interface.</span></span>

<span data-ttu-id="95c99-364">Uma abordagem híbrida é usar o DDD somente para as áreas transacionais ou mais complexas do aplicativo, mas não para as partes CRUD ou somente leitura mais simples do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="95c99-364">A hybrid approach would be to only use DDD for the transactional or more complex areas of the application, but not for simpler CRUD or read-only portions of the application.</span></span> <span data-ttu-id="95c99-365">Por exemplo, você não precisa ter as restrições de uma Agregação se está consultando dados para exibir um relatório ou visualizar os dados para um painel.</span><span class="sxs-lookup"><span data-stu-id="95c99-365">For instance, you needn't have the constraints of an Aggregate if you're querying data to display a report or to visualize data for a dashboard.</span></span> <span data-ttu-id="95c99-366">É perfeitamente aceitável ter um modelo de leitura mais simples e separado para esses requisitos.</span><span class="sxs-lookup"><span data-stu-id="95c99-366">It's perfectly acceptable to have a separate, simpler read model for such requirements.</span></span>

> ### <a name="references--domain-driven-design"></a><span data-ttu-id="95c99-367">Referências – Design Controlado por Domínio</span><span class="sxs-lookup"><span data-stu-id="95c99-367">References – Domain-Driven Design</span></span>
>
> - <span data-ttu-id="95c99-368">**DDD simplificado (resposta do StackOverflow)**</span><span class="sxs-lookup"><span data-stu-id="95c99-368">**DDD in Plain English (StackOverflow Answer)**</span></span>  
>   <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a><span data-ttu-id="95c99-369">Implantação</span><span class="sxs-lookup"><span data-stu-id="95c99-369">Deployment</span></span>

<span data-ttu-id="95c99-370">Há algumas etapas envolvidas no processo de implantação do aplicativo ASP.NET Core, independentemente do local em que ele será hospedado.</span><span class="sxs-lookup"><span data-stu-id="95c99-370">There are a few steps involved in the process of deploying your ASP.NET Core application, regardless of where it will be hosted.</span></span> <span data-ttu-id="95c99-371">A primeira etapa é publicar o aplicativo, que pode ser feita com o comando da CLI dotnet publish.</span><span class="sxs-lookup"><span data-stu-id="95c99-371">The first step is to publish the application, which can be done using the dotnet publish CLI command.</span></span> <span data-ttu-id="95c99-372">Isso compilará o aplicativo e colocará todos os arquivos necessários para executar o aplicativo em uma pasta designada.</span><span class="sxs-lookup"><span data-stu-id="95c99-372">This will compile the application and place all of the files needed to run the application into a designated folder.</span></span> <span data-ttu-id="95c99-373">Quando você faz a implantação por meio do Visual Studio, esta etapa é executada automaticamente para você.</span><span class="sxs-lookup"><span data-stu-id="95c99-373">When you deploy from Visual Studio, this step is performed for you automatically.</span></span> <span data-ttu-id="95c99-374">A pasta de publicação contém arquivos .exe e .dll para o aplicativo e suas dependências.</span><span class="sxs-lookup"><span data-stu-id="95c99-374">The publish folder contains .exe and .dll files for the application and its dependencies.</span></span> <span data-ttu-id="95c99-375">Um aplicativo autossuficiente também incluirá uma versão do tempo de execução do .NET.</span><span class="sxs-lookup"><span data-stu-id="95c99-375">A self-contained application will also include a version of the .NET runtime.</span></span> <span data-ttu-id="95c99-376">Os aplicativos ASP.NET Core também incluirão arquivos de configuração, ativos de cliente estático e exibições do MVC.</span><span class="sxs-lookup"><span data-stu-id="95c99-376">ASP.NET Core applications will also include configuration files, static client assets, and MVC views.</span></span>

<span data-ttu-id="95c99-377">Os aplicativos ASP.NET Core são aplicativos de console que devem ser iniciados quando o servidor é inicializado e reiniciados quando há falhas no aplicativo (ou no servidor).</span><span class="sxs-lookup"><span data-stu-id="95c99-377">ASP.NET Core applications are console applications that must be started when the server boots and restarted if the application (or server) crashes.</span></span> <span data-ttu-id="95c99-378">Um gerenciador de processos pode ser usado para automatizar esse processo.</span><span class="sxs-lookup"><span data-stu-id="95c99-378">A process manager can be used to automate this process.</span></span> <span data-ttu-id="95c99-379">Os gerenciadores de processos mais comuns para o ASP.NET Core são o Nginx e o Apache no Linux e o IIS ou o Serviço Windows no Windows.</span><span class="sxs-lookup"><span data-stu-id="95c99-379">The most common process managers for ASP.NET Core are Nginx and Apache on Linux and IIS or Windows Service on Windows.</span></span>

<span data-ttu-id="95c99-380">Além de um gerenciador de processos, os aplicativos ASP.NET Core hospedados no servidor Web Kestrel devem usar um servidor proxy reverso.</span><span class="sxs-lookup"><span data-stu-id="95c99-380">In addition to a process manager, ASP.NET Core applications hosted in the Kestrel web server must use a reverse proxy server.</span></span> <span data-ttu-id="95c99-381">Um servidor proxy reverso recebe solicitações HTTP da Internet e encaminha-as para o Kestrel após algum tratamento preliminar.</span><span class="sxs-lookup"><span data-stu-id="95c99-381">A reverse proxy server receives HTTP requests from the internet and forwards them to Kestrel after some preliminary handling.</span></span> <span data-ttu-id="95c99-382">Os servidores proxy reverso fornecem uma camada de segurança para o aplicativo e são necessários para implantações de borda (expostas ao tráfego pela Internet).</span><span class="sxs-lookup"><span data-stu-id="95c99-382">Reverse proxy servers provide a layer of security for the application, and are required for edge deployments (exposed to traffic from the Internet).</span></span> <span data-ttu-id="95c99-383">O Kestrel é relativamente novo e ainda não oferece proteção contra alguns ataques.</span><span class="sxs-lookup"><span data-stu-id="95c99-383">Kestrel is relatively new and does not yet offer defenses against certain attacks.</span></span> <span data-ttu-id="95c99-384">O Kestrel também não dá suporte à hospedagem de vários aplicativos na mesma porta e, portanto, técnicas como cabeçalhos de host não podem ser usadas com ele para habilitar a hospedagem de vários aplicativos na mesma porta e endereço IP.</span><span class="sxs-lookup"><span data-stu-id="95c99-384">Kestrel also doesn't support hosting multiple applications on the same port, so techniques like host headers cannot be used with it to enable hosting multiple applications on the same port and IP address.</span></span>

![Kestrel para a Internet](./media/image7-5.png)

<span data-ttu-id="95c99-386">Figura 7-5 ASP.NET hospedado no Kestrel atrás de um servidor proxy reverso</span><span class="sxs-lookup"><span data-stu-id="95c99-386">Figure 7-5 ASP.NET hosted in Kestrel behind a reverse proxy server</span></span>

<span data-ttu-id="95c99-387">Outro cenário em que um proxy reverso pode ser útil é para proteger vários aplicativos usando SSL/HTTPS.</span><span class="sxs-lookup"><span data-stu-id="95c99-387">Another scenario in which a reverse proxy can be helpful is to secure multiple applications using SSL/HTTPS.</span></span> <span data-ttu-id="95c99-388">Nesse caso, somente o proxy inverso precisa ter o SSL configurado.</span><span class="sxs-lookup"><span data-stu-id="95c99-388">In this case, only the reverse proxy would need to have SSL configured.</span></span> <span data-ttu-id="95c99-389">A comunicação entre o servidor proxy reverso e o Kestrel pode ocorrer por HTTP, conforme mostrado na Figura 7-6.</span><span class="sxs-lookup"><span data-stu-id="95c99-389">Communication between the reverse proxy server and Kestrel could take place over HTTP, as shown in Figure 7-6.</span></span>

![](./media/image7-6.png)

<span data-ttu-id="95c99-390">Figura 7-6 ASP.NET hospedado atrás de um servidor proxy reverso protegido por HTTPS</span><span class="sxs-lookup"><span data-stu-id="95c99-390">Figure 7-6 ASP.NET hosted behind an HTTPS-secured reverse proxy server</span></span>

<span data-ttu-id="95c99-391">Uma abordagem cada vez mais popular é hospedar o aplicativo ASP.NET Core em um contêiner do Docker, que pode ser então hospedado localmente ou implantado no Azure para a hospedagem baseada em nuvem.</span><span class="sxs-lookup"><span data-stu-id="95c99-391">An increasingly popular approach is to host your ASP.NET Core application in a Docker container, which then can be hosted locally or deployed to Azure for cloud-based hosting.</span></span> <span data-ttu-id="95c99-392">O contêiner do Docker pode conter o código do aplicativo, em execução no Kestrel, e ser implantado atrás de um servidor proxy reverso, conforme mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="95c99-392">The Docker container could contain your application code, running on Kestrel, and would be deployed behind a reverse proxy server, as shown above.</span></span>

<span data-ttu-id="95c99-393">Caso esteja hospedando seu aplicativo no Azure, use o Gateway de Aplicativo do Microsoft Azure como uma solução de virtualização dedicada para fornecer vários serviços.</span><span class="sxs-lookup"><span data-stu-id="95c99-393">If you're hosting your application on Azure, you can use Microsoft Azure Application Gateway as a dedicated virtual appliance to provide several services.</span></span> <span data-ttu-id="95c99-394">Além de atuar como um proxy reverso para aplicativos individuais, o Gateway de Aplicativo também pode oferecer os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="95c99-394">In addition to acting as a reverse proxy for individual applications, Application Gateway can also offer the following features:</span></span>

- <span data-ttu-id="95c99-395">Balanceamento de carga HTTP</span><span class="sxs-lookup"><span data-stu-id="95c99-395">HTTP load balancing</span></span>

- <span data-ttu-id="95c99-396">Descarregamento SSL (SSL apenas para a Internet)</span><span class="sxs-lookup"><span data-stu-id="95c99-396">SSL offload (SSL only to Internet)</span></span>

- <span data-ttu-id="95c99-397">SSL de ponta a ponta</span><span class="sxs-lookup"><span data-stu-id="95c99-397">End to End SSL</span></span>

- <span data-ttu-id="95c99-398">Roteamento de vários sites (consolide até 20 sites em um único Gateway de Aplicativo)</span><span class="sxs-lookup"><span data-stu-id="95c99-398">Multi-site routing (consolidate up to 20 sites on a single Application Gateway)</span></span>

- <span data-ttu-id="95c99-399">Firewall do Aplicativo Web</span><span class="sxs-lookup"><span data-stu-id="95c99-399">Web application firewall</span></span>

- <span data-ttu-id="95c99-400">Suporte do WebSockets</span><span class="sxs-lookup"><span data-stu-id="95c99-400">Websocket support</span></span>

- <span data-ttu-id="95c99-401">Diagnóstico avançado</span><span class="sxs-lookup"><span data-stu-id="95c99-401">Advanced diagnostics</span></span>

<span data-ttu-id="95c99-402">_Saiba mais sobre as opções de implantação do Azure no [Capítulo 10](development-process-for-azure.md)._</span><span class="sxs-lookup"><span data-stu-id="95c99-402">_Learn more about Azure deployment options in [Chapter 10](development-process-for-azure.md)._</span></span>

> ### <a name="references--deployment"></a><span data-ttu-id="95c99-403">Referências – Implantação</span><span class="sxs-lookup"><span data-stu-id="95c99-403">References – Deployment</span></span>
>
> - <span data-ttu-id="95c99-404">**Visão geral de hospedagem e implantação**</span><span class="sxs-lookup"><span data-stu-id="95c99-404">**Hosting and Deployment Overview**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/publishing/>
> - <span data-ttu-id="95c99-405">**Quando usar o Kestrel com um proxy reverso**</span><span class="sxs-lookup"><span data-stu-id="95c99-405">**When to use Kestrel with a reverse proxy**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - <span data-ttu-id="95c99-406">**Hospedar aplicativos ASP.NET Core no Docker**</span><span class="sxs-lookup"><span data-stu-id="95c99-406">**Host ASP.NET Core apps in Docker**</span></span>  
>   <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - <span data-ttu-id="95c99-407">**Introdução ao Gateway de Aplicativo do Azure**</span><span class="sxs-lookup"><span data-stu-id="95c99-407">**Introducing Azure Application Gateway**</span></span>  
>   <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
<span data-ttu-id="95c99-408">[Anterior](common-client-side-web-technologies.md)
[Próximo](work-with-data-in-asp-net-core-apps.md)</span><span class="sxs-lookup"><span data-stu-id="95c99-408">[Previous](common-client-side-web-technologies.md)
[Next](work-with-data-in-asp-net-core-apps.md)</span></span>
