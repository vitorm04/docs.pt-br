---
title: CustomDiscoveryMetadata
ms.date: 03/30/2017
ms.assetid: c42455fd-3652-4b7e-b698-ab3a2bb52e48
ms.openlocfilehash: 3e3a173d99f2ba0a2fb33dfd8f91908f03e3e871
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="customdiscoverymetadata"></a>CustomDiscoveryMetadata
Este exemplo mostra como inserir metadados XML personalizado para os metadados de descoberta para um ponto de extremidade detectável exposto por um serviço. O exemplo e mostra como um cliente pode procurar o serviço e extrair esses dados. Este exemplo consiste em dois projetos, serviço e cliente.  
  
## <a name="service"></a>Serviço  
 No `main` método, o exemplo mostra que um objeto do tipo <xref:System.Xml.Linq.XElement> é preenchida com os campos desejados e é adicionado para o <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>. Isso <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> é adicionado a um ponto de extremidade específico. Quando esse ponto de extremidade for descoberto, o Descoberta de metadados contém os dados personalizados que foram adicionados aqui.  
  
## <a name="client"></a>Cliente  
 O exemplo mostra o <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> método ser chamado em um <xref:System.ServiceModel.Discovery.DiscoveryClient>. Resultante <xref:System.ServiceModel.Discovery.FindResponse> é consultada para os elementos XML apropriados e esperados. Esses elementos são impressas, em seguida, no console.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Carregar a solução do projeto em [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] e compile o projeto.  
  
2.  Primeiro execute o aplicativo de serviço, gerado em \service\bin\debug [diretório base de solução] e, em seguida, executar o aplicativo cliente, gerado em \Client\bin\debug [diretório base de solução]  
  
3.  Observe que o serviço ficar online, o cliente localiza o serviço e imprime os metadados publicado no ponto de extremidade.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\DiscoveryExtensibility\CustomDiscoveryMetadata`  
  
## <a name="see-also"></a>Consulte também
