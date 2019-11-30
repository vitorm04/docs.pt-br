---
title: Como carregar resultados paginados (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: bb786ea4-f3ef-4ad3-9a41-3a0b7feb6a1f
ms.openlocfilehash: d651a66ac619e46d3ec6b46b194436f51300ff25
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569033"
---
# <a name="how-to-load-paged-results-wcf-data-services"></a>Como carregar resultados paginados (WCF Data Services)
WCF Data Services permite que o serviço de dados limite o número de entidades retornadas em um único feed de resposta. Quando isso acontece, a entrada final no feed contém um link para a próxima página de dados. O URI para a próxima página de dados é obtido chamando o método <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> do <xref:System.Data.Services.Client.QueryOperationResponse%601>, que é retornado quando o <xref:System.Data.Services.Client.DataServiceQuery%601> é executado. O URI representado por esse objeto é usado para carregar a próxima página de resultados. Para obter mais informações, consulte [carregando conteúdo adiado](loading-deferred-content-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criados quando você conclui o guia de [início rápido do WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa um loop `do…while` para carregar `Customers` entidades de um resultado paginado do serviço de dados.  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getcustomerspaged)]
 [!code-vb[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getcustomerspaged)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo retorna entidades de `Orders` relacionadas com cada entidade `Customers` e usa um loop `do…while` para carregar `Customers` páginas de entidades e um loop de `while` aninhado para carregar páginas de entidades de `Orders` relacionadas do serviço de dados.  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getcustomerspagednested)]
 [!code-vb[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getcustomerspagednested)]  
  
## <a name="see-also"></a>Consulte também

- [Carregando conteúdo adiado](loading-deferred-content-wcf-data-services.md)
- [Como carregar entidades relacionadas](how-to-load-related-entities-wcf-data-services.md)
