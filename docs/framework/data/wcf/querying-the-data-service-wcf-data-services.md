---
title: Consultando o serviço de dados (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 823e9444-27aa-4f1f-be8e-0486d67f54c0
ms.openlocfilehash: abae49e709fa2e77d641d991dd6e09cf82216732
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517285"
---
# <a name="querying-the-data-service-wcf-data-services"></a>Consultando o serviço de dados (WCF Data Services)
A biblioteca de cliente [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] permite executar consultas em um serviço de dados usando os padrões familiares de programação [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], incluindo LINK (consulta integrada à linguagem). A biblioteca de cliente converte uma consulta, que é definida no cliente como uma instância da classe <xref:System.Data.Services.Client.DataServiceQuery%601>, em uma mensagem de solicitação HTTP GET. A biblioteca recebe a mensagem de resposta e o converte em instâncias de classes de serviço de dados do cliente. Essas classes são rastreadas pelo <xref:System.Data.Services.Client.DataServiceContext> ao qual o <xref:System.Data.Services.Client.DataServiceQuery%601> pertence.  
  
## <a name="data-service-queries"></a>Consultas de serviço de dados  
 A classe genérica <xref:System.Data.Services.Client.DataServiceQuery%601> representa uma consulta que retorna uma coleção de zero ou mais instâncias de tipos de entidades. Uma consulta do serviço de dados sempre pertence a um contexto de serviço de dados existente. Esse contexto mantém as informações do URI de serviço e de metadados necessárias para compor e executar a consulta.  
  
 Quando você usa o **adicionar referência de serviço** caixa de diálogo para adicionar um serviço de dados para um [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]-cliente baseado em aplicativo, uma classe de contêiner de entidade é criado que herda o <xref:System.Data.Services.Client.DataServiceContext> classe. Essa classe inclui as propriedades que retornam instâncias <xref:System.Data.Services.Client.DataServiceQuery%601> tipadas. Existe uma propriedade para cada conjunto de entidades que o serviço de dados expõe. Essas propriedades facilitam a criação de uma instância <xref:System.Data.Services.Client.DataServiceQuery%601>tipada.  
  
 Uma consulta é executada nos seguintes cenários:  
  
-   Quando os resultados são enumerados implicitamente, como:  
  
    -   Quando uma propriedade de <xref:System.Data.Services.Client.DataServiceContext> que representa e o conjunto de entidades é enumerado, como durante uma `foreach` (C#) ou `For Each` loop (Visual Basic).  
  
    -   Quando a consulta é atribuída a uma coleção `List`.  
  
-   Quando o método <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> ou <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> é chamado explicitamente.  
  
-   Quando um operador de execução de consulta LINQ, como <xref:System.Linq.Enumerable.First%2A> ou <xref:System.Linq.Enumerable.Single%2A>, é chamado.  
  
 A consulta a seguir, quando executada, retorna todas as entidades `Customers` do serviço de dados Northwind:  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomersspecific)]  
 [!code-vb[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomersspecific)]  
  
 Para obter mais informações, confira [Como: Executar consultas de serviço de dados](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md).  
  
 O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] cliente dá suporte a consultas para objetos de associação tardia, como quando você usa o *dinâmico* digite C#. No entanto, por questões de desempenho, você sempre deve compor consultas fortemente tipadas no serviço de dados. O cliente não dá suporte ao tipo <xref:System.Tuple> e a objetos dinâmicos.  
  
## <a name="linq-queries"></a>Consultas LINQ  
 Porque o <xref:System.Data.Services.Client.DataServiceQuery%601> classe implementa as <xref:System.Linq.IQueryable%601> interface definida pelo LINQ, o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteca de cliente é capaz de transformar consultas LINQ em dados do conjunto de entidade em um URI que representa uma expressão de consulta avaliada em relação a um serviço de dados recurso. O exemplo a seguir é uma consulta LINQ que equivale à classe <xref:System.Data.Services.Client.DataServiceQuery%601> anterior que retorna `Orders` com um custo de frete superior a US$ 30 e ordena os resultados por custo de frete:  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]  
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]  
  
 Essa consulta LINQ é convertida na seguinte consulta de URI que é executado em baseado no Northwind [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) serviço de dados:  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
