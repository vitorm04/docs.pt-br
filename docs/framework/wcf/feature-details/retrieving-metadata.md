---
title: Recuperando metadados
ms.date: 03/30/2017
helpviewer_keywords:
- metadata [WCF], retrieving
ms.assetid: 18d8ba4c-af0f-4827-a50b-4202d767bacc
ms.openlocfilehash: 72a9b8445a83af3cbda15c5f4580a1c1df859339
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54533228"
---
# <a name="retrieving-metadata"></a>Recuperando metadados
Recuperação de metadados é o processo de solicitação e recuperando metadados de um ponto de extremidade de metadados, como um ponto de extremidade de metadados do WS-MetadataExchange (MEX) ou um ponto de extremidade de metadados HTTP/GET.  
  
## <a name="retrieving-metadata-from-the-command-line-using-svcutilexe"></a>Recuperar metadados de linha de comando usando Svcutil.exe  
 Você pode recuperar metadados de serviço usando solicitações WS-MetadataExchange ou HTTP/GET usando o [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) ferramenta e passando o `/target:metadata` switch e um endereço. Svcutil.exe baixa os metadados no endereço especificado e salva o arquivo no disco. Svcutil.exe usa um <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instância internamente e carrega da configuração de <xref:System.ServiceModel.Description.IMetadataExchange> configuração de ponto de extremidade cujo nome corresponda o esquema do endereço passado para Svcutil.exe como entrada.  
  
## <a name="retrieving-metadata-programmatically-using-the-metadataexchangeclient"></a>Recuperar metadados de forma programática, usando o MetadataExchangeClient  
 Windows Communication Foundation (WCF) pode recuperar metadados de serviço usando protocolos padronizados, como WS-MetadataExchange e solicitações HTTP/GET. Ambos os protocolos são compatíveis com o <xref:System.ServiceModel.Description.MetadataExchangeClient> tipo. Você recupera metadados de serviço usando o <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> tipo, fornecendo um endereço para o ponto de extremidade de metadados e uma associação opcional. A associação usada por um <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instância pode ser uma das associações padrão do <xref:System.ServiceModel.Description.MetadataExchangeBindings> carregado de classe estática, uma associação fornecida pelo usuário ou uma associação de uma configuração de ponto de extremidade para o `IMetadataExchange` contrato. O <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> também pode resolver referências de URL de HTTP a metadados usando o <xref:System.Net.HttpWebRequest> tipo.  
  
 Por padrão, uma <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> instância está vinculada a um único <xref:System.ServiceModel.ChannelFactory> instância. Você pode alterar ou substituir os <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType> instância usada por um <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> , substituindo o <xref:System.ServiceModel.Description.MetadataExchangeClient.GetChannelFactory%2A> método virtual. Da mesma forma, você pode alterar ou substituir os <xref:System.Net.HttpWebRequest> instância usada por um <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> para fazer solicitações HTTP/GET, substituindo o <xref:System.ServiceModel.Description.MetadataExchangeClient.GetWebRequest%2A?displayProperty=nameWithType> método virtual.  
  
## <a name="in-this-section"></a>Nesta seção  
 [Como: Use Svcutil.exe para baixar documentos de metadados](../../../../docs/framework/wcf/feature-details/how-to-use-svcutil-exe-to-download-metadata-documents.md)  
 Demonstra como usar Svcutil.exe para baixar documentos de metadados.  
  
 [Como: Utilizar o MetadataResolver para obter metadados de associação dinamicamente](../../../../docs/framework/wcf/feature-details/how-to-use-metadataresolver-to-obtain-binding-metadata-dynamically.md)  
 Demonstra como usar o <xref:System.ServiceModel.Description.MetadataResolver?displayProperty=nameWithType> para obter metadados de associação dinamicamente em tempo de execução.  
  
 [Como: Usar o MetadataExchangeClient para recuperar metadados](../../../../docs/framework/wcf/feature-details/how-to-use-metadataexchangeclient-to-retrieve-metadata.md)  
 Demonstra como usar o <xref:System.ServiceModel.Description.MetadataExchangeClient?displayProperty=nameWithType> classe para baixar os arquivos de metadados em um <xref:System.ServiceModel.Description.MetadataSet?displayProperty=nameWithType> objeto que contém <xref:System.ServiceModel.Description.MetadataSection?displayProperty=nameWithType> objetos a serem gravados em arquivos ou para outros usos.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Description.MetadataExchangeClient>
