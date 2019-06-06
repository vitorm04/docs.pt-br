---
title: Trabalhar com os dados em aplicativos ASP.NET Core
description: Arquitetar aplicativos Web modernos com o ASP.NET Core e o Azure | Trabalhando com os dados em aplicativos ASP.NET Core
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 9f765acce89bec1fd73e9c43a6e7d75d78be785d
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66423993"
---
# <a name="working-with-data-in-aspnet-core-apps"></a>Trabalhando com os dados em aplicativos ASP.NET Core

> "Os dados são uma coisa preciosa e vão durar mais do que os próprios sistemas."
>
> Tim Berners-Lee

O acesso a dados é uma parte importante de praticamente qualquer aplicativo de software. O ASP.NET Core é compatível com uma variedade de opções de acesso a dados, incluindo o Entity Framework Core (e também o Entity Framework 6) e pode trabalhar com qualquer estrutura de acesso a dados do .NET. A escolha de qual estrutura de acesso a dados usar depende das necessidades do aplicativo. A abstração dessas opções dos projetos de ApplicationCore e de interface do usuário e o encapsulamento dos detalhes de implementação na Infraestrutura ajudam a produzir um software testável e com acoplamento flexível.

## <a name="entity-framework-core-for-relational-databases"></a>Entity Framework Core (para bancos de dados relacionais)

Caso você esteja escrevendo um novo aplicativo ASP.NET Core que precisa trabalhar com os dados relacionais, o EF Core (Entity Framework Core) é a maneira recomendada para que seu aplicativo acesse os dados. O EF Core é um O/RM (mapeador relacional de objeto) que permite aos desenvolvedores do .NET persistir objetos bidirecionalmente em uma fonte de dados. Elimina a necessidade da maioria do código de acesso a dados que os desenvolvedores geralmente precisam escrever. Assim como o ASP.NET Core, o EF Core foi totalmente reformulado para dar suporte a aplicativos modulares multiplataforma. Você adiciona-o ao aplicativo como um pacote NuGet, configura-o em Startup e solicita-o por meio da injeção de dependência sempre que precisar dela.

Para usar o EF Core com um banco de dados do SQL Server, execute o seguinte comando da CLI do dotnet:

dotnet add package Microsoft.EntityFrameworkCore.SqlServer

Para adicionar suporte para uma fonte de dados InMemory para teste:

dotnet add package Microsoft.EntityFrameworkCore.InMemory

### <a name="the-dbcontext"></a>O DbContext

Para trabalhar com o EF Core, você precisa de uma subclasse de <xref:Microsoft.EntityFrameworkCore.DbContext>. Essa classe contém propriedades que representam coleções de entidades com as quais seu aplicativo trabalhará. A amostra de eShopOnWeb inclui um CatalogContext com coleções de itens, marcas e tipos:

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

O DbContext deve ter um construtor que aceite DbContextOptions e passa esse argumento para o construtor DbContext base. Observe que, se você tiver apenas um DbContext no aplicativo, poderá passar uma instância de DbContextOptions, mas se tiver mais de um, precisará usar o tipo genérico DbContextOptions\<T>, passando o tipo DbContext como o parâmetro genérico.

### <a name="configuring-ef-core"></a>Configurando o EF Core

No aplicativo ASP.NET Core, normalmente, você configurará o EF Core no método ConfigureServices. O EF Core usa um DbContextOptionsBuilder, que é compatível com vários métodos de extensão úteis para simplificar sua configuração. Para configurar o CatalogContext para que ele use um banco de dados do SQL Server com uma cadeia de conexão definida em Configuration, adicione o seguinte código ao ConfigureServices:

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

Para usar o banco de dados em memória:

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

Depois de instalar o EF Core, criar um tipo filho do DbContext e configurá-lo em ConfigureServices, você estará pronto para usar o EF Core. Você pode solicitar uma instância do tipo DbContext em qualquer serviço que precisar dela e começar a trabalhar com as entidades persistentes usando o LINQ como se elas apenas estivessem em uma coleção. O EF Core faz o trabalho de converter as expressões LINQ em consultas SQL para armazenar e recuperar os dados.

