---
title: Testar aplicativos MVC do ASP.NET Core
description: Projetar aplicativos Web modernos com ASP.NET Core e o Azure | Testar aplicativos MVC do ASP.NET Core
author: ardalis
ms.author: wiwagn
ms.date: 10/08/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.openlocfilehash: 4611ffa8334e124946e849306d3281b695830eb1
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/21/2017
---
# <a name="test-aspnet-core-mvc-apps"></a>Testar aplicativos MVC do ASP.NET Core

> _"Se você não deseja que seu produto de teste de unidade, provavelmente os clientes não gostam de testá-lo, ou."_
> _ - Anônimo -

## <a name="summary"></a>Resumo

Software de qualquer complexidade pode falhar de maneiras inesperadas em resposta a alterações. Assim, são necessário para todos os aplicativos mais simples (ou menos críticos), exceto testes depois de fazer alterações. Teste manual é o mais lento, menos confiável de maneira mais cara para testar o software. Infelizmente, se os aplicativos não são projetados para ser testável, pode ser o único meio disponível. Aplicativos escritos os princípios de arquitetura apresentados a seguir no capítulo X devem ser um teste de unidade e integração automatizada e testes funcionais também dar suporte a aplicativos ASP.NET Core.

## <a name="kinds-of-automated-tests"></a>Tipos de testes automatizados

Há muitos tipos de testes automatizados para aplicativos de software. A forma mais simples, teste de nível mais baixo é o teste de unidade. Em um nível superior ligeiramente há testes de integração e testes funcionais. Outros tipos de testes, como testes de interface do usuário, testes de carga, testes de estresse e testes smoke, estão além do escopo deste documento.

### <a name="unit-tests"></a>Testes de Unidade

Um teste de unidade testa uma única parte da lógica do aplicativo. Ainda mais um pode descrevê-lo por meio da lista algumas das coisas que não é. Um teste de unidade não testa como a código funciona com dependências ou infraestrutura – que é o que a integração de testes destinam-se. Um teste de unidade não testa a estrutura de em que seu código é escrito – você deve pressupor que ele funciona ou se achar que não, registrar um bug e uma solução alternativa de código. Um teste de unidade é executado completamente na memória e no processo. Ele não se comunicar com o sistema de arquivos, rede ou um banco de dados. Testes de unidade só devem testar seu código.

Testes de unidade, devido ao fato de que eles testar apenas uma única unidade de seu código, sem dependências externas, devem ser executado muito rapidamente. Assim, você deve ser capaz de executar os pacotes de testes de centenas de testes de unidade em alguns segundos. Executá-los com frequência, idealmente antes de cada envio por push para um repositório de controle do código-fonte compartilhado e certamente com cada compilação automatizada em seu servidor de compilação.

### <a name="integration-tests"></a>Testes de integração

Embora seja uma boa ideia para encapsular o código que interage com a infraestrutura, como bancos de dados e sistemas de arquivos, você ainda terá algumas que o código e você provavelmente desejará testá-lo. Além disso, você deve verificar que camadas do seu código interagem conforme o esperado quando dependências do aplicativo são totalmente resolvidas. Isso é responsabilidade de testes de integração. Testes de integração tendem a ser mais lento e mais difícil de configurar que testes de unidade, porque eles geralmente dependem de infraestrutura e as dependências externas. Portanto, você deve evitar coisas que podem ser testes com testes de unidade em testes de integração de teste. Se você pode testar um determinado cenário com um teste de unidade, você deve testá-lo com um teste de unidade. Se não for possível, considere usar um teste de integração.

Testes de integração geralmente terá uma configuração mais complexa e procedimentos de desmontagem de testes de unidade. Por exemplo, um teste de integração que vai em relação a um banco de dados real precisará de uma maneira de retornar o banco de dados para um estado conhecido antes de cada execução de teste. Conforme novos testes são adicionados e o esquema de banco de dados de produção evolui, esses scripts tendem a aumentar em tamanho e complexidade de teste. Em muitos sistemas grandes, não é prático para executar pacotes completos de testes de integração em estações de trabalho do desenvolvedor antes de verificar as alterações ao controle do código-fonte compartilhado. Nesses casos, os testes de integração podem ser executados em um servidor de compilação.

