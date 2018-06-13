---
title: Exemplo de proxy de descoberta
ms.date: 03/30/2017
ms.assetid: 1dfa02df-15b1-4e97-9c8e-f5f2772711b0
ms.openlocfilehash: e9cbfcb717f502a849d4d508d13df6c00b95db58
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33503178"
---
# <a name="discovery-proxy-sample"></a>Exemplo de proxy de descoberta
Este exemplo mostra como criar uma implementação de um proxy de descoberta para armazenar informações sobre os serviços existentes e como os clientes podem consultar para obter informações de proxy. Este exemplo consiste em três projetos:  
  
-   **Serviço**: um serviço de cálculo simples do Windows Communication Foundation (WCF) que é registrado com o proxy de descoberta.  
  
-   **Proxy de descoberta**: A implementação de um serviço de proxy de descoberta.  
  
-   **Cliente**: aplicativo de cliente do WCF de um que chama o proxy de descoberta para pesquisar para serviços.  
  
## <a name="demonstrates"></a>Demonstra  
 Implementação de proxy de descoberta  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryProxy`  
  
## <a name="discoveryproxy"></a>DiscoveryProxy  
 No `Main` método do arquivo Program.cs, o exemplo mostra como um serviço do tipo <xref:System.ServiceModel.Discovery.DiscoveryProxy> está hospedado. Ela expõe dois pontos de extremidade, um tipo <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> e outro tipo <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>. Ambos os pontos de extremidade usam o TCP como um transporte. O <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> está escutando no URI especificado pelo `probeEndpointAddress` parâmetro, isso é onde os clientes podem enviar mensagens de teste para consultar o proxy para seus dados. O <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> está escutando no URI especificado pelo `announcementEndpointAddress` parâmetro. Isso é onde o proxy ouve para anúncios. Quando um anúncio online é recebido, o proxy adiciona o serviço em seu cache e quando um comunicado offline é recebido remove o serviço do seu cache.  
  
 O DiscoveryProxy.cs contém a implementação do <xref:System.ServiceModel.Discovery.DiscoveryProxy>. O Proxy deve herdar do <xref:System.Object> classe e requer uma implementação de <xref:System.Runtime.Remoting.Messaging.AsyncResult>. Durante a instanciação, o Proxy cria um novo <xref:System.Collections.Generic.Dictionary%602>, que usa para armazenar elementos que ele conheça.  
  
 O arquivo é dividido em duas regiões, métodos de Cache de Proxy e a implementação de Proxy de descoberta. A região de métodos de Cache de Proxy contém métodos usados para atualizar o <xref:System.Collections.Generic.Dictionary%602>, executar consultas em relação a <xref:System.Collections.Generic.Dictionary%602>e imprimir os dados de usuários. A região de implementação de Proxy de descoberta contém métodos substituídos necessários para a funcionalidade de anúncio e investigação. Eles definem as ações realizadas por um proxy depois de receber um anúncio Online, um anúncio Offline ou uma mensagem de teste.  
  
## <a name="service"></a>Serviço  
 No arquivo Program.cs no projeto de serviço, o mesmo URI é usado para seu ponto de extremidade de anúncio como o proxy de descoberta. Isso ocorre porque o serviço usa o ponto de extremidade para enviar os anúncios, enquanto o proxy usa para recebê-los. O serviço usa o <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior> e adiciona um ponto de extremidade do anúncio a ele.  
  
## <a name="client"></a>Cliente  
 O projeto de cliente usa o mesmo URI para seu ponto de extremidade de teste como o Proxy. Isso ocorre porque os testes nesse cenário também estão sendo unicast especificamente para o ponto de extremidade disponível no proxy. O cliente se conecta a esse endereço conhecido e, em seguida, consulta o serviço. Depois de encontrar o serviço se conecta a ele.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Carregar a solução do projeto em [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] e compile o projeto.  
  
2.  Primeiro, execute o aplicativo de Proxy de descoberta, gerado em \DiscoveryProxy\bin\debug [diretório base de solução]. O Proxy de descoberta deve executar primeiro como pontos de extremidade TCP anúncio devem ser o serviço para enviar seus anúncios.  
  
3.  Em segundo lugar, execute o aplicativo de serviço gerado em \Service\bin\debug [diretório base de solução]. Na inicialização, o serviço envia um anúncio para o ponto de extremidade de lançamento do proxy de descoberta e está registrado no cache do proxy.  
  
4.  Em seguida, execute o aplicativo cliente, gerado em \Client\bin\debug [diretório base de solução]. O cliente consulta o proxy, obtém o endereço do serviço e, em seguida, conecta-se ao serviço.  
  
5.  Por fim, encerre o cliente, serviço e, em seguida, o proxy. O proxy deve estar executando para receber notificação offline do serviço.  
  
## <a name="see-also"></a>Consulte também
