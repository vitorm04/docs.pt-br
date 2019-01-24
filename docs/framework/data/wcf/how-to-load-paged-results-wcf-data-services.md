---
title: 'Como: Carregar resultados (WCF Data Services) paginados'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: bb786ea4-f3ef-4ad3-9a41-3a0b7feb6a1f
ms.openlocfilehash: 2305b57e636a252d50210e889c16b5035fbd813d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54555317"
---
# <a name="how-to-load-paged-results-wcf-data-services"></a>Como: Carregar resultados (WCF Data Services) paginados
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] permite que o serviço de dados limitar o número de entidades que são retornados em um única feed de resposta. Quando isso acontece, a entrada final no feed contém um link para a próxima página de dados. O URI para a próxima página de dados é obtido chamando o <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> método da <xref:System.Data.Services.Client.QueryOperationResponse%601>, que é retornado quando o <xref:System.Data.Services.Client.DataServiceQuery%601> é executado. O URI representado por esse objeto, em seguida, é usado para carregar a próxima página de resultados. Para obter mais informações, consulte [Carregando conteúdo adiado](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [início rápido do WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa uma `do…while` loop carregar `Customers` entidades de um resultados paginados do serviço de dados.  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getcustomerspaged)]
 [!code-vb[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getcustomerspaged)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo retorna relacionado `Orders` entidades com cada `Customers` entidade e usa um `do…while` loop carregar `Customers` páginas de entidades e aninhado `while` loop para carregar páginas de relacionados `Orders` entidades do serviço de dados .  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getcustomerspagednested)]
 [!code-vb[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getcustomerspagednested)]  
  
## <a name="see-also"></a>Consulte também
- [Carregando conteúdo adiado](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)
- [Como: Carregar entidades relacionadas](../../../../docs/framework/data/wcf/how-to-load-related-entities-wcf-data-services.md)
