---
title: Serviços e rastreamento de eventos WCF para Windows
ms.date: 03/30/2017
ms.assetid: eda4355d-0bd0-4dc9-80a2-d2c832152272
ms.openlocfilehash: b8a1f30f20aa2c541a574a070b3644569d633ca2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183206"
---
# <a name="wcf-services-and-event-tracing-for-windows"></a>Serviços e rastreamento de eventos WCF para Windows
Esta amostra demonstra como usar o rastreamento analítico no Windows Communication Foundation (WCF) para emitir eventos no Event Tracing for Windows (ETW). Os traços analíticos são eventos emitidos em pontos-chave na pilha WCF que permitem a solução de problemas de serviços WCF no ambiente de produção.

 O rastreamento analítico nos serviços wcf é o rastreamento que pode ser ligado em um ambiente de produção com impacto mínimo no desempenho. Esses traços são emitidos como eventos para uma sessão de ETW.

 Esta amostra inclui um serviço básico de WCF no qual os eventos são emitidos do serviço para o registro de eventos, que podem ser visualizados usando o Event Viewer. Também é possível iniciar uma sessão dedicada de ETW que ouve eventos do serviço WCF. A amostra inclui um script para criar uma sessão de ETW dedicada que armazena eventos em um arquivo binário que pode ser lido usando o Event Viewer.

#### <a name="to-use-this-sample"></a>Para usar este exemplo

1. Usando o Visual Studio 2012, abra o arquivo de solução EtwAnalyticTraceSample.sln.

2. Para criar a solução, pressione CTRL+SHIFT+B.

3. Para executar a solução, pressione CTRL+F5.

     No navegador da Web, clique em **Calculadora.svc**. O URI do documento WSDL para o serviço deve aparecer no navegador. Copie esse URI.

     Por padrão, o serviço começa a ouvir `http://localhost:1378/Calculator.svc`solicitações na porta 1378 .

4. Execute o cliente de teste WCF (WcfTestClient.exe).

     O cliente de teste WCF (WcfTestClient.exe) está localizado em `\<Visual Studio 2012 Install Dir>\Common7\IDE\WcfTestClient.exe`.  O visual studio padrão 2012 instalar dir é `C:\Program Files\Microsoft Visual Studio 10.0`.

5. Dentro do cliente de teste WCF, adicione o serviço selecionando **Arquivo**e, em seguida, **Adicione serviço**.

     Adicione o endereço do ponto de extremidade na caixa de entrada. O padrão é `http://localhost:1378/Calculator.svc`.

6. Abra o aplicativo visualizador de eventos.

     Antes de invocar o serviço, inicie o Event Viewer e certifique-se de que o registro de eventos esteja ouvindo o rastreamento de eventos emitidos pelo serviço WCF.

7. No menu **Iniciar,** selecione **Ferramentas Administrativas**e, em seguida, **Visualizador de Eventos**.  Habilite os **registros de análise** e **depuração.**

8. Na exibição da árvore no Event Viewer, navegue até **o Event Viewer,** **Applications and Services Logs,** **Microsoft,** **Windows**e, em seguida, **Application Server-Applications**. Clique com o botão direito do mouse **aplicativos de servidor de aplicativos,** selecione **Exibir**e, em seguida, mostrar registros de análise **e depuração**.

     Certifique-se de que a opção **Mostrar registros de análise e depuração** seja verificada.

9. Habilite o **registro analítico.**

     Na exibição da árvore no Event Viewer, navegue até **o Event Viewer,** **Applications and Services Logs,** **Microsoft,** **Windows**e, em seguida, **Application Server-Applications**. Clique com o botão direito do mouse **Em Análise** e **selecione Ativar log**.

#### <a name="to-test-the-service"></a>Para testar o serviço

1. Volte para o cliente de teste `Divide` WCF e clique duas vezes e mantenha os valores padrão, que especificam um denominador de 0.

     Se o denominador é 0, então o serviço lança uma falha.

2. Observe os eventos emitidos pelo serviço.

     Volte para o Visualizador de Eventos e navegue até **o Visualizador de Eventos,** **Registros de Aplicativos e Serviços,** **Microsoft,** **Windows**e, em seguida, Aplicativos de Servidor **de Aplicativos**. Clique com o botão direito do mouse **Em Analítica** e selecione **Atualizar**.

     Os eventos de rastreamento analítico wcf são exibidos no visualizador do evento. Observe que, como uma falha foi lançada pelo serviço, um evento de rastreamento de erro é exibido no visualizador do evento.

3. Repita as etapas 1 e 2, mas com entradas válidas. O valor `N2` do parâmetro pode ser qualquer número diferente de 0.

     Atualize o canal analítico para visualizar os eventos WCF não inclua nenhum evento de erro.

 A amostra demonstra os eventos de rastreamento analítico emitidos a partir de um serviço WCF.

#### <a name="to-cleanup-optional"></a>A limpeza (opcional)

1. Visualizador de EventosAberto.

2. Navegue até **o Visualizador de Eventos,** **Registros de aplicativos e serviços,** **Microsoft,** **Windows**e, em seguida, aplicativos de servidor **de aplicativos**. Clique com o botão direito do mouse **Em Analítica** e **selecione Desativar log**.

3. Navegue até **o Visualizador de Eventos,** **Registros de aplicativos e serviços,** **Microsoft,** **Windows**e, em seguida, aplicativos de servidor **de aplicativos**. Clique com o botão direito do mouse **Em Analítico** e selecione **Limpar Log**.

4. Escolha a opção **Limpar** para limpar os eventos.

> [!IMPORTANT]
> Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ETWTracing`  
  
## <a name="see-also"></a>Confira também

- [AppFabric que monitora Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
