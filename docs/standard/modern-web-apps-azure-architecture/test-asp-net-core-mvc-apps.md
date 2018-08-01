---
title: Testar aplicativos ASP.NET Core MVC
description: Projetar aplicativos Web modernos com o ASP.NET Core e o Azure | Testar aplicativos ASP.NET Core MVC
author: ardalis
ms.author: wiwagn
ms.date: 06/28/2018
ms.openlocfilehash: b6c881a445f5848829ab5ccc6ce8547a390d89f3
ms.sourcegitcommit: 4c158beee818c408d45a9609bfc06f209a523e22
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37404613"
---
# <a name="test-aspnet-core-mvc-apps"></a>Testar aplicativos ASP.NET Core MVC

> *"Se você não gostar de realizar o teste de unidade em seu produto, provavelmente, seus clientes não vão gostar de testá-lo também."*
 > \_ – Anônimo –

Um software de qualquer complexidade pode falhar de maneiras inesperadas em resposta a alterações. Portanto, depois de fazer alterações, é necessário realizar um teste em todos os aplicativos, exceto os mais triviais (ou menos críticos). O teste manual é a maneira mais lenta, menos confiável e mais cara de testar um software. Infelizmente, se os aplicativos não forem projetados para serem testáveis, esse poderá ser o único meio disponível. Os aplicativos codificados de acordo com os princípios de arquitetura apresentados no capítulo X devem podem ser submetidos a um teste de unidade, além disso os aplicativos ASP.NET Core são compatíveis com testes funcionais e de integração automatizados.

## <a name="kinds-of-automated-tests"></a>Tipos de testes automatizados

Há muitos tipos de testes automatizados para aplicativos de software. O teste mais simples de nível mais baixo é o teste de unidade. Em um nível ligeiramente superior, há testes de integração e testes funcionais. Outros tipos de testes, como testes de interface do usuário, testes de carga, testes de estresse e smoke tests, estão além do escopo deste documento.

### <a name="unit-tests"></a>Testes de unidade

Um teste de unidade testa uma única parte da lógica do aplicativo. Ainda podemos descrevê-lo listando algumas das coisas que ele não é. Um teste de unidade não testa como o código funciona com as dependências ou a infraestrutura – é para isso que servem os testes de integração. Um teste de unidade não testa a estrutura na qual o código foi escrito – você deve pressupor que ela funciona ou, se achar que não, registre um bug e codifique uma solução alternativa. Um teste de unidade é executado completamente na memória e no processo. Ele não se comunica com o sistema de arquivos, a rede ou um banco de dados. Os testes de unidade devem testar apenas o código.

Os testes de unidade, devido ao fato de testarem apenas uma única unidade do código, sem dependências externas, devem ser executados muito rapidamente. Portanto, você deve conseguir executar conjuntos de testes de centenas de testes de unidade em alguns segundos. Execute-os com frequência, de preferência, antes de cada push para um repositório de controle do código-fonte compartilhado e, certamente, a cada build automatizado no servidor de build.

### <a name="integration-tests"></a>Testes de integração

Embora seja uma boa ideia encapsular o código que interage com a infraestrutura, como bancos de dados e sistemas de arquivos, você ainda terá uma parte do código e, provavelmente, desejará testá-lo. Além disso, você deve verificar se as camadas do código interagem conforme esperado quando as dependências do aplicativo são totalmente resolvidas. Essa é a responsabilidade dos testes de integração. Os testes de integração tendem a ser mais lentos e mais difíceis de serem configurados do que os testes de unidade, porque geralmente dependem de infraestrutura e dependências externas. Portanto, você deve evitar testar coisas que podem ser testadas com testes de unidade em testes de integração. Se puder testar determinado cenário com um teste de unidade, você deverá testá-lo com um teste de unidade. Caso contrário, considere o uso de um teste de integração.

Os testes de integração costumam ter procedimentos de instalação e de desinstalação mais complexos em comparação com os testes de unidade. Por exemplo, um teste de integração feito em um banco de dados real precisará de uma maneira de retornar o banco de dados para um estado conhecido antes de cada execução de teste. Conforme novos testes forem adicionados e o esquema de banco de dados de produção evoluir, esses scripts de teste tenderão a aumentar em tamanho e complexidade. Em muitos sistemas grandes, não é prático executar conjuntos completos de testes de integração em estações de trabalho do desenvolvedor antes de fazer check-in das alterações no controle do código-fonte compartilhado. Nesses casos, os testes de integração podem ser executados em um servidor de build.