A classe de implementação LocalFileImageService implementa a lógica para buscar e retornando os bytes de um arquivo de imagem de uma pasta específica recebe uma id:

```cs
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
```

### <a name="functional-tests"></a>Testes funcionais

Testes de integração são gravados do ponto de vista do desenvolvedor, verifique se que alguns componentes do sistema funcionem corretamente. Testes funcionais são escritos da perspectiva do usuário e verificar a integridade do sistema com base em seus requisitos. O trecho a seguir oferece uma analogia útil para pensar sobre testes funcionais, em comparação comparadas testes de unidade como:

> "Muitas vezes o desenvolvimento de um sistema é comparado a construção de uma casa. Embora essa analogia não seja bastante correta, podemos poderá estendê-lo para fins de compreender a diferença entre unidade e testes funcionais. Testes de unidade é análoga a um Inspetor de construção, visite o site de construção de uma casa. Ele destina-se em vários sistemas internos de casa, a base de enquadramento, elétrica, encanamento e assim por diante. Ele garante (testes) que as partes da casa funcionarão corretamente e com segurança, ou seja, atender o código de construção. Testes funcionais neste cenário são análogos ao imóvel visitar esse mesmo site de construção. Ele pressupõe que os sistemas internos irão se comportar adequadamente, que o Inspetor de construção está executando suas tarefas. O proprietário é focado em que será como vida essa casa. Ele está preocupada com a aparência da casa, são as várias rooms um tamanho confortável, é a casa atender às necessidades da família, são as janelas um bom ponto para capturar o sun da manhã. O proprietário está executando testes funcionais em casa. Ele tem um ponto de vista do usuário. O Inspetor de construção está executando testes de unidade em casa. Ele tem perspectiva do construtor."

