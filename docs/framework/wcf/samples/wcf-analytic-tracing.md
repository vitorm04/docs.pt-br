---
title: Rastreamento analítico do WCF
ms.date: 03/30/2017
ms.assetid: 6029c7c7-3515-4d36-9d43-13e8f4971790
ms.openlocfilehash: ef636a672d9384e8e3d658f0488cfaadb8d293e4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183225"
---
# <a name="wcf-analytic-tracing"></a>Rastreamento analítico do WCF
Esta amostra demonstra como adicionar seus próprios eventos de rastreamento ao fluxo de traços analíticos [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]que a Windows Communication Foundation (WCF) escreve ao ETW em . Os traços analíticos são feitos para facilitar a visibilidade de seus serviços sem pagar uma multa de alto desempenho. Esta amostra mostra como <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> usar as APIs para escrever eventos que se integram aos serviços wcf.  
  
 Para obter mais <xref:System.Diagnostics.Eventing?displayProperty=nameWithType> informações sobre <xref:System.Diagnostics.Eventing?displayProperty=nameWithType>as APIs, consulte .  
  
 Para saber mais sobre o rastreamento de eventos no Windows, consulte [Melhorar a depuração e a sintonia de desempenho com o ETW](https://docs.microsoft.com/archive/msdn-magazine/2007/april/event-tracing-improve-debugging-and-performance-tuning-with-etw).  
  
## <a name="disposing-eventprovider"></a>Eliminando EventProvider  
 Esta amostra <xref:System.Diagnostics.Eventing.EventProvider?displayProperty=nameWithType> usa a classe, que implementa <xref:System.IDisposable?displayProperty=nameWithType>. Ao implementar o rastreamento de um serviço WCF, é <xref:System.Diagnostics.Eventing.EventProvider>provável que você possa usar os recursos durante toda a vida útil do serviço. Por essa razão, e para legibilidade, esta <xref:System.Diagnostics.Eventing.EventProvider>amostra nunca descarta o embrulho . Se por algum motivo seu serviço tiver requisitos diferentes para rastreamento e você tiver que descartar esse recurso, então você deve modificar esta amostra de acordo com as práticas recomendadas para eliminação de recursos não gerenciados. Para obter mais informações sobre a eliminação de recursos não gerenciados, consulte [Implementando um método de descarte](https://docs.microsoft.com/dotnet/standard/garbage-collection/implementing-dispose).  
  
## <a name="self-hosting-vs-web-hosting"></a>Auto-hospedagem vs. Hospedagem web  
 Para serviços hospedados na Web, os rastreamentos analíticos do WCF fornecem um campo chamado "HostReference", que é usado para identificar o serviço que está emitindo os rastreamentos. Os traços extensíveis do usuário podem participar deste modelo e esta amostra demonstra as melhores práticas para fazê-lo. O formato de uma referência de host da Web quando o caractere pipe '&#124;' realmente aparece na seqüência resultante pode ser qualquer um dos seguintes:  
  
- Se a aplicação não estiver na raiz.  
  
     \<Nome do \<site>\<aplicativoAplicativoVirtualPath \<>&#124;Serviçonome do serviço>>&#124;  
  
- Se a aplicação estiver na raiz.  
  
     \<SiteName \<>&#124;Serviço> \<de> de nome>&#124;do>  
  
 Para serviços autohospedados, os traços analíticos do WCF não preenchem o campo "HostReference". A `WCFUserEventProvider` classe nesta amostra se comporta consistentemente quando usada por um serviço auto-hospedado.  
  
## <a name="custom-event-details"></a>Detalhes personalizados do evento  
 O manifesto do Provedor de Eventos ETW da WCF define três eventos que foram projetados para serem emitidos por autores de serviços wcf a partir de dentro do código de serviço. A tabela a seguir mostra um detalhamento dos três eventos.  
  
|Evento|Descrição|ID do evento|  
|-----------|-----------------|--------------|  
|UserDefinedInformationEventOcorreu|Emita este evento quando algo de nota acontece em seu serviço que não é um problema. Por exemplo, você pode emitir um evento depois de fazer uma chamada com sucesso para um banco de dados.|301|  
|UserDefinedWarningOccurred|Emita este evento quando ocorre um problema que pode resultar em um fracasso no futuro. Por exemplo, você pode emitir um evento de aviso quando uma chamada para um banco de dados falha, mas você foi capaz de se recuperar voltando para um armazenamento de dados redundante.|302|  
|Erro definido pelo usuárioOcorreu|Emita este evento quando seu serviço não se comportar como esperado. Por exemplo, você pode emitir um evento se uma chamada para um banco de dados falhar e você não puder recuperar os dados de outro lugar.|303|  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1. Usando o Visual Studio 2012, abra o arquivo de solução WCFAnalyticTracingExtensibility.sln.  
  
2. Para criar a solução, pressione CTRL+SHIFT+B.  
  
3. Para executar a solução, pressione CTRL+F5.  
  
     No navegador da Web, clique em **Calculadora.svc**. O URI do documento WSDL para o serviço deve aparecer no navegador. Copie esse URI.  
  
4. Execute o cliente de teste WCF (WcfTestClient.exe).  
  
     O cliente de teste WCF (WcfTestClient.exe) está localizado em `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`. O visual studio padrão 2012 instalar dir é `C:\Program Files\Microsoft Visual Studio 10.0`.  
  
5. Dentro do cliente de teste WCF, adicione o serviço selecionando **Arquivo**e, em seguida, **Adicione serviço**.  
  
     Adicione o endereço do ponto de extremidade na caixa de entrada.  
  
6. Clique em **OK** para fechar o diálogo.  
  
     O serviço ICalculator é adicionado no painel esquerdo em **My Service Projects**.  
  
7. Abra o aplicativo visualizador de eventos.  
  
     Antes de invocar o serviço, inicie o Event Viewer e certifique-se de que o registro de eventos esteja ouvindo o rastreamento de eventos emitidos pelo serviço WCF.  
  
8. No menu **Iniciar,** selecione **Ferramentas Administrativas**e, em seguida, **Visualizador de Eventos**. Habilite os **registros de análise** e **depuração.**  
  
9. Na exibição da árvore no Event Viewer, navegue até **o Event Viewer,** **Applications and Services Logs,** **Microsoft,** **Windows**e, em seguida, **Application Server-Applications**. Clique com o botão direito do mouse **aplicativos de servidor de aplicativos,** selecione **Exibir**e, em seguida, mostrar registros de análise **e depuração**.  
  
     Certifique-se de que a opção **Mostrar registros de análise e depuração** seja verificada. Habilite o **registro analítico.**  
  
     Na exibição da árvore no Event Viewer, navegue até **o Event Viewer,** **Applications and Services Logs,** **Microsoft,** **Windows,** **Applications application**e, em seguida, **Analytic**. Clique com o botão direito do mouse **Em Análise** e **selecione Ativar log**.  
  
10. Testar o serviço usando a Test usuário.  
  
    1. No WCF Test Client, clique duas vezes **em Adicionar()** no nó de serviço iCalculator.  
  
         O método **Add()** aparece no painel direito com dois parâmetros.  
  
    2. Digite 2 para o primeiro parâmetro e 3 para o segundo parâmetro.  
  
    3. Clique **em Invocar** para invocar o método.  
  
11. Vá para a janela **Visualizador de eventos** que você já abriu. Navegar para **o Visualizador de Eventos,** **Registros de Aplicativos e Serviços,** **Microsoft,** **Windows,** **Aplicativos de Servidor de Aplicativos**.  
  
12. Clique com o botão direito do mouse no **nó Analítico** e **selecione Atualizar**.  
  
     Os eventos aparecem no painel direito.  
  
13. Localize o evento com o ID do 303 e clique duas vezes nele para abri-lo e inspecionar seu conteúdo.  
  
     Este evento foi emitido `Add()` pelo método do serviço ICalculator e tem uma carga útil igual a "2+3=5".  
  
#### <a name="to-clean-up-optional"></a>Para limpar (opcional)  
  
1. Abra o **Visualizador de Eventos**.  
  
2. Navegue até **o Visualizador de Eventos,** **Registros de aplicativos e serviços,** **Microsoft,** **Windows**e, em seguida, aplicativos de servidor **de aplicativos**. Clique com o botão direito do mouse **Em Analítica** e **selecione Desativar log**.  
  
3. Navegue até **o Visualizador de Eventos,** **Registros de Aplicativos e Serviços,** **Microsoft,** **Windows,** **Application-Server-Applications**e, em seguida, **Analytic**. Clique com o botão direito do mouse **Em Analítico** e selecione **Limpar Log**.  
  
4. Clique **em Limpar** para limpar os eventos.  
  
## <a name="known-issue"></a>Problema conhecido  
 Há um problema conhecido no **Event Viewer** onde ele pode falhar em decodificar eventos ETW. Você pode ver uma mensagem de erro que \<diz: "A descrição do ID de evento> de aplicativos de servidor de aplicativos microsoft-windows-application não pode ser encontrada. O componente que gera esse evento não está instalado no computador local ou a instalação está corrompida. Você pode instalar ou reparar o componente no computador local." Se você encontrar esse erro, **selecione Atualizar** no menu **Ações.** O evento deve então decodificar corretamente.  
  
> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTrace`  
  
## <a name="see-also"></a>Confira também

- [AppFabric que monitora Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
