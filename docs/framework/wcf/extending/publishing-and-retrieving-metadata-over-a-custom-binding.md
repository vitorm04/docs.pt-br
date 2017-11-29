---
title: "Publicando e recuperando metadados através de uma associação personalizada"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 904e11b4-d90e-45c6-9ee5-c3472c90008c
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 83aba5cc938b926285f78efd1ab8d62493ad59d7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="publishing-and-retrieving-metadata-over-a-custom-binding"></a>Publicando e recuperando metadados através de uma associação personalizada
O <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> fornece suporte para adicionar o ponto de extremidade de metadados para um serviço. Esses pontos de extremidade de metadados podem responder a solicitações HTTP GET em uma URL que tenha um `?wsdl` querystring e solicitações GET do WS-transferência conforme definido na especificação WS-MetadataExchange (MEX). Pontos de extremidade MEX implementam o <xref:System.ServiceModel.Description.IMetadataExchange?displayProperty=nameWithType> contrato.  
  
## <a name="publishing-metadata-over-a-custom-binding"></a>Publicando metadados através de uma associação personalizada  
 Os pontos de extremidade de metadados HTTP GET e HTTPS obter pontos de extremidade de metadados estão habilitados, definindo o <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A?displayProperty=nameWithType> propriedades `true`. As ligações para esses pontos de extremidade não podem ser configuradas.  
  
 O <xref:System.ServiceModel.Description.IMetadataExchange> contrato, no entanto, pode ser usado com qualquer ponto de extremidade, incluindo aquelas que usam associações personalizadas, como <xref:System.ServiceModel.Description.IMetadataExchange> pontos de extremidade são idênticos a qualquer outro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ponto de extremidade de serviço. Se você souber como modificar a configuração de uma associação fornecida pelo sistema ou você sabe como configurar um <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>, em seguida, você pode configurar uma associação para uso com um <xref:System.ServiceModel.Description.IMetadataExchange> ponto de extremidade.  
  
## <a name="retrieving-metadata-over-a-custom-binding"></a>Recuperando metadados através de uma associação personalizada  
 Metadados podem ser recuperados de pontos de extremidade de metadados Get do HTTP e HTTPS Get usando solicitações de HTTP ou HTTPS GET padrão.  
  
 Para recuperar metadados de um ponto de extremidade de metadados MEX geralmente não é pode usar uma das ligações de MEX padrão suportadas pelo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>. O <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> tipo e a ferramenta Svcutil.exe selecionar automaticamente um essas associações MEX padrão com base no endereço do ponto de extremidade de metadados especificado.  
  
 Se um ponto de extremidade de metadados MEX usa outra associação de uma das ligações de MEX padrão, você pode configurar a associação usada pelo <xref:System.ServiceModel.Description.MetadataExchangeClient> usando código ou oferecendo um <xref:System.ServiceModel.Description.IMetadataExchange> configuração de ponto de extremidade do cliente. A ferramenta Svcutil.exe carrega automaticamente do seu arquivo de configuração de um <xref:System.ServiceModel.Description.IMetadataExchange> configuração de ponto de extremidade do cliente que tenha o mesmo nome que o esquema de URI para o endereço de ponto de extremidade de metadados.  
  
## <a name="security"></a>Segurança  
 Ao publicar metadados sobre uma associação personalizada, certifique-se de que a associação fornece o suporte de segurança que exige de seus metadados. Por exemplo, para evitar a divulgação de informações e certifique-se de que o cliente tem o direito para obter os metadados, você pode tornar seu aplicativo e seus metadados mais seguro configurando seu <xref:System.ServiceModel.Description.IMetadataExchange> ponto de extremidade para exigir a autenticação e criptografia. O exemplo [personalizado proteger metadados de ponto de extremidade](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) demonstra esse cenário.  
  
## <a name="see-also"></a>Consulte também  
 [Securing Services](../../../../docs/framework/wcf/securing-services.md) (Protegendo serviços)  
 [Associações do WS-MetadataExchange](../../../../docs/framework/wcf/extending/ws-metadataexchange-bindings.md)  
 [Como: configurar um personalizado WS-Metadata Exchange associação](../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)  
 [Como: recuperar metadados através de uma associação não MEX](../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
