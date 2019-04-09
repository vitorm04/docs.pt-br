---
title: 'Como: Anexar uma entidade existente ao DataServiceContext (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
ms.assetid: e3f2d71d-434c-4e98-91c3-95adae4702b6
ms.openlocfilehash: 6fa8e9d66fa89eb058aafd1e74164097b7f5c3a3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59157842"
---
# <a name="how-to-attach-an-existing-entity-to-the-dataservicecontext-wcf-data-services"></a>Como: Anexar uma entidade existente ao DataServiceContext (WCF Data Services)
Quando uma entidade já existe em um serviço de dados, o [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteca de cliente permite que você anexe um objeto que representa a entidade diretamente para o <xref:System.Data.Services.Client.DataServiceContext> sem primeiro executar uma consulta. Para obter mais informações, consulte [atualização do serviço de dados](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
 O exemplo deste tópico usa o serviço de dados de exemplo Northwind e as classes de serviço de dados do cliente geradas automaticamente. Esse serviço e as classes de dados do cliente são criadas quando você concluir o [início rápido do WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como criar um existente `Customer` objeto que contém as alterações a serem salvas para o serviço de dados. O objeto é anexado ao contexto e o <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> método é chamado para marcar o objeto anexado como <xref:System.Data.Services.Client.EntityStates.Modified> antes do <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> método é chamado.  
  
 [!code-csharp[Astoria Northwind Client#AttachObject](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#attachobject)]
 [!code-vb[Astoria Northwind Client#AttachObject](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#attachobject)]  
  
## <a name="see-also"></a>Consulte também

- [Biblioteca de cliente do WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
