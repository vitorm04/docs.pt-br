---
title: AspNetRouteIntegration
ms.date: 03/30/2017
ms.assetid: 0638ce0e-d053-47df-a447-688e447a03fb
ms.openlocfilehash: 8d9a0710e5106cbc3d02a06e81f4f8ed9ae3e03b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43475875"
---
# <a name="aspnetrouteintegration"></a>AspNetRouteIntegration
Este exemplo demonstra como hospedar um serviço REST do Windows Communication Foundation (WCF) usando rotas do ASP.NET. O [serviço de recurso básico](../../../../docs/framework/wcf/samples/basic-resource-service.md) exemplo mostra uma versão auto-hospedado deste cenário e descreve a implementação do serviço em camadas. Este tópico enfoca o recurso de integração do ASP.NET. Para obter mais informações sobre roteamento do ASP.NET, consulte <xref:System.Web.Routing>.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 O serviço WCF expõe uma coleção de clientes de uma maneira de recurso-oriented/REST. Assim como um serviço WCF baseado em SOAP, o serviço pode ser hospedado no ASP.NET usando um arquivo. svc. No entanto, isso geralmente não é preferível para cenários HTTP, porque ele requer tendo. svc na URL para o serviço. Além disso, ele exige a implantação de um arquivo. svc, juntamente com a biblioteca de serviço. Essas limitações podem ser evitadas ao hospedar o serviço de uso de rotas do ASP.NET, conforme demonstrado neste exemplo.  
  
 O exemplo hospeda o serviço no ASP.NET, adicionando um <xref:System.ServiceModel.Activation.ServiceRoute> em um arquivo global. asax. O <xref:System.ServiceModel.Activation.ServiceRoute> Especifica o tipo do serviço ('Service' neste caso), o tipo da fábrica do host de serviço a ser usado para o serviço (<xref:System.ServiceModel.Activation.WebServiceHostFactory> nesse caso) e o endereço para o serviço básico de HTTP ('~ / clientes neste caso).  
  
 Além disso, o exemplo inclui um Web. config que adiciona o <xref:System.Web.Routing.UrlRoutingModule> (para ativar as rotas do ASP.NET) e inclui a configuração para o serviço. Em particular, a configuração configura o serviço WCF com um padrão <xref:System.ServiceModel.Description.WebHttpEndpoint> que tem o <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> definir como `true`. Como resultado, a infraestrutura do WCF cria uma página de ajuda baseados em HTML automática em `http://localhost/Customers/help` que fornece informações sobre como construir HTTP solicitações para o serviço e como acessar a resposta do serviço HTTP – por exemplo, um exemplo de como o cliente detalhes são representados em XML e JSON.  
  
 Expor a coleção de cliente (e, de modo geral, qualquer recurso) dessa maneira permite que um cliente para interagir com um serviço de maneira uniforme usando HTTP e URIs `GET`, `PUT`, `DELETE` e `POST`.  
  
 Program.cs no projeto do cliente demonstra como esse cliente pode ser criados usando <xref:System.Net.HttpWebRequest>. Observe que isso é apenas uma maneira de acessar um serviço WCF. Também é possível acessar o serviço usando outras classes do .NET Framework, como a fábrica de canais do WCF e <xref:System.Net.WebClient>. Outros exemplos no SDK (como o [serviço HTTP básico](../../../../docs/framework/wcf/samples/basic-http-service.md) exemplo e o [seleção automática de formato](../../../../docs/framework/wcf/samples/automatic-format-selection.md) exemplo) mostram como usar essas classes para se comunicar com um serviço WCF.  
  
 Esse exemplo consiste em 3 projetos:  
  
 Serviço  
 Um projeto de aplicativo Web que inclui um serviço de HTTP do WCF hospedado no ASP.NET.  
  
 Cliente  
 Um projeto de aplicativo de console que faz chamadas para o serviço.  
  
 Comuns  
 Uma biblioteca compartilhada que contém o `Customer` tipo usado pelo cliente e serviço. Como o aplicativo de console do cliente é executado, o cliente faz solicitações para o serviço e grava as informações pertinentes das respostas à janela do console.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Abra a solução para o exemplo de integração de rotas do ASP.NET em [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Pressione CTRL+SHIFT+B para criar a solução.  
  
3.  Se não ainda estiver aberto, pressione "CTRL + W, S" para abrir o **Gerenciador de soluções** janela.  
  
4.  Do **Gerenciador de soluções** windows, clique com botão direito a **Service** do projeto e coloque o cursor sobre o **depurar** opção de menu de contexto, de modo que o **iniciar Nova instância** menu de contexto é exibido e selecione **iniciar uma nova instância**.  Isso inicia o ASP.NET development server, que hospeda o serviço.  
  
5.  Do **Gerenciador de soluções** windows, clique com botão direito a **cliente** do projeto e coloque o cursor sobre o **depurar** opção de menu de contexto para que o **Iniciar novo Instância** menu de contexto é exibido e selecione **iniciar uma nova instância**.  
  
6.  A janela de console do cliente é exibida e fornece o URI do serviço em execução e o URI do HTML na página para a execução do serviço de Ajuda. A qualquer momento, você pode exibir a página de ajuda HTML, digitando o URI da página de Ajuda em um navegador. Como o exemplo é executado, o cliente grava o status da atividade atual.  
  
7.  Pressione qualquer tecla para encerrar o aplicativo de console do cliente.  
  
8.  Pressione Shift + F5 para parar a depuração de serviço e na área de notificação do Windows, clique com botão direito no ícone do ASP.NET development server e selecione **parar** no menu de contexto.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetRouteIntegration`  
  
## <a name="see-also"></a>Consulte também
