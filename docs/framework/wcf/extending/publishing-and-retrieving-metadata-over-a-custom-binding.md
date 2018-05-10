---
title: Publicando e recuperando metadados através de uma associação personalizada
ms.date: 03/30/2017
ms.assetid: 904e11b4-d90e-45c6-9ee5-c3472c90008c
ms.openlocfilehash: 528f7662ee3a1f956427e5e42f540816f55027f8
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="publishing-and-retrieving-metadata-over-a-custom-binding"></a>Publicando e recuperando metadados através de uma associação personalizada
O <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> fornece suporte para adicionar o ponto de extremidade de metadados para um serviço. Esses pontos de extremidade de metadados podem responder a solicitações HTTP GET em uma URL que tenha um `?wsdl` querystring e solicitações GET do WS-transferência conforme definido na especificação WS-MetadataExchange (MEX). Pontos de extremidade MEX implementam o <xref:System.ServiceModel.Description.IMetadataExchange?displayProperty=nameWithType> contrato.  
  
## <a name="publishing-metadata-over-a-custom-binding"></a>Publicando metadados através de uma associação personalizada  
 Os pontos de extremidade de metadados HTTP GET e HTTPS obter pontos de extremidade de metadados estão habilitados, definindo o <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A?displayProperty=nameWithType> propriedades `true`. As ligações para esses pontos de extremidade não podem ser configuradas.  
  
 O <xref:System.ServiceModel.Description.IMetadataExchange> contrato, no entanto, pode ser usado com qualquer ponto de extremidade, incluindo aquelas que usam associações personalizadas, como <xref:System.ServiceModel.Description.IMetadataExchange> pontos de extremidade são idênticos a qualquer outro ponto de extremidade de serviço de Windows Communication Foundation (WCF). Se você souber como modificar a configuração de uma associação fornecida pelo sistema ou você sabe como configurar um <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>, em seguida, você pode configurar uma associação para uso com um <xref:System.ServiceModel.Description.IMetadataExchange> ponto de extremidade.  
  
## <a name="retrieving-metadata-over-a-custom-binding"></a>Recuperando metadados através de uma associação personalizada  
 Metadados podem ser recuperados de pontos de extremidade de metadados Get do HTTP e HTTPS Get usando solicitações de HTTP ou HTTPS GET padrão.  
  
 Para recuperar metadados de um ponto de extremidade de metadados MEX que geralmente você pode usar uma das ligações de MEX padrão com suporte do WCF. Para obter mais informações, consulte <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>. O <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> tipo e a ferramenta Svcutil.exe selecionar automaticamente um essas associações MEX padrão com base no endereço do ponto de extremidade de metadados especificado.  
  
 Se um ponto de extremidade de metadados MEX usa outra associação de uma das ligações de MEX padrão, você pode configurar a associação usada pelo <xref:System.ServiceModel.Description.MetadataExchangeClient> usando código ou oferecendo um <xref:System.ServiceModel.Description.IMetadataExchange> configuração de ponto de extremidade do cliente. A ferramenta Svcutil.exe carrega automaticamente do seu arquivo de configuração de um <xref:System.ServiceModel.Description.IMetadataExchange> configuração de ponto de extremidade do cliente que tenha o mesmo nome que o esquema de URI para o endereço de ponto de extremidade de metadados.  
  
## <a name="security"></a>Segurança  
 Ao publicar metadados sobre uma associação personalizada, certifique-se de que a associação fornece o suporte de segurança que exige de seus metadados. Por exemplo, para evitar a divulgação de informações e certifique-se de que o cliente tem o direito para obter os metadados, você pode tornar seu aplicativo e seus metadados mais seguro configurando seu <xref:System.ServiceModel.Description.IMetadataExchange> ponto de extremidade para exigir a autenticação e criptografia. O exemplo [personalizado proteger metadados de ponto de extremidade](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) demonstra esse cenário.  
  
## <a name="see-also"></a>Consulte também  
 [Protegendo serviços](../../../../docs/framework/wcf/securing-services.md)  
 [Associações de WS-MetadataExchange](../../../../docs/framework/wcf/extending/ws-metadataexchange-bindings.md)  
 [Como configurar uma associação personalizada do WS-Metadata Exchange](../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)  
 [Como recuperar metadados por meio de uma associação não MEX](../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