Fonte: [versus testes funcionais de teste de unidade](http://www.softwaretestingtricks.com/2007/01/unit-testing-versus-functional-tests.html)

Estou de jogos de dizer "como os desenvolvedores, podemos falha de duas maneiras: criamos a coisa errada ou criamos a coisa errada." Testes de unidade, verifique se que você está criando o direito de coisa; testes funcionais Verifique se que você está criando o certo.

Desde que os testes funcionais operam no nível do sistema, eles podem exigir um certo grau de automação de interface do usuário. Como testes de integração, elas geralmente funcionam com algum tipo de infraestrutura de teste também. Isso os torna mais lento e mais frágil que testes de unidade e a integração. Você deve ter somente quantos testes funcionais conforme necessário garantir que o sistema está se comportando conforme esperam de usuários.

### <a name="testing-pyramid"></a>Teste de pirâmide

Martin Fowler gravou sobre a teste pirâmide, um exemplo é mostrado na Figura 9-1.

![](./media/image9-1.png)

Figura 9-1 teste pirâmide

As diferentes camadas de pirâmide e seus tamanhos relativos, representam tipos diferentes de testes e quantos você deve escrever para seu aplicativo. Como você pode ver, a recomendação é ter uma grande base de testes de unidade, suportados por uma camada menor de testes de integração, com uma camada ainda menor de testes funcionais. Cada camada idealmente deve ter somente testes que não pode ser executada de forma adequada em uma camada inferior. Lembre-se da pirâmide teste quando você estiver tentando decidir qual tipo de teste para um cenário específico.

### <a name="what-to-test"></a>O que testar

Um problema comum para os desenvolvedores que não tiver experiência com a criação de testes automatizados está chegando com o teste. É um bom ponto de partida testar a lógica condicional. Onde quer que tenha um método com o comportamento que as alterações com base em uma instrução condicional (if-else, alternar, etc.), você poderá criar pelo menos dois testes que confirmam se o comportamento correto para determinadas condições. Se seu código tem condições de erro, é melhor criar pelo menos um teste para o "caminho feliz" através do código (com sem erros) e pelo menos um teste para o "caminho sad" (com erros ou resultados atípicos) para confirmar que seu aplicativo se comporta como esperado no caso de erros. Por fim, tente se concentrar no teste de coisas que podem falhar, em vez de nos concentrarmos no métricas como cobertura de código. Cobertura de código mais geralmente é melhor do que o menor. No entanto, gravar alguns testes mais de um método muito complexo e críticos para os negócios é normalmente um melhor uso de tempo que escrever testes para autopropriedades apenas para melhorar as métricas de cobertura de código de teste.

## <a name="organizing-test-projects"></a>Organizar projetos de teste

Projetos de teste podem ser organizados, mas funciona melhor para você. É uma boa ideia separe os testes por tipo (teste de unidade, teste de integração) e o estão sendo testado (por projeto, namespace). Se essa separação consistirá de pastas dentro de um projeto de teste único ou vários projetos de teste, é uma decisão de design. Um projeto é mais simples, mas para projetos grandes, com muitos testes ou para executar mais facilmente os diferentes conjuntos de testes, você talvez queira ter vários projetos de teste diferente. Muitas equipes organizam projetos de teste baseados no projeto que estão testando, que pode resultar em um grande número de projetos de teste, especialmente se você ainda dividir essas acordo com os tipo de testes que estão em cada projeto para aplicativos com mais de alguns projetos. Uma abordagem de comprometimento é ter um projeto por tipo de teste, por aplicativo, com pastas dentro de projetos de teste para indicar o projeto (e a classe) que está sendo testado.

Uma abordagem comum é organizar os projetos de aplicativo em uma pasta de 'src' e projetos de teste do aplicativo em uma pasta de 'teste' paralelos. Você pode criar pastas de solução correspondente no Visual Studio, se você encontrar esta organização útil.

![](./media/image9-2.png)

Figura 9-2 organização de teste em sua solução

Você pode usar qualquer estrutura de teste que você preferir. A estrutura xUnit funciona bem e que todos os testes do ASP.NET Core e EF principal são gravados. Você pode adicionar um projeto de teste xUnit no Visual Studio usando o modelo mostrado na Figura 9-3 ou da CLI usando dotnet xunit de novo.

![](./media/image9-3.png)

Figura 9-3 adicionar um projeto de teste xUnit no Visual Studio

### <a name="test-naming"></a>Teste de nomenclatura

Você deve nomear os testes de maneira consistente, com nomes que indiquem o que faz cada teste. É uma abordagem com que tive grande sucesso classes de nome de teste de acordo com a classe e o método que estão sendo testado. Isso resulta em várias classes de teste pequena, mas ele torna extremamente limpar o que é responsável por cada teste. Com o nome de classe de teste configurado para identificar a classe e o método a ser testada, o nome do método de teste pode ser usado para especificar o comportamento que está sendo testado. Isso deve incluir o comportamento esperado e qualquer entrada ou suposições que devem gerar esse comportamento. Alguns exemplos de nomes de teste:

-   CatalogControllerGetImage.CallsImageServiceWithId

-   CatalogControllerGetImage.LogsWarningGivenImageMissingException

-   CatalogControllerGetImage.ReturnsFileResultWithBytesGivenSuccess

-   CatalogControllerGetImage.ReturnsNotFoundResultGivenImageMissingException

Uma variação dessa abordagem termina o nome de cada classe de teste com "Deve" e modifica os tempos verbais ligeiramente:

-   CatalogControllerGetImage**devem**. **Chamar**ImageServiceWithId

-   CatalogControllerGetImage**devem**. **Log**WarningGivenImageMissingException

Algumas equipes localizar a segunda abordagem de nomenclatura mais clara, embora um pouco mais detalhado. Em qualquer caso, tente usar uma convenção de nomenclatura que fornece informações sobre o comportamento de teste, para que quando um ou mais testes falharem, seja óbvio em seus nomes quais casos falharam. Evite nomeando testes vagamente, como ControllerTests.Test1, como eles oferecem nenhum valor quando você vê-los nos resultados de teste.

Se você seguir uma convenção de nomenclatura, como mostrado acima que produz muitas classes de teste pequena, é uma boa ideia para organizar ainda mais seus testes usando pastas e namespaces. Figura 9-4 mostra uma abordagem para organizar testes por pasta em vários projetos de teste.

![](./media/image9-4.png)

**Figura 9-4.** Organizando classes de teste por pasta com base na classe que está sendo testado.

É claro que, se uma classe específica do aplicativo tem muitos métodos que está sendo testados (e, portanto, muitas classes de teste), talvez faça sentido para colocá-los em uma pasta correspondente para a classe do aplicativo. Esta organização não é diferente de como você pode organizar arquivos em pastas em outro lugar. Se você tiver mais de três ou quatro arquivos em uma pasta que contém muitos outros arquivos relacionados a, geralmente é útil para movê-los em sua própria subpasta.

## <a name="unit-testing-aspnet-core-apps"></a>Aplicativos de ASP.NET Core de teste de unidade

Em um aplicativo bem projetado do ASP.NET Core, a maioria da complexidade e lógica de negócios será encapsulada em entidades de negócios e uma variedade de serviços. O aplicativo ASP.NET MVC de núcleo em si, com seus controladores, filtros, viewmodels e modos de exibição, deve exigir muito poucos testes de unidade. Muitas das funcionalidades de uma determinada ação está fora do método de ação. Teste se o roteamento funciona corretamente ou o tratamento de erro global, não pode ser feito efetivamente com um teste de unidade. Da mesma forma, quaisquer filtros, incluindo autenticação e validação de modelo e filtros de autorização, não pode ser teste de unidade. Sem essas fontes de comportamento, a maioria dos métodos de ação deve ser muito pequeno, a maior parte do seu trabalho para serviços que pode ser testado independentemente do controlador que usa a delegação.

Às vezes, você precisará refatorar o código de pedido para teste de unidade. Com frequência, isso envolve identificando abstrações e usando a injeção de dependência para acessar a abstração no código que você deseja testar, em vez de codificar diretamente na infraestrutura. Por exemplo, considere este método de ação simples para exibir imagens:

```cs
[HttpGet("[controller]/pic/{id}")]
public IActionResult GetImage(int id)
{
    var contentRoot = _env.ContentRootPath + "//Pics";
    var path = Path.Combine(contentRoot, id + ".png");
    Byte[] b = System.IO.File.ReadAllBytes(path);
    return File(b, "image/png");
}
```

Esse método de teste de unidade torna difícil por sua dependência direta System.IO, que ele usa para ler do sistema de arquivos. Você pode testar esse comportamento para garantir que ele funciona conforme o esperado, mas fazer isso com arquivos reais é um teste de integração. Vale a pena observar não é possível testar rota desse método – você verá como fazer isso com um teste funcional em breve.

Se você não é o comportamento do sistema de arquivos de teste de unidade diretamente e não é possível testar a rota, o que há testar? Bem, depois de refatoração para possibilitar o teste de unidade, você pode descobrir alguns casos de teste e comportamento ausente, como o tratamento de erros. O que o método faz quando não for encontrado um arquivo? O que ele deve fazer? Neste exemplo, o método refatorado tem esta aparência:

```cs
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

O \_agente e \_imageService são injetadas como dependências. Agora você pode testar se a mesma id que é passada para o método de ação é passada para o \_imageService, e que os bytes resultantes serão retornados como parte do FileResult. Você também pode testar que o log de erros está ocorrendo conforme o esperado, e que um resultado encontrado será retornado se a imagem estiver ausente, supondo que esse é o comportamento de aplicativo importantes (ou seja, não apenas código temporário o desenvolvedor adicionado para diagnosticar um problema). A lógica real do arquivo foi movido para um serviço de implementação separada e foi aumentada para retornar uma exceção específica do aplicativo para o caso de um arquivo ausente. Você pode testar essa implementação de forma independente, usando um teste de integração.

## <a name="integration-testing-aspnet-core-apps"></a>Integração de teste ASP.NET Core aplicativos

```cs
    }
        catch (FileNotFoundException ex)
        {
            throw new CatalogImageMissingException(ex);
        }
    }
}
```

Esse serviço usa IHostingEnvironment, assim como o CatalogController código foi antes que ele foi refatorado em um serviço separado. Já que esse foi o código somente no controlador que usado IHostingEnvironment, essa dependência foi removida do construtor do CatalogController.

Para testar a que este serviço está funcionando corretamente, você precisa criar um arquivo de imagem de teste conhecido e verificar que o serviço retorna uma entrada específica. Você deve ter cuidado para não usar objetos fictícios o comportamento que você realmente deseja testar (nesse caso, o sistema de arquivos de leitura). No entanto, os objetos fictícios ainda podem ser útil para configurar testes de integração. Nesse caso, você pode simular IHostingEnvironment para que seu ContentRootPath aponta para a pasta que você pretende usar para a imagem de teste. A classe de teste de integração completa do trabalho é mostrada aqui:

```cs
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
> a maior parte do código que o teste é muito simple, é necessária para configurar o sistema e criar a infraestrutura de teste (no caso, um arquivo real ser lidas do disco). Isso é típico para testes de integração, que geralmente exigem o trabalho de configuração mais complexo que testes de unidade.

