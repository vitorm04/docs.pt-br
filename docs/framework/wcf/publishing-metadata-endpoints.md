---
title: Publicando pontos de extremidade de metadados
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 4c6ac81f0c97415dc21ff3346178dd1e9936b7a5
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319903"
---
# <a name="publishing-metadata-endpoints"></a>Publicando pontos de extremidade de metadados
Os serviços Windows Communication Foundation (WCF) publicam metadados publicando um ou mais pontos de extremidade de metadados. A publicação de metadados de serviço torna os metadados disponíveis usando protocolos padronizados, como WS-MetadataExchange (MEX) e solicitações HTTP/GET. Os pontos de extremidade de metadados são semelhantes a outros pontos de extremidade de serviço, pois têm um endereço, uma associação e um contrato, e podem ser adicionados a um host de serviço por meio da configuração ou no código. Para habilitar a publicação de pontos de extremidade de metadados, você deve adicionar o comportamento de serviço <xref:System.ServiceModel.Description.ServiceMetadataBehavior> ao serviço.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como publicar metadados para um serviço usando um arquivo de configuração](./feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Demonstra como configurar um serviço WCF para publicar metadados para que os clientes possam recuperar os metadados usando uma solicitação WS-MetadataExchange ou HTTP/GET usando a cadeia de caracteres de consulta `?wsdl`.  
  
 [Como publicar metadados para um serviço utilizando código](./feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Demonstra como habilitar a publicação de metadados para um serviço WCF no código para que os clientes possam recuperar os metadados usando uma solicitação WS-MetadataExchange ou HTTP/GET usando a cadeia de caracteres de consulta `?wsdl`.  
  
## <a name="see-also"></a>Consulte também

- [Publicando metadados](./feature-details/publishing-metadata.md)
