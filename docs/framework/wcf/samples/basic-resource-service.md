---
title: "Serviço de recursos básicos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4360063e-cc8c-4648-846e-c05a5af51a7a
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d8ba436cba284201f14635162ed394abfa9a14db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="basic-resource-service"></a>Serviço de recursos básicos
Este exemplo demonstra como implementar um serviço baseado em HTTP usando o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] modelo de programação REST que expõe uma coleção de clientes que dá suporte a recuperar, adicionar, excluir e substituir operações. Este exemplo consiste em 2 componentes – uma auto-hospedado [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço HTTP (Service.cs) e um aplicativo de console (program.cs) que cria o serviço e faz chamadas para ele.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço expõe uma coleção de clientes de uma maneira de recurso-orientado/REST. Em resumo, isso envolve a necessidade de URIs exclusivo para a coleção de clientes e todos os clientes na coleção. O serviço oferece suporte ao envio de um HTTP `GET` na coleção de URI para recuperar a coleção inteira e HTTP `POST` na coleção de URI para adicionar um novo cliente à coleção. Também no URI para um cliente individual, ele oferece suporte a HTTP `GET` para obter detalhes, HTTP de cliente `PUT` para substituir os detalhes do cliente e HTTP `DELETE` para remover o cliente da coleção. Quando um novo cliente é adicionado à coleção, o serviço atribui um URI exclusivo e armazena o URI como parte dos detalhes do cliente. Além disso, ele se comunica o URI para o cliente usando o cabeçalho de local HTTP da resposta.  
  
 O arquivo App. config configura o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço com um padrão <xref:System.ServiceModel.Description.WebHttpEndpoint> que tem o <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> propriedade definida como `true`. Como resultado, o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cria uma página de Ajuda em HTML automática no `http://localhost:8000/Customers/help` que fornece informações sobre como construir HTTP solicitações para o serviço e como acessar a resposta de HTTP do serviço – por exemplo, um exemplo de como o cliente detalhes é representado em XML e JSON.  
  
 Expondo a coleção de cliente (e de forma geral, qualquer recurso) dessa maneira permite que o cliente interagir com ela, de maneira uniforme usando HTTP e URIs `GET`, `PUT`, `DELETE` e `POST`. Program.cs demonstra como o cliente pode ser criados usando <xref:System.Net.HttpWebRequest>. Observe que isso é apenas uma maneira de acessar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço REST. Também é possível acessar o serviço usando outras classes do .NET Framework, como o <xref:System.ServiceModel.ChannelFactory> e <xref:System.Net.WebClient>. Outros exemplos no SDK (como o [serviço básico de HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md) exemplo e o [seleção automática de formato](../../../../docs/framework/wcf/samples/automatic-format-selection.md) exemplo) mostram como usar essas classes para se comunicar com um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço.  
  
 O exemplo consiste em um serviço auto-hospedado e um cliente que ambos executado dentro de um aplicativo de console. Como o aplicativo de console é executado, o cliente faz solicitações para o serviço e grava as informações pertinentes entre as respostas para a janela do console.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Abra a solução de exemplo de serviço básico do recurso. Ao iniciar [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], você deve executar como administrador para o exemplo para executar com êxito. Fazer isso clicando com o [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ícone e selecionando **executar como administrador** no menu de contexto.  
  
2.  Pressione CTRL + SHIFT + B para compilar a solução e, em seguida, pressione Ctrl + F5 para executar o aplicativo de console. A janela do console é exibida e fornece o URI do serviço em execução e o URI do HTML ajuda a página para o serviço em execução. A qualquer momento, você pode exibir a página de ajuda HTML digitando o URI da página de Ajuda em um navegador. Como o exemplo é executado, o cliente grava o status da atividade atual.  
  
3.  Pressione qualquer tecla para encerrar o exemplo.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicResourceService`  
  
## <a name="see-also"></a>Consulte também  
 [Serviço básico de HTTP](../../../../docs/framework/wcf/samples/basic-http-service.md)  
 [Seleção automática de formato](../../../../docs/framework/wcf/samples/automatic-format-selection.md)
