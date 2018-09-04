---
title: CustomDiscoveryMetadata
ms.date: 03/30/2017
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
ms.openlocfilehash: 181910db3f1dd6da892f6ae2ddcbf7bd5859ff17
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525415"
---
# <a name="customdiscoverymetadata"></a>CustomDiscoveryMetadata
Este exemplo mostra como inserir metadados personalizados do XML de metadados de descoberta para um ponto de extremidade podem ser descoberto exposto por um serviço. O exemplo, em seguida, mostra como um cliente pode procurar o serviço e extrair esses dados. Esse exemplo consiste em dois projetos, serviço e cliente.  
  
## <a name="service"></a>Serviço  
 No `main` método, o exemplo mostra que um objeto do tipo <xref:System.Xml.Linq.XElement> é preenchida com os campos desejados e é adicionado ao <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>. Isso <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> é adicionado a um ponto de extremidade específico. Quando esse ponto de extremidade é descoberto, os metadados de descoberta contém os dados personalizados que foi adicionados aqui.  
  
## <a name="client"></a>Cliente  
 O exemplo mostra a <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> método sendo chamado em um <xref:System.ServiceModel.Discovery.DiscoveryClient>. Resultante <xref:System.ServiceModel.Discovery.FindResponse> é consultada para os elementos XML apropriados e esperados. Esses elementos, em seguida, são impressas no console.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Carregar a solução do projeto em [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] e compile o projeto.  
  
2.  Executar o aplicativo de serviço, gerado em [diretório da solução] \service\bin\debug, primeiro e, em seguida, execute o aplicativo de cliente gerado em [diretório da solução] \Client\bin\debug  
  
3.  Observe que o serviço fica online, o cliente localiza o serviço e imprime os publicado no ponto de extremidade de metadados.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a>Consulte também
