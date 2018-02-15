---
title: Trabalhar com dados em aplicativos do ASP.NET Core
description: Projetar aplicativos Web modernos com ASP.NET Core e o Azure | Trabalhando com dados no asp
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 648e0a4cdd388cf4a322f0fc049d5dcfca53d54b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="working-with-data-in-aspnet-core-apps"></a>Trabalhando com dados em aplicativos ASP.NET Core

> "Os dados é uma coisa preciosa e irão durar mais que os próprios sistemas de".

Tim Berners-Lee

## <a name="summary"></a>Resumo

Acesso a dados é uma parte importante de praticamente qualquer aplicativo de software. ASP.NET Core dá suporte a uma variedade de opções de acesso de dados, incluindo o Entity Framework Core (e também para o Entity Framework 6) e pode trabalhar com qualquer acesso de dados do .NET framework. A escolha do framework usar de acesso a dados dos quais depende necessidades do aplicativo. Abstrair essas opções dos projetos ApplicationCore e interface de usuário e encapsula os detalhes de implementação na infraestrutura, ajudam a produzir um software acoplado, podem ser testado.

## <a name="entity-framework-core-for-relational-databases"></a>Entity Framework Core (para bancos de dados relacionais)

Se você estiver escrevendo um novo aplicativo ASP.NET Core que precisa para trabalhar com dados relacionais, Entity Framework Core (EF Core) é a maneira recomendada para seu aplicativo acessar seus dados. Núcleo do EF é mapeador relacional de objeto (O/RM) que permite que os desenvolvedores de .NET manter os objetos em uma fonte de dados. Elimina a necessidade para a maioria dos desenvolvedores normalmente precisa escrever código de acesso do dados. Como o ASP.NET Core EF Core foi recriado desde o início para suporte a aplicativos de plataforma cruzada modular. Você adicioná-lo ao seu aplicativo como um pacote NuGet, configurá-lo na inicialização e solicitá-la por meio de injeção de dependência, onde for necessário.

Para usar o EF Core com um banco de dados do SQL Server, execute o seguinte comando CLI dotnet:

dotnet Adicionar pacote Microsoft.EntityFrameworkCore.SqlServer

Para adicionar suporte para uma fonte de dados InMemory para teste:

dotnet Adicionar pacote Microsoft.EntityFrameworkCore.InMemory

### <a name="the-dbcontext"></a>O DbContext

Para trabalhar com EF Core, você precisa de uma subclasse de DbContext. Essa classe contém propriedades que representam coleções de entidades que seu aplicativo funcionará com. O exemplo de eShopOnWeb inclui um CatalogContext com coleções de itens, marcas e tipos:

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {

    }

    public DbSet<CatalogItem> CatalogItems { get; set; }

    public DbSet<CatalogBrand> CatalogBrands { get; set; }

    public DbSet<CatalogType> CatalogTypes { get; set; }
}
```

O DbContext deve ter um construtor que aceite DbContextOptions e passar esse argumento para o construtor DbContext base. Observe que, se você tiver apenas um DbContext em seu aplicativo, você pode passar uma instância de DbContextOptions, mas se você tiver mais de um você deve usar o genérico DbContextOptions<T> tipo, passando o tipo DbContext como o parâmetro genérico.

### <a name="configuring-ef-core"></a>Configurar os principais EF

Seu aplicativo ASP.NET Core, normalmente você vai configurar EF principal em seu método ConfigureServices. Núcleo EF usa um DbContextOptionsBuilder, que oferece suporte a vários métodos de extensão útil para simplificar sua configuração. Para configurar CatalogContext para usar um banco de dados do SQL Server com uma cadeia de caracteres de conexão definida na configuração, você adicionaria o código a seguir para ConfigureServices:

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

Para usar o banco de dados na memória:

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

Depois de instalado EF Core, criado um tipo filho DbContext e configurado no ConfigureServices, você está pronto para usar o EF Core. Você pode solicitar uma instância do seu tipo DbContext em qualquer serviço que precisa dele e começar a trabalhar com suas entidades persistentes usando LINQ como se estivesse em uma coleção. EF Core funciona a transferir suas expressões LINQ em consultas SQL para armazenar e recuperar seus dados.

Você pode ver as consultas EF principal está em execução, configurando um agente de log e garantindo seu nível é definido para pelo menos informações, como mostrado na Figura 8-1.

![](./media/image8-1.png)

Consultas de log EF Core Figura 8-1 para o console

### <a name="fetching-and-storing-data"></a>Buscando e armazenando dados

Para recuperar dados de EF Core, você acessa a propriedade apropriada e usa o LINQ para filtrar o resultados. Você também pode usar o LINQ para executar projeção, transformar o resultado de um tipo para outro. O exemplo a seguir recuperaria CatalogBrands, ordenados por nome, filtrados por sua propriedade Enabled e projetado em um tipo SelectListItem:

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

É importante no exemplo acima para adicionar a chamada para ToListAsync para executar a consulta imediatamente. Caso contrário, a instrução atribuirá um IQueryable<SelectListItem> para brandItems, que não será executado até que ele é enumerado. Há vantagens e desvantagens para retornar resultados IQueryable de métodos. Ele permite que a consulta que EF Core criará para mais ser modificada, mas também pode resultar em erros que ocorrem apenas em tempo de execução, se as operações são adicionadas à consulta que EF principal não pode traduzir. Ele geralmente é mais seguro passar todos os filtros para o método executar o acesso a dados e fazer o retorno de uma coleção de memória (por exemplo,<T>) como o resultado.

Núcleo EF rastreia as alterações nas entidades que ele busca de persistência. Para salvar as alterações para uma entidade controlada, apenas você chamar o método SaveChanges no DbContext, tornando-se de que é a mesma instância de DbContext que foi usada para buscar a entidade. Adicionando e removendo entidades são diretamente na propriedade DbSet apropriada, novamente com uma chamada para SaveChanges para executar os comandos de banco de dados. O exemplo a seguir demonstra a adicionar, atualizar e remover entidades de persistência.

```csharp
// create
var newBrand = new CatalogBrand() { Brand = "Acme" };
_context.Add(newBrand);
await _context.SaveChangesAsync();

