---
title: 'Como: Adicionar opções de consulta a uma consulta de serviço de dados (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: e4258526-557e-4e96-91e1-2175400c7c8f
ms.openlocfilehash: 2056b803b34faafdaebb85883de8b76ea2f9dcd8
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59518052"
---
# <a name="how-to-add-query-options-to-a-data-service-query-wcf-data-services"></a>Como: Adicionar opções de consulta a uma consulta de serviço de dados (WCF Data Services)
O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] permite consultar um serviço de dados de um aplicativo cliente baseado em .NET Framework usando as classes de serviço de dados do cliente geradas. O mais fácil de fazer isso é para compor uma expressão de consulta Language Integrated Query (LINQ) que inclui as opções de consulta desejado. Você também pode chamar uma série de métodos de consulta LINQ para compor uma consulta equivalente. Por fim, você pode usar o <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> método adicionar opções de consulta a uma consulta. Em cada um desses casos, o URI que é gerado pelo cliente inclui o conjunto de entidade solicitada com as opções de consulta selecionada aplicadas. Para obter mais informações, consulte [consultando o Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [início rápido do WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como compor uma expressão de consulta LINQ que retorna apenas ordens com um custo de frete de mais de US $30 e que os resultados por data de envio em ordem decrescente.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinq)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinq)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como compor uma consulta LINQ usando métodos de consulta LINQ que equivale à consulta anterior.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqexpression)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqexpression)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o para o <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> método para criar um <xref:System.Data.Services.Client.DataServiceQuery%601> que é equivalente dos exemplos anteriores.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptions)]
 [!code-vb[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptions)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `$orderby` opção de consulta para filtrar e classificar os objetos de pedidos de retornada pela propriedade frete.  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#orderwithfilter)]  
  
## <a name="see-also"></a>Consulte também

- [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md) (Consultando o serviço de dados)
- [Como: Resultados de consulta do projeto](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)
