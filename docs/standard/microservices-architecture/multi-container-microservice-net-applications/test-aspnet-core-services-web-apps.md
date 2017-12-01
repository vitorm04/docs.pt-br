---
title: "Teste os serviços principais do ASP.NET e aplicativos web"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Teste os serviços principais do ASP.NET e aplicativos web"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: f756a679befee676db2bf6d402fd7e34b1621b9d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="testing-aspnet-core-services-and-web-apps"></a>Teste os serviços principais do ASP.NET e aplicativos web

Os controladores são uma parte central de qualquer serviço de API do ASP.NET Core e o aplicativo Web do ASP.NET MVC. Como tal, você deve ter confiança que se comportam conforme o esperado para seu aplicativo. Testes automatizados podem fornecer essa confiança e podem detectar erros antes que elas atinjam a produção.

Você precisa testar como o controlador se comporta com base nas entradas válidas ou inválidas e respostas de controlador com base no resultado da operação de negócios que ele executa um teste. No entanto, você deve ter esses tipos de teste sua microservices:

-   Testes de unidade. Eles garantem que os componentes individuais do aplicativo funcionam como esperado. Asserções testar a API do componente.

-   Testes de integração. Eles garantem que as interações do componente funcionam como esperado em artefatos externos, como bancos de dados. Asserções podem testar a API do componente, interface do usuário ou os efeitos colaterais de ações, como e/s de banco de dados, log, etc.

-   Testes funcionais para cada microsserviço. Eles garantem que o aplicativo funciona conforme o esperado da perspectiva do usuário.

-   Testes de serviço. Eles garantem que os casos de uso do serviço de ponta a ponta, incluindo testes de vários serviços ao mesmo tempo, são testados. Para esse tipo de teste, você precisa preparar o ambiente primeiro. Nesse caso, isso significa que iniciar os serviços (por exemplo, usando o docker-compor backup).

### <a name="implementing-unit-tests-for-aspnet-core-web-apis"></a>Implementação de testes de unidade para APIs de Web do ASP.NET Core

Testes de unidade envolve uma parte de um aplicativo de teste em isolamento de sua infraestrutura e as dependências. Quando a lógica do controlador, somente o conteúdo de uma única ação de teste de unidade você ou método é testado, não o comportamento de suas dependências ou a própria estrutura. Testes de unidade não detectam problemas na interação entre componentes, que é o objetivo do teste de integração.

Como você unidade suas ações do controlador de teste, verifique se que você se concentrar apenas em seus comportamentos. Um teste de unidade do controlador evita coisas como filtros, roteamento ou associação de modelo. Como eles se concentrar no teste apenas uma coisa, testes de unidade geralmente são simples de escrever e rápido executar. Um conjunto bem escrito de testes de unidade pode ser executado com frequência sem muita sobrecarga.

Testes de unidade são implementados com base nas estruturas de teste como xUnit.net, MSTest, Moq ou NUnit. Para o aplicativo de exemplo eShopOnContainers, estamos usando XUnit.

Quando você grava um teste de unidade para um controlador de API da Web, você instanciar a classe do controlador diretamente usando a nova palavra-chave C\#, de modo que o teste será executado mais rápido possível. O exemplo a seguir mostra como fazer isso ao usar [XUnit](https://xunit.github.io/) como a estrutura de teste.

```csharp
[Fact]
public void Add_new_Order_raises_new_event()
{
    // Arrange
    var street = " FakeStreet ";
    var city = "FakeCity";
    // Other variables omitted for brevity ...
    // Act
    var fakeOrder = new Order(new Address(street, city, state, country, zipcode),
        cardTypeId, cardNumber,
        cardSecurityNumber, cardHolderName,
        cardExpiration);
    // Assert
    Assert.Equal(fakeOrder.DomainEvents.Count, expectedResult);
}
```

### <a name="implementing-integration-and-functional-tests-for-each-microservice"></a>Implementação de integração e testes funcionais para cada microsserviço

Conforme observado, testes de integração e testes funcionais têm metas e objetivos diferentes. No entanto, a maneira como você implementa ambos ao testar controladores do ASP.NET Core é semelhante, portanto nesta seção, nos concentraremos em testes de integração.

Testes de integração, você garante que componentes de um aplicativo funcionam corretamente quando montado. ASP.NET Core dá suporte a teste de integração usando estruturas de teste de unidade e um host da web internos de teste que pode ser usado para tratar as solicitações sem sobrecarga de rede.

Ao contrário de testes de unidade, testes de integração com frequência envolvem preocupações de infraestrutura de aplicativo, como um banco de dados, sistema de arquivos, recursos de rede, ou web solicitações e respostas. Testes de unidade usam fakes ou simular objetos no lugar essas preocupações. Mas a finalidade de testes de integração confirmar se o sistema funciona conforme esperado com esses sistemas, forma para testes de integração não usar fakes ou simular objetos. Em vez disso, você pode incluir a infraestrutura, como a invocação de acesso ou o serviço de banco de dados de outros serviços.

