---
title: Serviço de recursos básicos
ms.date: 03/30/2017
ms.assetid: 4360063e-cc8c-4648-846e-c05a5af51a7a
ms.openlocfilehash: 2d55aecfdf6579b1de4c0cc324e59e23c251b12d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520130"
---
# <a name="basic-resource-service"></a>Serviço de recursos básicos
Este exemplo demonstra como implementar um serviço baseado em HTTP, usando o modelo de programação de REST do Windows Communication Foundation (WCF) que expõe uma coleção de customers que dá suporte a recuperar, adicionar, excluir e substituir operações. Esse exemplo consiste em 2 componentes – um serviço auto-hospedado do HTTP do WCF (Service.cs) e um aplicativo de console (program.cs) que cria o serviço e faz chamadas para ele.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 O serviço WCF expõe uma coleção de clientes de uma maneira de recurso-oriented/REST. Em resumo, isso envolve a ter URIs exclusivos para a coleção de clientes e todos os clientes na coleção. O serviço oferece suporte ao envio de um HTTP `GET` na coleção de URI para recuperar a coleção inteira e HTTP `POST` no URI para adicionar um novo cliente à coleção da coleção. Também no URI para um cliente individual, ele dá suporte a HTTP `GET` para obter detalhes, HTTP de cliente `PUT` para substituir os detalhes do cliente e HTTP `DELETE` para remover o cliente da coleção. Quando um novo cliente é adicionado à coleção, o serviço atribui a ele um URI exclusivo e armazena o URI como parte dos detalhes do cliente. Além disso, ele se comunica o URI para o cliente usando o cabeçalho de local HTTP da resposta.  
  
 O arquivo App. config configura o serviço WCF com um padrão <xref:System.ServiceModel.Description.WebHttpEndpoint> que tem o <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> propriedade definida como `true`. Como resultado, o WCF cria uma página de Ajuda em HTML automática no `http://localhost:8000/Customers/help` que fornece informações sobre como construir HTTP solicitações para o serviço e como acessar a resposta do serviço HTTP – por exemplo, um exemplo de como os detalhes do cliente é representado em XML e JSON.  
  
 Expor a coleção de cliente (e, de modo geral, qualquer recurso) dessa maneira permite que o cliente interagir com ele, de maneira uniforme usando HTTP e URIs `GET`, `PUT`, `DELETE` e `POST`. Program.cs demonstra como esse cliente pode ser criados usando <xref:System.Net.HttpWebRequest>. Observe que isso é apenas uma maneira de acessar um serviço REST do WCF. Também é possível acessar o serviço de uso de outras classes do .NET Framework, como o <xref:System.ServiceModel.ChannelFactory> e <xref:System.Net.WebClient>. Outros exemplos no SDK (como o [serviço HTTP básico](../../../../docs/framework/wcf/samples/basic-http-service.md) exemplo e o [seleção automática de formato](../../../../docs/framework/wcf/samples/automatic-format-selection.md) exemplo) mostram como usar essas classes para se comunicar com um serviço WCF.  
  
 O exemplo consiste em um serviço auto-hospedado e um cliente que ambos executados em um aplicativo de console. Como o aplicativo de console é executado, o cliente faz solicitações para o serviço e grava as informações pertinentes das respostas à janela do console.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Abra a solução para o exemplo de serviço básico do recurso. Ao iniciar [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], você deve executar como administrador para o exemplo para executar com êxito. Fazer isso clicando com o [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] ícone e selecionando **executar como administrador** no menu de contexto.  
  
2.  Pressione CTRL + SHIFT + B para compilar a solução e, em seguida, pressione Ctrl + F5 para executar o aplicativo de console. A janela do console é exibida e fornece o URI do serviço em execução e o URI do HTML na página para a execução do serviço de Ajuda. A qualquer momento, você pode exibir a página de ajuda HTML, digitando o URI da página de Ajuda em um navegador. Como o exemplo é executado, o cliente grava o status da atividade atual.  
  
3.  Pressione qualquer tecla para encerrar a amostra.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\BasicResourceService`  
  
## <a name="see-also"></a>Consulte também  
 [Serviço HTTP básico](../../../../docs/framework/wcf/samples/basic-http-service.md)  
 [Seleção automática de formato](../../../../docs/framework/wcf/samples/automatic-format-selection.md)
