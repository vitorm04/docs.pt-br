---
title: Publicando e recuperando metadados através de uma associação personalizada
ms.date: 03/30/2017
ms.assetid: 904e11b4-d90e-45c6-9ee5-c3472c90008c
ms.openlocfilehash: 33777358262465e9ecbadd75df8abf066bafcd01
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991205"
---
# <a name="publishing-and-retrieving-metadata-over-a-custom-binding"></a>Publicando e recuperando metadados através de uma associação personalizada
O <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> fornece suporte para adicionar o ponto de extremidade de metadados para um serviço. Esses pontos de extremidade de metadados podem responder a solicitações HTTP GET em uma URL que tem um `?wsdl` querystring e as solicitações GET do WS-Transfer conforme definido na especificação de WS-MetadataExchange (MEX). Pontos de extremidade MEX implementam o <xref:System.ServiceModel.Description.IMetadataExchange?displayProperty=nameWithType> contrato.  
  
## <a name="publishing-metadata-over-a-custom-binding"></a>Publicando metadados através de uma associação personalizada  
 Os pontos de extremidade de metadados HTTP GET e pontos de extremidade HTTPS GET de metadados estão habilitados, definindo o <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A?displayProperty=nameWithType> ou <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A?displayProperty=nameWithType> propriedades a serem `true`. As associações para esses pontos de extremidade não podem ser configuradas.  
  
 O <xref:System.ServiceModel.Description.IMetadataExchange> contrato, no entanto, pode ser usado com qualquer ponto de extremidade, incluindo aqueles que usam ligações personalizadas, pois <xref:System.ServiceModel.Description.IMetadataExchange> pontos de extremidade são idênticos a qualquer outra extremidade de serviço do Windows Communication Foundation (WCF). Se você souber como modificar a configuração de uma associação fornecida pelo sistema ou saber como configurar uma <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>, em seguida, você pode configurar uma associação para uso com um <xref:System.ServiceModel.Description.IMetadataExchange> ponto de extremidade.  
  
## <a name="retrieving-metadata-over-a-custom-binding"></a>Recuperando metadados através de uma associação personalizada  
 Metadados podem ser recuperados do Get de HTTP e HTTPS obter pontos de extremidade de metadados usando solicitações HTTP ou HTTPS GET padrão.  
  
 Para recuperar metadados de um ponto de extremidade de metadados MEX que geralmente pode usar uma das ligações de MEX padrão com suporte do WCF. Para obter mais informações, consulte <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>. O <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> tipo e a ferramenta Svcutil.exe selecionar automaticamente uma dessas associações de MEX padrão com base no endereço do ponto de extremidade de metadados especificado.  
  
 Se um ponto de extremidade de metadados MEX usa uma associação diferente das associações MEX padrão, você pode configurar a associação usada pela <xref:System.ServiceModel.Description.MetadataExchangeClient> usando código ou ao fornecer um <xref:System.ServiceModel.Description.IMetadataExchange> configuração de ponto de extremidade do cliente. A ferramenta Svcutil.exe carrega automaticamente do seu arquivo de configuração um <xref:System.ServiceModel.Description.IMetadataExchange> configuração de ponto de extremidade do cliente que tem o mesmo nome que o esquema de URI para o endereço do ponto de extremidade de metadados.  
  
## <a name="security"></a>Segurança  
 Quando a publicação de metadados sobre uma associação personalizada, certifique-se de que a associação fornece o suporte de segurança que exige que seus metadados. Por exemplo, para evitar a divulgação de informações e verifique se o seu cliente tem o direito de obter os metadados, você pode tornar seus metadados e o seu aplicativo mais seguro configurando seu <xref:System.ServiceModel.Description.IMetadataExchange> ponto de extremidade exigem autenticação e criptografia. O exemplo [ponto de extremidade do personalizado proteger metadados](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) demonstra esse cenário.  
  
## <a name="see-also"></a>Consulte também

- [Protegendo serviços](../../../../docs/framework/wcf/securing-services.md)
- [Associações de WS-MetadataExchange](../../../../docs/framework/wcf/extending/ws-metadataexchange-bindings.md)
- [Como: Configurar um personalizado WS-Metadata Exchange associação](../../../../docs/framework/wcf/extending/how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [Como: Recuperar metadados através de uma associação não MEX](../../../../docs/framework/wcf/extending/how-to-retrieve-metadata-over-a-non-mex-binding.md)