// read and update
var existingBrand = _context.CatalogBrands.Find(1);
existingBrand.Brand = "Updated Brand";
await _context.SaveChangesAsync();

// read and delete (alternate Find syntax)
var brandToDelete = _context.Find<CatalogBrand>(2);
_context.CatalogBrands.Remove(brandToDelete);
await _context.SaveChangesAsync();
```

EF Core dá suporte a ambos síncrona e os métodos assíncronos para buscar e salvar. Em aplicativos da web, é recomendável usar o padrão assíncrono/await com os métodos assíncronos, para que os threads de servidor da web não estão bloqueadas enquanto aguarda a conclusão das operações de acesso dados.

### <a name="fetching-related-data"></a>Buscando dados relacionados

Quando o EF Core recupera entidades, preenche todas as propriedades que são armazenadas diretamente com a entidade no banco de dados. Propriedades de navegação, como listas de entidades relacionadas, não são preenchidas e pode ter seu valor definido como null. Isso garante que o EF Core é não busca mais dados do que é necessário, que é especialmente importante para aplicativos web, que devem processar solicitações e respostas de retorno de uma maneira eficiente rapidamente. Para incluir relações com uma entidade usando *carregamento adiantado*, especifique a propriedade usando o método de extensão incluir na consulta, conforme mostrado:

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

Você pode incluir várias relações, e você também pode incluir relações sub usando ThenInclude. EF Core será executado uma única consulta para recuperar o conjunto resultante de entidades.

Outra opção para carregar dados relacionados é usar *carregamento explícito*. Carregamento explícito permite carregar dados adicionais em uma entidade que já foram recuperada. Como isso envolve uma solicitação separada para o banco de dados, ele não é recomendado para aplicativos web, que devem minimizar o número de banco de dados viagens de ida e feitas por solicitação.

*Carregamento preguiçoso* é um recurso que carrega automaticamente os dados relacionados porque ele é referenciado pelo aplicativo. EF Core atualmente não há suporte, mas como com carregamento explícito deve normalmente ser desabilitado para aplicativos da web.

### <a name="resilient-connections"></a>Conexões

Recursos externos, como bancos de dados SQL, ocasionalmente, podem estar indisponíveis. Em caso de indisponibilidade temporária, os aplicativos podem usar a lógica de repetição para não gerar uma exceção. Essa técnica é conhecida como *resiliência de conexão*. Você pode implementar seu [própria repetição com retirada exponencial](https://docs.microsoft.com/azure/architecture/patterns/retry) técnica pela tentativa de repetição com um tempo de espera aumentando exponencialmente, até um máximo de tentativas foi atingida. Essa técnica adota o fato de que recursos de nuvem podem estar temporariamente indisponíveis por curtos períodos de tempo, resultando em falha de algumas solicitações.

Para o Azure SQL DB, Entity Framework Core já fornece lógica de resiliência e repetição de conexão de banco de dados interno. Mas você precisa habilitar a estratégia de execução de Entity Framework para cada conexão DbContext se você quiser que têm conexões de EF Core.

Por exemplo, o código a seguir no nível de conexão do EF Core permite conexões de SQL que são repetidas se a conexão falhar.

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        //...
        services.AddDbContext<OrderingContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
        {
            sqlOptions.EnableRetryOnFailure(
            maxRetryCount: 5,
            maxRetryDelay: TimeSpan.FromSeconds(30), 
            errorNumbersToAdd: null); 
        });
    });
}
//...
```

  #### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Estratégias de execução e transações explícitas usando BeginTransaction e vários DbContexts 
  
  Quando novas tentativas são habilitadas em conexões EF Core, cada operação que você executar usando EF principal se torna sua própria operação repetível. Cada chamada para SaveChanges e cada consulta serão repetidas como uma unidade se ocorrer uma falha temporária.
  
  No entanto, se seu código inicia uma transação usando BeginTransaction, você está definindo seu próprio grupo de operações que precisam ser tratados como uma unidade — tudo dentro da transação ser revertida se ocorrer uma falha. Se você tentar executar a transação ao usar uma estratégia de execução EF (política de repetição) e incluir várias SaveChanges de vários DbContexts nele, você verá uma exceção semelhante ao seguinte.

