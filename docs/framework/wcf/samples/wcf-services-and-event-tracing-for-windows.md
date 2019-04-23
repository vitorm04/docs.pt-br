---
title: Serviços e rastreamento de eventos WCF para Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: 35d0202a3b9cf4060240dc521554644d419a5c23
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338963"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>Serviços e rastreamento de eventos WCF para Windows
Este exemplo demonstra como usar o rastreamento analítico no Windows Communication Foundation (WCF) para emitir eventos no rastreamento de eventos para Windows (ETW). Os rastreamentos analíticos são eventos emitidos nos pontos-chave na pilha do WCF que permitem a solução de problemas dos serviços WCF no ambiente de produção.

 Rastreamento analítico nos serviços do WCF é rastreamento que pode ser ativado em um ambiente de produção com impacto mínimo no desempenho. Esses rastreamentos são emitidos como eventos em uma sessão do ETW.

 Este exemplo inclui um serviço WCF básico no qual os eventos são emitidos pelo serviço no log de eventos, que podem ser exibidos usando o Visualizador de eventos. Também é possível iniciar uma sessão ETW dedicada que escuta eventos do serviço WCF. O exemplo inclui um script para criar uma sessão ETW dedicada que armazena os eventos em um arquivo binário que pode ser lido usando o Visualizador de eventos.

#### <a name="to-use-this-sample"></a>Para usar este exemplo

1. Usando o Visual Studio 2012, abra o arquivo de solução EtwAnalyticTraceSample.sln.

2. Para criar a solução, pressione CTRL+SHIFT+B.

3. Para executar a solução, pressione CTRL+F5.

     No navegador da Web, clique em **Calculator.svc**. O URI do documento WSDL para o serviço deve aparecer no navegador. Copie esse URI.

     Por padrão, o serviço começa a escutar solicitações na porta 1378 `http://localhost:1378/Calculator.svc`.

4. Execute o cliente de teste do WCF (WcfTestClient.exe).

     O cliente de teste do WCF (WcfTestClient.exe) está localizado em `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.  Dir de instalação do Visual Studio 2012 padrão é `C:\Program Files\Microsoft Visual Studio 10.0`.

5. Dentro do cliente de teste do WCF, adicione o serviço, selecionando **arquivo**e então **Adicionar serviço**.

     Adicione o endereço do ponto de extremidade na caixa de entrada. O padrão é `http://localhost:1378/Calculator.svc`.

6. Abra o aplicativo visualizador de eventos.

     Antes de invocar o serviço, inicie o Visualizador de eventos e certifique-se de que o log de eventos é escutando eventos de rastreamento emitidos de serviço do WCF.

7. Dos **inicie** menu, selecione **ferramentas administrativas**e, em seguida, **Visualizador de eventos**.  Habilitar o **analítico** e **depurar** logs.

8. Na exibição de árvore no Visualizador de eventos, navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida, **Aplicativos de servidor**. Clique com botão direito **aplicativos de servidor**, selecione **exibição**e então **Mostrar Logs analíticos e depuração**.

     Certifique-se de que o **Mostrar Logs analíticos e depuração** opção estiver marcada.

9. Habilitar o **analítico** log.

     Na exibição de árvore no Visualizador de eventos, navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida, **Aplicativos de servidor**. Clique com botão direito **analítico** e selecione **Habilitar Log**.

#### <a name="to-test-the-service"></a>Para testar o serviço

1. Volte para o cliente de teste do WCF e clique duas vezes em `Divide` e mantenha os valores padrão, que especificam um denominador de 0.

     Se o denominador é 0, o serviço gera uma falha.

2. Observe os eventos emitidos de serviço.

     Retorne ao Visualizador de eventos e navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida, **Aplicativos de servidor**. Clique com botão direito **analítico** e selecione **atualizar**.

     Os eventos de rastreamento analítico do WCF são exibidos no Visualizador de eventos. Observe que porque uma falha foi gerada pelo serviço que é um evento de rastreamento de erro exibidos em Visualizar eventos.

3. Repita as etapas 1 e 2, mas com as entradas válidas. O valor da `N2` parâmetro pode ser qualquer número diferente de 0.

     Atualizar o canal analítico para exibir o WCF eventos não incluem nenhum evento de erro.

 O exemplo demonstra os eventos de rastreamento analítico emitidos de um serviço WCF.

#### <a name="to-cleanup-optional"></a>A limpeza (opcional)

1. Visualizador de EventosAberto.

2. Navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida,  **Aplicativos de servidor**. Clique com botão direito **analítico** e selecione **desabilitar Log**.

3. Navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**e, em seguida,  **Aplicativos de servidor**. Clique com botão direito **analítico** e selecione **Limpar Log**.

4. Escolha o **limpar** opção para limpar os eventos.

> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>Consulte também

- [AppFabric que monitora exemplos](https://go.microsoft.com/fwlink/?LinkId=193959)
