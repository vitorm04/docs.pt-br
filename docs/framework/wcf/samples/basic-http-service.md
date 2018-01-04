---
title: "Serviço básico de HTTP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 27048b43-8a54-4f2a-9952-594bbfab10ad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 687eba2a346b3f554c8a7618bebe2e9c04f4d5b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="basic-http-service"></a>Serviço básico de HTTP
Este exemplo demonstra como implementar um serviço baseado em HTTP, baseados em RPC - popularmente conhecido como "POX" (Plain Old XML) de serviço – usando o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] modelo de programação REST. Este exemplo consiste em dois componentes: um auto-hospedado [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço HTTP (Service.cs) e um aplicativo de console (Program.cs) que cria o serviço e faz chamadas para ele.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço expõe 2 operações, `EchoWithGet` e `EchoWithPost`, que retorna a cadeia de caracteres que foi passada como entrada.  
  
 O `EchoWithGet` operação é anotada com <xref:System.ServiceModel.Web.WebGetAttribute>, que indica que a operação processa HTTP `GET` solicitações. Porque o <xref:System.ServiceModel.Web.WebGetAttribute> não especificar explicitamente um <xref:System.UriTemplate>, a operação de espera a cadeia de caracteres de entrada a ser passado usando um parâmetro de cadeia de caracteres de consulta com o nome `s`. Observe que o formato do URI que espera que o serviço pode ser personalizado usando o <xref:System.ServiceModel.Web.WebGetAttribute.UriTemplate%2A> propriedade.  
  
 O `EchoWithPost` operação é anotada com <xref:System.ServiceModel.Web.WebInvokeAttribute>, que indica que ele não é um `GET` operação (ele tem efeitos colaterais). Porque o <xref:System.ServiceModel.Web.WebInvokeAttribute> não especificar explicitamente um `Method`, a operação processa HTTP `POST` solicitações com a cadeia de caracteres no corpo da solicitação (no formato XML, por exemplo). Observe que o método HTTP e o formato do URI da solicitação podem ser personalizados usando o <xref:System.ServiceModel.Web.WebInvokeAttribute.Method%2A> e <xref:System.ServiceModel.Web.WebInvokeAttribute.UriTemplate> propriedades respectivamente.  
  
 O arquivo App. config configura o serviço WCF com um padrão <xref:System.ServiceModel.Description.WebHttpEndpoint> que tem o <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> propriedade definida como `true`. Como resultado, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infraestrutura cria uma página de ajuda automático baseado em HTML em `http://localhost:8000/Customers/help` que fornece informações sobre como construir solicitações HTTP para o serviço e como utilizar a resposta HTTP do serviço.  
  
 Program.cs demonstra como um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] fábrica de canais pode ser usada para fazer chamadas para as respostas do serviço e do processos. Observe que isso é apenas uma maneira de acessar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço. Também é possível acessar o serviço usando outras classes do .NET Framework como <xref:System.Net.HttpWebRequest> e <xref:System.Net.WebClient>. Outros exemplos no SDK (como o [seleção automática de formato](../../../../docs/framework/wcf/samples/automatic-format-selection.md) exemplo e [serviço básico do recurso](../../../../docs/framework/wcf/samples/basic-resource-service.md) exemplo) mostram como usar essas classes para se comunicar com um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço.  
  
 O exemplo consiste em um serviço auto-hospedado e um cliente que ambos executado dentro de um aplicativo de console. Como o aplicativo de console é executado, o cliente faz solicitações para o serviço e grava as informações pertinentes entre as respostas para a janela do console.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Abra a solução para o exemplo de serviço básico do Http. Ao iniciar [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], você deve executar como administrador para o exemplo para executar com êxito. Fazer isso clicando com o [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ícone e selecionando **executar como administrador** no menu de contexto.  
  
2.  Pressione CTRL + SHIFT + B para compilar a solução e, em seguida, pressione Ctrl + F5 para executar o aplicativo de console sem depuração. A janela do console é exibida e fornece o URI do serviço em execução e o URI do HTML ajuda a página para o serviço em execução. A qualquer momento, você pode exibir a página de ajuda HTML digitando o URI da página de Ajuda em um navegador. Como o exemplo é executado, o cliente grava o status da atividade atual.  
  
3.  Pressione qualquer tecla para encerrar o exemplo.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicHttpService`  
  
## <a name="see-also"></a>Consulte também  
 [Seleção automática de formato](../../../../docs/framework/wcf/samples/automatic-format-selection.md)  
 [Serviço de recursos básicos](../../../../docs/framework/wcf/samples/basic-resource-service.md)
