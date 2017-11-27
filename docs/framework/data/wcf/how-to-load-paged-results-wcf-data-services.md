---
title: "Como: carregar paginável resultados (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: bb786ea4-f3ef-4ad3-9a41-3a0b7feb6a1f
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 91414ac4d392b9c042c9e236d2bfb69b44ead4ff
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-load-paged-results-wcf-data-services"></a>Como: carregar paginável resultados (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]permite que o serviço de dados limitar o número de entidades que são retornados em uma única resposta de feed. Quando isso acontece, a entrada final no feed contém um link para a próxima página de dados. O URI para a próxima página de dados é obtido chamando o <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> método o <xref:System.Data.Services.Client.QueryOperationResponse%601>, que é retornado quando o <xref:System.Data.Services.Client.DataServiceQuery%601> é executado. O URI representado pelo objeto, em seguida, é usado para carregar a próxima página de resultados. Para obter mais informações, consulte [carregar conteúdo adiada](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo usa um `do…while` loop carregar `Customers` entidades de um resultados paginados do serviço de dados.  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getcustomerspaged)]
 [!code-vb[Astoria Northwind Client#GetCustomersPaged](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getcustomerspaged)]  
  
## <a name="example"></a>Exemplo  
 Este exemplo retorna relacionado `Orders` entidades com cada `Customers` entidade e usa um `do…while` loop carregar `Customers` páginas de entidades e um aninhados `while` loop para carregar páginas relacionados `Orders` entidades do serviço de dados .  
  
 [!code-csharp[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getcustomerspagednested)]
 [!code-vb[Astoria Northwind Client#GetCustomersPagedNested](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getcustomerspagednested)]  
  
## <a name="see-also"></a>Consulte também  
 [Carregamento adiado conteúdo](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 [Como: carregar entidades relacionadas](../../../../docs/framework/data/wcf/how-to-load-related-entities-wcf-data-services.md)