## <a name="functional-testing-aspnet-core-apps"></a>Testando aplicativos do ASP.NET Core funcional

Para aplicativos do ASP.NET Core, a classe TestServer faz testes funcionais relativamente fáceis de escrever. Você configurar um TestServer usando um WebHostBuilder, assim como faria normalmente para seu aplicativo. Este WebHostBuilder deve ser configurado como host real do seu aplicativo, mas você pode modificar qualquer aspectos que facilitar os testes. Na maioria das vezes, você vai utilizar o mesmo TestServer em muitos casos de teste, para que você pode encapsulá-lo em um método reutilizável (talvez em uma classe base):

```cs
public abstract class BaseWebTest
{
    protected readonly HttpClient _client;
    protected string _contentRoot;

    public BaseWebTest()
    {
        _client = GetClient();
    }
    
    protected HttpClient GetClient()
    {
        var startupAssembly = typeof(Startup).GetTypeInfo().Assembly;
        _contentRoot = GetProjectPath("src", startupAssembly);
        var builder = new WebHostBuilder()
        .UseContentRoot(_contentRoot)
        .UseStartup&lt;Startup&gt;();
        var server = new TestServer(builder);
        var client = server.CreateClient();
        return client;
    }
}
```

O método GetProjectPath simplesmente retorna o caminho físico para o projeto da web (solução de exemplo de download). O WebHostBuilder nesse caso simplesmente especifica onde o conteúdo raiz para o aplicativo web e referencia a mesma classe de inicialização que usa o aplicativo web real. Para trabalhar com o TestServer, você pode usar o tipo de System.Net.HttpClient para fazer solicitações a ele. TestServer expõe um método de CreateClient útil que fornece um cliente pré-configurado que está pronto para fazer solicitações para o aplicativo em execução no TestServer. Use este cliente (definido como protegido \_membro do cliente no teste de base acima) ao escrever testes funcionais para seu aplicativo ASP.NET Core:

