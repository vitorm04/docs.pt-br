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
ms.openlocfilehash: c49e0b170743332d6cc3aaef7e5503eabab52d97
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91182786"
---
# <a name="how-to-load-paged-results-wcf-data-services"></a>Como carregar resultados paginados (WCF Data Services)

WCF Data Services permite que o serviço de dados limite o número de entidades retornadas em um único feed de resposta. Quando isso acontece, a entrada final no feed contém um link para a próxima página de dados. O URI para a próxima página de dados é obtido chamando o <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> método de <xref:System.Data.Services.Client.QueryOperationResponse%601> , que é retornado quando o <xref:System.Data.Services.Client.DataServiceQuery%601> é executado. O URI representado por esse objeto é usado para carregar a próxima página de resultados. Para obter mais informações, consulte [carregando conteúdo adiado](loading-deferred-content-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criados quando você conclui o guia de [início rápido do WCF Data Services](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  

 Este exemplo usa um `do…while` loop para carregar `Customers` entidades de um resultado paginado do serviço de dados.  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getcustomerspaged)]
 [!code-vb[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getcustomerspaged)]  
  
## <a name="example"></a>Exemplo  

 Este exemplo retorna `Orders` entidades relacionadas com cada `Customers` entidade e usa um `do…while` loop para carregar `Customers` páginas de entidades e um `while` loop aninhado para carregar páginas de entidades relacionadas `Orders` do serviço de dados.  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getcustomerspagednested)]
 [!code-vb[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getcustomerspagednested)]  
  
## <a name="see-also"></a>Veja também

- [Carregar conteúdo adiado](loading-deferred-content-wcf-data-services.md)
- [Como: carregar entidades relacionadas](how-to-load-related-entities-wcf-data-services.md)
