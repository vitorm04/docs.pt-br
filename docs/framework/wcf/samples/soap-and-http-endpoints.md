---
title: Pontos de extremidade SOAP e HTTP
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: c07391ccd1f8db6e5d2cb6e0c24fc06152d7517f
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617517"
---
# <a name="soap-and-http-endpoints"></a>Pontos de extremidade SOAP e HTTP
Este exemplo demonstra como implementar um serviço baseado em RPC e expô-lo no formato SOAP e o formato "Plain Old XML" (POX) usando o modelo de programação da Web do WCF. Consulte a [serviço HTTP básico](../../../../docs/framework/wcf/samples/basic-http-service.md) exemplo para obter mais detalhes sobre a associação de HTTP para o serviço. Este exemplo se concentra nos detalhes que pertencem ao expor o mesmo serviço via SOAP e HTTP usando ligações diferentes.  
  
## <a name="demonstrates"></a>Demonstra  
 Expondo um serviço RPC via SOAP e HTTP usando o WCF.  
  
## <a name="discussion"></a>Discussão  
 Esse exemplo consiste em dois componentes: um projeto de aplicativo Web (serviço) que contém um serviço WCF e um aplicativo de console (cliente) que chama as operações de serviço usando associações HTTP e SOAP.  
  
 O serviço WCF expõe 2 operações –`GetData` e `PutData` – que a cadeia de caracteres que foi passada como entrada de eco. As operações de serviço são anotadas com <xref:System.ServiceModel.Web.WebGetAttribute> e <xref:System.ServiceModel.Web.WebInvokeAttribute>. Esses atributos controlam a projeção de HTTP dessas operações. Além disso, eles são anotados com <xref:System.ServiceModel.OperationContractAttribute>, que permite que eles sejam expostos ao longo de associações SOAP. O serviço `PutData` método lança um <xref:System.ServiceModel.Web.WebFaultException>, que é enviado novamente via HTTP usando o código de status HTTP e é enviado de volta por meio do SOAP como uma falha de SOAP.  
  
 O arquivo Web. config configura o serviço WCF com pontos de extremidade de 3:  
  
- O ponto de extremidade ~/service.svc/mex que expõe os metadados de serviço para acesso por clientes baseados em SOAP.  
  
- O ponto de extremidade ~/service.svc/http que permite que os clientes acessem o serviço usando a associação HTTP.  
  
- O ponto de extremidade ~/service.svc/soap que permite que os clientes acessar o serviço usando o SOAP por associação HTTP.  
  
 O ponto de extremidade HTTP é configurado com um <`webHttp`> ponto de extremidade padrão que tem `helpEnabled` definido como `true`. Como resultado, o serviço expõe uma página de ajuda XHTML com base em ~/service.svc/http/help clientes baseados em HTTP podem usar para acessar o serviço.  
  
 O projeto do cliente demonstra como acessar o serviço usando um proxy SOAP (gerado por meio **adicionar referência de serviço**) e acessar o serviço usando <xref:System.Net.WebClient>.  
  
 O exemplo consiste em um serviço hospedado na Web e um aplicativo de console. Como o aplicativo de console é executado, o cliente faz solicitações para o serviço e grava as informações pertinentes das respostas à janela do console.  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1. Abra a solução para o exemplo de pontos de extremidade de HTTP e SOAP.  
  
2. Pressione CTRL+SHIFT+B para criar a solução.  
  
3. Se não ainda estiver aberto, pressione CTRL + W, S para abrir o **Gerenciador de soluções** janela.  
  
4. Do **Gerenciador de soluções** janela, com o botão direito o **Service** do projeto e coloque o cursor sobre o **depurar** opção de menu de contexto, de modo que o **iniciar nova Instância** menu de contexto é exibido. Clique em **iniciar nova instância**. Isso inicia o ASP.NET development server, que hospeda o serviço.  
  
5. Das janelas Solution Explorer, clique com botão direito do projeto de cliente e coloque o cursor sobre o **Debug** opção de menu de contexto para que o **iniciar nova instância** menu de contexto é exibido. Clique em **iniciar nova instância**.  
  
6. A janela de console do cliente é exibida e fornece o URI do serviço em execução e o URI do HTML na página para a execução do serviço de Ajuda. A qualquer momento, você pode exibir a página de ajuda HTML, digitando o URI da página de Ajuda em um navegador.  
  
7. Como o exemplo é executado, o cliente grava o status da atividade atual.  
  
8. Pressione qualquer tecla para encerrar o aplicativo de console do cliente.  
  
9. Pressione SHIFT + F5 para parar a depuração de serviço.  
  
10. Na área de notificação do Windows, clique com botão direito no ícone do ASP.NET development server e selecione **parar** no menu de contexto.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