```cs
public class CatalogControllerGetImage : BaseWebTest
{
    [Fact]
    public async Task ReturnsFileContentResultGivenValidId()
    {
        var testFilePath = Path.Combine(_contentRoot, "pics//1.png");
        var expectedFileBytes = File.ReadAllBytes(testFilePath);
        var response = await _client.GetAsync("/catalog/pic/1");
        response.EnsureSuccessStatusCode();
        var streamResponse = await response.Content.ReadAsStreamAsync();
        byte[] byteResult;
        using (var ms = new MemoryStream())
        {
            streamResponse.CopyTo(ms);
            byteResult = ms.ToArray();
        }
        Assert.Equal(expectedFileBytes, byteResult);
    }
}
```

Esse teste funcional emprega a pilha de aplicativo MVC do ASP.NET Core completa, incluindo todos os middleware, filtros, associadores, etc. que pode estar em vigor. Ele verifica se uma determinada rota ("/ pic/catálogo/1") retorna a matriz de bytes esperados para um arquivo em um local conhecido. Ele faz isso sem configurar um servidor web real e portanto evita muito a fragilidade que servidor de teste pode ocorrer (por exemplo, problemas com as configurações de firewall) usando uma web real. Testes funcionais executadas em TestServer são geralmente mais lentas do que a integração e testes de unidade, mas são muito mais rápidos que testes que seriam executado pela rede para um servidor de teste da web.

>[!div class="step-by-step"]
[Anterior] (work-with-data-in-asp-net-core-apps.md) [Avançar] (desenvolvimento-processo-para-azure.md)
