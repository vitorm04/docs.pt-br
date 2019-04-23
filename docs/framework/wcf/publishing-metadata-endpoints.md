---
title: Publicando pontos de extremidade de metadados
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 143a46ce18a0d9dee89bbbffac9be9a467e951df
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59121726"
---
# <a name="publishing-metadata-endpoints"></a>Publicando pontos de extremidade de metadados
Serviços Windows Communication Foundation (WCF) publicam metadados, um ou mais pontos de extremidade de metadados de publicação. Publicação de metadados de serviço disponibiliza os metadados usando protocolos padronizados, como solicitações de WS-MetadataExchange (MEX) e HTTP/GET. Pontos de extremidade de metadados são semelhantes aos outros pontos de extremidade de serviço que têm um endereço, uma ligação e um contrato, e eles podem ser adicionados a um host de serviço por meio da configuração ou no código. Para habilitar a publicação pontos de extremidade de metadados, você deve adicionar o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> comportamento para o serviço de serviço.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: Publicar metadados para um serviço usando um arquivo de configuração](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Demonstra como configurar um serviço WCF para publicar metadados para que os clientes podem recuperar os metadados usando um WS-MetadataExchange ou uma solicitação HTTP/GET usando o `?wsdl` cadeia de caracteres de consulta.  
  
 [Como: Publicar metadados para um serviço usando código](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Demonstra como habilitar a publicação de metadados para um serviço WCF em código para que os clientes podem recuperar os metadados usando um WS-MetadataExchange ou uma solicitação HTTP/GET usando o `?wsdl` cadeia de caracteres de consulta.  
  
## <a name="see-also"></a>Consulte também

- [Publicando metadados](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
