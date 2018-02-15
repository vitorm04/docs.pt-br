---
title: "Desenvolvimento de aplicativos do núcleo do ASP.NET MVC"
description: Projetar aplicativos Web modernos com ASP.NET Core e o Azure | desenvolvimento de aplicativos do ASP.NET Core MVC
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c10bf66dd37f0d99c038db7f95999d84986152fa
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="develop-aspnet-core-mvc-apps"></a>Desenvolver aplicativos do núcleo do ASP.NET MVC

> "Não é importante acertar na primeira vez. É extremamente importante acertar a última vez."  
> _-Busca Andrew e David Thomas_

## <a name="summary"></a>Resumo

ASP.NET Core é uma estrutura de plataforma cruzada, o código-fonte aberto para a criação de aplicativos web modernos otimizada para a nuvem. Aplicativos ASP.NET Core são simples e modulares, com o suporte interno para a injeção de dependência, permitindo maior capacidade de teste e facilidade de manutenção. Combinado com MVC, que oferece suporte à criação moderno APIs da web além de aplicativos baseados no modo de exibição, o ASP.NET Core é uma estrutura eficiente para a criação enterprise aplicativos web.

## <a name="mapping-requests-to-responses"></a>Solicitações de mapeamento para respostas

Em sua essência, os aplicativos do ASP.NET Core mapeiam solicitações de entrada para respostas de saída. Em um nível baixo, isso é feito com middleware e simples de aplicativos do ASP.NET Core e microservices podem ser compostas apenas de middleware personalizado. Ao usar o ASP.NET Core MVC, você pode trabalhar em um nível um pouco maior, pensando em termos de *rotas*, *controladores*, e *ações*. Cada solicitação de entrada é comparada com a tabela de roteamento do aplicativo e se uma rota correspondente for encontrada, o método de ação associada (pertencente a um controlador) é chamado para manipular a solicitação. Se nenhuma rota correspondente for encontrada, um manipulador de erro (nesse caso, retornando um resultado não encontrado) é chamado.

Aplicativos MVC do ASP.NET Core podem usar rotas convencionais, rotas de atributo ou ambos. Rotas convencionais são definidas no código, especificando o roteamento *convenções* usando a sintaxe como no exemplo a seguir:

```csharp
app.UseMvc(routes =>;
{
    routes.MapRoute("default","{controller=Home}/{action=Index}/{id?}");
});
```

Neste exemplo, uma rota denominada "padrão" foi adicionada à tabela de roteamento. Define um modelo de rota com espaços reservados para *controlador*, *ação*, e *id*. Os espaços reservados de controlador e ação têm padrão especificado ("Início" e "Index", respectivamente), e o espaço reservado da id é opcional (em virtude de um "?" aplicado). A convenção definidas aqui indica que a primeira parte de uma solicitação deve corresponder ao nome do controlador, a segunda parte para a ação, e, em seguida, se for necessária uma terceira parte representará um parâmetro de id. Rotas convencionais costumam ser definidas em um local para o aplicativo, como no método configurar na classe de inicialização.

Rotas de atributo são aplicadas diretamente a controladores e ações, em vez de global especificadas. Isso tem a vantagem de torná-los mais detectável quando você está olhando para um método específico, mas significa que as informações de roteamento não são mantidas em um único lugar no aplicativo. Rotas de atributo, você pode facilmente especificar várias rotas para uma determinada ação, bem como combinar rotas entre controladores e ações. Por exemplo:

```csharp
[Route("Home")]
public class HomeController : Controller
{
    [Route("")] // Combines to define the route template "Home"
    [Route("Index")] // Combines to define route template "Home/Index"
    [Route("/")] // Does not combine, defines the route template ""
    public IActionResult Index() {}
```

Rotas podem ser especificadas em [HttpGet] e atributos semelhantes, evitando a necessidade de adicionar separam [rota\] atributos. Rotas de atributo também podem usar tokens para reduzir a necessidade de repetir a ação ou controlador nomes, conforme mostrado abaixo:

```csharp
[Route("[controller\]")]
public class ProductsController : Controller
{
    [Route("")] // Matches 'Products'
    [Route("Index")] // Matches 'Products/Index'
    public IActionResult Index()
}
```

