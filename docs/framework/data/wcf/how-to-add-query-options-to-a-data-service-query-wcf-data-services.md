---
title: 'Como: adicionar opções de consulta para uma consulta de serviço de dados (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: e4258526-557e-4e96-91e1-2175400c7c8f
ms.openlocfilehash: 330581c699ca4beede3333315844af084f27e672
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-add-query-options-to-a-data-service-query-wcf-data-services"></a>Como: adicionar opções de consulta para uma consulta de serviço de dados (WCF Data Services)
O [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] permite consultar um serviço de dados de um aplicativo cliente baseado em .NET Framework usando as classes de serviço de dados do cliente geradas. É o mais fácil de fazer isso para compor uma expressão de consulta de linguagem LINQ (consulta integrada) que inclui as opções de consulta desejado. Você também pode chamar uma série de métodos de consulta LINQ para compor uma consulta equivalente. Finalmente, você pode usar o <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> para adicionar opções de consulta para uma consulta. Em cada um desses casos, o URI que é gerado pelo cliente inclui o conjunto de entidades solicitado com as opções de consulta selecionada aplicadas. Para obter mais informações, consulte [consultando o Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como criar uma expressão de consulta LINQ que retorna apenas as ordens com um custo de frete de mais de US $30 e que os resultados por data de remessa em ordem decrescente.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinq)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinq)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como para compor uma consulta LINQ usando métodos de consulta LINQ que é equivalente à consulta anterior.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqexpression)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqexpression)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar para o <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> método para criar um <xref:System.Data.Services.Client.DataServiceQuery%601> que é equivalente dos exemplos anteriores.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptions)]
 [!code-vb[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptions)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `$orderby` opção de consulta de filtro e ordem retornada objetos pedidos pela propriedade Freight.  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#orderwithfilter)]  
  
## <a name="see-also"></a>Consulte também  
 [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md) (Consultando o serviço de dados)  
 [Como fazer para projetar resultados de consulta](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)
