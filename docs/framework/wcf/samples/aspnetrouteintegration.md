---
title: AspNetRouteIntegration
ms.date: 03/30/2017
ms.assetid: 0638ce0e-d053-47df-a447-688e447a03fb
ms.openlocfilehash: c2b2a47a0c817e23a06c39d622bca9c649cbadb4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="aspnetrouteintegration"></a>AspNetRouteIntegration
Este exemplo demonstra como hospedar um serviço REST do Windows Communication Foundation (WCF) usando o ASP.NET rotas. O [serviço básico do recurso](../../../../docs/framework/wcf/samples/basic-resource-service.md) exemplo mostra uma versão auto-hospedado deste cenário e descreve a implementação do serviço em camadas. Este tópico enfoca o recurso de integração do ASP.NET. Para obter mais informações sobre roteamento ASP.NET, consulte <xref:System.Web.Routing>.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço expõe uma coleção de clientes de uma maneira de recurso-orientado/REST. Assim como um baseado em SOAP [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, o serviço pode ser hospedado no ASP.NET usando um arquivo. svc. No entanto, isso nem sempre é preferencial para cenários HTTP, porque ele requer tendo. svc na URL para o serviço. Além disso, requer a implantação de um arquivo. svc junto com a biblioteca de serviço. Essas limitações podem ser evitadas hospedando o serviço usando o ASP.NET rotas, conforme é mostrado neste exemplo.  
  
 O exemplo hospeda o serviço em ASP.NET, adicionando um <xref:System.ServiceModel.Activation.ServiceRoute> em um arquivo global. asax. O <xref:System.ServiceModel.Activation.ServiceRoute> Especifica o tipo do serviço ('serviço' neste caso), o tipo da fábrica do host de serviço a ser usado para o serviço (<xref:System.ServiceModel.Activation.WebServiceHostFactory> nesse caso) e o HTTP endereço para o serviço de base ('~ / clientes neste caso).  
  
 Além disso, o exemplo inclui um Web. config que adiciona o <xref:System.Web.Routing.UrlRoutingModule> (para ativar o ASP.NET rotas) e inclui a configuração para o serviço. Em particular, a configuração configura o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço com um padrão <xref:System.ServiceModel.Description.WebHttpEndpoint> que tem o <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> definindo como `true`. Como resultado, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infraestrutura cria uma página de ajuda automático baseado em HTML em `http://localhost/Customers/help` que fornece informações sobre como construir HTTP solicitações para o serviço e como acessar a resposta de HTTP do serviço – por exemplo, um exemplo de como os detalhes do cliente são representados no XML e JSON.  
  
 Expondo a coleção de cliente (e de forma geral, qualquer recurso) dessa maneira permite que um cliente interagir com um serviço de maneira uniforme usando HTTP e URIs `GET`, `PUT`, `DELETE` e `POST`.  
  
 Program.cs no projeto do cliente demonstra como o cliente pode ser criados usando <xref:System.Net.HttpWebRequest>. Observe que isso é apenas uma maneira de acessar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço. Também é possível acessar o serviço usando outras classes do .NET Framework, como o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fábrica de canais e <xref:System.Net.WebClient>. Outros exemplos no SDK (como o [serviço básico de HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) exemplo e o [seleção automática de formato](../../../../docs/framework/wcf/samples/automatic-format-selection.md) exemplo) mostram como usar essas classes para se comunicar com um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço.  
  
 Este exemplo consiste em 3 projetos:  
  
 Serviço  
 Um projeto de aplicativo Web que inclui um serviço HTTP do WCF hospedado no ASP.NET.  
  
 Cliente  
 Um projeto de aplicativo de console que faz chamadas ao serviço.  
  
 Comuns  
 Uma biblioteca compartilhada que contém o `Customer` tipo usado pelo cliente e serviço. Quando o aplicativo de console do cliente é executado, o cliente faz solicitações para o serviço e grava as informações pertinentes entre as respostas para a janela do console.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Abra a solução para o exemplo de integração de rotas do ASP.NET em [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Pressione CTRL+SHIFT+B para criar a solução.  
  
3.  Se ainda não estiver aberta, pressione "CTRL + W, S" para abrir o **Solution Explorer** janela.  
  
4.  Do **Gerenciador de soluções** windows, clique o **Service** do projeto e coloque o cursor sobre o **depurar** opção de menu de contexto para que o **iniciar Nova instância** menu de contexto é exibido e selecione **iniciar uma nova instância**.  Isso inicia o ASP.NET development server, que hospeda o serviço.  
  
5.  Do **Solution Explorer** windows, clique o **cliente** do projeto e coloque o cursor sobre o **depurar** opção de menu de contexto para que o **iniciar nova Instância** menu de contexto é exibido e selecione **iniciar uma nova instância**.  
  
6.  A janela de console do cliente é exibida e fornece o URI do serviço em execução e o URI do HTML ajuda a página para o serviço em execução. A qualquer momento, você pode exibir a página de ajuda HTML digitando o URI da página de Ajuda em um navegador. Como o exemplo é executado, o cliente grava o status da atividade atual.  
  
7.  Pressione qualquer tecla para fechar o aplicativo de console de cliente.  
  
8.  Pressione Shift + F5 para parar a depuração de serviço e na área de notificação do Windows, clique no ícone do servidor de desenvolvimento ASP.NET e selecione **parar** no menu de contexto.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetRouteIntegration`  
  
## <a name="see-also"></a>Consulte também
