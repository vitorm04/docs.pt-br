---
title: Exemplo de integração de SystemWebRouting
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 2f12d80085e3ac27dac8ce80b6bb09f69337bfd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143948"
---
# <a name="systemwebrouting-integration-sample"></a>Exemplo de integração de SystemWebRouting
Esta amostra demonstra a integração da camada <xref:System.Web.Routing> de hospedagem com as classes no namespace. As classes <xref:System.Web.Routing> no namespace permitem que um aplicativo use URLs que não correspondam diretamente a um recurso físico. O uso do roteamento da Web permite que o desenvolvedor crie endereços virtuais para HTTP que são então mapeados de volta aos serviços WCF reais. Isso é útil quando um serviço WCF deve ser hospedado sem exigir um arquivo físico ou recurso, ou quando os serviços devem ser acessados com URLs que não contêm arquivos como .html ou .aspx. Esta amostra demonstra como <xref:System.Web.Routing.RouteTable> utilizar a classe para criar URIs virtuais que mapeiam para executar serviços definidos em global.asax.

> [!NOTE]
> As classes <xref:System.Web.Routing> no namespace só funcionam para serviços hospedados em HTTP.  
  
Este exemplo usa WCF para criar dois `movies` feeds `channels` RSS: um feed e um feed. Os URLs para ativar os serviços não contêm `Application_Start` uma `Global` extensão e <xref:System.Web.HttpApplication> estão registrados no método da classe derivada da classe.  
  
> [!NOTE]
> Essa amostra só funciona em Serviços de Informação da Internet (IIS) 7.0 e posteriormente, pois o IIS 6.0 usa um método diferente para suportar URLs sem extensão.  

#### <a name="to-download-this-sample"></a>Para baixar esta amostra
  
Esta amostra já pode estar instalada no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  

`<InstallDrive>:\WF_WCF_Samples`  

 Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  

`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1. Usando o Visual Studio, abra o arquivo WebRoutingIntegration.sln.  
  
2. Para executar a solução e iniciar o servidor de desenvolvimento web, pressione F5.  
  
     Uma lista de diretórios para a amostra é exibida. Observe que não há arquivos com uma extensão de arquivo .svc.  
  
3. Na barra de `movies` endereços, `http://localhost:[port]/movies` adicione à URL, para que ela leia e pressione ENTER.  
  
     O feed de filmes aparece no navegador.  
  
4. Na barra de `channels` endereços, adicione à URL, `http://localhost:[port]/channels` de modo que seja leitura e pressione ENTER.  
  
     O feed de canais aparece no navegador.  
  
5. Feche o navegador da Web pressionando ALT+F4.  
  
     Se o servidor de desenvolvimento não tiver saído, clique com o botão direito do mouse no ícone da área de notificação e selecione **Parar**.  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a>Para usar esta amostra quando hospedado no IIS  
  
1. Usando o Visual Studio, abra o arquivo WebRoutingIntegration.sln.  
  
2. Construa o projeto, pressionando CTRL+SHIFT+B.  
  
3. Crie um aplicativo web no Gerenciador de Serviços de Informação da Internet (IIS).  
  
    1. No IIS Manager, clique com o botão direito do mouse no **Site padrão da Web** e **selecione Adicionar um aplicativo**.  
  
    2. Para o **alias,** digite `WebRoutingIntegration`.  
  
    3. Para o **Caminho Físico,** selecione a pasta Serviço dentro do projeto.  
  
    4. Pressione **OK**.  
  
4. Inicie o aplicativo, clicando com o botão direito do mouse no aplicativo web e selecionando **Gerenciar o aplicativo** e, em seguida, **procurar**.  
  
5. Na barra de `movies` endereços, adicione à URL, `http://localhost:[port]/movies` de modo que seja leitura e pressione ENTER.  
  
     O feed de filmes aparece no navegador.  
  
6. Na barra de `channels` endereços, adicione à URL, `http://localhost:[port]/channels` de modo que seja leitura e pressione ENTER.  
  
     O feed de canais aparece no navegador.  
  
7. Feche o navegador da Web pressionando ALT+F4.  
  
 Esta amostra demonstra que a camada de hospedagem <xref:System.Web.Routing> é capaz de compor com as classes no namespace para roteamento das solicitações de serviços hospedados em HTTP.  
  
> [!NOTE]
> Você deve atualizar a versão padrão do pool de aplicativos para .NET Framework 4 se estiver definida como versão 2.  
  
## <a name="see-also"></a>Confira também

- [Hospedagem de AppFabric e persistência Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))