A classe de implementação LocalFileImageService implementa a lógica para buscar e retornar os bytes de um arquivo de imagem de uma pasta específica, considerando uma ID:

```csharp
public class LocalFileImageService : IImageService
{
    private readonly IHostingEnvironment _env;
    public LocalFileImageService(IHostingEnvironment env)
    {
        _env = env;
    }
    public byte[] GetImageBytesById(int id)
    {
        try
        {
            var contentRoot = _env.ContentRootPath + "//Pics";
            var path = Path.Combine(contentRoot, id + ".png");
            return File.ReadAllBytes(path);
        }
        catch (FileNotFoundException ex)
        {
            throw new CatalogImageMissingException(ex);
        }
    }
}
```

### <a name="functional-tests"></a>Testes funcionais

Os testes de integração são escritos da perspectiva do desenvolvedor, para verificar se alguns componentes do sistema funcionam corretamente juntos. Os testes funcionais são escritos da perspectiva do usuário e verificam a correção do sistema com base em seus requisitos. O trecho a seguir oferece uma analogia útil de como considerar os testes funcionais, em comparação com os testes de unidade:

> "Muitas vezes, o desenvolvimento de um sistema é comparado à construção de uma casa. Embora essa analogia não seja muito correta, podemos estendê-la para compreender a diferença entre os testes de unidade e os testes funcionais. O teste de unidade se assemelha a um inspetor de construção visitando o canteiro de obras de uma casa. Ele está concentrado nos vários sistemas internos da casa, na base, na estrutura, na parte elétrica, no encanamento e assim por diante. Ele garante (testa) que as partes da casa funcionarão corretamente e com segurança, ou seja, seguirão o código de construção. Os testes funcionais, neste cenário, se assemelham ao proprietário da casa visitando esse mesmo canteiro de obras. Ele pressupõe que os sistemas internos se comportarão corretamente e que o inspetor de construção está realizando sua tarefa. O proprietário da casa está voltado para a ideia de como será morar nessa casa. Ele está preocupado com a aparência da casa, se os vários quartos têm um tamanho confortável, se a casa atende às necessidades da família, se as janelas estão em um bom lugar para capturar o sol da manhã. O proprietário da casa está realizando testes funcionais na casa. Ele tem a perspectiva do usuário. O inspetor de construção está realizando testes de unidade na casa. Ele tem a perspectiva do construtor."

