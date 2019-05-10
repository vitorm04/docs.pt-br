---
title: O carregamento adiado de conteúdo (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 32f9b588-c832-44c4-a7e0-fcce635df59a
ms.openlocfilehash: db0127712ab0cb4586b364abf899bcf4765632d7
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645597"
---
# <a name="loading-deferred-content-wcf-data-services"></a>O carregamento adiado de conteúdo (WCF Data Services)
Por padrão, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] limita a quantidade de dados que retorna uma consulta. No entanto, você pode carregar explicitamente dados adicionais, incluindo entidades relacionadas, dados de respostas paginadas e fluxos de dados binários do serviço de dados quando ele for necessário. Este tópico descreve como carregar tal conteúdo adiado para o aplicativo.  
  
## <a name="related-entities"></a>Entidades relacionadas  
 Quando você executa uma consulta, apenas as entidades no conjunto de entidades endereçados são retornadas. Por exemplo, quando uma consulta no serviço de dados Northwind retorna `Customers` entidades, por padrão, relacionado `Orders` entidades não são retornadas, mesmo que haja uma relação entre `Customers` e `Orders`. Além disso, quando a paginação está habilitada no serviço de dados, você deverá carregar explicitamente as páginas de dados subsequentes do serviço. Há duas maneiras de carregar entidades relacionadas:  
  
- **O carregamento adiantado**: Você pode usar o `$expand` opção de consulta para solicitar que a consulta retorne entidades relacionadas por uma associação para a entidade que defina a consulta solicitada. Use o <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> método em de <xref:System.Data.Services.Client.DataServiceQuery%601> para adicionar o `$expand` opção para a consulta que é enviada para o serviço de dados. Você pode solicitar que vários entidade relacionada define, separando-os por vírgula, como no exemplo a seguir. Todas as entidades que solicitado pela consulta são retornadas em uma única resposta. O exemplo a seguir retorna `Order_Details` e `Customers` junto com o `Orders` conjunto de entidades:  
  
     [!code-csharp[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetailsspecific)]  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] limita a 12, o número de conjuntos de entidades que podem ser incluídos em uma única consulta por meio de `$expand` opção de consulta.  
  
- **Carregamento explícito**: Você pode chamar o <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> método no <xref:System.Data.Services.Client.DataServiceContext> instância para carregar explicitamente entidades relacionadas. Cada chamada para o <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> método cria uma solicitação separada para o serviço de dados. O exemplo a seguir carrega explicitamente `Order_Details` para um `Orders` entidade:  
  
     [!code-csharp[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedorderdetailsspecific)]  
  
 Quando você considera qual opção usar, perceba que há um equilíbrio entre o número de solicitações para o serviço de dados e a quantidade de dados que são retornados em uma única resposta. Use o carregamento adiantado quando seu aplicativo requer que objetos associados e você quiser evitar a latência de solicitações adicionais para recuperá-los explicitamente. No entanto, se há casos em que o aplicativo precisa apenas dos dados para instâncias específicas de entidade relacionada, considere carregar explicitamente essas entidades, chamando o <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> método. Para obter mais informações, confira [Como: Carregar entidades relacionadas](../../../../docs/framework/data/wcf/how-to-load-related-entities-wcf-data-services.md).  
  
## <a name="paged-content"></a>Conteúdo paginado  
 Quando a paginação está habilitada no serviço de dados, o número de entradas no feed que o serviço de dados retorna é limitado pela configuração do serviço de dados. Limites de página podem ser definidos separadamente para cada conjunto de entidades. Para obter mais informações, consulte [Configurando o serviço de dados](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Quando a paginação está habilitada, a entrada final no feed contém um link para a próxima página de dados. Esse link está contido em um <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> objeto. Obter o URI para a próxima página de dados chamando o <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> método em de <xref:System.Data.Services.Client.QueryOperationResponse%601> retornado quando o <xref:System.Data.Services.Client.DataServiceQuery%601> é executado. Retornado <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> objeto, em seguida, é usado para carregar a próxima página de resultados. Você deve enumerar o resultado da consulta antes de chamar o <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> método. Considere o uso de um `do…while` loop para enumerar pela primeira vez o resultado da consulta e, em seguida, verificar um `non-null` valor do próximo link. Quando o <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> retorn `null` (`Nothing` no Visual Basic), não há nenhuma página de resultados adicionais para a consulta original. A exemplo a seguir mostra um `do…while` paginável de loop que carrega os dados do cliente do serviço de dados de exemplo Northwind.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadnextlink)]
 [!code-vb[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadnextlink)]  
  
 Quando um solicitações de consulta que entidades relacionadas são retornados em uma única resposta junto com o conjunto de entidade solicitada, limites de paginação podem afetar feeds aninhados que são incluídas embutidas com a resposta. Por exemplo, quando um limite de paginação é definido no serviço de dados de exemplo Northwind para o `Customers` conjunto de entidades, também pode ser definido um limite de paginação independentes para relacionado `Orders` entidade definida, como no exemplo a seguir do Northwind.svc.cs arquivos que Define o serviço de dados de exemplo Northwind.  
  
 [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
 [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
 Nesse caso, você deve implementar a paginação para ambos os nível superior `Customers` e aninhada `Orders` feeds de entidade. A exemplo a seguir mostra a `while` loop usada para carregar páginas de `Orders` entidades relacionadas para um selecionado `Customers` entidade.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadnextorderslink)]
 [!code-vb[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadnextorderslink)]  
  
 Para obter mais informações, confira [Como: Carregar resultados paginados](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md).  
  
## <a name="binary-data-streams"></a>Fluxos de dados binários  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] permite que você acesse dados de objeto binário grande (BLOB) como um fluxo de dados. Streaming adia o carregamento de dados binários, até que ela é necessária e o cliente com mais eficiência pode processar esses dados. Para tirar proveito dessa funcionalidade, o serviço de dados deve implementar o <xref:System.Data.Services.Providers.IDataServiceStreamProvider> provedor. Para obter mais informações, consulte [provedor de Streaming](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md). Quando o streaming está habilitado, os tipos de entidade são retornados sem os dados binários relacionados. Nesse caso, você deve usar o <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> método da <xref:System.Data.Services.Client.DataServiceContext> classe para acessar o fluxo de dados para os dados binários do serviço. Da mesma forma, usar o <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> método para adicionar ou alterar os dados binários para uma entidade como um fluxo. Para obter mais informações, consulte [trabalhando com dados binários](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md).  
  
## <a name="see-also"></a>Consulte também

- [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
- [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md) (Consultando o serviço de dados)