Depois que uma determinada solicitação corresponda a uma rota, mas antes da ação de método é chamado, o MVC do ASP.NET Core executará [associação de modelo](https://docs.microsoft.com/aspnet/core/mvc/models/model-binding) e [validação do modelo](https://docs.microsoft.com/aspnet/core/mvc/models/validation) na solicitação. Associação de modelo é responsável para converter os dados de entrada HTTP para os tipos de .NET especificados como parâmetros do método de ação a ser chamado. Por exemplo, se o método de ação espera um parâmetro de id int, associação de modelos tentará fornecer esse parâmetro de um valor fornecido como parte da solicitação. Para fazer isso, a associação de modelo procura valores em um formulário publicado, os valores da rota em si e valores de cadeia de caracteres de consulta. Supondo que um valor de id é encontrado, ele será convertido em um número inteiro antes de ser passado para o método de ação.

Depois de associar o modelo, mas antes de chamar o método de ação, ocorre a validação do modelo. Validação de modelo usa atributos opcionais no tipo de modelo e pode ajudar a garantir que o objeto do modelo fornecido está em conformidade com certos requisitos de dados. Certos valores podem ser especificados como necessários ou limitados a um determinado comprimento ou intervalo numérico, etc. Se os atributos de validação são especificados, mas o modelo não está de acordo com seus requisitos, a propriedade ModelState será false e o conjunto de regras de validação de não estará disponível para enviar ao cliente que está fazendo a solicitação.

Se você estiver usando a validação do modelo, certifique-se sempre verificar se o modelo é válido antes de executar os comandos de alteração de estado, para garantir que seu aplicativo não está corrompido por dados inválidos. Você pode usar um [filtro](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) para evitar a necessidade de adicionar o código para isso em cada ação. Filtros MVC do ASP.NET Core oferecem uma maneira de interceptação de grupos de solicitações, para que políticas comuns e resolvem preocupações podem ser aplicadas em uma base de destino. Filtros podem ser aplicados para ações individuais, controladores de inteiros, ou globalmente para um aplicativo.

Para APIs da web, MVC do ASP.NET Core dá suporte a [ *negociação de conteúdo*](https://docs.microsoft.com/aspnet/core/mvc/models/formatting), permitindo solicitações especificar como as respostas devem ser formatadas. Com base em cabeçalhos fornecidos na solicitação, retornando dados de ações formatará a resposta em XML, JSON ou outro formato com suporte. Esse recurso permite que a mesma API a ser usado por vários clientes com requisitos de formato de dados diferentes.

> ### <a name="references--mapping-requests-to-responses"></a>Solicitações de mapeamento de referências – para respostas
> - **O roteamento para ações do controlador**
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/routing>
> - **Associação de modelo** https://docs.microsoft.com/aspnet/core/mvc/models/model-binding
> - **Validação de modelo**
> <https://docs.microsoft.com/aspnet/core/mvc/models/validation>
> - **Filters** https://docs.microsoft.com/aspnet/core/mvc/controllers/filters

## <a name="working-with-dependencies"></a>Trabalhando com dependências

ASP.NET Core tem suporte interno para e internamente usa uma técnica conhecida como [injeção de dependência](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection). Injeção de dependência é uma técnica que habilitado acoplamento fraco entre diferentes partes de um aplicativo. Menor acoplamento é desejável, porque isso facilita isolar partes do aplicativo, permitindo a substituição ou de teste. Ele também torna menos provável que uma alteração em uma parte do aplicativo terá um impacto inesperado em outro lugar no aplicativo. Injeção de dependência baseia-se do princípio de inversão de dependência e geralmente é fundamental para alcançar o princípio de abertura/fechamento. Ao avaliar como o aplicativo funciona com suas dependências, tenha cuidado com o [adesivos](http://deviq.com/static-cling/) cheiro de código e lembre-se de aphorism "[novo é liga](http://ardalis.com/new-is-glue)."

Adesivos ocorre quando suas classes de fazer chamadas para métodos estáticos ou propriedades estáticas, que têm efeitos colaterais ou dependências na infraestrutura de acesso. Por exemplo, se você tiver um método que chama um método estático, que por sua vez grava em um banco de dados, o método está acoplado ao banco de dados. Qualquer coisa que violam essa chamada de banco de dados interromperá o método. Esses métodos de teste é notoriamente difíceis, desde que tais testes exigem comerciais bibliotecas fictícias para simular as chamadas estáticas, ou somente podem ser testados com um banco de dados de teste em vigor. Chamadas estáticas que não tem nenhuma dependência de infraestrutura, especialmente aqueles que estão completamente sem monitoração de estado, são permitidas chamar e não ter nenhum impacto sobre o acoplamento ou a capacidade de teste (além de combinar código para a própria chamada estática).

Muitos desenvolvedores entender os riscos de adesivos e estado global, mas ainda rigidamente serão acoplar o seu código para implementações específicas por meio de instanciação direta. "Novo é liga" deve ser um lembrete desse acoplamento e não um condemnation geral do uso da palavra-chave nova. Assim como com chamadas de método estático, novas instâncias de tipos que não têm nenhuma dependência externa normalmente não totalmente acoplar o código para obter detalhes de implementação ou tornar o teste mais difícil. No entanto, cada vez que uma classe é instanciada, levar um breve momento a considerar se faz sentido embutir aquela instância específica em um local específico, ou se ele seria um melhor design para solicitar essa instância como uma dependência.

### <a name="declare-your-dependencies"></a>Declare as suas dependências

ASP.NET Core foi criado para ter métodos e classes declarar suas dependências, solicitando-os como argumentos. Aplicativos ASP.NET normalmente são definidos em uma classe de inicialização, que por si só é configurado para dar suporte a injeção de dependência em vários pontos. Se sua classe de inicialização tem um construtor, ele pode solicitar dependências por meio do construtor, da seguinte forma:

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

A classe de inicialização é interessante que não há nenhum requisito de tipo explícito para ele. Ela não herda de uma classe base de inicialização especial nem implementar a qualquer interface específica. Você pode atribuir um construtor, ou não, e você pode especificar quantos parâmetros você deseja no construtor. Quando o host da web que você configurou para seu aplicativo é iniciado, ele chamará a classe de inicialização que você informou que ele use e usará a injeção de dependência para preencher todas as dependências que requer que a classe de inicialização. É claro que, se você solicitar parâmetros que não estão configurados no contêiner de serviços usado pelo ASP.NET Core, você receberá uma exceção, mas desde que ultrapasse dependências contêiner conhece, você pode solicitar que quiser.

Injeção de dependência é criada em seus aplicativos do ASP.NET Core desde o início, quando você cria a instância de inicialização. Não parar existe para a classe de inicialização. Você também pode solicitar dependências no método configurar:

```csharp
public void Configure(IApplicationBuilder app,
    IHostingEnvironment env,
    ILoggerFactory loggerFactory)
{

}
```

O método ConfigureServices é a exceção a esse comportamento; ele deve ter apenas um parâmetro do tipo IServiceCollection. Ele não precisa dar suporte a injeção de dependência, como por um lado é responsável por adicionar objetos para o contêiner de serviços, e no outro, ele tem acesso a todos os serviços configurados no momento por meio do parâmetro IServiceCollection. Assim, você pode trabalhar com dependências definidas na coleção de serviços ASP.NET Core em cada parte da classe de inicialização, solicitando o serviço necessário como um parâmetro ou trabalhando com IServiceCollection em ConfigureServices.

> [!NOTE]
> Se você precisa garantir que determinados serviços estão disponíveis para sua classe de inicialização, você pode configurá-los usando WebHostBuilder e seu método ConfigureServices.

A classe de inicialização é um modelo de como você deve estruturar outras partes de seu aplicativo ASP.NET Core, controladores de Middleware para filtros para seus próprios serviços. Em cada caso, você deve seguir o [princípio de dependências explícitas](http://deviq.com/explicit-dependencies-principle/), solicitando suas dependências em vez de diretamente criá-las e aproveitando a injeção de dependência em seu aplicativo. Tenha cuidado de onde e como você instancia diretamente implementações, especialmente os objetos que funcionam com a infraestrutura ou têm efeitos colaterais e serviços. Preferir trabalhar com abstrações definido no núcleo do seu aplicativo e transmitidos como argumentos para codificar referências a tipos específicos de implementação.

## <a name="structuring-the-application"></a>Estruturação do aplicativo

Aplicativos monolíticos normalmente têm um único ponto de entrada. No caso de um aplicativo web ASP.NET Core, o ponto de entrada será o projeto da web ASP.NET Core. No entanto, isso não significa que a solução deve consistir de apenas um único projeto. É útil dividir o aplicativo em camadas diferentes para que você siga a separação de preocupações. Depois de dividida em camadas, é útil ir além de pastas para projetos, que podem ajudar a obter o melhor encapsulamento separados. A melhor abordagem para atingir essas metas com um aplicativo do ASP.NET Core é uma variação da arquitetura limpa discutido no capítulo 5. Seguir essa abordagem, solução do aplicativo será composta de bibliotecas separadas para a interface do usuário, infraestrutura e ApplicationCore.

Além desses projetos, projetos de teste separados são incluídos também (teste é discutido no capítulo 9).

Modelo de objeto do aplicativo e as interfaces devem ser colocadas no projeto ApplicationCore. Este projeto terá dependências ao menor número possível, e os outros projetos na solução fará referência a ele. Entidades de negócios que precisam ser mantidos são definidas no projeto ApplicationCore, assim como os serviços que dependem diretamente infraestrutura.

Detalhes de implementação, como a persistência é executada ou como as notificações podem ser enviadas a um usuário, são mantidas no projeto de infra-estrutura. Este projeto fizer referência a pacotes específicos de implementação, como Entity Framework Core, mas não deve expor os detalhes sobre essas implementações fora do projeto. Repositórios e serviços de infraestrutura devem implementar interfaces que são definidos no projeto ApplicationCore e suas implementações de persistência serão responsáveis por recuperar e armazenar entidades definidas em ApplicationCore.

O projeto do ASP.NET Core em si é responsável por quaisquer dúvidas de nível de interface do usuário, mas não deve incluir os detalhes de infraestrutura ou lógica de negócios. Na verdade, o ideal é que mesmo não devia uma dependência sobre o projeto de infra-estrutura, que ajuda a garantir que nenhuma dependência entre os dois projetos é introduzida acidentalmente. Isso pode ser feito usando um contêiner de injeção de dependência de terceiros como StructureMap, que permite que você defina regras de DI em classes de registro em cada projeto.

Outra abordagem para desacoplar o aplicativo de detalhes de implementação é ter o aplicativo chamada microservices, talvez implantado em contêineres individuais do Docker. Isso fornece ainda maior separação de preocupações e desacoplamento que aproveitando a injeção de dependência entre dois projetos, mas tem uma complexidade adicional.

### <a name="feature-organization"></a>Organização do recurso

Por padrão, os aplicativos do ASP.NET Core organizam sua estrutura de pasta para incluir controladores e exibições e frequentemente ViewModels. Código do lado do cliente para oferecer suporte a essas estruturas do lado do servidor geralmente armazenado separadamente na pasta wwwroot. No entanto, os aplicativos grandes podem encontrar problemas com esta organização, como trabalhar em qualquer determinado recurso geralmente requer saltar entre essas pastas. Isso é mais difícil à medida que aumenta o número de arquivos e subpastas em cada pasta, resultando em uma grande quantidade de rolar pelo Gerenciador de soluções. Uma solução para esse problema é organizar o código do aplicativo por *recurso* em vez de por tipo de arquivo. Esse estilo organizacional é normalmente conhecido como pastas de recurso ou fatias de recurso (Consulte também: [fatias verticais](http://deviq.com/vertical-slices/)).

Núcleo do ASP.NET MVC oferece suporte a áreas para essa finalidade. Usando áreas, você pode criar conjuntos separados de controladores e exibições pastas (bem como os modelos associados) em cada pasta de área. Figura 7-1 mostra uma estrutura de pasta de exemplo, usando áreas.

![](./media/image7-1.png)

Figura 7-1 organização de área de exemplo

Ao usar áreas, você deve usar atributos para decorar os controladores com o nome da área à qual pertencem:

```csharp
[Area("Catalog")]
public class HomeController
{}
```

Você também precisará adicionar suporte a área para suas rotas:

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

Além do suporte interno para áreas, você também pode usar sua própria estrutura de pasta e convenções no lugar de atributos e rotas personalizadas. Isso permitiria que você tiver pastas de recurso que não incluem pastas separadas para modos de exibição, controladores, etc., mantendo a hierarquia mais simples e tornando mais fácil ver que todos os arquivos em um único local para cada recurso relacionados.

ASP.NET Core usa tipos de convenção internas para controlar seu comportamento. Você pode modificar ou substituir estas convenções. Por exemplo, você pode criar uma convenção que receberá automaticamente o nome do recurso para um determinado controlador com base em seu namespace (que geralmente se correlaciona com a pasta na qual o controlador está localizado):

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

Em seguida, especifique essa convenção de como uma opção quando você adiciona suporte para o MVC para seu aplicativo no ConfigureServices:

```csharp
services.AddMvc(o => o.Conventions.Add(new FeatureConvention()));
```

Núcleo do ASP.NET MVC também usa uma convenção para localizar os modos de exibição. Você pode substituí-la com uma convenção personalizada para que os modos de exibição estarão localizados em suas pastas de recurso (usando o nome de recurso fornecido pelo FeatureConvention, acima). Você pode saber mais sobre essa abordagem e baixar um exemplo de funcionamento do artigo do MSDN, [fatias de recurso para o ASP.NET MVC de núcleo](https://msdn.microsoft.com/magazine/mt763233.aspx).

### <a name="cross-cutting-concerns"></a>Interesses paralelos

Conforme os aplicativos crescem, ele se torna cada vez mais importante fatorar resolvem preocupações para eliminar a duplicação e manter a consistência. Alguns exemplos de resolvem preocupações em aplicativos do ASP.NET Core são autenticação, as regras de validação de modelo, o cache de saída e tratamento de erros, embora haja muitos outros. Núcleo do ASP.NET MVC [filtros](https://docs.microsoft.com/aspnet/core/mvc/controllers/filters) permitem executar código antes ou depois de algumas etapas no pipeline de processamento de solicitação. Por exemplo, um filtro pode executar antes e após a associação de modelo, antes e depois de uma ação ou antes e após o resultado de uma ação. Você também pode usar um filtro de autorização para controlar o acesso para o restante do pipeline. Figuras 7-2 mostra como solicitar fluxos de execução por meio de filtros, se configurado.

![A solicitação é processada por meio de Filtros de autorização, Filtros de recurso, Associação de modelos, Filtros de ação, Execução de ação e Conversão do resultado de ação, Filtros de exceção, Filtros de resultado e Execução de resultado. Na saída, a solicitação é processada somente por Filtros de resultado e Filtros de recurso antes de se tornar uma resposta enviada ao cliente.](./media/image7-2.png)

Figura 7-2 a execução da solicitação por meio de filtros e pipeline de solicitação.

Os filtros são normalmente implementados como atributos, para que você pode aplicá-los controladores ou ações. Quando adicionados dessa maneira, os filtros especificados na substituição de nível de ação ou compilação em filtros especificada no nível do controlador, que se substituem os filtros globais. Por exemplo, o \[rota\] atributo pode ser usado para criar rotas entre controladores e ações. Da mesma forma, autorização pode ser configurada no nível do controlador e, em seguida, substituída por ações individuais, como mostra o exemplo a seguir:

```csharp
[Authorize]
public class AccountController : Controller

{
    [AllowAnonymous]
    public async Task<IActionResult> Login() {}
    public async Task<IActionResult> ForgotPassword() {}
}
```

O primeiro método, o logon, usa o filtro de AllowAnonymous (atributo) para substituir o filtro de autorização definida no nível do controlador. A ação ForgotPassword (e qualquer outra ação na classe que não tem um atributo AllowAnonymous) exigirá uma solicitação autenticada.

Filtros podem ser usados para eliminar a duplicação na forma de tratamento de políticas para APIs de erros comuns. Por exemplo, uma política de API típica é retornar uma resposta não encontrado para solicitações referenciando chaves não existirem e uma resposta BadRequest se houver falha na validação do modelo. O exemplo a seguir demonstra essas duas políticas em ação:

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

Não permitir que os métodos de ação tornar-se atravancados com código condicional como este. Em vez disso, receber as políticas de filtros que podem ser aplicados de forma conforme necessário. Neste exemplo, a verificação de validação de modelo, que deve ocorrer a qualquer momento em que um comando é enviado para a API, pode ser substituída pelo seguinte atributo:

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

Da mesma forma, um filtro pode ser usado para verificar se um registro existe e retornar 404 antes que a ação é executada, eliminando a necessidade de executar essas verificações na ação. Depois de retirada convenções comuns e organizados sua solução para separar a lógica de negócios e código de infraestrutura de sua interface do usuário, seus métodos de ação do MVC devem ser extremamente dinâmico:

```csharp
// PUT api/authors/2/5
[HttpPut("{id}")]
[ValidateAuthorExists]
public async Task<IActionResult> Put(int id, [FromBody]Author author)
{
    await _authorRepository.UpdateAsync(author);
    return Ok();
}
```

Você pode ler mais sobre a implementação de filtros e baixar um exemplo de funcionamento do artigo do MSDN, [Real World ASP.NET Core MVC filtros](https://msdn.microsoft.com/magazine/mt767699.aspx).

> ### <a name="references--structuring-applications"></a>Referências – estruturar aplicativos
> - **Áreas**  
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/areas>
> - **MSDN-fatias de recurso para o ASP.NET Core MVC**
>  <https://msdn.microsoft.com/magazine/mt763233.aspx>
> - **Filtros**  
> <https://docs.microsoft.com/aspnet/core/mvc/controllers/filters>
> - **MSDN – filtros do mundo Real Core ASP.NET MVC**  
> <https://msdn.microsoft.com/magazine/mt767699.aspx>

## <a name="security"></a>Segurança

Protegendo aplicativos da web é um tópico grande, com muitas considerações. Em seu nível mais básico, a segurança envolve garantindo que você sabe que uma determinada solicitação é proveniente e, em seguida, verificar se essa solicitação só tem acesso a recursos que deveria. A autenticação é o processo de comparar as credenciais fornecidas com uma solicitação para aqueles em um repositório de dados confiável, para ver se a solicitação deve ser tratada como provenientes de uma entidade conhecida. Autorização é o processo de restringir o acesso a certos recursos com base na identidade do usuário. Uma terceira preocupação de segurança está protegendo as solicitações de espionagem por terceiros, para o qual você deve, pelo menos, [Certifique-se de que o SSL é usado pelo seu aplicativo](https://docs.microsoft.com/aspnet/core/security/enforcing-ssl).

### <a name="authentication"></a>Autenticação

Identidade do ASP.NET Core é um sistema de associação que você pode usar para oferecer suporte a funcionalidade de logon para o seu aplicativo. Ele tem suporte para contas de usuário local, bem como suporte ao provedor de logon externo de provedores de como Account da Microsoft, Twitter, Facebook, Google e muito mais. Além de identidade do ASP.NET Core, seu aplicativo pode usar a autenticação do windows ou um provedor de identidade de terceiros, como [Identity Server](https://github.com/IdentityServer/IdentityServer4).

Identidade do ASP.NET Core está incluída em novos modelos de projeto se a opção de contas de usuário Individual é selecionada. Esse modelo inclui suporte para registro, logon, logons externos, senhas esquecidas e funcionalidade adicional.

![](./media/image7-3.png)

Figura 7-3 Selecione contas individuais de usuário com identidade pré-configurado.

Suporte de identidade é configurado na inicialização, tanto em ConfigureServices e configurar:

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

É importante que UseIdentity aparecer antes de UseMvc no método configurar. Ao configurar a identidade em ConfigureServices, você observará uma chamada para AddDefaultTokenProviders. Isso não tem nada a ver com tokens que podem ser usadas para proteger as comunicações de web, mas em vez disso, se refere a provedores que criar avisos que podem ser enviados aos usuários por email para poderem ou SMS para confirmar sua identidade.

Você pode aprender mais sobre [Configurando a autenticação de dois fatores](https://docs.microsoft.com/aspnet/core/security/authentication/2fa) e [Habilitando provedores de logon externo](https://docs.microsoft.com/aspnet/core/security/authentication/social/) da documentação oficial do ASP.NET Core.

### <a name="authorization"></a>Autorização

A forma mais simples de autorização envolve restringir o acesso a usuários anônimos. Isso pode ser feito simplesmente aplicando o \[autorizar\] atributo determinados controladores ou ações. Se as funções estiverem sendo usadas, o atributo pode ser estendido adicional para restringir o acesso a usuários que pertencem a determinadas funções, conforme mostrado:

```csharp
[Authorize(Roles = "HRManager,Finance")]
public class SalaryController : Controller
{

}
```

Nesse caso, os usuários que pertencem as funções HRManager ou finanças (ou ambos) teria acesso para o SalaryController. Para exigir que um usuário pertencer a várias funções (não apenas um dos vários), você pode aplicar o atributo várias vezes, especificando uma função necessária cada vez.

Especificar determinados conjuntos de funções como cadeias de caracteres em muitos diferentes controladores e ações podem levar a repetição indesejável. Você pode configurar políticas de autorização, que encapsula as regras de autorização, e, em seguida, especifique a política em vez de funções individuais ao aplicar o \[autorizar\] atributo:

```csharp
[Authorize(Policy = "CanViewPrivateReport")]
public IActionResult ExecutiveSalaryReport()
{
    return View();
}
```

Usando políticas dessa forma, você pode separar os tipos de ações sejam restritas a funções específicas ou regras que se aplicam a ele. Posteriormente, se você criar uma nova função que precisa ter acesso a determinados recursos, você pode simplesmente atualizar uma política, ao invés de atualizar cada lista de funções em cada \[autorizar\] atributo.

#### <a name="claims"></a>declarações

Declarações são pares de valor de nome que representam as propriedades de um usuário autenticado. Por exemplo, você pode armazenar o número de usuários de funcionário como uma declaração. Declarações, em seguida, podem ser usadas como parte de diretivas de autorização. Você pode criar uma diretiva chamada "EmployeeOnly" que requer a existência de uma declaração chamada "EmployeeNumber", conforme mostrado neste exemplo:

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

Essa política pode ser usada com a \[autorizar\] atributo para proteger qualquer controlador de e/ou ação, conforme descrito acima.

#### <a name="securing-web-apis"></a>Proteger APIs da Web

A maioria das APIs de web devem implementar um sistema de autenticação baseada em token. Autenticação de token é projetado para ser dimensionável e sem monitoração de estado. Em um sistema de autenticação baseada em token, o cliente deve primeiro ser autenticado com o provedor de autenticação. Se for bem-sucedido, o cliente é emitido um token, que é simplesmente uma criptograficamente significativa cadeia de caracteres. Quando o cliente precisa, em seguida, emitir uma solicitação para uma API, ele adiciona esse token como um cabeçalho na solicitação. O servidor, em seguida, valida o token encontrado no cabeçalho da solicitação antes de concluir a solicitação. Figura 7-4 demonstra esse processo.

![TokenAuth](./media/image7-4.png)

**Figura 7-4.** Autenticação baseada em token para APIs da Web.

> ### <a name="references--security"></a>Referências – segurança
> - **Visão geral de documentos de segurança**  
> https://docs.microsoft.com/aspnet/core/security/
> - **Imposição de SSL em um aplicativo do ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/security/enforcing-ssl>
> - **Introdução ao Identity**  
> <https://docs.microsoft.com/aspnet/core/security/authentication/identity>
> - **Introdução à autorização**  
> <https://docs.microsoft.com/aspnet/core/security/authorization/introduction>
> - **Autenticação e autorização para aplicativos de API no serviço de aplicativo do Azure**  
> <https://docs.microsoft.com/azure/app-service-api/app-service-api-authentication>

## <a name="client-communication"></a>Comunicação do cliente

Além de fornecer páginas e responder às solicitações de dados por meio de APIs da web, os aplicativos do ASP.NET Core podem se comunicar diretamente com os clientes conectados. A comunicação de saída pode usar uma variedade de tecnologias de transporte, o mais comum sendo WebSocket. O SignalR do ASP.NET Core é uma biblioteca que torna simples para o tipo de funcionalidade de comunicação de servidor-para-cliente em tempo real para seus aplicativos. SignalR dá suporte a uma variedade de tecnologias de transporte, incluindo o WebSocket e resume longe muitos dos detalhes de implementação do desenvolvedor.

O SignalR do ASP.NET Core está em desenvolvimento e estarão disponível na próxima versão do ASP.NET Core. No entanto, outros [Abrir fonte WebSockets bibliotecas](https://github.com/radu-matei/websocket-manager) estão disponíveis no momento.

Comunicação de cliente em tempo real, se usar WebSockets diretamente ou outras técnicas são úteis em uma variedade de cenários de aplicativo. Eis alguns exemplos:

-   Aplicativos de sala de bate-papo ao vivo

-   Monitoramento de aplicativos

-   Atualizações de andamento do trabalho

-   Notificações

-   Aplicativos de formulários interativos

Ao criar a comunicação do cliente em seus aplicativos, normalmente há dois componentes:

-   Gerenciador de conexão do servidor (SignalR Hub, WebSocketManager WebSocketHandler)

-   Biblioteca de cliente

Os clientes não estão limitados aos navegadores – aplicativos móveis, aplicativos de console, e outros aplicativos nativos também podem se comunicar usando SignalR/WebSocket. O programa simple a seguir exibe todo o conteúdo enviado para um aplicativo de chat no console, como parte de um aplicativo de exemplo WebSocketManager:

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
```

Considere a possibilidade de ocorrer de maneiras em que seus aplicativos se comunicam diretamente com os aplicativos cliente em considere se comunicação em tempo real podem melhorar o usuário do aplicativo.

> ### <a name="references--client-communication"></a>Referências a comunicação do cliente
> - **SignalR do ASP.NET Core**  
> <https://github.com/aspnet/SignalR>
> - **Gerenciador de WebSocket**  
> https://github.com/radu-matei/websocket-manager

## <a name="domain-driven-design--should-you-apply-it"></a>Design – controlado por domínio deve aplicá-lo?

Design orientado a domínio (DDD) é uma abordagem agile para criação de um software que enfatiza a se concentrar no *domínio corporativo*. Coloca uma forte ênfase em comunicação e interação com expert(s) de domínio de negócios que pode estar relacionada a desenvolvedores de como funciona o sistema do mundo real. Por exemplo, se você estiver criando um sistema que manipula a negociação de ações, o especialista de domínio pode ser um agente de estoque experiente. DDD foi projetado para resolver problemas comerciais grandes e complexos e geralmente não é adequado para aplicativos menores e mais simples, como o investimento em conhecimento e modelagem de domínio não é a pena.

Ao criar o software a seguir uma abordagem DDD, sua equipe (incluindo participantes não técnicos e colaboradores) deve desenvolver uma *idioma onipresente* para o problema de espaço. Ou seja, a mesma terminologia deve ser usada para qualquer estruturas que podem existir para persistir o conceito (por exemplo, tabelas de banco de dados), o equivalente de software e o conceito do mundo real que está sendo modelado. Portanto, os conceitos descritos no idioma onipresente devem formam a base para o *modelo de domínio*.

O modelo de domínio é composto por objetos que interagem entre si para representar o comportamento do sistema. Esses objetos podem se enquadram nas categorias a seguir:

-   [Entidades](http://deviq.com/entity/), que representam objetos com um thread de identidade. Entidades são normalmente armazenadas no persistência com uma chave pela qual elas posteriormente podem ser recuperadas.

-   [Agregações](http://deviq.com/aggregate-pattern/), que representam grupos de objetos que devem ser persistentes como uma unidade.

-   [Objetos de valor](http://deviq.com/value-object/), que representam os conceitos que podem ser comparados com base na soma de seus valores de propriedade. Por exemplo, DateRange consiste em uma data de início e término.

-   [Eventos de domínio](https://martinfowler.com/eaaDev/DomainEvent.html), que representam coisas acontecendo dentro do sistema que são de interesse de outras partes do sistema.

Observe que um modelo de domínio DDD deve encapsular comportamento complexo dentro do modelo. Entidades, em particular, não devem apenas ser coleções de propriedades. Quando o modelo de domínio não tem o comportamento e representa apenas o estado do sistema, ele é chamado de um [anêmica modelo](http://deviq.com/anemic-model/), que é indesejável no DDD.

Além desses tipos de modelo, DDD normalmente emprega uma variedade de padrões:

-   [Repositório](http://deviq.com/repository-pattern/), para abstraindo os detalhes de persistência.

-   [Fábrica](https://en.wikipedia.org/wiki/Factory_method_pattern), para encapsular a criação de objetos complexos.

-   Eventos de domínio, para desacoplar o comportamento dependente de disparar o comportamento.

-   [Serviços de](http://gorodinski.com/blog/2012/04/14/services-in-domain-driven-design-ddd/), para encapsular comportamento complexo e/ou detalhes de implementação de infraestrutura.

-   [Comando](https://en.wikipedia.org/wiki/Command_pattern), para desacoplar emitir comandos e executar o comando em si.

-   [Especificação de](http://deviq.com/specification-pattern/), para encapsular os detalhes da consulta.

DDD também recomenda o uso da arquitetura de limpar discutida anteriormente, permitindo acoplamento, o encapsulamento e o código que facilmente possa ser verificado usando testes de unidade.

### <a name="when-should-you-apply-ddd"></a>Quando você aplica DDD

DDD é adequado para aplicativos grandes com complexidade significativa de negócios (não apenas técnica). O aplicativo deve exigir o conhecimento de especialistas de domínio. O modelo de domínio, que representa as regras de negócio e interações além de simplesmente armazenar e recuperar o estado atual de vários registros de armazenamentos de dados deve ser o comportamento significativo.

### <a name="when-shouldnt-you-apply-ddd"></a>Quando você não deve aplicar DDD

DDD envolve os investimentos em comunicação que não pode ser garantida menor aplicativos ou aplicativos que são essencialmente apenas CRUD (criar/ler/atualizar/excluir), arquitetura e modelagem. Se você optar por abordagem de seu aplicativo a seguir DDD, mas encontrar o domínio tiver um modelo anêmica com nenhum comportamento, você precisará Repense na sua abordagem. O seu aplicativo talvez não seja necessário DDD ou você pode precisar de assistência refatoração seu aplicativo para encapsular a lógica de negócios no modelo de domínio, em vez de na sua interface de usuário ou banco de dados.

Uma abordagem híbrida seria usar DDD somente para as áreas de transacionais ou mais complexas do aplicativo, mas não para CRUD mais simples ou somente leitura partes do aplicativo. Por exemplo, você não precisa ter as restrições de uma agregação se você estiver consultando dados para exibir um relatório ou para visualizar os dados para um painel. É aceitável perfeitamente ter um modelo separado mais simples de leitura para esses requisitos.

> ### <a name="references--domain-driven-design"></a>Referências – Design controlado por domínio
> - **DDD em inglês (StackOverflow resposta)**  
> <https://stackoverflow.com/questions/1222392/can-someone-explain-domain-driven-design-ddd-in-plain-english-please/1222488#1222488>

## <a name="deployment"></a>Implantação

Há algumas etapas envolvidas no processo de implantação de seu aplicativo ASP.NET Core, independentemente de onde ele será hospedado. A primeira etapa é publicar o aplicativo, que pode ser feito usando o dotnet publicar o comando CLI. Isso irá compilar o aplicativo e colocar todos os arquivos necessários para executar o aplicativo em uma pasta designada. Quando você implanta no Visual Studio, esta etapa é executada automaticamente para você. A pasta de publicação contém arquivos .exe e. dll para o aplicativo e suas dependências. Um aplicativo autocontido também incluirá uma versão do tempo de execução .NET. Aplicativos do ASP.NET Core também incluirá os arquivos de configuração, ativos de cliente estático e exibições do MVC.

Aplicativos do ASP.NET Core são aplicativos de console que devem ser iniciados quando o servidor é inicializado e reiniciado quando falhas de aplicativo (ou servidor). Um Gerenciador de processo pode ser usado para automatizar esse processo. Os gerenciadores de processo mais comuns para o ASP.NET Core são Nginx e Apache no Linux e o IIS ou o serviço do Windows no Windows.

Além de um Gerenciador de processo, os aplicativos ASP.NET Core hospedados no servidor web Kestrel devem usar um servidor de proxy reverso. Um servidor proxy reverso recebe solicitações HTTP da internet e encaminha-os para Kestrel após alguns tratamentos preliminar. Servidores de proxy reverso fornecem uma camada de segurança para o aplicativo e são necessários para implantações de borda (expostas ao tráfego da Internet). Kestrel é relativamente novo e ainda não oferece proteção contra certos ataques. Kestrel também não dá suporte a hospedagem de vários aplicativos na mesma porta, portanto técnicas, como cabeçalhos de host não podem ser usadas com ele para habilitar a hospedagem de vários aplicativos na mesma porta e endereço IP.

![Kestrel para Internet](./media/image7-5.png)

Figura 7-5 ASP.NET hospedado no Kestrel atrás de um servidor proxy reverso

É outro cenário em que um proxy reverso pode ser útil proteger vários aplicativos usando HTTPS/SSL. Nesse caso, somente o proxy inverso precisa ter o SSL configurado. Comunicação entre o servidor proxy reverso e Kestrel pode ocorrer por HTTP, como mostrado na Figura 7-6.

![](./media/image7-6.png)

Figura 7-6 ASP.NET hospedado por trás de um servidor proxy reverso protegido por HTTPS

É uma abordagem de cada vez mais popular hospedar seu aplicativo ASP.NET Core em um contêiner do Docker, que pode ser hospedado localmente ou implantado no Azure para hospedar baseado em nuvem. O contêiner do Docker pode conter seu código de aplicativo em execução no Kestrel e seria implantado em um servidor de proxy reverso, como mostrado acima.

Se você estiver hospedando seu aplicativo no Azure, você pode usar o Gateway de aplicativo do Microsoft Azure como um dispositivo virtual dedicado para fornecer vários serviços. Além de atuar como um proxy reverso para aplicativos individuais, o Application Gateway também pode oferecer os seguintes recursos:

-   Balanceamento de carga HTTP

-   Descarregamento SSL (SSL apenas para a Internet)

-   SSL de ponta a ponta

-   Roteamento de vários locais (consolidar até 20 sites em um único Gateway de aplicativo)

-   Firewall do aplicativo Web

-   Suporte para WebSocket

-   Diagnóstico avançado

*Saiba mais sobre as opções de implantação do Azure no capítulo 10.*

> ### <a name="references--deployment"></a>Referências – implantação
> - **Visão geral da implantação e hospedagem**  
> <https://docs.microsoft.com/aspnet/core/publishing/>
> - **Quando usar Kestrel com um proxy reverso**  
> <https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel#when-to-use-kestrel-with-a-reverse-proxy>
> - **Hospedar aplicativos do ASP.NET Core no Docker**  
> <https://docs.microsoft.com/aspnet/core/publishing/docker>
> - **Introdução ao Gateway de aplicativo do Azure**  
> <https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction>

>[!div class="step-by-step"]
[Anterior] (comum-cliente-lado-web-technologies.md) [Avançar] (work-with-data-in-asp-net-core-apps.md)
