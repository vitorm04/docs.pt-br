---
title: 'Como: anexar uma entidade existente para o DataServiceContext (WCF Data Services)'
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
helpviewer_keywords: WCF Data Services, changing data
ms.assetid: e3f2d71d-434c-4e98-91c3-95adae4702b6
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d90d8783ac3039b7ed382a2957600376b9bc764f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-attach-an-existing-entity-to-the-dataservicecontext-wcf-data-services"></a>Como: anexar uma entidade existente para o DataServiceContext (WCF Data Services)
Quando uma entidade já existe no serviço de dados, o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteca de cliente permite que você anexar um objeto que representa a entidade diretamente para o <xref:System.Data.Services.Client.DataServiceContext> sem primeiro executar uma consulta. Para obter mais informações, consulte [atualizar o serviço de dados](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como criar um existente `Customer` objeto que contém as alterações a serem salvas para o serviço de dados. O objeto está associado ao contexto e o <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> método é chamado para marcar o objeto anexado como <xref:System.Data.Services.Client.EntityStates.Modified> antes do <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> método é chamado.  
  
 [!code-csharp[Astoria Northwind Client#AttachObject](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#attachobject)]
 [!code-vb[Astoria Northwind Client#AttachObject](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#attachobject)]  
  
## <a name="see-also"></a>Consulte também  
 [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md) (Biblioteca de clientes do WCF Data Services)