System. InvalidOperationException: A estratégia de execução configurada 'SqlServerRetryingExecutionStrategy' não oferece suporte a transações iniciadas pelo usuário. Use a estratégia de execução retornada por 'DbContext.Database.CreateExecutionStrategy()' para executar todas as operações na transação como uma unidade repetível.

A solução é chamar a estratégia de execução EF manualmente com um delegado que representa tudo o que precisa ser executada. Se ocorrer uma falha transitória, a estratégia de execução invocará o representante novamente. O código a seguir mostra como implementar essa abordagem:

```csharp
// Use of an EF Core resiliency strategy when using multiple DbContexts
// within an explicit transaction
// See:
// https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
var strategy = _catalogContext.Database.CreateExecutionStrategy(); 
await strategy.ExecuteAsync(async () =>
{
    // Achieving atomicity between original Catalog database operation and the
    // IntegrationEventLog thanks to a local transaction
    using (var transaction = _catalogContext.Database.BeginTransaction())
    {
        _catalogContext.CatalogItems.Update(catalogItem);
        await _catalogContext.SaveChangesAsync();
        
        // Save to EventLog only if product price changed
        if (raiseProductPriceChangedEvent)
        await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
        transaction.Commit();
    }
});
```

É o primeiro DbContext o \_catalogContext e o segundo DbContext está dentro a \_integrationEventLogService objeto. Por fim, a confirmação de ação deve ser executada várias DbContexts e usando uma estratégia de execução EF.

> ### <a name="references--entity-framework-core"></a>Referências – Entity Framework Core
> - **Documentos principais EF**  
> <https://docs.microsoft.com/ef/>
> - **EF principal: Dados relacionados**  
> <https://docs.microsoft.com/ef/core/querying/related-data>
> - **Evite entidades de carregamento lento em aplicativos ASPNET**  
> <http://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a>EF Core ou MICRO-ORM?