> [!NOTE]
>  O conjunto de consultas que podem ser expressas na sintaxe LINQ é mais amplo do que as consultas permitidas na sintaxe URI baseada em REST (Representational State Transfer). Uma classe <xref:System.NotSupportedException> é gerada quando a consulta não pode ser mapeada para um URI no serviço de dados de destino.  
  
 Para obter mais informações, consulte [considerações sobre o LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md).  
  
## <a name="adding-query-options"></a>Adicionando opções de consulta  
 As consultas de serviço de dados dão suporte a todas as opções de consulta que o componente [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]s fornece. Chame o método <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> para acrescentar opções de consulta a uma instância <xref:System.Data.Services.Client.DataServiceQuery%601>. <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> retorna uma nova instância <xref:System.Data.Services.Client.DataServiceQuery%601>, que equivale à consulta original, mas com o novo conjunto de opções de consulta. A consulta a seguir, quando executada, retorna `Orders`, que são filtrados pelo valor `Freight` e ordenados por `OrderID`, em ordem decrescente:  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionsspecific)]  
 [!code-vb[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionsspecific)]  
  
 Você pode usar a opção de consulta `$orderby` para ordenar e filtrar uma consulta com base em uma única propriedade, como no exemplo a seguir, que filtra e ordena os `Orders` retornados com base no valor da propriedade `Freight`:  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#orderwithfilter)]  
  
 Você pode chamar o método <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> consecutivamente para construir expressões de consulta complexas. Para obter mais informações, confira [Como: Adicionar opções de consulta a uma consulta de serviço de dados](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md).  
  
 As opções de consulta oferecem uma outra maneira de expressar os componentes sintáticos de uma consulta LINQ. Para obter mais informações, consulte [considerações sobre o LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md).  
  
> [!NOTE]
>  A opção de consulta `$select` não pode ser adicionada a um URI de consulta usando o método <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>. Recomendamos usar o método LINQ <xref:System.Linq.Enumerable.Select%2A> para que o cliente gere a opção de consulta `$select` no URI de solicitação.  
  
<a name="executingQueries"></a>   
## <a name="client-versus-server-execution"></a>Execução do cliente e execução do servidor  
 O cliente executa uma consulta em duas partes. Sempre que possível, as expressões em uma consulta são avaliadas primeiro no cliente; em seguida, uma consulta baseada em URI é gerada e enviada ao serviço de dados para avaliação em relação aos dados no serviço. Considere a seguinte consulta LINQ:  
  
 [!code-csharp[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryclientevalspecific)]  
 [!code-vb[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryclientevalspecific)]  
  
 Neste exemplo, a expressão `(basePrice – (basePrice * discount))` é avaliada no cliente. Por essa razão, o URI de consulta real `http://localhost:12345/northwind.svc/Products()?$filter=(UnitPrice gt 90.00M) and substringof('bike',ProductName)`, que é enviado para o serviço de dados, contém o valor decimal já calculado de `90` na cláusula de filtro. Outras partes da expressão de filtragem, incluindo a expressão da subcadeia de caracteres, são avaliadas pelo serviço de dados. As expressões que são avaliadas no cliente seguem a semântica CLR (Common Language Runtime), enquanto as expressões enviadas para o serviço de dados dependem da implementação do serviço de dados do protocolo [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]. Você também deve estar ciente dos cenários onde essa avaliação separada pode causar resultados inesperados, por exemplo, quando o cliente e o serviço executam avaliações com base na hora em fusos horários diferentes.  
  
## <a name="query-responses"></a>Respostas de consulta  
 Quando executada, a classe <xref:System.Data.Services.Client.DataServiceQuery%601> retorna <xref:System.Collections.Generic.IEnumerable%601> do tipo de entidade solicitado. Esse resultado da consulta pode ser convertido em um objeto <xref:System.Data.Services.Client.QueryOperationResponse%601>, como no exemplo a seguir:  
  
 [!code-csharp[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getresponsespecific)]
 [!code-vb[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getresponsespecific)]  
  
 As instâncias de tipos de entidade que representam entidades no serviço de dados são criadas no cliente por um processo chamado materialização de objeto. Para obter mais informações, consulte [Materialization de objeto](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md). O objeto <xref:System.Data.Services.Client.QueryOperationResponse%601> implementa <xref:System.Collections.Generic.IEnumerable%601> para fornecer acesso aos resultados da consulta.  
  
 A classe <xref:System.Data.Services.Client.QueryOperationResponse%601> também possui membros a seguir que permitem acessar informações adicionais sobre um resultado da consulta:  
  