Porque o exercitam de testes de integração maior de segmentos de código que testes de unidade e testes de integração se basear em elementos de infraestrutura, eles tendem a ser ordens de magnitude menor do que testes de unidade. Portanto, é uma boa ideia limitar quantos testes de integração, gravar e executar.

ASP.NET Core inclui um teste interno host da web que pode ser usado para tratar as solicitações HTTP sem sobrecarga de rede, que significa que você pode executar esses testes mais rapidamente ao usar um host da web real. O host de teste da web está disponível em um componente do NuGet como Microsoft.AspNetCore.TestHost. Ele pode ser adicionado a projetos de teste de integração e aplicativos usados para hospedar o ASP.NET Core.

Como você pode ver no código a seguir, quando você cria testes de integração para o ASP.NET Core controladores, você pode instanciar os controladores por meio do host de teste. Isso é equivalente a uma solicitação HTTP, mas ele é executado mais rapidamente.

```csharp
public class PrimeWebDefaultRequestShould
{
    private readonly TestServer _server;
    private readonly HttpClient _client;

    public PrimeWebDefaultRequestShould()
    {
        // Arrange
        _server = new TestServer(new WebHostBuilder()
           .UseStartup<Startup>());
           _client = _server.CreateClient();
    }

    [Fact]
    public async Task ReturnHelloWorld()
    {
        // Act
        var response = await _client.GetAsync("/");
        response.EnsureSuccessStatusCode();
        var responseString = await response.Content.ReadAsStringAsync();
        // Assert
        Assert.Equal("Hello World!", responseString);
    }
}
```

#### <a name="additional-resources"></a>Recursos adicionais

-   **Steve Smith. Controladores de teste** (ASP.NET Core) [ *https://docs.microsoft.com/aspnet/core/mvc/controllers/testing*](https://docs.microsoft.com/aspnet/core/mvc/controllers/testing)

-   **Steve Smith. Testes de integração** (ASP.NET Core) [ *https://docs.microsoft.com/aspnet/core/testing/integration-testing*](https://docs.microsoft.com/aspnet/core/testing/integration-testing)

-   **Teste de unidade no .NET Core usando dotnet teste**
    [*https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test*](https://docs.microsoft.com/dotnet/core/testing/unit-testing-with-dotnet-test)

-   **xUnit.net**. Site oficial.
    [*https://xUnit.GitHub.IO/*](https://xunit.github.io/)

-   **Noções básicas de teste de unidade. ** 
     [ *https://msdn.microsoft.com/en-us/library/hh694602.aspx*](https://msdn.microsoft.com/en-us/library/hh694602.aspx)

-   **Moq**. Repositório do GitHub.
    [*https://GitHub.com/moq/moq*](https://github.com/moq/moq)

-   **NUnit**. Site oficial.
    [*https://www.NUnit.org/*](https://www.nunit.org/)

### <a name="implementing-service-tests-on-a-multi-container-application"></a>Testes de implementação de serviços em um aplicativo de contêiner de vários 

Conforme observado anteriormente, quando você testar o contêiner de vários aplicativos, todos os microservices precisa estar executando dentro do cluster de host ou o contêiner do Docker. Testes de serviço de ponta a ponta que incluem várias operações que envolvem várias microservices exigem que você implantar e iniciar o aplicativo inteiro no host do Docker executando docker-compor up (ou um mecanismo comparável se você estiver usando um orchestrator). Quando o aplicativo inteiro e todos os seus serviços estiver em execução, você pode executar testes funcionais e integração de ponta a ponta.

Existem algumas abordagens que você pode usar. No arquivo de docker compose.yml que você usa para implantar o aplicativo (ou aquelas semelhantes, como o docker compose.ci.build.yml), no nível da solução você pode expandir o ponto de entrada para usar [dotnet teste](https://docs.microsoft.com/dotnet/core/tools/dotnet-test). Você também pode usar outro arquivo de redação que executará os testes na imagem de que destino. Usando outro arquivo de redação para testes de integração que inclui seu microservices e bancos de dados em contêineres, você pode garantir que os dados relacionados sempre são redefinidos para seu estado original antes de executar os testes.

Depois que o aplicativo de redação está em execução, você pode tirar proveito de pontos de interrupção e exceções se você estiver executando o Visual Studio. Ou você pode executar os testes de integração automaticamente em seu pipeline de CI no Visual Studio Team Services ou qualquer outro sistema de CI/CD que dá suporte a contêineres do Docker.

>[!div class="step-by-step"]
[Anterior] (assinar-events.md) [Avançar] (... /microservice-DDD-CQRS-Patterns/index.MD)