Você pode ver as consultas executadas pelo EF Core configurando um agente e garantindo que seu nível está definido com, pelo menos, Informações, conforme mostrado na Figura 8-1.

![](./media/image8-1.png)

Figura 8-1 Registrando em log consultas do EF Core no console

### <a name="fetching-and-storing-data"></a>Buscando e armazenando dados

Para recuperar dados do EF Core, acesse a propriedade apropriada e use o LINQ para filtrar o resultado. Também use o LINQ para executar a projeção, transformando o resultado de um tipo para outro. O seguinte exemplo recupera CatalogBrands, ordenadas por nome, filtradas por sua propriedade Enabled e projetadas em um tipo SelectListItem:

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

É importante, no exemplo acima, adicionar a chamada a ToListAsync para executar a consulta imediatamente. Caso contrário, a instrução atribuirá um IQueryable\<SelectListItem> a brandItems, que não será executado enquanto não for enumerado. Há vantagens e desvantagens em retornar resultados IQueryable de métodos. Ele permite que a consulta construída pelo EF Core seja modificada ainda mais, mas também pode resultar em erros que ocorrem apenas em tempo de execução, caso as operações sejam adicionadas à consulta que o EF Core não pode converter. Em geral, é mais seguro passar todos os filtros para o método que executa o acesso a dados e retornar uma coleção em memória (por exemplo, List\<T>) como o resultado.

O EF Core controla as alterações nas entidades que ele busca da persistência. Para salvar as alterações em uma entidade controlada, basta chamar o método SaveChanges no DbContext, verificando se ela é a mesma instância de DbContext que foi usada para buscar a entidade. A adição e remoção de entidades é feita diretamente na propriedade DbSet apropriada, novamente com uma chamada a SaveChanges para executar os comandos de banco de dados. O exemplo a seguir demonstra como adicionar, atualizar e remover entidades da persistência.

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

O EF Core é compatível com métodos síncronos e assíncronos para busca e salvamento. Em aplicativos Web, é recomendável usar o padrão async/await com os métodos async, de modo que os threads do servidor Web não sejam bloqueados enquanto aguardam a conclusão das operações de acesso a dados.

### <a name="fetching-related-data"></a>Buscando dados relacionados

Quando o EF Core recupera entidades, ele popula todas as propriedades armazenadas diretamente nessa entidade no banco de dados. Propriedades de navegação, como listas de entidades relacionadas, não são populadas e podem ter seu valor definido como nulo. Isso garante que o EF Core não busca mais dados do que necessário, o que é especialmente importante para aplicativos Web, que devem processar solicitações e retornar respostas de uma maneira eficiente e com agilidade. Para incluir relações com uma entidade usando o _carregamento adiantado_, especifique a propriedade usando o método de extensão Include na consulta, conforme mostrado:

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

Você pode incluir várias relações e também incluir sub-relações usando ThenInclude. O EF Core executará uma única consulta para recuperar o conjunto resultante de entidades. Como alternativa, você pode incluir propriedades de navegação de propriedades de navegação passando uma cadeia de caracteres separada por '.' para o método de extensão `.Include()`, da seguinte forma:

```csharp
    .Include(“Items.Products”)
```

Além de encapsular a lógica de filtragem, uma especificação pode especificar a forma dos dados a serem retornados, incluindo quais propriedades devem ser populadas. O exemplo eShopOnWeb inclui várias especificações que demonstram o encapsulamento das informações de carregamento adiantado dentro da especificação. Veja aqui como a especificação é usada como parte de uma consulta:

```csharp
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```

Outra opção para carregar dados relacionados é usar o _carregamento explícito_. O carregamento explícito permite carregar dados adicionais em uma entidade que já foi recuperada. Como isso envolve uma solicitação separada para o banco de dados, isso não é recomendado para aplicativos Web, que devem minimizar o número de viagens de ida e volta de banco de dados feitas por solicitação.

