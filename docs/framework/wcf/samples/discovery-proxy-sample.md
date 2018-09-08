---
title: Exemplo de proxy de descoberta
ms.date: 03/30/2017
ms.assetid: 1dfa02df-15b1-4e97-9c8e-f5f2772711b0
ms.openlocfilehash: 6fc0680bc6b61a6fe1b4b141c8b1e5081df5a124
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180391"
---
# <a name="discovery-proxy-sample"></a>Exemplo de proxy de descoberta
Este exemplo mostra como criar uma implementação de um proxy de descoberta para armazenar informações sobre os serviços existentes e como os clientes podem consultar esse proxy para obter informações. Esse exemplo consiste em três projetos:  
  
-   **Serviço**: um serviço de calculadora simples do Windows Communication Foundation (WCF) que se registra com o proxy de descoberta.  
  
-   **Proxy de descoberta**: A implementação de um serviço de proxy de descoberta.  
  
-   **Cliente**: aplicativo de cliente do WCF de um que chama o proxy de descoberta para pesquisar por serviços.  
  
## <a name="demonstrates"></a>Demonstra  
 Implementação de proxy de descoberta  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryProxy`  
  
## <a name="discoveryproxy"></a>DiscoveryProxy  
 No `Main` método do arquivo Program.cs, o exemplo mostra como um serviço do tipo <xref:System.ServiceModel.Discovery.DiscoveryProxy> está hospedado. Ele expõe dois pontos de extremidade, uma do tipo <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> e outro do tipo <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>. Ambos os pontos de extremidade usam o TCP como um transporte. O <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> está escutando no URI especificado pelo `probeEndpointAddress` parâmetro, isso é onde os clientes podem enviar mensagens de teste para consultar o proxy para seus dados. O <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> está escutando no URI especificado pelo `announcementEndpointAddress` parâmetro. Isso é onde o proxy ouve a anúncios. Quando um comunicado online é recebido, o proxy adiciona o serviço ao seu cache e quando um comunicado offline é recebido remove o serviço do seu cache.  
  
 O DiscoveryProxy.cs contém a implementação do <xref:System.ServiceModel.Discovery.DiscoveryProxy>. O Proxy deve herdar de <xref:System.Object> de classe e requer uma implementação de <xref:System.Runtime.Remoting.Messaging.AsyncResult>. Na instanciação, o Proxy cria uma nova <xref:System.Collections.Generic.Dictionary%602>, que é usado para armazenar elementos que ele sabe sobre.  
  
 O arquivo é dividido em duas regiões, métodos de Cache de Proxy e a implementação de Proxy de descoberta. A região de métodos de Cache de Proxy contém métodos usados para atualizar o <xref:System.Collections.Generic.Dictionary%602>, executar consultas em relação a <xref:System.Collections.Generic.Dictionary%602>e imprimir os dados para os usuários. A região de implementação de Proxy de descoberta contém métodos substituídos necessários para a funcionalidade de anúncio e investigação. Elas definem as ações realizadas por um proxy depois de receber um comunicado Online, um comunicado Offline ou uma mensagem de teste.  
  
## <a name="service"></a>Serviço  
 No arquivo Program.cs no projeto de serviço, o mesmo URI é usado para seu ponto de extremidade de comunicado como o proxy de descoberta. Isso ocorre porque o serviço usa o ponto de extremidade para o envio de comunicados, enquanto o proxy usa para recebê-los. O serviço usa o <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> e adiciona um ponto de extremidade de comunicado a ele.  
  
## <a name="client"></a>Cliente  
 O projeto de cliente usa o mesmo URI para seu ponto de extremidade de investigação como o Proxy. Isso ocorre porque os testes neste cenário também estão sendo unicast especificamente para o ponto de extremidade disponível no proxy. O cliente se conecta a esse endereço bem conhecido e a consulta, em seguida, para o serviço. Depois que ele encontrou o serviço que ele se conecta a ele.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Carregar a solução do projeto em [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] e compile o projeto.  
  
2.  Primeiro, execute o aplicativo de Proxy de descoberta, gerado em \DiscoveryProxy\bin\debug [diretório da solução]. O Proxy de descoberta deve executar pela primeira vez como pontos de extremidade de comunicado de TCP devem ser assina o serviço para enviar seus anúncios.  
  
3.  Em segundo lugar, execute o aplicativo de serviço gerado no \Service\bin\debug [diretório da solução]. Na inicialização, o serviço envia um comunicado para o ponto de extremidade de comunicado do proxy de descoberta e é registrado no cache de proxy.  
  
4.  Em seguida, execute o aplicativo de cliente gerado em \Client\bin\debug [diretório da solução]. O cliente consulta o proxy, obtém o endereço do serviço e, em seguida, conecta-se ao serviço.  
  
5.  Por fim, encerrar o cliente, serviço e, em seguida, o proxy. O proxy deve estar executando para que ele receba comunicado offline do serviço.  
  
## <a name="see-also"></a>Consulte também
