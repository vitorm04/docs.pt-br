---
title: Publicando metadados
ms.date: 03/30/2017
helpviewer_keywords:
- meatadata [WCF], publishing
ms.assetid: 3a56831a-cabc-45c0-bd02-12e2e9bd7313
ms.openlocfilehash: 97836cef12cd1f220e97d2c38d2dca1b878d7484
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59183064"
---
# <a name="publishing-metadata"></a>Publicando metadados
Serviços Windows Communication Foundation (WCF) publicam metadados, um ou mais pontos de extremidade de metadados de publicação. Publicação de metadados de serviço disponibiliza os metadados usando protocolos padronizados, como solicitações de WS-MetadataExchange (MEX) e HTTP/GET. Pontos de extremidade de metadados são semelhantes aos outros pontos de extremidade de serviço que têm um endereço, uma ligação e um contrato, e eles podem ser adicionados a um host de serviço por meio de configuração ou código obrigatório.  
  
## <a name="publishing-metadata-endpoints"></a>Publicando pontos de extremidade de metadados  
 Para publicar pontos de extremidade de metadados para um serviço WCF, primeiro você deve adicionar o <xref:System.ServiceModel.Description.ServiceMetadataBehavior> comportamento para o serviço de serviço. Adicionando um <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> instância permite que seu serviço para expor pontos de extremidade de metadados. Depois de adicionar o <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> comportamento de serviço, em seguida, você pode expor pontos de extremidade de metadados que suportam o protocolo MEX ou que respondem a solicitações HTTP/GET.  
  
 O <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> usa um <xref:System.ServiceModel.Description.WsdlExporter> para exportar metadados para todos os pontos de extremidade de serviço em seu serviço. Para obter mais informações sobre como exportar metadados de um serviço, consulte [exportando e importando metadados](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md).  
  
 O <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> adiciona um <xref:System.ServiceModel.Description.ServiceMetadataExtension> instância como uma extensão para o host de serviço. O <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> fornece a implementação para os protocolos de publicação de metadados. Você também pode usar o <xref:System.ServiceModel.Description.ServiceMetadataExtension?displayProperty=nameWithType> para obter metadados do serviço em tempo de execução acessando o <xref:System.ServiceModel.Description.ServiceMetadataExtension.Metadata%2A?displayProperty=nameWithType> propriedade.  
  
### <a name="mex-metadata-endpoints"></a>Pontos de extremidade de metadados MEX  
 Para adicionar pontos de extremidade de metadados que usam o protocolo MEX, adicionar pontos de extremidade de serviço para seu host de serviço que usam o `IMetadataExchange` contrato de serviço. O WCF inclui um <xref:System.ServiceModel.Description.IMetadataExchange> interface com este nome de contrato de serviço que você pode usar como parte do modelo de programação do WCF. Pontos de extremidade do WS-MetadataExchange ou pontos de extremidade MEX, podem usar uma das ligações de padrão de quatro métodos de fábrica estáticos expõem no <xref:System.ServiceModel.Description.MetadataExchangeBindings> classe para corresponder as associações padrão usadas por ferramentas do WCF como Svcutil.exe. Você também pode configurar pontos de extremidade de metadados MEX usando sua própria associação personalizada.  
  
### <a name="http-get-metadata-endpoints"></a>Pontos de extremidade de metadados do HTTP GET  
 Para adicionar um ponto de extremidade de metadados para o serviço que responde a solicitações HTTP/GET, defina a <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> propriedade sobre a <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> para `true`. Você também pode configurar um ponto de extremidade de metadados que usa HTTPS, definindo o <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> propriedade em de <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> para `true`.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: publicar metadados para um serviço usando um arquivo de configuração](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 Demonstra como configurar um serviço WCF para publicar metadados para que os clientes podem recuperar os metadados usando um WS-MetadataExchange ou uma solicitação HTTP/GET usando o `?wsdl` cadeia de caracteres de consulta.  
  
 [Como: publicar metadados utilizando código para um serviço](../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-code.md)  
 Demonstra como habilitar a publicação de metadados para um serviço WCF em código para que os clientes podem recuperar os metadados usando um WS-MetadataExchange ou uma solicitação HTTP/GET usando o `?wsdl` cadeia de caracteres de consulta.  
  
## <a name="reference"></a>Referência  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>  
  
 <xref:System.ServiceModel.Description.IMetadataExchange>  
  
 <xref:System.ServiceModel.Description.ServiceMetadataExtension>  
  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings>  
  
## <a name="see-also"></a>Consulte também

- [Exportando e importando metadados](../../../../docs/framework/wcf/feature-details/exporting-and-importing-metadata.md)