O _carregamento lento_ é um recurso que carrega automaticamente os dados relacionados conforme eles são referenciados pelo aplicativo. Foi adicionado o suporte para carregamento lento na versão 2.1 do EF Core. O carregamento lento não está habilitado por padrão e requer a instalação do `Microsoft.EntityFrameworkCore.Proxies`. Assim como acontece com o carregamento explícito, o carregamento lento normalmente deve estar desabilitado para aplicativos Web, pois seu uso resulta em mais consultas de banco de dados em cada solicitação da Web. Infelizmente, a sobrecarga causada pelo carregamento lento muitas vezes passa despercebida no momento do desenvolvimento, quando a latência é pequena e, geralmente, os conjuntos de dados usados para teste também são pequenos. No entanto, na produção, com mais usuários, mais dados e mais latência, as solicitações de banco de dados adicionais podem resultar em baixo desempenho dos aplicativos Web que usam o carregamento lento de forma intensiva.

[Avoid Lazy Loading Entities in Web Applications](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications) (Evitar entidades de carregamento lento em aplicativos Web)

### <a name="encapsulating-data"></a>Encapsulando dados

O EF Core é compatível com vários recursos que permitem que o modelo encapsule seu próprio estado corretamente. Um problema comum nos modelos de domínio é que eles expõem propriedades de navegação de coleção como tipos de lista publicamente acessíveis. Isso permite que qualquer colaborador manipule o conteúdo desses tipos de coleção, podendo ignorar regras de negócios importantes relacionadas à coleção e deixar o objeto em um estado inválido. A solução para isso é expor o acesso somente leitura às coleções relacionadas e fornecer métodos explicitamente definindo de que forma os clientes podem manipulá-las, como neste exemplo:

```csharp
public class Basket : BaseEntity
{
    public string BuyerId { get; set; }
    private readonly List<BasketItem> _items = new List<BasketItem>();
    public IReadOnlyCollection<BasketItem> Items => _items.AsReadOnly();

    public void AddItem(int catalogItemId, decimal unitPrice, int quantity = 1)
    {
        if (!Items.Any(i => i.CatalogItemId == catalogItemId))
        {
            _items.Add(new BasketItem()
            {
                CatalogItemId = catalogItemId,
                Quantity = quantity,
                UnitPrice = unitPrice
            });
            return;
        }
        var existingItem = Items.FirstOrDefault(i => i.CatalogItemId == catalogItemId);
        existingItem.Quantity += quantity;
    }
}
```

Observe que esse tipo de entidade não expõe uma propriedade pública `List` ou `ICollection`, mas sim um tipo `IReadOnlyCollection` que encapsula o tipo de Lista subjacente. Ao usar esse padrão, é possível indicar ao Entity Framework Core que ele deve usar o campo de suporte da seguinte forma:

```csharp
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```

Outra maneira de melhorar seu modelo de domínio é usar objetos de valor para os tipos que não têm identidade e são diferenciados apenas por suas propriedades. O uso desses tipos como propriedades das entidades pode ajudar a manter a lógica específica do objeto de valor ao qual pertence e pode evitar a duplicação de lógica entre várias entidades que usam o mesmo conceito. No Entity Framework Core, você pode manter os objetos de valor na mesma tabela que a entidade proprietária configurando o tipo como uma entidade própria, da seguinte forma:

```csharp
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```

Neste exemplo, a propriedade `ShipToAddress` é do tipo `Address`. `Address` é um objeto de valor com várias propriedades, como `Street` e `City`. O EF Core mapeia o objeto `Order` à tabela dele com uma coluna por propriedade `Address`, prefixando cada nome de coluna com o nome da propriedade. Neste exemplo, a tabela `Order` incluiria colunas, como `ShipToAddress_Street` e `ShipToAddress_City`.

