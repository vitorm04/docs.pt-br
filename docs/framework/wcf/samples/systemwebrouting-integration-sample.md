---
title: Exemplo de integração de SystemWebRouting
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: a9f9dc871b92b8cd689234c79b09c98e38a2848d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650993"
---
# <a name="systemwebrouting-integration-sample"></a>Exemplo de integração de SystemWebRouting
Este exemplo demonstra a integração da camada de hospedagem com as classes de <xref:System.Web.Routing> namespace. As classes de <xref:System.Web.Routing> namespace permitem que um aplicativo usar URLs que não correspondem diretamente a um recurso físico. Usando o roteamento da Web permite que o desenvolvedor crie endereços virtuais para HTTP, em seguida, são mapeados para os serviços WCF reais. Isso é útil quando um serviço WCF deve ser hospedado sem a necessidade de um arquivo físico ou recurso, ou quando os serviços devem ser acessados com URLs que não contêm arquivos como. HTML ou. aspx. Este exemplo demonstra como utilizar o <xref:System.Web.Routing.RouteTable> classe para criar URIs virtuais que são mapeados para executar serviços definidos no global. asax. 

> [!NOTE]
>  As classes de <xref:System.Web.Routing> namespace só funcionam para serviços hospedados por HTTP.  
  
Este exemplo usa o WCF para criar dois feeds de RSS: uma `movies` feed e um `channels` feed. As URLs para ativar os serviços não contêm uma extensão e são registradas na `Application_Start` método da `Global` classe derivada a <xref:System.Web.HttpApplication> classe.  
  
> [!NOTE]
>  Este exemplo só funciona no Internet Information Services (IIS) 7.0 e posterior, como o IIS 6.0 usa um método diferente para dar suporte a URLs sem extensão.  

#### <a name="to-download-this-sample"></a>Para baixar esse exemplo
  
Este exemplo pode já estar instalado no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1. Usando o Visual Studio, abra o arquivo de WebRoutingIntegration.sln.  
  
2. Para executar a solução e iniciar o Web development server, pressione F5.  
  
     Um listagem de diretório para a amostra é exibida. Observe que não há nenhum arquivo com uma extensão de arquivo. svc.  
  
3. Na barra de endereços, adicione `movies` à URL, para que ele apareça `http://localhost:[port]/movies` e pressione ENTER.  
  
     O feed de filmes é exibida no navegador.  
  
4. Na barra de endereços, adicione `channels` à URL, portanto, que é leituras `http://localhost:[port]/channels` e pressione ENTER.  
  
     O feed de canais é exibida no navegador.  
  
5. Feche o navegador da Web, pressionando ALT + F4.  
  
     Se o servidor de desenvolvimento não tiver sido encerrado, o botão direito do mouse no ícone da área de notificação e selecione **parar**.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>Para usar este exemplo quando hospedado no IIS  
  
1. Usando o Visual Studio, abra o arquivo de WebRoutingIntegration.sln.  
  
2. Compile o projeto, pressionando CTRL + SHIFT + B.  
  
3. Crie um aplicativo Web no Gerenciador de serviços de informações da Internet (IIS).  
  
    1. Clique com botão direito no Gerenciador do IIS, o **Site padrão** e selecione **adicionar um aplicativo**.  
  
    2. Para o **alias**, digite `WebRoutingIntegration`.  
  
    3. Para o **caminho físico**, selecione a pasta de serviço dentro do projeto.  
  
    4. Pressione **OK**.  
  
4. Iniciar o aplicativo, clicando duas vezes o aplicativo Web e selecionando **gerenciar aplicativo** e, em seguida **procurar**.  
  
5. Na barra de endereços, adicione `movies` à URL, portanto, que é leituras `http://localhost:[port]/movies` e pressione ENTER.  
  
     O feed de filmes é exibida no navegador.  
  
6. Na barra de endereços, adicione `channels` à URL, portanto, que é leituras `http://localhost:[port]/channels` e pressione ENTER.  
  
     O feed de canais é exibida no navegador.  
  
7. Feche o navegador da Web, pressionando ALT + F4.  
  
 Este exemplo demonstra que a camada de hospedagem é capaz de composição com as classes de <xref:System.Web.Routing> namespace para as solicitações de serviços hospedados por meio de HTTP de roteamento.  
  
> [!NOTE]
>  Você deve atualizar a versão padrão do pool de aplicativo para [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] se ele estiver definido para a versão 2.  
  
## <a name="see-also"></a>Consulte também

- [Hospedagem de AppFabric e persistência exemplos](https://go.microsoft.com/fwlink/?LinkId=193961)
