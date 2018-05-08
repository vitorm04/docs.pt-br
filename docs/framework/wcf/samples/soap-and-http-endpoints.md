---
title: Pontos de extremidade SOAP e HTTP
ms.date: 03/30/2017
ms.assetid: e3c8be75-9dda-4afa-89b6-a82cb3b73cf8
ms.openlocfilehash: bf11563b937426c3c1701e7fed79e82e4e4669ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="soap-and-http-endpoints"></a>Pontos de extremidade SOAP e HTTP
Este exemplo demonstra como implementar um serviço baseado no RPC e expô-lo no formato SOAP e o "Plain Old XML" (POX) Formatar usando o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] modelo de programação da Web. Consulte o [serviço básico de HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) exemplo para obter mais detalhes sobre a associação HTTP para o serviço. Este exemplo enfoca os detalhes que pertencem ao expor o mesmo serviço via SOAP e HTTP usando ligações diferentes.  
  
## <a name="demonstrates"></a>Demonstra  
 Expor um serviço RPC sobre HTTP e SOAP usando [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="discussion"></a>Discussão  
 Este exemplo consiste em dois componentes: um projeto de aplicativo Web (serviço) que contém um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço e um aplicativo de console (cliente) que invoca as operações de serviço usando associações HTTP e SOAP.  
  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço expõe 2 operações –`GetData` e `PutData` – que a cadeia de caracteres que foi passada como entrada de eco. As operações de serviço são anotadas com <xref:System.ServiceModel.Web.WebGetAttribute> e <xref:System.ServiceModel.Web.WebInvokeAttribute>. Esses atributos controlam a projeção de HTTP dessas operações. Além disso, eles são anotados com <xref:System.ServiceModel.OperationContractAttribute>, que permite que eles sejam expostos por associações de SOAP. O serviço `PutData` método lança um <xref:System.ServiceModel.Web.WebFaultException>, que é enviado de volta via HTTP usando o código de status HTTP e é enviado pela SOAP como uma falha de SOAP.  
  
 O arquivo Web. config configura o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço com 3 pontos de extremidade:  
  
-   O ponto de extremidade de ~/service.svc/mex que expõe os metadados de serviço para acesso por clientes baseados em SOAP.  
  
-   O ponto de extremidade de ~/service.svc/http que permite que os clientes acessem o serviço usando a associação HTTP.  
  
-   O ponto de extremidade de ~/service.svc/soap que permite que os clientes acessar o serviço usando o SOAP por associação HTTP.  
  
 O ponto de extremidade HTTP é configurado com um <`webHttp`> ponto de extremidade padrão que tem `helpEnabled` definido como `true`. Como resultado, o serviço expõe uma página de ajuda XHTML com base em ~/service.svc/http/help que os clientes baseados em HTTP podem usar para acessar o serviço.  
  
 O projeto cliente demonstra acessando o serviço usando um proxy SOAP (gerados por meio de **adicionar referência de serviço**) e acessar o serviço usando <xref:System.Net.WebClient>.  
  
 O exemplo consiste em um serviço hospedado da Web e um aplicativo de console. Como o aplicativo de console é executado, o cliente faz solicitações para o serviço e grava as informações pertinentes entre as respostas para a janela do console.  
  
#### <a name="to-run-the-sample"></a>Para executar a amostra  
  
1.  Abra a solução para o exemplo de pontos de extremidade de HTTP e SOAP.  
  
2.  Pressione CTRL+SHIFT+B para criar a solução.  
  
3.  Se ainda não estiver aberta, pressione CTRL + W, S para abrir o **Solution Explorer** janela.  
  
4.  Do **Gerenciador de soluções** janela, com o botão direito do **serviço** do projeto e coloque o cursor sobre o **depurar** opção de menu de contexto para que o **iniciar nova Instância** menu de contexto é exibido. Clique em **iniciar nova instância**. Isso inicia o ASP.NET development server, que hospeda o serviço.  
  
5.  Na janela Gerenciador de soluções, clique com botão direito no projeto cliente e coloque o cursor sobre o **depurar** opção de menu de contexto para que o **iniciar uma nova instância** menu de contexto é exibido. Clique em **iniciar nova instância**.  
  
6.  A janela de console do cliente é exibida e fornece o URI do serviço em execução e o URI do HTML ajuda a página para o serviço em execução. A qualquer momento, você pode exibir a página de ajuda HTML digitando o URI da página de Ajuda em um navegador.  
  
7.  Como o exemplo é executado, o cliente grava o status da atividade atual.  
  
8.  Pressione qualquer tecla para fechar o aplicativo de console de cliente.  
  
9. Pressione SHIFT + F5 para parar a depuração de serviço.  
  
10. Na área de notificação do Windows, clique no ícone do servidor de desenvolvimento ASP.NET e selecione **parar** no menu de contexto.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\SoapAndHttpEndpoints`