[O EF Core 2.2 introduz o suporte para coleções de entidades próprias](https://docs.microsoft.com/ef/core/what-is-new/ef-core-2.2#collections-of-owned-entities)

### <a name="resilient-connections"></a>Conexões resilientes

Recursos externos, como bancos de dados SQL, ocasionalmente, podem não estar disponíveis. Em caso de indisponibilidade temporária, os aplicativos podem usar a lógica de repetição para evitar gerar uma exceção. Em geral, essa técnica é conhecida como _resiliência de conexão_. Implemente sua [própria técnica de repetição com retirada exponencial](https://docs.microsoft.com/azure/architecture/patterns/retry) pela tentativa de repetir com um tempo de espera que aumenta exponencialmente, até atingir um número máximo de repetições. Essa técnica aceita o fato de que os recursos de nuvem podem estar intermitentemente não disponíveis por curtos períodos, resultando na falha de algumas solicitações.

Para o BD SQL do Azure, o Entity Framework Core já fornece resiliência interna de conexão de banco de dados e lógica de repetição. Mas você precisará habilitar a estratégia de execução do Entity Framework para cada conexão de DbContext, caso deseje ter conexões do EF Core resilientes.

Por exemplo, o código a seguir no nível de conexão do EF Core permite conexões SQL resilientes que serão repetidas se a conexão falhar.

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

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a>Estratégias de execução e transações explícitas que usam BeginTransaction e várias DbContexts

Quando novas tentativas são habilitadas em conexões do EF Core, cada operação executada que usa o EF Core se torna sua própria operação repetível. Cada consulta e cada chamada a SaveChanges serão repetidas como uma unidade se ocorrer uma falha temporária.

No entanto, se o código iniciar uma transação usando BeginTransaction, você estará definindo seu próprio grupo de operações que precisam ser tratadas como uma unidade: tudo dentro da transação precisará ser revertido caso ocorra uma falha. Você verá uma exceção como a mostrada a seguir se tentar executar essa transação ao usar uma estratégia de execução do EF (política de repetição) e incluir várias chamadas SaveChanges de diversos DbContexts na transação.

System.InvalidOperationException: A estratégia de execução configurada 'SqlServerRetryingExecutionStrategy' não é compatível com transações iniciadas pelo usuário. Use a estratégia de execução retornada por 'DbContext.Database.CreateExecutionStrategy()' para executar todas as operações na transação como uma unidade repetível.

A solução é invocar manualmente a estratégia de execução do EF com um delegado que representa tudo que precisa ser executado. Se ocorrer uma falha temporária, a estratégia de execução invocará o delegado novamente. O seguinte código mostra como implementar essa abordagem:

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

O primeiro DbContext é o \_catalogContext e o segundo DbContext está dentro do objeto \_integrationEventLogService. Por fim, a ação de Confirmação é executada em vários DbContexts e usando uma Estratégia de Execução do EF.

> ### <a name="references--entity-framework-core"></a>Referências – Entity Framework Core
>
> - **Documentação do EF Core**  
>   <https://docs.microsoft.com/ef/>
> - **EF Core: Dados relacionados**  
>   <https://docs.microsoft.com/ef/core/querying/related-data>
> - **Evitar entidades de carregamento lento em aplicativos ASP.NET**  
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a>EF Core ou micro-ORM?

Embora o EF Core seja uma ótima opção para o gerenciamento da persistência e, na maioria das vezes, encapsule os detalhes de banco de dados para abstraí-los dos desenvolvedores de aplicativos, ele não é a única opção. Outra alternativa de software livre popular é o [Dapper](https://github.com/StackExchange/Dapper), um assim chamado micro-ORM. Um micro-ORM é uma ferramenta leve e menos completa para o mapeamento de objetos para estruturas de dados. No caso do Dapper, seu design visa o foco no desempenho, em vez do encapsulamento total das consultas subjacentes usadas por ele para recuperar e atualizar os dados. Como ele não abstrai o SQL do desenvolvedor, o Dapper fica "mais próximo do metal" e permite aos desenvolvedores escreverem as consultas exatas que desejam usar para determinada operação de acesso a dados.

O EF Core tem dois recursos significativos que os separam do Dapper, mas também contribuem com a sobrecarga de desempenho. O primeiro é a conversão de expressões LINQ em SQL. Essas conversões são armazenadas em cache, mas ainda assim há sobrecarga na execução na primeira vez. O segundo é o controle de alterações em entidades (de forma que instruções de atualização eficientes possam ser geradas). Esse comportamento pode ser desativado para consultas específicas com a extensão AsNotTracking. O EF Core também gera consultas SQL que geralmente são muito eficientes e, de qualquer modo, perfeitamente aceitáveis do ponto de vista de desempenho. No entanto, caso precise ter um controle refinado sobre a consulta precisa a ser executada, passe um SQL personalizado (ou execute um procedimento armazenado) usando o EF Core também. Nesse caso, o Dapper ainda supera o EF Core, mas somente um pouco. Julie Lerman apresenta alguns dados de desempenho em seu artigo do MSDN de maio de 2016 [Dapper, Entity Framework e aplicativos híbridos](https://msdn.microsoft.com/magazine/mt703432.aspx). Encontre dados de parâmetro de comparação de desempenho adicionais para uma variedade de métodos de acesso a dados [no site do Dapper](https://github.com/StackExchange/Dapper).

Para ver a diferença entre a sintaxe do Dapper e do EF Core, considere estas duas versões do mesmo método para recuperar uma lista de itens:

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

Caso você precise criar gráficos de objetos mais complexos com o Dapper, precisará escrever as consultas associadas (em vez de adicionar um método Include como faria no EF Core). Isso é compatível com uma variedade de sintaxes, incluindo um recurso chamado Mapeamento Múltiplo, que permite mapear linhas individuais para vários objetos mapeados. Por exemplo, considerando uma classe Post com uma propriedade Owner do tipo User, o seguinte SQL retorna todos os dados necessários:

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

Cada linha retornada inclui os dados de User e Post. Como os dados de User devem ser anexados aos dados de Post por meio de sua propriedade Owner, a seguinte função é usada:

```csharp
(post, user) => { post.Owner = user; return post; }
```

A listagem de código completa para retornar uma coleção de postagens com a propriedade Owner populada com os dados de usuário associados é:

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

Como ele oferece menos encapsulamento, o Dapper exige que os desenvolvedores saibam mais sobre como seus dados são armazenados, como consultá-los de forma eficiente e codificar mais para buscá-los. Quando o modelo é alterado, em vez de simplesmente criar uma nova migração (outro recurso do EF Core) e/ou atualizar as informações de mapeamento em um local em um DbContext, cada consulta afetada deve ser atualizada. Essas consultas não têm garantias de tempo de compilação e, portanto, podem ser interrompidas no tempo de execução em resposta a alterações no modelo ou no banco de dados, dificultando a detecção rápida de erros. Em compensação por essa vantagem, o Dapper oferece um desempenho extremamente rápido.

Para a maioria dos aplicativos e a maioria das partes de quase todos os aplicativos, o EF Core oferece um desempenho aceitável. Portanto, seus benefícios de produtividade do desenvolvedor provavelmente superam a sobrecarga de desempenho. Para consultas que podem se beneficiar com o cache, a consulta real pode ser executada apenas em um pequeno percentual do tempo, tornando irrelevantes as pequenas diferenças no desempenho da consulta.

## <a name="sql-or-nosql"></a>SQL ou NoSQL

Tradicionalmente, bancos de dados relacionais como o SQL Server dominaram o marketplace em armazenamento de dados persistente, mas não são a única solução disponível. Bancos de dados NoSQL, como o [MongoDB](https://www.mongodb.com/what-is-mongodb), oferecem uma abordagem diferente para armazenar objetos. Em vez de mapear objetos para tabelas e linhas, outra opção é serializar o grafo de objeto inteiro e armazenar o resultado. Os benefícios dessa abordagem são, pelo menos inicialmente, simplicidade e desempenho. É certamente mais simples armazenar um único objeto serializado com uma chave do que decompor o objeto em muitas tabelas com relações e atualizar as linhas que podem ter sido alteradas desde a última recuperação do objeto do banco de dados. Da mesma forma, a busca e a desserialização de um único objeto de um repositório baseado em chaves geralmente são muito mais rápidas e mais fáceis do que junções complexas ou várias consultas de banco de dados necessárias para compor totalmente o mesmo objeto de um banco de dados relacional. A falta de bloqueios ou transações ou de um esquema fixo também torna os bancos de dados NoSQL muito receptivos ao dimensionamento em vários computadores, dando suporte a conjuntos de dados muito grandes.

Por outro lado, os bancos de dados NoSQL (como são normalmente chamados) trazem algumas desvantagens. Os bancos de dados relacionais usam a normalização para impor a consistência e evitar a duplicação de dados. Isso reduz o tamanho total do banco de dados e garante que as atualizações nos dados compartilhados estejam disponíveis imediatamente em todo o banco de dados. Em um banco de dados relacional, uma tabela Address pode referenciar uma tabela Country por ID, de modo que, se o nome de um país/região for alterado, os registros de endereço se beneficiarão com a atualização sem que eles mesmos precisem ser atualizados. No entanto, em um banco de dados NoSQL, Address e seu Country associado podem ser serializados como parte de muitos objetos armazenados. Uma atualização em um nome de país/região exige que todos esses objetos sejam atualizados, em vez de uma única linha. Os bancos de dados relacionais também podem garantir a integridade relacional pela imposição de regras como chaves estrangeiras. Normalmente, os bancos de dados NoSQL não oferecem essas restrições em seus dados.

Outra complexidade com a qual os bancos de dados NoSQL precisar lidar é o controle de versão. Quando as propriedades de um objeto são alteradas, ele pode não ser desserializado das versões anteriores que foram armazenadas. Portanto, todos os objetos existentes que têm uma versão (anterior) serializada do objeto precisam ser atualizados para que estejam em conformidade com seu novo esquema. Isso não é conceitualmente diferente de um banco de dados relacional, no qual as alterações de esquema às vezes exigem scripts de atualização ou atualizações de mapeamento. No entanto, o número de entradas que precisa ser modificado costuma ser muito maior na abordagem NoSQL, porque há mais duplicação de dados.

Em bancos de dados NoSQL, é possível armazenar várias versões de objetos, algo para o qual os bancos de dados relacionais de esquema fixo normalmente não dão suporte. No entanto, nesse caso, o código do aplicativo precisará levar em conta a existência de versões anteriores de objetos, adicionando mais complexidade.

Normalmente, os bancos de dados NoSQL não impõem o [ACID](https://en.wikipedia.org/wiki/ACID), o que significa que eles trazem vantagens de desempenho e escalabilidade comparado aos bancos de dados relacionais. Eles são adequados para conjuntos de dados extremamente grandes e objetos que não são apropriados para o armazenamento em estruturas de tabela normalizadas. Não há nenhum motivo pelo qual um único aplicativo não possa aproveitar ambos os bancos de dados relacional e NoSQL, usando cada um deles nos casos em que for mais adequado.

## <a name="azure-documentdb"></a>Azure DocumentDB

O Azure DocumentDB é um serviço de banco de dados NoSQL totalmente gerenciado que oferece armazenamento de dados sem esquemas baseado em nuvem. O DocumentDB foi criado para desempenho rápido e previsível, alta disponibilidade, dimensionamento elástico e distribuição global. Apesar de ser um banco de dados NoSQL, os desenvolvedores podem usar funcionalidades avançadas e conhecidas de consultas SQL em dados JSON. Todos os recursos do DocumentDB são armazenados como documentos JSON. Os recursos são gerenciados como _itens_, que são documentos que contém metadados, e _feeds_, que são coleções de itens. A Figura 8-2 mostra a relação entre os diferentes recursos do DocumentDB.

![A relação hierárquica entre os recursos do DocumentDB, um banco de dados JSON NoSQL](./media/image8-2.png)

**Figura 8-2.** Organização de recursos do DocumentDB.

A linguagem de consulta do DocumentDB é uma interface simples mas avançada para a consulta de documentos JSON. A linguagem é compatível com um subconjunto da gramática ANSI SQL e adiciona integração profunda de objeto JavaScript, matrizes, construção de objeto e invocação de função.

**Referências – DocumentDB**

- Introdução ao DocumentDB  
  <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a>Outras opções de persistência

Além das opções de armazenamento relacional e NoSQL, os aplicativos ASP.NET Core podem usar o Armazenamento do Azure para armazenar uma variedade de formatos de dados e arquivos de forma escalonável e baseada em nuvem. O Armazenamento do Azure é altamente escalonável e, portanto, você pode começar armazenando pequenas quantidades de dados e aumentar até armazenar centenas ou terabytes, caso seu aplicativo precise. O Armazenamento do Azure é compatível com quatro tipos de dados:

- Armazenamento de Blobs para armazenamento de texto não estruturado ou binário, também conhecido como armazenamento de objeto.

- Armazenamento de Tabelas para conjuntos de dados estruturados, acessíveis por meio de chaves de linha.

- Armazenamento de Filas para mensagens confiáveis baseadas em fila.

- Armazenamento de Arquivos para acesso a arquivos compartilhados entre aplicativos locais e as máquinas virtuais do Azure.

**Referências – Armazenamento do Azure**

- Introdução ao Armazenamento do Azure  
  <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a>Cache

Em aplicativos Web, cada solicitação da Web deve ser concluída no menor tempo possível. Uma maneira de fazer isso é limitar o número de chamadas externas que o servidor deve fazer para concluir a solicitação. O cache envolve o armazenamento de uma cópia dos dados no servidor (ou em outro armazenamento de dados que é consultado com mais facilidade do que a fonte dos dados). Os aplicativos Web, e especialmente aplicativos Web tradicionais não SPA, precisam criar toda a interface do usuário a cada solicitação. Isso geralmente envolve fazer muitas das mesmas consultas de banco de dados repetidamente de uma solicitação de usuário para a próxima. Na maioria dos casos, esses dados são raramente alterados e, portanto, há pouca justificativa para solicitá-los constantemente do banco de dados. O ASP.NET Core é compatível com cache de resposta, armazenamento em cache de páginas inteiras e cache de dados, que é compatível com um comportamento de cache mais granular.

Ao implementar o cache, é importante ter em mente a separação de interesses. Evite a implementação da lógica de cache na lógica de acesso a dados ou na interface do usuário. Em vez disso, encapsule o cache em suas próprias classes e use a configuração para gerenciar seu comportamento. Isso segue os princípios de Aberto/Fechado e Responsabilidade Única e facilitará o gerenciamento de como você usa o cache em seu aplicativo à medida que ele cresce.

### <a name="aspnet-core-response-caching"></a>Cache de resposta do ASP.NET Core

O ASP.NET Core é compatível com dois níveis de cache de resposta. O primeiro nível não armazena nada em cache no servidor, mas adiciona cabeçalhos HTTP que instruem os clientes e servidores proxy a armazenar as respostas em cache. Isso é implementado pela adição do atributo ResponseCache a controladores ou ações individuais:

```csharp
    [ResponseCache(Duration = 60)]
    public IActionResult Contact()
    { }

    ViewData["Message"] = "Your contact page.";
    return View();
}
```

O exemplo anterior resultará no seguinte cabeçalho que está sendo adicionado à resposta, instruindo os clientes a armazenarem o resultado em cache por até 60 segundos.

Cache-Control: public,max-age=60

Para adicionar cache na memória do lado do servidor ao aplicativo, referencie o pacote NuGet Microsoft.AspNetCore.ResponseCaching e, em seguida, adicione o middleware de cache de resposta. Este middleware é configurado em ConfigureServices e na Configuração de Inicialização:

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

O middleware de cache de resposta armazenará em cache automaticamente as respostas baseadas em um conjunto de condições, que pode ser personalizado. Por padrão, apenas respostas 200 (OK) solicitadas por meio de métodos GET ou HEAD são armazenadas em cache. Além disso, as solicitações devem ter uma resposta com um cabeçalho público Cache-Control: e não pode incluir cabeçalhos de Authorization ou Set-Cookie. Consulte uma [lista completa das condições de cache usadas pelo middleware de cache de resposta](/aspnet/core/performance/caching/middleware#conditions-for-caching).

### <a name="data-caching"></a>Cache de dados

Em vez de (ou além de) armazenar em cache as respostas da Web completas, você pode armazenar em cache os resultados de consultas de dados individuais. Para isso, você pode usar o cache em memória no servidor Web ou usar [um cache distribuído](/aspnet/core/performance/caching/distributed). Esta seção demonstrará como implementar o cache em memória.

Adicione suporte para o cache em memória (ou distribuído) em ConfigureServices:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

Lembre-se de adicionar também o pacote NuGet Microsoft.Extensions.Caching.Memory.

Depois de adicionar o serviço, solicite IMemoryCache por meio da injeção de dependência sempre que precisar acessar o cache. Neste exemplo, o CachedCatalogService usa o padrão de design Proxy (ou Decorador), fornecendo uma implementação alternativa de ICatalogService que controla o acesso à implementação de CatalogService subjacente ou que adiciona um comportamento a ela.

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

Para configurar o aplicativo para usar a versão armazenada em cache do serviço, mas ainda permitir que o serviço obtenha a instância de CatalogService necessária em seu construtor, adicione o seguinte em ConfigureServices:

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

Com isso em vigor, as chamadas de banco de dados para buscar os dados de catálogo serão feitas apenas uma vez por minuto, em vez de a cada solicitação. Dependendo do tráfego para o site, isso pode ter um impacto muito significativo no número de consultas feitas para o banco de dados e no tempo médio de carregamento de página da home page que atualmente depende de todas as três consultas expostas por esse serviço.

Um problema que ocorre quando o cache é implementado são _dados obsoletos_ – ou seja, dados que foram alterados na fonte, mas cuja versão desatualizada permanece no cache. Uma maneira simples de atenuar esse problema é usar pequenas durações de cache, pois há benefícios adicionais limitados em estender a duração de armazenamento em cache dos dados para um aplicativo ocupado. Por exemplo, considere uma página que faz uma consulta de banco de dados individual e é solicitada 10 vezes por segundo. Se essa página for armazenada em cache por um minuto, isso resultará no número de consultas de banco de dados feitas por minuto para reduzir de 600 para 1, uma redução de 99,8%. Se, em vez disso, a duração do cache foi feita em uma hora, a redução geral é de 99,997%, mas agora, a probabilidade e a idade potencial dos dados obsoletos são aumentadas consideravelmente.

Outra abordagem é remover as entradas de cache de forma proativa quando os dados que elas contêm são atualizados. As entradas individuais podem ser removidas se sua chave é conhecida:

```csharp
_cache.Remove(cacheKey);
```

Se o aplicativo expõe a funcionalidade para atualizar as entradas que ele armazena em cache, você pode remover as entradas de cache correspondentes no código que executa as atualizações. Às vezes, pode haver muitas entradas diferentes que dependem de determinado conjunto de dados. Nesse caso, pode ser útil criar dependências entre as entradas de cache, usando um CancellationChangeToken. Com um CancellationChangeToken, você pode expirar várias entradas de cache de uma vez com o cancelamento do token.

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

O cache pode melhorar consideravelmente o desempenho das páginas da Web que solicitam repetidamente os mesmos valores do banco de dados. Meça o desempenho da página e o acesso a dados antes de aplicar o cache e somente aplique o cache quando houver necessidade de melhoria. O cache consome recursos de memória do servidor Web e aumenta a complexidade do aplicativo, portanto, é importante que você não se apresse em otimizar usando essa técnica.

>[!div class="step-by-step"]
>[Anterior](develop-asp-net-core-mvc-apps.md)
>[Próximo](test-asp-net-core-mvc-apps.md)
