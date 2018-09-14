---
title: Rastreamento analítico do WCF
ms.date: 03/30/2017
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
ms.openlocfilehash: 006f8aa0bc2f32e43269aa83433e8ca7a773a1c9
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2018
ms.locfileid: "45597336"
---
# <a name="wcf-analytic-tracing"></a>Rastreamento analítico do WCF
Este exemplo demonstra como adicionar seus próprios eventos de rastreamento no fluxo de rastreamentos analíticos que grava ETW no Windows Communication Foundation (WCF) [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]. Rastreamentos de analíticos destinam-se tornar mais fácil de obter visibilidade em seus serviços sem pagar uma penalidade de alto desempenho. Este exemplo mostra como usar o <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> APIs para eventos de gravação que se integram com os serviços WCF.  
  
 Para obter mais informações sobre o <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> APIs, consulte <xref:System.Diagnostics.Eventing?displayProperty=nameWithType>.  
  
 Para saber mais sobre o rastreamento de eventos no Windows, consulte [melhorar a depuração e ajuste de desempenho com o ETW](https://go.microsoft.com/fwlink/?LinkId=166488).  
  
## <a name="disposing-eventprovider"></a>Descartando EventProvider  
 Este exemplo usa o <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> de classe que implementa <xref:System.IDisposable?displayProperty=nameWithType>. Ao implementar o rastreamento para um serviço WCF, é provável que você pode usar o <xref:System.Diagnostics.Eventing.EventProvider>do recursos para o tempo de vida do serviço. Por esse motivo e para facilitar a leitura, este exemplo nunca descarta encapsulado <xref:System.Diagnostics.Eventing.EventProvider>. Se por algum motivo, o serviço tem diferentes requisitos de rastreamento e você devem descartar este recurso, você deve modificar esse exemplo de acordo com as práticas recomendadas para o descarte de recursos não gerenciados. Para obter mais informações sobre como descartar os recursos não gerenciados, consulte [implementando um método Dispose](https://go.microsoft.com/fwlink/?LinkId=166436).  
  
## <a name="self-hosting-vs-web-hosting"></a>Hospedagem interna vs. Hospedagem na Web  
 Para serviços hospedados na Web, rastreamentos de analítica do WCF fornecem um campo chamado "HostReference", que é usado para identificar o serviço que está emitindo rastreamentos. Os rastreamentos do usuário extensível podem participar desse modelo e este exemplo demonstra as práticas recomendadas para fazer isso. O formato de um host da Web de referência quando o pipe '&#124;' caracteres será exibida na resultante cadeia de caracteres pode ser qualquer um dos seguintes:  
  
-   Se o aplicativo não estiver na raiz.  
  
     \<NomeDoSite >\<ApplicationVirtualPath >&#124;\<ServiceVirtualPath >&#124;\<ServiceName >  
  
-   Se o aplicativo está na raiz.  
  
     \<Nome do site >&#124;\<ServiceVirtualPath >&#124;\<ServiceName >  
  
 Para serviços são hospedados, os rastreamentos de analítica do WCF não preencher o campo de "HostReference". O `WCFUserEventProvider` classe neste exemplo se comporta de forma consistente quando usado por um serviço auto-hospedado.  
  
## <a name="custom-event-details"></a>Detalhes do evento personalizado  
 Manifesto do provedor de eventos ETW do WCF define três eventos que são projetados para ser emitida por autores de serviço do WCF de dentro do código de serviço. A tabela a seguir mostra uma divisão dos três eventos.  
  
|evento|Descrição|ID do evento|  
|-----------|-----------------|--------------|  
|UserDefinedInformationEventOccurred|Emita esse evento quando algo de nota acontece em seu serviço que não é um problema. Por exemplo, você pode emitir um evento depois de fazer com êxito uma chamada para um banco de dados.|301|  
|UserDefinedWarningOccurred|Emitir este evento quando ocorre um problema que pode resultar em uma falha no futuro. Por exemplo, você pode emitir um evento de aviso quando uma chamada para um banco de dados falha, mas você conseguir recuperar ao fazer fallback para um armazenamento de dados redundantes.|302|  
|UserDefinedErrorOccurred|Emita esse evento quando o serviço não se comportar conforme o esperado. Por exemplo, você pode emitir um evento se uma chamada para um banco de dados falha e você não foi possível recuperar os dados de qualquer outro lugar.|303|  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo de solução WCFAnalyticTracingExtensibility.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione CTRL+F5.  
  
     No navegador da Web, clique em **Calculator.svc**. O URI do documento WSDL para o serviço deve aparecer no navegador. Copie esse URI.  
  
4.  Execute o cliente de teste do WCF (WcfTestClient.exe).  
  
     O cliente de teste do WCF (WcfTestClient.exe) está localizado na \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] diretório de instalação > \Common7\IDE\ WcfTestClient.exe (padrão [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] dir de instalação é C:\Program Files\Microsoft Visual Studio 10.0).  
  
5.  Dentro do cliente de teste do WCF, adicione o serviço, selecionando **arquivo**e então **Adicionar serviço**.  
  
     Adicione o endereço do ponto de extremidade na caixa de entrada.  
  
6.  Clique em **Okey** para fechar a caixa de diálogo.  
  
     O serviço de ICalculator é adicionado no painel esquerdo, sob **meus projetos de serviço**.  
  
7.  Abra o aplicativo visualizador de eventos.  
  
     Antes de invocar o serviço, inicie o Visualizador de eventos e certifique-se de que o log de eventos é escutando eventos de rastreamento emitidos de serviço do WCF.  
  
8.  Dos **inicie** menu, selecione **ferramentas administrativas**e, em seguida, **Visualizador de eventos**. Habilitar o **analítico** e **depurar** logs.  
  
9. Na exibição de árvore no Visualizador de eventos, navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida, **Aplicativos de servidor**. Clique com botão direito **aplicativos de servidor**, selecione **exibição**e então **Mostrar Logs analíticos e depuração**.  
  
     Certifique-se de que o **Mostrar Logs analíticos e depuração** opção estiver marcada. Habilitar o **analítico** log.  
  
     Na exibição de árvore no Visualizador de eventos, navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**,  **Aplicativos de servidor**e então **analítica**. Clique com botão direito **analítico** e selecione **Habilitar Log**.  
  
10. Testar o serviço usando a Test usuário.  
  
    1.  No cliente de teste do WCF, clique duas vezes em **Add ()** sob o nó do serviço de ICalculator.  
  
         O **Add ()** método aparece no painel direito com dois parâmetros.  
  
    2.  Digite 2 para o primeiro parâmetro e 3 para o segundo parâmetro.  
  
    3.  Clique em **Invoke** para invocar o método.  
  
11. Vá para o **Visualizador de eventos** janela que você já abriu. Navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**, **aplicativo Aplicativos de servidor**.  
  
12. Clique com botão direito do **analítico** nó e selecione **atualizar**.  
  
     Os eventos são exibidos no painel direito.  
  
13. Localize o evento com a ID do 303 e clique duas vezes nele para abri-lo e inspecione seu conteúdo.  
  
     Esse evento foi emitido pela `Add()` método do serviço de ICalculator e tem uma carga igual a "2 + 3 = 5".  
  
#### <a name="to-clean-up-optional"></a>Para limpar (opcional)  
  
1.  Abra **Visualizador de eventos**.  
  
2.  Navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida,  **Aplicativos de servidor**. Clique com botão direito **analítico** e selecione **desabilitar Log**.  
  
3.  Navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**,  **Aplicativos de servidor**e então **analítica**. Clique com botão direito **analítico** e selecione **Limpar Log**.  
  
4.  Clique em **limpar** para limpar os eventos.  
  
## <a name="known-issue"></a>Problema conhecido  
 Há um problema conhecido na **Visualizador de eventos** onde ele pode não decodifica eventos ETW. Você poderá ver uma mensagem de erro que diz: "a descrição para a ID de evento \<id > Microsoft-Windows-aplicativos de servidor de origem não podem ser encontrados. Qualquer o componente que gerencie esse evento não é instalado em seu computador local ou na instalação for danificado. Você pode instalar ou reparar o componente no computador local." Se você encontrar esse erro, selecione **Refresh** da **ações** menu. O evento, em seguida, deve decodificar corretamente.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>Consulte também  
 [AppFabric que monitora exemplos](https://go.microsoft.com/fwlink/?LinkId=193959)
