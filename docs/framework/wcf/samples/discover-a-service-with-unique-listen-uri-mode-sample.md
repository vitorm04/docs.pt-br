---
title: Descubra um serviço com exemplo de modo único de URI de escuta
ms.date: 03/30/2017
ms.assetid: 9a6d35b2-0469-43c8-a0c9-63623e3d2733
ms.openlocfilehash: e6129594df6170f94a06caa08a9f16e4770bbfd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="discover-a-service-with-unique-listen-uri-mode-sample"></a>Descubra um serviço com exemplo de modo único de URI de escuta
Este exemplo demonstra como descobrir um serviço que tem o <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> propriedade definida como <xref:System.ServiceModel.Description.ListenUriMode.Unique>. Quando o <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> está definida como <xref:System.ServiceModel.Description.ListenUriMode.Unique>, o ListenUri é garantido como sendo exclusivo definindo a porta a ser exclusivo ou o caminho ser exclusivo, acrescentando um GUID.  
  
### <a name="features-on-the-service"></a>Recursos do serviço  
 O <xref:System.ServiceModel.Channels.BindingContext.ListenUriMode%2A> está definida como <xref:System.ServiceModel.Description.ListenUriMode.Unique> para o ponto de extremidade TCP. O serviço é feito detectável em uma <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ponto de extremidade.  
  
### <a name="features-on-the-client"></a>Recursos no cliente  
 Esse cliente se conecta ao serviço usando o correto `Via.Uri` usando o <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> método. O <xref:System.ServiceModel.Discovery.FindResponse> que é retornado do método é consultado para se ele contém um válido <xref:System.ServiceModel.Endpoint.ListenUri%2A> e se ele for diferente `Address.Uri`. As informações apropriadas é então passadas para o `InvokeCalculatorService` método. No `InvokeCalculatorService` método, o <xref:System.ServiceModel.Endpoint.ListenUri%2A> foi passado pelo chamador, em seguida, um `ClientViaBehavior` com o nome correto `Via.Uri` é adicionado ao ponto de extremidade do cliente.  
  
##### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra UniqueListenUriMode.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Execute o aplicativo de serviço, que é gerado na pasta \service\bin\debug [diretório base de solução].  
  
4.  Execute o aplicativo cliente, que é gerado na pasta \Client\bin\debug [diretório base de solução].  
  
     O cliente localiza o serviço em execução e grava os metadados publicados pelo ponto de extremidade do serviço no console.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\UniqueListenUriMode`  
  
## <a name="see-also"></a>Consulte também