-   <xref:System.Data.Services.Client.OperationResponse.Error%2A> - obtém um erro gerado pela operação, caso algum tenha ocorrido.  
  
-   <xref:System.Data.Services.Client.OperationResponse.Headers%2A> - contém a coleção de cabeçalhos de resposta HTTP associados à resposta da consulta.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse.Query%2A> - obtém a classe <xref:System.Data.Services.Client.DataServiceQuery%601> original que gerou <xref:System.Data.Services.Client.QueryOperationResponse%601>.  
  
-   <xref:System.Data.Services.Client.OperationResponse.StatusCode%2A> - obtém o código de resposta HTTP para a resposta da consulta.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> - obtém o número total de entidades no conjunto de entidades quando o método <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> foi chamado na classe <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse.GetContinuation%2A> - retorna um objeto <xref:System.Data.Services.Client.DataServiceQueryContinuation> que contém o URI da próxima página de resultados.  
  
 Por padrão, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] retorna apenas os dados selecionados explicitamente por um URI de consulta. Isso oferece a opção de carregar explicitamente dados adicionais do serviço de dados quando necessário. Uma solicitação será enviada para o serviço de dados toda vez que você carregar explicitamente dados do serviço de dados. Os dados que podem ser explicitamente carregados incluem entidades relacionadas, dados de respostas paginadas e fluxos de dados binários.  
  
> [!NOTE]
>  Como um serviço de dados pode retornar uma resposta paginada, recomendamos que seu aplicativo use o padrão de programação para manipular uma resposta do serviço de dados paginados. Para obter mais informações, consulte [Carregando conteúdo adiado](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 Para reduzir a quantidade de dados retornada por uma consulta, é possível especificar que apenas determinadas propriedades de uma entidade sejam retornadas na resposta. Para obter mais informações, consulte [projeções de consulta](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md).  
  
## <a name="getting-a-count-of-the-total-number-of-entities-in-the-set"></a>Obtendo uma contagem do número total de entidades no conjunto  
 Em alguns cenários, é útil saber o número total de entidades em um conjunto de entidades e não simplesmente o número retornado pela consulta. Chame o método <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> em <xref:System.Data.Services.Client.DataServiceQuery%601> para solicitar que essa contagem total de entidades no conjunto seja incluída no resultado da consulta. Nesse caso, a propriedade <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> da classe <xref:System.Data.Services.Client.QueryOperationResponse%601> retornada retorna o número total de entidades no conjunto.  
  
 Você também pode obter apenas a contagem total de entidades no conjunto como um valor <xref:System.Int32> ou <xref:System.Int64> chamando os métodos <xref:System.Linq.Enumerable.Count%2A> ou <xref:System.Linq.Enumerable.LongCount%2A>, respectivamente. Quando esses métodos são chamados, uma classe <xref:System.Data.Services.Client.QueryOperationResponse%601> não é retornada; somente o valor da contagem é retornado. Para obter mais informações, confira [Como: Determinar o número de entidades retornadas por uma consulta](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md).  
  
## <a name="in-this-section"></a>Nesta seção  
 [Projeções de consulta](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)  
  
 [Materialização de objetos](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)  
  
 [LINQ Considerations](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md) (Considerações sobre LINQ)  
  
 [Como: Executar consultas de serviço de dados](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 [Como: Adicionar opções de consulta a uma consulta de serviço de dados](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)  
  
 [Como: Determinar o número de entidades retornadas por uma consulta](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md)  
  
 [Como: Especifique as credenciais do cliente para um serviço de dados de solicitação](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md)  
  
 [Como: Definir os cabeçalhos da solicitação do cliente](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md)  
  
 [Como: Resultados de consulta do projeto](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)  
  
## <a name="see-also"></a>Consulte também

- [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
