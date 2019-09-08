---
title: Publicando e recuperando metadados através de uma associação personalizada
ms.date: 03/30/2017
ms.assetid: 904e11b4-d90e-45c6-9ee5-c3472c90008c
ms.openlocfilehash: 329daa39a14ed4c839ecbaa6cf9df036ceabee34
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795507"
---
# <a name="publishing-and-retrieving-metadata-over-a-custom-binding"></a>Publicando e recuperando metadados através de uma associação personalizada
O <xref:System.ServiceModel.Description.ServiceMetadataBehavior?displayProperty=nameWithType> fornece suporte para adicionar um ponto de extremidade de metadados a um serviço. Esses pontos de extremidade de metadados podem responder a solicitações HTTP Get em uma URL que tenha `?wsdl` uma QueryString e para solicitações GET de WS-Transfer, conforme definido na especificação WS-MetadataExchange (MEX). Os pontos de extremidade MEX implementam o <xref:System.ServiceModel.Description.IMetadataExchange?displayProperty=nameWithType> contrato.  
  
## <a name="publishing-metadata-over-a-custom-binding"></a>Publicando metadados em uma associação personalizada  
 Os pontos de extremidade de metadados de Get de http e de metadados Get de HTTPS são habilitados <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A?displayProperty=nameWithType> definindo <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A?displayProperty=nameWithType> as propriedades `true`ou como. As associações para esses pontos de extremidade não podem ser configuradas.  
  
 O <xref:System.ServiceModel.Description.IMetadataExchange> contrato, no entanto, pode ser usado com qualquer ponto de extremidade, incluindo aqueles que usam associações <xref:System.ServiceModel.Description.IMetadataExchange> personalizadas, porque os pontos de extremidade são idênticos a qualquer outro ponto final de serviço do Windows Communication Foundation (WCF). Se você souber como modificar a configuração de uma associação fornecida pelo sistema ou souber como configurar uma <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>, poderá configurar uma associação para uso com um <xref:System.ServiceModel.Description.IMetadataExchange> ponto de extremidade.  
  
## <a name="retrieving-metadata-over-a-custom-binding"></a>Recuperando metadados em uma associação personalizada  
 Os metadados podem ser recuperados de pontos de extremidade HTTP Get e HTTPS Get de metadados usando solicitações HTTP GET padrão ou HTTPS.  
  
 Para recuperar metadados de um ponto de extremidade de metadados MEX, você geralmente pode usar uma das associações MEX padrão com suporte pelo WCF. Para obter mais informações, consulte <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType>. O <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> tipo e a ferramenta svcutil. exe selecionam automaticamente uma dessas associações de MEX padrão com base no endereço do ponto de extremidade de metadados especificado.  
  
 Se um ponto de extremidade de metadados MEX usar uma associação diferente de uma das associações de MEX padrão, você poderá configurar a associação usada <xref:System.ServiceModel.Description.MetadataExchangeClient> pelo código de uso ou fornecendo <xref:System.ServiceModel.Description.IMetadataExchange> uma configuração de ponto de extremidade do cliente. A ferramenta svcutil. exe é carregada automaticamente de seu arquivo de <xref:System.ServiceModel.Description.IMetadataExchange> configuração uma configuração de ponto de extremidade de cliente que tem o mesmo nome que o esquema de URI para o endereço do ponto de extremidade de metadados.  
  
## <a name="security"></a>Segurança  
 Ao publicar metadados em uma associação personalizada, verifique se a associação fornece o suporte de segurança que seus metadados exigem. Por exemplo, para evitar a divulgação de informações e garantir que o cliente tenha o direito de obter os metadados, você pode tornar seus metadados e seu aplicativo mais seguros <xref:System.ServiceModel.Description.IMetadataExchange> configurando seu ponto de extremidade para exigir autenticação e criptografia. O [ponto de extremidade de metadados seguro personalizado](../samples/custom-secure-metadata-endpoint.md) de exemplo demonstra esse cenário.  
  
## <a name="see-also"></a>Consulte também

- [Protegendo serviços](../securing-services.md)
- [Associações de WS-MetadataExchange](ws-metadataexchange-bindings.md)
- [Como: Configurar uma associação de WS-Metadata Exchange personalizada](how-to-configure-a-custom-ws-metadata-exchange-binding.md)
- [Como: Recuperar metadados em uma associação não MEX](how-to-retrieve-metadata-over-a-non-mex-binding.md)
