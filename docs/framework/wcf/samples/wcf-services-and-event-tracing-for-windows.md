---
title: Serviços e rastreamento de eventos WCF para Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: ea917ee87b598fc3ad01df70d9aedfadfd1396a4
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>Serviços e rastreamento de eventos WCF para Windows
Este exemplo demonstra como usar o rastreamento analítico no Windows Communication Foundation (WCF) para emissão de eventos no evento de rastreamento para Windows (ETW). Os rastreamentos analíticos são emitidos nos pontos-chave na pilha do WCF que permitem a solução de problemas de serviços WCF no ambiente de produção de eventos.  
  
 Rastreamento analítico nos serviços do WCF é aquele que pode ser ativado em um ambiente de produção com impacto mínimo no desempenho. Os rastreamentos são emitidos como eventos para uma sessão do ETW.  
  
 Este exemplo inclui um serviço WCF básico no qual eventos são emitidos do serviço de log de eventos, que podem ser exibido usando o Visualizador de eventos. Também é possível iniciar uma sessão ETW dedicada que escuta eventos do serviço WCF. O exemplo inclui um script para criar uma sessão ETW dedicada que armazena os eventos em um arquivo binário que pode ser lida usando o Visualizador de eventos.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra o arquivo de solução de EtwAnalyticTraceSample.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione CTRL+F5.  
  
     No navegador da Web, clique em **Calculator.svc**. O URI do documento WSDL para o serviço deve aparecer no navegador. Copie esse URI.  
  
     Por padrão, o serviço começa a escuta de solicitações na porta 1378 (http://localhost:1378/Calculator.svc).  
  
4.  Execute o cliente de teste do WCF (WcfTestClient.exe).  
  
     O cliente de teste do WCF (WcfTestClient.exe) está localizado no \< [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] instalar Dir > \Common7\IDE\ WcfTestClient.exe (padrão [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] dir de instalação é C:\Program Files\Microsoft Visual Studio 10.0).  
  
5.  No cliente de teste de WCF, adicione o serviço selecionando **arquivo**e, em seguida, **Adicionar serviço**.  
  
     Adicione o endereço do ponto de extremidade na caixa de entrada. O padrão é http://localhost:1378/Calculator.svc.  
  
6.  Abra o aplicativo visualizador de eventos.  
  
     Antes de chamar o serviço, inicie o Visualizador de eventos e certifique-se de que o log de eventos está escutando para rastreamento de eventos emitidos do serviço WCF.  
  
7.  Do **iniciar** menu, selecione **ferramentas administrativas**e, em seguida, **Visualizador de eventos**.  Habilitar o **analítico** e **depurar** logs.  
  
8.  Na exibição de árvore no Visualizador de eventos, navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida, **Aplicativos de servidor de aplicativo**. Clique com botão direito **aplicativos de servidor de aplicativo**, selecione **exibição**e, em seguida, **Mostrar Logs analíticos e depuração**.  
  
     Certifique-se de que o **Mostrar Logs analíticos e depuração** opção estiver marcada.  
  
9. Habilitar o **analítico** log.  
  
     Na exibição de árvore no Visualizador de eventos, navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida, **Aplicativos de servidor de aplicativo**. Clique com botão direito **analítico** e selecione **Habilitar Log**.  
  
#### <a name="to-test-the-service"></a>Para testar o serviço  
  
1.  Retorne ao cliente de teste do WCF e clique duas vezes em `Divide` e mantenha os valores padrão, que especificam um denominador igual a 0.  
  
     Se o denominador é 0, o serviço gera uma falha.  
  
2.  Observe os eventos emitidos a partir do serviço.  
  
     Retorne ao Visualizador de eventos e navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida, **Aplicativos de servidor de aplicativo**. Clique com botão direito **analítico** e selecione **atualizar**.  
  
     Os eventos de rastreamento analítico do WCF são exibidos no Visualizador de eventos. Observe que porque uma falha foi gerada pelo serviço que é um evento de rastreamento de erro no evento exibidas visualizador.  
  
3.  Repita as etapas 1 e 2, mas com as entradas válidas. O valor de `N2` parâmetro pode ser qualquer número diferente de 0.  
  
     Atualizar o canal analítico para exibir o WCF eventos não têm qualquer evento de erro.  
  
 O exemplo demonstra que os eventos de rastreamento analítico emitidos a partir de um serviço WCF.  
  
#### <a name="to-cleanup-optional"></a>A limpeza (opcional)  
  
1.  Visualizador de EventosAberto.  
  
2.  Navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida,  **Aplicativos de servidor de aplicativo**. Clique com botão direito **analítico** e selecione **desabilitar Log**.  
  
3.  Navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida,  **Aplicativos de servidor de aplicativo**. Clique com botão direito **analítico** e selecione **Limpar Log**.  
  
4.  Escolha o **limpar** opção para limpar os eventos.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de monitoramento do AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
