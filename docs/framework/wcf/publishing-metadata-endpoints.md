---
title: Publicando pontos de extremidade de metadados
ms.date: 03/30/2017
ms.assetid: 29cd8a60-dfb7-460c-bf5a-c2b31b782671
ms.openlocfilehash: 6060850b78c890e043dfaf6f242460bc6e0ef627
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="publishing-metadata-endpoints"></a>Publicando pontos de extremidade de metadados
Serviços Windows Communication Foundation (WCF) publicar metadados, um ou mais pontos de extremidade de metadados de publicação. Metadados de serviço de publicação disponibiliza os metadados usando protocolos padronizados, como solicitações de WS-MetadataExchange (MEX) e HTTP/GET. Pontos de extremidade de metadados são semelhantes aos outros pontos de extremidade de serviço que têm um endereço, uma ligação e um contrato e podem ser adicionadas a um host de serviço por meio de configuração ou em código. Para habilitar a publicação pontos de extremidade de metadados, você deve adicionar o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> comportamento para o serviço de serviço.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como publicar metadados para um serviço usando um arquivo de configuração](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Demonstra como configurar um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] serviço para publicar metadados, de forma que os clientes podem recuperar os metadados usando um WS-MetadataExchange ou uma solicitação HTTP/GET usando o `?wsdl` cadeia de caracteres de consulta.  
  
 [Como publicar metadados para um serviço utilizando código](../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Demonstra como habilitar a publicação de metadados para um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] no código de serviço para que os clientes podem recuperar os metadados usando um WS-MetadataExchange ou uma solicitação HTTP/GET usando o `?wsdl` cadeia de caracteres de consulta.  
  
## <a name="see-also"></a>Consulte também  
 [Publicando metadados](../../../docs/framework/wcf/feature-details/publishing-metadata.md)
