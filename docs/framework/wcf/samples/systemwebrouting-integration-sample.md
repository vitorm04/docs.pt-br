---
title: Exemplo de integração de SystemWebRouting
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 52b908d354771cb2b351e339881647462340b716
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806520"
---
# <a name="systemwebrouting-integration-sample"></a>Exemplo de integração de SystemWebRouting
Este exemplo demonstra a integração da camada de hospedagem com as classes de <xref:System.Web.Routing> namespace. As classes de <xref:System.Web.Routing> namespace permitem que um aplicativo usar URLs não correspondem diretamente a um recurso físico. Usando o roteamento da Web permite ao desenvolvedor criar endereços virtuais para HTTP, em seguida, são mapeados para os serviços WCF reais. Isso é útil quando um serviço WCF deve ser hospedado sem a necessidade de um arquivo físico ou recurso, ou quando os serviços devem ser acessados com URLs que não contêm arquivos, como HTML ou. aspx. Este exemplo demonstra como utilizar o <xref:System.Web.Routing.RouteTable> classe para criar URIs virtuais que são mapeados para executar serviços definidos em global. asax. 

> [!NOTE]
>  As classes de <xref:System.Web.Routing> namespace só funciona para serviços hospedados por HTTP.  
  
Este exemplo usa o WCF para criar dois feeds RSS: um `movies` feed e um `channels` feed. As URLs para ativar os serviços não contêm uma extensão e são registradas no `Application_Start` método o `Global` classe derivada do <xref:System.Web.HttpApplication> classe.  
  
> [!NOTE]
>  Este exemplo funciona apenas no Internet Information Services (IIS) 7.0 e posterior, como o IIS 6.0 usa um método diferente para dar suporte a URLs sem extensão.  

#### <a name="to-download-this-sample"></a>Para baixar esse exemplo
  
Este exemplo pode já estar instalado no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando o Visual Studio, abra o arquivo WebRoutingIntegration.sln.  
  
2.  Para executar a solução e iniciar o servidor de desenvolvimento da Web, pressione F5.  
  
     Uma listagem para o exemplo de diretório é exibida. Observe que não há nenhum arquivo com uma extensão de arquivo. svc.  
  
3.  Na barra de endereços, adicionar `movies` para a URL, para que ele apareça http://localhost:[port] filmes e pressione ENTER.  
  
     O feed de filmes aparece no navegador.  
  
4.  Na barra de endereços, adicionar `channels` para a URL, isso é leituras http://localhost:[porta] / canais e pressione ENTER.  
  
     O feed de canais é exibida no navegador.  
  
5.  Feche o navegador da Web, pressionando ALT + F4.  
  
     Se o servidor de desenvolvimento não saiu, clique no ícone da área de notificação e selecione **parar**.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>Para usar esse exemplo, quando hospedados no IIS  
  
1.  Usando o Visual Studio, abra o arquivo WebRoutingIntegration.sln.  
  
2.  Compile o projeto, pressionando CTRL + SHIFT + B.  
  
3.  Crie um aplicativo Web no Gerenciador de serviços de informações da Internet (IIS).  
  
    1.  Clique com botão direito no Gerenciador do IIS, o **Default Web Site** e selecione **adicionar um aplicativo**.  
  
    2.  Para o **alias**, digite `WebRoutingIntegration`.  
  
    3.  Para o **caminho físico**, selecione a pasta do serviço dentro do projeto.  
  
    4.  Press **OK**.  
  
4.  Iniciar o aplicativo, clicando duas vezes o aplicativo Web e selecionando **gerenciar aplicativo** e **procurar**.  
  
5.  Na barra de endereços, adicionar `movies` para a URL, isso é leituras http://localhost:[port] filmes e pressione ENTER.  
  
     O feed de filmes aparece no navegador.  
  
6.  Na barra de endereços, adicionar `channels` para a URL, isso é leituras http://localhost:[porta] / canais e pressione ENTER.  
  
     O feed de canais é exibida no navegador.  
  
7.  Feche o navegador da Web, pressionando ALT + F4.  
  
 Este exemplo demonstra que a camada de hospedagem é capaz de composição com as classes de <xref:System.Web.Routing> namespace para direcionar solicitações de serviços hospedados por HTTP.  
  
> [!NOTE]
>  Você deve atualizar a versão de pool de aplicativos padrão para [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] se ele estiver definido para a versão 2.  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de persistência e hospedagem de AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
