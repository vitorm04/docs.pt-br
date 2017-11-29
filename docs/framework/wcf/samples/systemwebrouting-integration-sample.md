---
title: "Exemplo de integração de SystemWebRouting"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e5050834ff01ebb6a25e746d88f7d328ded505cd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="systemwebrouting-integration-sample"></a>Exemplo de integração de SystemWebRouting
Este exemplo demonstra a integração da camada de hospedagem com as classes de <xref:System.Web.Routing> namespace. As classes de <xref:System.Web.Routing> namespace permitem que um aplicativo usar URLs não correspondem diretamente a um recurso físico. Usando o roteamento da Web permite ao desenvolvedor criar endereços virtuais para HTTP, em seguida, são mapeados para real [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços. Isso é útil quando um serviço WCF deve ser hospedado sem a necessidade de um arquivo físico ou recurso, ou quando os serviços devem ser acessados com URLs que não contêm arquivos, como HTML ou. aspx. Este exemplo demonstra como utilizar o <xref:System.Web.Routing.RouteTable> classe para criar URIs virtuais que são mapeados para executar serviços definidos em global. asax. Neste exemplo, há dois feeds RSS criados usando o WCF: um `movies` feed e um `channels` feed. As URLs para ativar os serviços não contêm uma extensão e são registradas no `Application_Start` método o `Global` classe derivada do <xref:System.Web.HttpApplication.Application_Start> classe.  
  
> [!NOTE]
>  As classes de <xref:System.Web.Routing> namespace só funciona para serviços hospedados por HTTP.  
  
> [!NOTE]
>  Este exemplo só funciona [!INCLUDE[iisver](../../../../includes/iisver-md.md)], como [!INCLUDE[iis60](../../../../includes/iis60-md.md)] usa um método diferente para dar suporte a URLs sem extensão.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo WebRoutingIntegration.sln.  
  
2.  Para executar a solução e iniciar o servidor de desenvolvimento da Web, pressione F5.  
  
     Uma listagem para o exemplo de diretório é exibida. Observe que não há nenhum arquivo com uma extensão de arquivo. svc.  
  
3.  Na barra de endereços, adicionar `movies` à URL, isso é leituras http://localhost: [porta] filmes e pressione ENTER.  
  
     O feed de filmes aparece no navegador.  
  
4.  Na barra de endereços, adicionar `channels` à URL, isso é leituras http://localhost: [porta] / canais e pressione ENTER.  
  
     O feed de canais é exibida no navegador.  
  
5.  Feche o navegador da Web, pressionando ALT + F4.  
  
     Se o servidor de desenvolvimento não saiu, clique no ícone da área de notificação e selecione **parar**.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>Para usar esse exemplo, quando hospedados no IIS  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo WebRoutingIntegration.sln.  
  
2.  Compile o projeto, pressionando CTRL + SHIFT + B.  
  
3.  Crie um aplicativo Web no Gerenciador de serviços de informações da Internet (IIS).  
  
    1.  Clique com botão direito no Gerenciador do IIS, o **Default Web Site** e selecione **adicionar um aplicativo**.  
  
    2.  Para o **alias**, digite `WebRoutingIntegration`.  
  
    3.  Para o **caminho físico**, selecione a pasta do serviço dentro do projeto.  
  
    4.  Press **OK**.  
  
4.  Iniciar o aplicativo, clicando duas vezes o aplicativo Web e selecionando **gerenciar aplicativo** e **procurar**.  
  
5.  Na barra de endereços, adicionar `movies` à URL, isso é leituras http://localhost: [porta] filmes e pressione ENTER.  
  
     O feed de filmes aparece no navegador.  
  
6.  Na barra de endereços, adicionar `channels` à URL, isso é leituras http://localhost: [porta] / canais e pressione ENTER.  
  
     O feed de canais é exibida no navegador.  
  
7.  Feche o navegador da Web, pressionando ALT + F4.  
  
 Este exemplo demonstra que a camada de hospedagem é capaz de composição com as classes de <xref:System.Web.Routing> namespace para direcionar solicitações de serviços hospedados por HTTP.  
  
> [!NOTE]
>  Atualize a versão de pool de aplicativos padrão para [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] se ele estiver definido para a versão 2.  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de persistência e hospedagem de AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
