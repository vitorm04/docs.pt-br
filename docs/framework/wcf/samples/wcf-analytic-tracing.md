---
title: Rastreamento analítico do WCF
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 57e3ee18848031bce8ffbb54d26353fe36ee1def
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="wcf-analytic-tracing"></a>Rastreamento analítico do WCF
Este exemplo demonstra como adicionar seus próprios eventos de rastreamento no fluxo de analíticos rastreamentos que [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] grava ETW no [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]. Rastreamentos analíticos destinam-se para tornar mais fácil obter visibilidade em seus serviços sem pagar uma penalidade de desempenho alto. Este exemplo mostra como usar o <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> APIs para eventos de gravação que se integram ao [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviços.  
  
 Para obter mais informações sobre o <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> APIs, consulte <xref:System.Diagnostics.Eventing?displayProperty=nameWithType>.  
  
 Para saber mais sobre o rastreamento de eventos do Windows, consulte [melhorar a depuração e ajuste de desempenho com o ETW](http://go.microsoft.com/fwlink/?LinkId=166488).  
  
## <a name="disposing-eventprovider"></a>Descartando EventProvider  
 Este exemplo usa o <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> de classe que implementa <xref:System.IDisposable?displayProperty=nameWithType>. Ao implementar o rastreamento para uma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] serviço, é provável que você pode usar o <xref:System.Diagnostics.Eventing.EventProvider>de recursos para o tempo de vida do serviço. Por esse motivo e para facilitar a leitura, este exemplo nunca descarta o encapsulado <xref:System.Diagnostics.Eventing.EventProvider>. Se por algum motivo, o serviço tem diferentes requisitos de rastreamento e você devem descartar este recurso, você deve modificar esse exemplo de acordo com as práticas recomendadas para o descarte de recursos não gerenciados. Para obter mais informações sobre como descartar os recursos não gerenciados, consulte [implementar um método Dispose](http://go.microsoft.com/fwlink/?LinkId=166436).  
  
## <a name="self-hosting-vs-web-hosting"></a>Auto-hospedagem vs. Hospedagem na Web  
 Para serviços Web hospedados, rastreamentos analíticos do WCF fornecem um campo chamado "HostReference", que é usado para identificar o serviço que está emitindo rastreamentos. Os rastreamentos do usuário extensíveis podem participar neste modelo e demonstra práticas recomendadas para fazer isso. O formato de um host da Web referência quando o pipe '&#124;' caractere será exibida na resultante cadeia de caracteres pode ser qualquer um dos seguintes:  
  
-   Se o aplicativo não estiver na raiz.  
  
     \<Nome do site >\<ApplicationVirtualPath >&#124;\<ServiceVirtualPath >&#124;\<ServiceName >  
  
-   Se o aplicativo está na raiz.  
  
     \<Nome do site >&#124;\<ServiceVirtualPath >&#124;\<ServiceName >  
  
 Para serviços de hospedagem interna, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]do rastreamentos analíticos não preenchem o campo "HostReference". O `WCFUserEventProvider` classe neste exemplo se comporta de forma consistente quando usado por um serviço auto-hospedado.  
  
## <a name="custom-event-details"></a>Detalhes do evento personalizado  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]do manifesto do provedor de eventos ETW define três eventos que são projetados para ser emitida por [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] autores de dentro do código de serviço do serviço. A tabela a seguir mostra uma divisão dos três eventos.  
  
|evento|Descrição|ID do evento|  
|-----------|-----------------|--------------|  
|UserDefinedInformationEventOccurred|Emita esse evento quando algo Observação acontece em seu serviço que não é um problema. Por exemplo, você pode emitir um evento com êxito após uma chamada para um banco de dados.|301|  
|UserDefinedWarningOccurred|Emitir este evento quando ocorre um problema que pode resultar em uma falha no futuro. Por exemplo, você pode emitir um evento de aviso quando uma chamada para um banco de dados falhar, mas você conseguiu recuperar voltando para um repositório de dados redundantes.|302|  
|UserDefinedErrorOccurred|Emita esse evento quando seu serviço não se comportar conforme o esperado. Por exemplo, você pode emitir um evento se uma chamada para um banco de dados falha e você não foi possível recuperar os dados de qualquer outro lugar.|303|  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo de solução de WCFAnalyticTracingExtensibility.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione CTRL+F5.  
  
     No navegador da Web, clique em **Calculator.svc**. O URI do documento WSDL para o serviço deve aparecer no navegador. Copie esse URI.  
  
4.  Execute o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente de teste (WcfTestClient.exe).  
  
     O [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente de teste (WcfTestClient.exe) está localizado no \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] instalar Dir > \Common7\IDE\ WcfTestClient.exe (padrão [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] dir de instalação é C:\Program Files\Microsoft Visual Studio 10.0).  
  
5.  Dentro de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente de teste, adicione o serviço selecionando **arquivo**e, em seguida, **Adicionar serviço**.  
  
     Adicione o endereço do ponto de extremidade na caixa de entrada.  
  
6.  Clique em **Okey** para fechar a caixa de diálogo.  
  
     O serviço de ICalculator é adicionado no painel esquerdo, em **meus projetos de serviço**.  
  
7.  Abra o aplicativo visualizador de eventos.  
  
     Antes de chamar o serviço, iniciar o Visualizador de eventos e certifique-se de que o log de eventos está escutando para rastreamento de eventos emitidas a partir de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.  
  
8.  Do **iniciar** menu, selecione **ferramentas administrativas**e, em seguida, **Visualizador de eventos**. Habilitar o **analítico** e **depurar** logs.  
  
9. Na exibição de árvore no Visualizador de eventos, navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida, **Aplicativos de servidor de aplicativo**. Clique com botão direito **aplicativos de servidor de aplicativo**, selecione **exibição**e, em seguida, **Mostrar Logs analíticos e depuração**.  
  
     Certifique-se de que o **Mostrar Logs analíticos e depuração** opção estiver marcada. Habilitar o **analítico** log.  
  
     Na exibição de árvore no Visualizador de eventos, navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**,  **Aplicativos de servidor de aplicativo**e, em seguida, **analíticos**. Clique com botão direito **analítico** e selecione **Habilitar Log**.  
  
10. Testar o serviço usando a Test usuário.  
  
    1.  No cliente de teste do WCF, clique duas vezes em **Add** sob o nó de serviço ICalculator.  
  
         O **Add** método aparece no painel direito, com dois parâmetros.  
  
    2.  Digite 2 para o primeiro parâmetro e 3 para o segundo parâmetro.  
  
    3.  Clique em **Invoke** para invocar o método.  
  
11. Vá para o **Visualizador de eventos** janela que você já abriu. Navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**, **aplicativo Aplicativos de servidor**.  
  
12. Clique com botão direito do **analítico** nó e selecione **atualizar**.  
  
     Os eventos são exibidos no painel direito.  
  
13. Localize o evento com a ID do 303 e clique duas vezes nele para abri-lo e inspecionar o conteúdo.  
  
     Esse evento foi emitido pelo `Add()` método do serviço ICalculator e tem uma carga igual a "2 + 3 = 5".  
  
#### <a name="to-clean-up-optional"></a>Para limpar (opcional)  
  
1.  Abra **Visualizador de eventos**.  
  
2.  Navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida,  **Aplicativos de servidor de aplicativo**. Clique com botão direito **analítico** e selecione **desabilitar Log**.  
  
3.  Navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**,  **Aplicativos de servidor de aplicativo**e, em seguida, **analíticos**. Clique com botão direito **analítico** e selecione **Limpar Log**.  
  
4.  Clique em **limpar** para limpar os eventos.  
  
## <a name="known-issue"></a>Problema conhecido  
 Há um problema conhecido no **Visualizador de eventos** onde ele poderá falhar ao decodificar eventos ETW. Você verá uma mensagem de erro que diz: "a descrição da identificação de evento \<id > de fonte de aplicativos de servidor de aplicativo do Microsoft Windows não podem ser encontrados. Qualquer o componente que gerencie esse evento não é instalado em seu computador local ou na instalação for danificado. Você pode instalar ou reparar o componente no computador local." Se você encontrar esse erro, selecione **atualizar** do **ações** menu. O evento, em seguida, deve decodificar corretamente.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de monitoramento do AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
