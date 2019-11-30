---
title: 'Como: adicionar opções de consulta a uma consulta de serviço de dados (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- querying the data service [WCF Data Services]
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: e4258526-557e-4e96-91e1-2175400c7c8f
ms.openlocfilehash: 7b5a9c15f2d46c89abf8fb5bc0f4be99e501a267
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569179"
---
# <a name="how-to-add-query-options-to-a-data-service-query-wcf-data-services"></a>Como: adicionar opções de consulta a uma consulta de serviço de dados (WCF Data Services)
WCF Data Services permite consultar um serviço de dados de um aplicativo cliente baseado em .NET Framework usando as classes de serviço de dados do cliente geradas. A maneira mais fácil de fazer isso é compor uma expressão de consulta LINQ (consulta integrada à linguagem) que inclui as opções de consulta desejadas. Você também pode chamar uma série de métodos de consulta LINQ para compor uma consulta equivalente. Por fim, você pode usar o método <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> para adicionar opções de consulta a uma consulta. Em cada um desses casos, o URI gerado pelo cliente inclui o conjunto de entidades solicitadas com as opções de consulta selecionadas aplicadas. Para obter mais informações, consulte [consultando o serviço de dados](querying-the-data-service-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criados quando você conclui o guia de [início rápido do WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como compor uma expressão de consulta LINQ que retorna somente pedidos com um custo de frete de mais de $30 e que ordena os resultados pela data de remessa em ordem decrescente.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinq)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinq](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinq)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como compor uma consulta LINQ usando métodos de consulta LINQ equivalentes à consulta anterior.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqexpression)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpression](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqexpression)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o para o método <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> para criar um <xref:System.Data.Services.Client.DataServiceQuery%601> que seja equivalente aos exemplos anteriores.  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptions)]
 [!code-vb[Astoria Northwind Client#AddQueryOptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptions)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar a opção de consulta `$orderby` para filtrar e ordenar objetos de pedidos retornados pela propriedade Freight.  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#orderwithfilter)]  
  
## <a name="see-also"></a>Consulte também

- [Querying the Data Service](querying-the-data-service-wcf-data-services.md) (Consultando o serviço de dados)
- [Como fazer para projetar resultados de consulta](how-to-project-query-results-wcf-data-services.md)
