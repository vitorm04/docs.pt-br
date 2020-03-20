---
title: Pontos de extremidade SOAP e HTTP
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: f10b1aa4514aee50c0c0d17cabdb9516a3ca7584
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144013"
---
# <a name="soap-and-http-endpoints"></a>Pontos de extremidade SOAP e HTTP
Esta amostra demonstra como implementar um serviço baseado em RPC e expô-lo no formato SOAP e no formato "Plain Old XML" (POX) usando o modelo de Programação Web WCF. Consulte a amostra [básica do serviço HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) para obter mais detalhes sobre a vinculação HTTP para o serviço. Esta amostra se concentra nos detalhes relativos à exposição do mesmo serviço sobre SOAP e HTTP usando diferentes vinculações.  
  
## <a name="demonstrates"></a>Demonstra  
 Expondo um serviço RPC sobre SOAP e HTTP usando WCF.  
  
## <a name="discussion"></a>Discussão  
 Esta amostra consiste em dois componentes: um projeto de Aplicação Web (Serviço) que contém um serviço WCF e um aplicativo de console (Client) que invoca operações de serviço usando ligações SOAP e HTTP.  
  
 O serviço WCF expõe`GetData` 2 `PutData` operações – e – que ecoam a string que foi passada como entrada. As operações de serviço <xref:System.ServiceModel.Web.WebGetAttribute> são <xref:System.ServiceModel.Web.WebInvokeAttribute>anotadas com e . Esses atributos controlam a projeção HTTP dessas operações. Além disso, eles são anotados com <xref:System.ServiceModel.OperationContractAttribute>, o que permite que eles sejam expostos sobre as ligações soap. O método `PutData` do serviço <xref:System.ServiceModel.Web.WebFaultException>lança um , que é enviado de volta através de HTTP usando o código de status HTTP e é enviado de volta sobre SOAP como uma falha SOAP.  
  
 O arquivo Web.config configura o serviço WCF com 3 pontos finais:  
  
- O ponto final ~/service.svc/mex que expõe os metadados do serviço para acesso por clientes baseados em SOAP.  
  
- O ponto final ~/service.svc/http que permite que os clientes acessem o serviço usando a vinculação HTTP.  
  
- O ponto final ~/service.svc/soap que permite que os clientes acessem o serviço usando o SOAP sobre a vinculação HTTP.  
  
 O ponto final HTTP é `webHttp` configurado com um `helpEnabled` ponto `true`final padrão <> que foi definido como . Como resultado, o serviço expõe uma página de ajuda baseada em XHTML em ~/service.svc/http/help que os clientes baseados em HTTP podem usar para acessar o serviço.  
  
 O projeto cliente demonstra acessar o serviço usando um proxy SOAP (gerado <xref:System.Net.WebClient>através do Add Service **Reference)** e acessar o serviço usando .  
  
 A amostra consiste em um serviço hospedado na Web e um aplicativo de console. À medida que o aplicativo do console é executado, o cliente faz solicitações ao serviço e escreve as informações pertinentes a partir das respostas à janela do console.  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1. Abra a solução para a amostra SOAP e HTTP Endpoints.  
  
2. Pressione CTRL+SHIFT+B para criar a solução.  
  
3. Se ainda não estiver aberto, pressione CTRL+W, S para abrir a janela **Solution Explorer.**  
  
4. Na janela **Solution Explorer,** clique com o botão direito do mouse no projeto **Serviço** e coloque o cursor sobre a opção **Debug** context menu para que o menu de contexto **Iniciar nova instância** seja exibido. Clique **em Iniciar nova instância**. Isso lança o ASP.NET servidor de desenvolvimento, que hospeda o serviço.  
  
5. Nas janelas do Solution Explorer, clique com o botão direito do mouse no projeto Cliente e coloque o cursor sobre a opção **Debug** context menu para que o menu de contexto **Iniciar nova instância** seja exibido. Clique **em Iniciar nova instância**.  
  
6. A janela do console cliente aparece e fornece o URI do serviço em execução e o URI da página de ajuda HTML para o serviço em execução. A qualquer momento, você pode visualizar a página de ajuda HTML digitando o URI da página de ajuda em um navegador.  
  
7. À medida que a amostra é executada, o cliente escreve o status da atividade atual.  
  
8. Pressione qualquer tecla para encerrar o aplicativo do console cliente.  
  
9. Pressione SHIFT+F5 para parar de depurar o serviço.  
  
10. Na área de notificação do Windows, clique com o botão direito do mouse no ícone do servidor de desenvolvimento ASP.NET e selecione **Parar** no menu de contexto.  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
