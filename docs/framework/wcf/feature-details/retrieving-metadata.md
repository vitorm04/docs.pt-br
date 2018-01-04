---
title: Recuperando metadados
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: metadata [WCF], retrieving
ms.assetid: 18d8ba4c-af0f-4827-a50b-4202d767bacc
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfc96c585ba55fbf63283d7cb23fae5b364b0465
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="retrieving-metadata"></a>Recuperando metadados
Recuperação de metadados é o processo de solicitar e recuperar metadados de um ponto de extremidade de metadados, como um ponto de extremidade de metadados do WS-MetadataExchange (MEX) ou um ponto de extremidade de metadados HTTP/GET.  
  
## <a name="retrieving-metadata-from-the-command-line-using-svcutilexe"></a>Recuperando metadados de linha de comando usando Svcutil.exe  
 Você pode recuperar metadados de serviço usando o WS-MetadataExchange ou HTTP/GET solicitações por meio de [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta e passando o `/target:metadata` switch e um endereço. Svcutil.exe baixa os metadados no endereço especificado e salva o arquivo no disco. Svcutil.exe usa um <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instância internamente e carrega da configuração de <xref:System.ServiceModel.Description.IMetadataExchange> configuração de ponto de extremidade cujo nome corresponda ao esquema do endereço passado para Svcutil.exe como entrada.  
  
## <a name="retrieving-metadata-programmatically-using-the-metadataexchangeclient"></a>Recuperando metadados programaticamente usando o MetadataExchangeClient  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]pode recuperar metadados de serviço usando protocolos padronizados, como WS-MetadataExchange e solicitações HTTP/GET. Ambos os protocolos com suporte a <xref:System.ServiceModel.Description.MetadataExchangeClient> tipo. Recuperar metadados de serviço usando o <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> tipo, fornecendo um endereço para o ponto de extremidade de metadados e uma associação opcional. A associação usada por um <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instância pode ser uma das associações padrão da <xref:System.ServiceModel.Description.MetadataExchangeBindings> classe estática, uma associação fornecida pelo usuário ou uma associação carregado de uma configuração de ponto de extremidade para o `IMetadataExchange` contrato. O <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> também pode resolver referências de URL de HTTP a metadados usando o <xref:System.Net.HttpWebRequest> tipo.  
  
 Por padrão, um <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instância está associada a um único <xref:System.ServiceModel.ChannelFactory> instância. Você pode alterar ou substituir o <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> instância usada por um <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> , substituindo o <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> método virtual. Da mesma forma, você pode alterar ou substituir o <xref:System.Net.HttpWebRequest> instância usada por um <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> para fazer solicitações HTTP/GET, substituindo o <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType> método virtual.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como usar o Svcutil.exe para baixar documentos de metadados](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)  
 Demonstra como usar o Svcutil.exe para baixar documentos de metadados.  
  
 [Como utilizar o MetadataResolver para obter metadados de associação dinamicamente](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)  
 Demonstra como usar o <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> para obter metadados de associação dinamicamente em tempo de execução.  
  
 [Como usar o MetadataExchangeClient para recuperar metadados](../../../../docs/framework/wcf/feature-details/how-to-use-metadataexchangeclient-to-retrieve-metadata.md)  
 Demonstra como usar o <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> classe para baixar os arquivos de metadados em um <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> objeto que contém <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> objetos para gravar arquivos de ou para outros usos.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Description.MetadataExchangeClient>