Enquanto o EF Core é uma ótima opção para o gerenciamento de persistência e para a maior parte encapsula os detalhes de banco de dados de desenvolvedores de aplicativos, não é a única opção. Outra alternativa de código aberto popular é [Dapper](https://github.com/StackExchange/Dapper), um MICRO-ORM chamado. Um MICRO-ORM é uma leve, menos ferramenta completa para o mapeamento de objetos para estruturas de dados. No caso de Dapper, seu design metas foque no desempenho, em vez de consulta totalmente encapsular subjacente usa para recuperar e atualizar dados. Porque ele não abstrata SQL do desenvolvedor, Dapper "mais próximo de metal" e permite que desenvolvedores gravem exato consultas que desejam usar para uma determinada data acessarem a operação.

EF Core tem dois recursos significativos fornece que separam de Dapper, mas também adicionar à sua sobrecarga de desempenho. A primeira é a tradução de expressões LINQ para SQL. Essas conversões são armazenados em cache, mas ainda assim há sobrecarga em execução na primeira vez. A segunda é que o controle de alterações em entidades (de forma que as instruções update eficiente podem ser geradas). Esse comportamento pode ser desativado para consultas específicas usando a extensão AsNotTracking. EF principal também gera consultas SQL que são geralmente muito eficiente e em qualquer caso perfeitamente aceitáveis de um ponto de vista de desempenho, mas se precisar excelente controle sobre a consulta precisa ser executada, você pode passar de SQL personalizados (ou executar um procedimento armazenado) usando EF Núcleo, muito. Nesse caso, ainda Dapper supera EF Core, mas somente um pouco. Julie Lerman apresenta alguns dados de desempenho em sua podem artigo do MSDN 2016 [Dapper, Entity Framework e aplicativos híbridos](https://msdn.microsoft.com/magazine/mt703432.aspx). Dados de parâmetro de comparação de desempenho adicionais para uma variedade de métodos de acesso de dados podem ser encontrados no [o site Dapper](https://github.com/StackExchange/Dapper).

Para ver como a sintaxe para Dapper varia EF núcleo, considere estas duas versões do mesmo método para recuperar uma lista de itens:

```csharp
// EF Core
private readonly CatalogContext _context;
public async Task<IEnumerable<CatalogType>> GetCatalogTypes()
{
    return await _context.CatalogTypes.ToListAsync();
}

// Dapper
private readonly SqlConnection _conn;
public async Task<IEnumerable<CatalogType>> GetCatalogTypesWithDapper()
{
    return await _conn.QueryAsync<CatalogType>("SELECT * FROM CatalogType");
}
```

Se você precisar criar gráficos de objeto mais complexos com Dapper, você precisa gravar as consultas associadas (em vez de adicionar uma inclusão como você faria no núcleo do EF). Isso é suportado por meio de uma variedade de sintaxes, incluindo um recurso chamado várias mapeamento que lhe permite mapear as linhas individuais para vários objetos mapeados. Por exemplo, dada a classe Post com uma propriedade do proprietário do tipo de usuário, o SQL a seguir retornará todos os dados necessários:

```sql
select * from #Posts p
left join \#Users u on u.Id = p.OwnerId
Order by p.Id
```

Cada linha retornada inclui dados de usuário e o Post. Como os dados de usuário devem ser conectados aos dados de postagem por meio de sua propriedade de proprietário, a função a seguir é usada:

```csharp
(post, user) => { post.Owner = user; return post; }
```

A listagem de código completa para retornar uma coleção de postagens com a propriedade proprietário preenchida com os dados de usuário associada seria:

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

Porque ele oferece menos encapsulamento, Dapper exige que os desenvolvedores saber mais sobre como os dados são armazenados, como consultá-los de forma eficiente e escrever código mais para obtê-lo. Quando o modelo for alterado, em vez de simplesmente criar uma nova migração (outro recurso principal do EF) e/ou atualizar informações de mapeamento em um local em um DbContext, cada consulta que é afetada deve ser atualizada. Essas consultas tem não garantias de tempo de compilação, portanto, eles podem ser quebradas em tempo de execução em resposta a alterações no modelo ou banco de dados, tornando os erros mais difíceis de detectar rapidamente. Em compensação essa possibilidade, Dapper oferece um desempenho extremamente rápido.

Para a maioria dos aplicativos e a maioria das partes de quase todos os aplicativos, Core EF oferece um desempenho aceitável. Portanto, seus benefícios de produtividade do desenvolvedor são provavelmente superam sua sobrecarga de desempenho. Para consultas que podem se beneficiar do cache, a consulta real pode ser executada apenas uma pequena porcentagem do tempo, fazer relativamente pequeno questão de diferenças de desempenho de consulta.

## <a name="sql-or-nosql"></a>SQL ou NoSQL

Tradicionalmente, bancos de dados relacionais, como o SQL Server tem influenciado mercado para armazenamento de dados persistentes, mas eles não são a única solução disponível. Bancos de dados NoSQL, como [MongoDB](https://www.mongodb.com/what-is-mongodb) oferecem uma abordagem diferente para armazenar objetos. Em vez de objetos de mapeamento para tabelas e linhas, outra opção é serializar o gráfico de objeto inteiro e armazenar o resultado. Os benefícios dessa abordagem são pelo menos inicialmente, simplicidade e desempenho. É certamente mais simples armazenar um único objeto serializado com uma chave ao decompor o objeto em muitas tabelas com relações e atualização e linhas que podem ter sido alterado desde que o objeto foi recuperado do banco de dados. Da mesma forma, busca e a desserialização de um único objeto de um repositório de chave é geralmente muito mais rápido e mais fácil do que as junções complexas ou várias consultas de banco de dados necessárias para compor totalmente o mesmo objeto de banco de dados relacional. A falta de bloqueios ou transações ou um esquema fixo também facilita a bancos de dados NoSQL muito receptivos ao dimensionamento em várias máquinas, dando suporte a conjuntos de dados muito grandes.

Por outro lado, bancos de dados NoSQL (conforme eles normalmente são chamados) tem algumas desvantagens. Bancos de dados relacionais usam a normalização para impor a consistência e evitar a duplicação de dados. Isso reduz o tamanho total do banco de dados e garante que as atualizações aos dados compartilhados estejam disponíveis imediatamente em todo o banco de dados. Em um banco de dados relacional, uma tabela de endereço pode referenciar uma tabela de país por ID, de modo que, se o nome do país foram alterado, os registros de endereço pode se beneficiar da atualização sem se precisar ser atualizado. No entanto, em um banco de dados NoSQL, endereço e seu país associado podem ser serializado como parte do número de objetos armazenado. Uma atualização para um nome de país requer que todos esses objetos a serem atualizados, em vez de uma única linha. Bancos de dados relacionais também podem garantir a integridade relacional através da aplicação de regras, como chaves estrangeiras. Bancos de dados NoSQL normalmente não oferecem essas restrições em seus dados.

Complexidade outra NoSQL bancos de dados devem lidar com é o controle de versão. Quando alteram propriedades de um objeto, ele não poderá ser desserializado das versões anteriores que foram armazenadas. Assim, todos os objetos existentes que têm uma versão (anterior) serializada do objeto devem ser atualizados para estar de acordo com seu novo esquema. Isso não é conceitualmente diferente de um banco de dados relacional, onde as alterações de esquema às vezes exigem scripts de atualização ou atualizações de mapeamento. No entanto, o número de entradas que devem ser modificados geralmente é muito maior na abordagem NoSQL, porque não há mais de eliminação de duplicação de dados.

É possível em bancos de dados NoSQL para armazenar várias versões de objetos, bancos de dados relacionais do esquema fixo algo normalmente não oferecem suporte. No entanto, nesse caso o código do aplicativo precisará levar em conta a existência de versões anteriores de objetos, adicionando complexidade adicional.

Bancos de dados NoSQL normalmente não impõem [ACID](http://en.wikipedia.org/wiki/ACID), que significa que eles têm vantagens de desempenho e escalabilidade em bancos de dados relacionais. Eles são ideais para extremamente grandes conjuntos de dados e objetos que não são apropriados para o armazenamento em estruturas de tabela normalizada. Não há nenhum motivo por que um único aplicativo não pode tirar proveito de ambas relacionais e bancos de dados NoSQL, usando cada um em que é melhor adequada.

## <a name="azure-documentdb"></a>Azure DocumentDB

Documentos do Azure é um serviço de banco de dados NoSQL totalmente gerenciado que oferece armazenamento baseado em nuvem os dados sem esquema. DocumentDB é criado para desempenho rápido e previsível, alta disponibilidade, dimensionamento Elástico e distribuição global. Apesar de ser um banco de dados NoSQL, os desenvolvedores podem usar familiares e avançados recursos de consulta SQL em dados JSON. Todos os recursos em documentos são armazenados como documentos JSON. Os recursos são gerenciados como *itens*, que são documentos que contém metadados, e *feeds*, que são coleções de itens. Figura 8-2 mostra a relação entre os diferentes recursos de DocumentDB.


![A relação hierárquica entre os recursos no DocumentDB, um banco de dados NoSQL JSON](./media/image8-2.png)

**Figura 8-2.** Organização do recurso de documentos.

A linguagem de consulta do DocumentDB é uma interface simple e poderosas para consultar documentos JSON. A linguagem dá suporte a um subconjunto de gramática SQL ANSI e adiciona integração profunda do objeto, matrizes, construção de objeto e invocação de função JavaScript.

**Referências a documentos**

-   Documentos Introduction\
    <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a>Outras opções de persistência

Além relacionais e NoSQL opções de armazenamento, aplicativos do ASP.NET Core podem usar o armazenamento do Azure para armazenar uma variedade de formatos de dados e arquivos de forma escalonável, baseado em nuvem. Armazenamento do Azure é altamente escalonável, portanto, você pode iniciar out armazenar pequenas quantidades de dados e a escala até armazenar centenas ou terabytes, se seu aplicativo exija isso. Armazenamento do Azure dá suporte a quatro tipos de dados:

-   Armazenamento de blob para texto não estruturado ou armazenamento binário, também conhecido como armazenamento de objeto.

-   Armazenamento de tabelas para conjuntos de dados estruturados, acessíveis por meio de chaves de linha.

-   Armazenamento de fila de mensagens confiáveis com base em fila.

-   Armazenamento de arquivo para acesso a arquivos compartilhados entre aplicativos locais e de máquinas virtuais do Azure.

**Referências – armazenamento do Azure**

-   Introduction\ de armazenamento do Azure
    <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a>Cache

Em aplicativos web, cada solicitação da web deve ser concluída no menor tempo possível. Uma maneira de fazer isso é limitar o número de chamadas externas, que o servidor deve fazer para concluir a solicitação. Cache envolve armazenar uma cópia dos dados no servidor (ou outros de repositório de dados que é mais facilmente consultado que a fonte de dados). Aplicativos da Web e especialmente aplicativos web tradicionais não SPA, necessário criar a interface do usuário com cada solicitação. Isso geralmente envolve muitas das mesmas consultas de banco de dados repetidamente da solicitação de um usuário para o próximo. Na maioria dos casos, esses dados sejam alterados raramente, portanto, há justificam constantemente solicitá-la do banco de dados. ASP.NET Core dá suporte a cache de resposta, para armazenar em cache páginas inteiras e cache de dados, que dá suporte ao comportamento de cache mais granular.

Ao implementar o armazenamento em cache, é importante manter na separação de ideia de problemas. Evite implementando lógica de cache em sua lógica de acesso a dados, ou em sua interface de usuário. Em vez disso, encapsular o cache em suas próprias classes e usar a configuração para gerenciar seu comportamento. Isso segue o aberto/fechado e princípios de responsabilidade única e tornará mais fácil para você gerenciar como você usa o cache em seu aplicativo à medida que cresce.

### <a name="aspnet-core-response-caching"></a>O cache de resposta do ASP.NET Core

ASP.NET Core dá suporte a dois níveis de cache de resposta. O primeiro nível não armazena em cache nada no servidor, mas adiciona cabeçalhos HTTP que instruem os clientes e servidores proxy para respostas de cache. Isso é implementado, adicionando o atributo ResponseCache controladores individuais ou ações:

```csharp
    [ResponseCache(Duration = 60)]
    public IActionResult Contact()
    { }
    
    ViewData["Message"] = "Your contact page.";
    return View();
}

The above example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.

Cache-Control: public,max-age=60

In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware. This middleware is configured in both ConfigureServices and Configure in Startup:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddResponseCaching();
}

public void Configure(IApplicationBuilder app)
{
    app.UseResponseCaching();
}
```

O Middleware de cache de resposta automaticamente armazenará em cache respostas com base em um conjunto de condições que você pode personalizar. Por padrão, apenas 200 respostas (Okey) solicitadas por meio de métodos GET ou HEAD são armazenadas em cache. Além disso, as solicitações devem ter uma resposta com um Cache-Control: cabeçalho público e não pode incluir cabeçalhos de autorização ou Set-Cookie. Consulte uma [lista completa das condições cache usada pela resposta de cache middleware](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching).

### <a name="data-caching"></a>Cache de dados

Em vez de (ou além) armazenar em cache respostas de web completo, você pode armazenar em cache os resultados de consultas de dados individuais. Para isso, você pode usar no cache de memória no servidor web ou usar [um cache distribuído](https://docs.microsoft.com/aspnet/core/performance/caching/distributed). Esta seção demonstrará como implementar no cache de memória.

Adicionar suporte para memória (ou distribuído) ConfigureServices de cache:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

Certifique-se de adicionar o pacote do Microsoft.Extensions.Caching.Memory NuGet também.

Depois de adicionar o serviço, você solicitar IMemoryCache por meio de injeção de dependência sempre que você precisa acessar o cache. Neste exemplo, o CachedCatalogService está usando o padrão de design de Proxy (ou decorador), fornecendo uma implementação alternativa de ICatalogService que controla o acesso ao (ou adiciona um comportamento) a implementação CatalogService subjacente.

```csharp
public class CachedCatalogService : ICatalogService
{
    private readonly IMemoryCache _cache;
    private readonly CatalogService _catalogService;
    private static readonly string _brandsKey = "brands";
    private static readonly string _typesKey = "types";
    private static readonly string _itemsKeyTemplate = "items-{0}-{1}-{2}-{3}";
    private static readonly TimeSpan _defaultCacheDuration = TimeSpan.FromSeconds(30);
    public CachedCatalogService(IMemoryCache cache,
    CatalogService catalogService)
    {
        _cache = cache;
        _catalogService = catalogService;
    }
    
    public async Task<IEnumerable<SelectListItem>> GetBrands()
    {
        return await _cache.GetOrCreateAsync(_brandsKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetBrands();
        });
    }
    
    public async Task<Catalog> GetCatalogItems(int pageIndex, int itemsPage, int? brandID, int? typeId)
    {
        string cacheKey = String.Format(_itemsKeyTemplate, pageIndex, itemsPage, brandID, typeId);
        return await _cache.GetOrCreateAsync(cacheKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetCatalogItems(pageIndex, itemsPage, brandID, typeId);
        });
    }
    
    public async Task<IEnumerable<SelectListItem>> GetTypes()
    {
        return await _cache.GetOrCreateAsync(_typesKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetTypes();
        });
    }
}
```

Para configurar o aplicativo para usar a versão armazenada em cache do serviço, mas ainda permitir que o serviço obter a instância de CatalogService que precisa de seu construtor, adicione o seguinte no ConfigureServices:

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

Com isso em vigor, as chamadas de banco de dados para buscar os dados de catálogo serão feitas apenas uma vez por minuto, em vez de em cada solicitação. Dependendo do tráfego para o site, isso pode ter um impacto significativo muito o número de consultas feitas para o banco de dados e o tempo de carregamento de página médio para a home page que depende de três das consultas expostas por este serviço no momento.

É um problema que ocorre quando o cache é implementado *dados obsoletos* – ou seja, os dados que foram alterados em uma versão desatualizada, mas a fonte permanecem no cache. Uma maneira simples de atenuar esse problema é usar pequenas durações de cache, pois há benefícios adicionais limitados para estender o comprimento de dados é armazenado em cache para um aplicativo ocupado. Por exemplo, considere uma página que faz com que uma consulta de banco de dados único, e é solicitado 10 vezes por segundo. Se esta página é armazenada em cache por um minuto, resultará no número de consultas de banco de dados feitas por minuto para soltar de 600 para 1, uma redução de 99,8%. Se em vez disso, a duração do cache foi feita uma hora, a redução global seria 99.997%, mas a idade de probabilidade e o potencial de dados obsoletos são ambos aumenta consideravelmente.

Outra abordagem é proativamente remover entradas de cache quando os dados que eles contêm são atualizados. Todas as entradas individuais podem ser removidas se a chave for conhecida:

```csharp
_cache.Remove(cacheKey);
```

Se seu aplicativo expõe a funcionalidade para atualizar as entradas que ele armazena em cache, você pode remover as entradas de cache correspondentes no seu código que executa as atualizações. Às vezes, pode haver muitas entradas diferentes que dependem de um determinado conjunto de dados. Nesse caso, pode ser útil criar dependências entre as entradas de cache, usando um CancellationChangeToken. Com um CancellationChangeToken, você pode expirar várias entradas de cache de uma vez ao cancelar o token.

```csharp
// configure CancellationToken and add entry to cache
var cts = new CancellationTokenSource();
_cache.Set("cts", cts);
_cache.Set(cacheKey,
itemToCache,
new CancellationChangeToken(cts.Token));

// elsewhere, expire the cache by cancelling the token\
_cache.Get<CancellationTokenSource>("cts").Cancel();
```

>[!div class="step-by-step"]
[Anterior] (develop-asp-net-core-mvc-apps.md) [Avançar] (test-asp-net-core-mvc-apps.md)