Fonte: [Teste de unidade versus testes funcionais](https://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)

Gosto de dizer que "como desenvolvedores, falhamos de duas maneiras: criamos a coisa da maneira errada ou criamos a coisa errada". Os testes de unidade garantem que você está criando a coisa da maneira certa; os testes funcionais garantem que você está criando a coisa certa.

Como os testes funcionais operam no nível do sistema, eles podem exigir um certo grau de automação da interface do usuário. Assim como os testes de integração, elas geralmente funcionam com algum tipo de infraestrutura de teste também. Isso faz com que eles fiquem mais lentos e mais frágeis do que os testes de unidade e de integração. Você deve ter somente a quantidade de testes funcionais de que precisa para ter certeza de que o sistema está se comportando conforme esperado pelos usuários.

### <a name="testing-pyramid"></a>Pirâmide de testes

Martin Fowler escreveu sobre a pirâmide de testes, cujo exemplo é mostrado na Figura 9-1.

![](./media/image9-1.png)

Figura 9-1 Pirâmide de testes

As diferentes camadas da pirâmide e seus tamanhos relativos representam tipos diferentes de testes e quantos você deve gravar para seu aplicativo. Como você pode ver, a recomendação é ter uma grande base de testes de unidade, apoiada por uma camada menor de testes de integração, com uma camada ainda menor de testes funcionais. O ideal é que cada camada tenha somente testes que não podem ser realizados de forma adequada em uma camada inferior. Lembre-se da pirâmide de testes quando estiver tentando decidir qual tipo de teste é necessário para um cenário específico.

### <a name="what-to-test"></a>O que testar

Um problema comum para os desenvolvedores que não têm experiência com a criação de testes automatizados é decidir o que testar. Um bom ponto de partida é testar a lógica condicional do teste. Sempre que você tiver um método com um comportamento que é alterado de acordo com uma instrução condicional (if-else, alternância, etc.), você deverá pensar em, pelo menos, dois testes que confirmem esse comportamento correto em determinadas condições. Se o código apresentar condições de erro, será melhor gravar, pelo menos, um teste para o "caminho certo" pelo código (sem erros) e, pelo menos, um teste para o "caminho errado" (com erros ou resultados atípicos) para confirmar que o aplicativo se comporta conforme esperado em caso de erros. Por fim, tente se concentrar no teste de coisas que podem falhar, em vez de se concentrar em métricas como cobertura de código. Em geral, mais cobertura de código é melhor do que menos. No entanto, é melhor utilizar o tempo criando mais alguns testes de um método muito complexo e comercialmente crítico do que criando testes para propriedades automáticas, apenas para melhorar as métricas de cobertura de código de teste.

## <a name="organizing-test-projects"></a>Organizando projetos de teste

Os projetos de teste podem ser organizados da maneira mais adequada à sua situação. É uma boa ideia separar os testes por tipo (teste de unidade, teste de integração) e pelo que eles estão testando (por projeto, por namespace). Indicar se essa separação consiste em pastas dentro de um único projeto de teste ou de vários projetos de teste é uma decisão de design. Um projeto é o mais simples, mas para projetos grandes com muitos testes ou para executar diferentes conjuntos de testes com mais facilidade, talvez você deseje ter vários projetos de teste diferentes. Muitas equipes organizam projetos de teste com base no projeto que estão testando, o que, para aplicativos com mais de alguns projetos, pode resultar em um grande número de projetos de teste, especialmente se você ainda divide-os de acordo com o tipo de testes existente em cada projeto. Uma abordagem de meio-termo é ter um projeto por tipo de teste, por aplicativo, com pastas dentro dos projetos de teste para indicar o projeto (e a classe) que está sendo testado.

Uma abordagem comum é organizar os projetos de aplicativo em uma pasta 'src' e os projetos de teste do aplicativo em uma pasta 'tests' paralela. Crie pastas de solução correspondentes no Visual Studio se achar esta organização útil.

![](./media/image9-2.png)

Figura 9-2 Organização de testes na solução

Você pode usar qualquer estrutura de teste que preferir. A estrutura xUnit funciona bem e é nela em que todos os testes do ASP.NET Core e do EF Core são criados. Você pode adicionar um projeto de teste do xUnit no Visual Studio usando o modelo mostrado na Figura 9-3 ou por meio da CLI usando o comando dotnet new xunit.

![](./media/image9-3.png)

Figura 9-3 Adicionar um projeto de teste do xUnit no Visual Studio

### <a name="test-naming"></a>Nomenclatura de testes

Você deve nomear os testes de maneira consistente, com nomes que indicam o que cada teste faz. Uma abordagem na qual tive grande sucesso é nomear as classes de teste de acordo com a classe e o método que elas estão testando. Isso resulta em muitas classes de teste pequenas, mas deixa extremamente claro pelo que é responsável cada teste. Com o nome da classe de teste configurado para identificar a classe e o método a serem testados, o nome do método de teste pode ser usado para especificar o comportamento que está sendo testado. Isso deve incluir o comportamento esperado e as entradas ou suposições que devem gerar esse comportamento. Alguns nomes de teste de exemplo:

- `CatalogControllerGetImage.CallsImageServiceWithId`

- `CatalogControllerGetImage.LogsWarningGivenImageMissingException`

- `CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess`

- `CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException`

Uma variação dessa abordagem termina o nome de cada classe de teste com "Should" e modifica ligeiramente os tempos verbais:

- `CatalogControllerGetImage`**Should**`.`**Call**`ImageServiceWithId`

- `CatalogControllerGetImage`**Should**`.`**Log**`WarningGivenImageMissingException`

Algumas equipes consideram a segunda abordagem de nomenclatura mais clara, embora um pouco mais detalhada. De qualquer forma, tente usar uma convenção de nomenclatura que fornece informações sobre o comportamento de teste, de modo que quando um ou mais testes falharem, seja óbvio descobrir, com base nos nomes, quais casos falharam. Evite nomear os testes de modo vago, como ControllerTests.Test1, pois essa nomenclatura não oferece nenhum valor quando você vê esses nomes em resultados de teste.

Se você segue uma convenção de nomenclatura como a mostrada acima, que produz muitas classes de teste pequenas, é uma boa ideia organizar ainda mais os testes usando pastas e namespaces. A Figura 9-4 mostra uma abordagem para organizar os testes por pasta dentro de vários projetos de teste.

![](./media/image9-4.png)

**Figura 9-4.** Organizando classes de teste por pasta com base na classe que está sendo testada.

É claro que, se uma classe de aplicativo específica tiver muitos métodos que estão sendo testados (e, portanto, muitas classes de teste), talvez faça sentido colocá-los em uma pasta correspondente à classe de aplicativo. Essa organização não é diferente da forma como você pode organizar arquivos em pastas em outro lugar. Caso você tenha mais de três ou quatro arquivos relacionados em uma pasta que contém muitos outros arquivos, geralmente, é útil movê-los para sua própria subpasta.

## <a name="unit-testing-aspnet-core-apps"></a>Realizando teste de unidade em aplicativos ASP.NET Core

Em um aplicativo ASP.NET Core bem projetado, a maior parte da complexidade e da lógica de negócios será encapsulada em entidades de negócios e uma variedade de serviços. O aplicativo ASP.NET Core MVC em si, com seus controladores, filtros, modelos de exibição e exibições, deve exigir muito poucos testes de unidade. Grande parte da funcionalidade de determinada ação se encontra fora do próprio método de ação. O teste para saber se o roteamento funciona corretamente, ou o tratamento de erro global, não pode ser feito efetivamente com um teste de unidade. Da mesma forma, os filtros, incluindo filtros de validação de modelo e autenticação e autorização, não podem ser testados com testes de unidade. Sem essas fontes de comportamento, a maioria dos métodos de ação deve ser insignificantemente pequena, com a delegação da maior parte de seu trabalho para serviços que podem ser testados sem depender do controlador que os usa.

Às vezes, você precisará refatorar o código para submetê-lo ao teste de unidade. Com frequência, isso envolve a identificação de abstrações e o uso da injeção de dependência para acessar a abstração no código que você deseja testar, em vez da codificação direta na infraestrutura. Por exemplo, considere este método de ação simples para a exibição de imagens:

```csharp
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    var contentRoot = _env.ContentRootPath + "//Pics";
    var path = Path.Combine(contentRoot, id + ".png");
    Byte[] b = System.IO.File.ReadAllBytes(path);
    return File(b, "image/png");
}
```

Submeter esse método ao teste de unidade é dificultado por sua dependência direta de System.IO.File, que ele usa para ler o sistema de arquivos. Você pode testar esse comportamento para garantir que ele funciona conforme esperado, mas fazer isso com arquivos reais é um teste de integração. Vale a pena observar que não é possível testar a rota desse método – você verá como fazer isso com um teste funcional em breve.

Se você não pode realizar o teste de unidade no comportamento do sistema de arquivos diretamente e não pode testar a rota, o que há para testar? Bem, depois de fazer a refatoração para possibilitar o teste de unidade, talvez você descubra alguns casos de teste e um comportamento ausente, como o tratamento de erro. O que o método faz quando um arquivo não é encontrado? O que ele deve fazer? Neste exemplo, o método refatorado tem esta aparência:

```csharp
[HttpGet("[controller]/pic/{id}")\]
public IActionResult GetImage(int id)
{
    byte[] imageBytes;
    try
    {
        imageBytes = _imageService.GetImageBytesById(id);
    }
    catch (CatalogImageMissingException ex)
    {
        _logger.LogWarning($"No image found for id: {id}");
        return NotFound();
    }
    return File(imageBytes, "image/png");
}
```

O \_agente e o \_imageService são injetados como dependências. Agora você pode testar se a mesma ID passada para o método de ação é passada para o \_imageService, e se os bytes resultantes são retornados como parte do FileResult. Você também pode testar se o log de erros ocorre conforme esperado e se um resultado NotFound é retornado caso a imagem esteja ausente, supondo que esse seja um comportamento importante do aplicativo (ou seja, não apenas um código temporário adicionado pelo desenvolvedor para diagnosticar um problema). A lógica real do arquivo foi movida para um serviço de implementação separado e foi aumentada para retornar uma exceção específica do aplicativo para o caso de um arquivo ausente. Você pode testar essa implementação de forma independente, usando um teste de integração.

## <a name="integration-testing-aspnet-core-apps"></a>Realizando testes de integração em aplicativos ASP.NET Core

Para testar se um LocalFileImageService funciona corretamente usando um teste de integração, você precisa criar um arquivo de imagem de teste conhecido e verificar se o serviço o retorna fornecendo uma entrada específica. Você deve ter cuidado para não usar objetos fictícios no comportamento que você realmente deseja testar (nesse caso, a leitura do sistema de arquivos). No entanto, os objetos fictícios ainda podem ser úteis para configurar testes de integração. Nesse caso, você pode simular o IHostingEnvironment, de modo que seu ContentRootPath aponte para a pasta que você pretende usar para a imagem de teste. A classe de teste de integração funcional completa é mostrada aqui:

```csharp
public class LocalFileImageServiceGetImageBytesById
{
    private byte[] _testBytes = new byte[] { 0x01, 0x02, 0x03 };
    private readonly Mock<IHostingEnvironment> _mockEnvironment = new Mock<IHostingEnvironment>();
    private int _testImageId = 123;
    private string _testFileName = "123.png";

    public LocalFileImageServiceGetImageBytesById()
    {
        // create folder if necessary
        Directory.CreateDirectory(Path.Combine(GetFileDirectory(), "Pics"));
        string filePath = GetFilePath(_testFileName);
        System.IO.File.WriteAllBytes(filePath, _testBytes);
        _mockEnvironment.SetupGet<string>(m => m.ContentRootPath).Returns(GetFileDirectory());
    }

    private string GetFilePath(string fileName)
    {
        return Path.Combine(GetFileDirectory(), "Pics", fileName);
        }
            private string GetFileDirectory()
        {
        var location = System.Reflection.Assembly.GetEntryAssembly().Location;
        return Path.GetDirectoryName(location);
    }

    [Fact]
    public void ReturnsFileContentResultGivenValidId()
    {
        var fileService = new LocalFileImageService(_mockEnvironment.Object);
        var result = fileService.GetImageBytesById(_testImageId);
        Assert.Equal(_testBytes, result);
    }
}
```

> [!NOTE]
> O teste em si é muito simples – a maior parte do código é necessária para configurar o sistema e criar a infraestrutura de teste (nesse caso, um arquivo real a ser lido do disco). Isso é típico dos testes de integração, que geralmente exigem um trabalho de instalação mais complexo do que os testes de unidade.

## <a name="functional-testing-aspnet-core-apps"></a>Realizando teste funcional em aplicativos ASP.NET Core

Para aplicativos ASP.NET Core, a classe TestServer facilita muito a gravação de testes funcionais. É possível configurar um TestServer usando um WebHostBuilder diretamente (assim como você normalmente para seu aplicativo) ou com o tipo WebApplicationFactory (disponível no 2.1). Você deve tentar corresponder o host de teste ao host de produção ao máximo possível, para que seus testes exerçam um comportamento semelhante ao que o aplicativo exercerá em produção. A classe WebApplicationFactory é útil para a configuração de ContentRoot do TestServer, que é usado pelo ASP.NET Core para localizar recursos estáticos, como Exibições.

Você pode criar testes funcionais simples criando uma classe de teste que implementa IClassFixture<WebApplicationFactory<TEntry>> em que TEntry é a classe de inicialização do aplicativo Web. Com isso em vigor, o acessório de teste pode criar um cliente usando o método CreateClient do alocador:

```cs
public class BasicWebTests : IClassFixture<WebApplicationFactory<Startup>>
{
    protected readonly HttpClient _client;

    public BaseWebTest(WebApplicationFactory<Startup> factory)
    {
        _client = factory.CreateClient();
    }

    // write tests that use _client
}
```

Geralmente é necessário executar alguma configuração adicional do site antes da execução de cada teste, como configurar o aplicativo para usar um armazenamento de dados na memória e, em seguida, propagar o aplicativo com os dados de teste. Para fazer isso, você deve criar sua própria subclasse de WebApplicationFactory<TEntry> e substituir seu método ConfigureWebHost. O exemplo a seguir é do projeto FunctionalTests de eShopOnWeb e é usado como parte dos testes no aplicativo Web principal.

```cs
using Infrastructure.Data;
using Microsoft.AspNetCore.Hosting;
using Microsoft.AspNetCore.Mvc.Testing;
using Microsoft.eShopWeb;
using Microsoft.Extensions.DependencyInjection;
using Microsoft.Extensions.Logging;
using System;
using Microsoft.EntityFrameworkCore;
using Infrastructure.Identity;

namespace FunctionalTests.WebRazorPages
{
    public class CustomWebRazorPagesApplicationFactory<TStartup>
    : WebApplicationFactory<Startup>
    {
        protected override void ConfigureWebHost(IWebHostBuilder builder)
        {
            builder.ConfigureServices(services =>
            {
                // Create a new service provider.
                var serviceProvider = new ServiceCollection()
                    .AddEntityFrameworkInMemoryDatabase()
                    .BuildServiceProvider();

                // Add a database context (ApplicationDbContext) using an in-memory
                // database for testing.
                services.AddDbContext<CatalogContext>(options =>
                {
                    options.UseInMemoryDatabase("InMemoryDbForTesting");
                    options.UseInternalServiceProvider(serviceProvider);
                });

                services.AddDbContext<AppIdentityDbContext>(options =>
                {
                    options.UseInMemoryDatabase("Identity");
                    options.UseInternalServiceProvider(serviceProvider);
                });

                // Build the service provider.
                var sp = services.BuildServiceProvider();

                // Create a scope to obtain a reference to the database
                // context (ApplicationDbContext).
                using (var scope = sp.CreateScope())
                {
                    var scopedServices = scope.ServiceProvider;
                    var db = scopedServices.GetRequiredService<CatalogContext>();
                    var loggerFactory = scopedServices.GetRequiredService<ILoggerFactory>();

                    var logger = scopedServices
                        .GetRequiredService<ILogger<CustomWebRazorPagesApplicationFactory<TStartup>>>();

                    // Ensure the database is created.
                    db.Database.EnsureCreated();

                    try
                    {
                        // Seed the database with test data.
                        CatalogContextSeed.SeedAsync(db, loggerFactory).Wait();
                    }
                    catch (Exception ex)
                    {
                        logger.LogError(ex, $"An error occurred seeding the " +
                            "database with test messages. Error: {ex.Message}");
                    }
                }
            });
        }
    }
}
```

Os testes podem usar esse WebApplicationFactory personalizado para criar um cliente e, em seguida, fazer solicitações ao aplicativo usando essa instância do cliente. O aplicativo terá dados propagados que poderão ser usados como parte das asserções do teste. Esse teste verifica se a home page do aplicativo Razor Pages eShopOnWeb é carregada corretamente e inclui uma listagem de produto que foi adicionada ao aplicativo como parte dos dados de semente.

```cs
using Microsoft.eShopWeb.RazorPages;
using System.Net.Http;
using System.Threading.Tasks;
using Xunit;

namespace FunctionalTests.WebRazorPages
{
    public class HomePageOnGet : IClassFixture<CustomWebRazorPagesApplicationFactory<Startup>>
    {
        public HomePageOnGet(CustomWebRazorPagesApplicationFactory<Startup> factory)
        {
            Client = factory.CreateClient();
        }

        public HttpClient Client { get; }

        [Fact]
        public async Task ReturnsHomePageWithProductListing()
        {
            // Arrange & Act
            var response = await Client.GetAsync("/");
            response.EnsureSuccessStatusCode();
            var stringResponse = await response.Content.ReadAsStringAsync();

            // Assert
            Assert.Contains(".NET Bot Black Sweatshirt", stringResponse); // from seed data
        }
    }
}
```

Esse teste funcional emprega a pilha completa do aplicativo ASP.NET Core MVC/Razor Pages, incluindo todos os middlewares, filtros, associadores e outros que possam estar em vigor. Ele verifica se uma determinada rota ("/") retorna o código de status de êxito esperado e a saída HTML. Ele faz isso sem configurar um servidor Web real e, portanto, evita grande parte da fragilidade decorrente do uso de um servidor Web real (por exemplo, problemas com as configurações de firewall). Em geral, os testes funcionais executados no TestServer são mais lentos do que os testes de integração e de unidade, mas são muito mais rápidos do que os testes que seriam executados na rede em um servidor Web de teste. Use os testes funcionais para garantir a que pilha de front-end do aplicativo esteja funcionando conforme o esperado. Esses testes são úteis principalmente quando você encontra duplicação em seus controladores ou páginas e soluciona a duplicação adicionando filtros. O ideal é que essa refatoração não altere o comportamento do aplicativo e um conjunto de testes funcionais pode verificar se isso ocorreu.

>[!div class="step-by-step"]
[Anterior](work-with-data-in-asp-net-core-apps.md)
[Próximo](development-process-for-azure.md)
