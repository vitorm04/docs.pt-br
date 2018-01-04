---
title: Dados de extrair WF usando o rastreamento
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e30c68f5-8c6a-495a-bd20-667a4364c68e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d6c269dc9c8b5a0050cfc3ffcefc3160b07c897
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="extract-wf-data-using-tracking"></a>Dados de extrair WF usando o rastreamento
Este exemplo demonstra como usar o rastreamento de fluxo de trabalho para extrair variáveis e argumentos de fluxo de trabalho de atividades. Ele também mostra a adição de anotações a acompanhar registros e a extração de carregamento útil dos dados dentro dos registros personalizados de rastreamento. O exemplo usa o rastreamento de evento para o Windows (ETW) que controla o participante para extrair dados de fluxo de trabalho.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 [!INCLUDE[wf](../../../../includes/wf-md.md)] fornece o rastreamento para a visibilidade de ganho em execução de uma instância de fluxo de trabalho. O tempo de execução de rastreamento emite-se registros de acompanhamento de fluxo de trabalho durante a execução de fluxo de trabalho. Juntamente com os registros de acompanhamento de fluxo de trabalho, os dados dentro de instância de fluxo de trabalho podem ser extraídos de fluxo de trabalho. A lista a seguir detalha os tipos de dados que podem ser extraídos de registros de acompanhamento:  
  
1.  Variáveis de fluxo de trabalho em uma atividade e registros de rastreamento durante a execução da atividade.  
  
     Para extrair variáveis de fluxo de trabalho, as variáveis a ser extraídos são especificados em um perfil. As variáveis a ser extraídos só podem ser especificados com `ActivityStateQueries`. O exemplo de código a seguir demonstra um perfil de rastreamento usado para extrair a variável de fluxo de trabalho de uma atividade.  
  
    ```xml  
    <activityStateQuery activityName="StockPriceService">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <variables>  
              <variable name="symbol"/>  
         </variables>  
    </activityStateQuery>  
    ```  
  
2.  Argumentos de atividade e estado da atividade que acompanha registros.  
  
     Os argumentos definem os fluxos de dados de forma ou de uma atividade. Os argumentos para ser extraídos são especificados usando <xref:System.Activities.Tracking.ActivityStateQuery>. O exemplo de código é um perfil de rastreamento que extrai o argumento de `Value` .  
  
    ```xml  
    <activityStateQuery activityName="GetStockPrice">  
         <states>  
              <state name="Closed"/>  
         </states>  
         <arguments>  
              <argument name="Value"/>  
         </arguments>  
    </activityStateQuery>  
    ```  
  
3.  As anotações são pares chave/valor que pode ser adicionado a qualquer registro de rastreamento que é emitida.  
  
     As anotações servem como um mecanismo de posicionamento de rótulos para controlar registros. As anotações são adicionadas a acompanhar registros com um perfil de rastreamento. As anotações podem ser adicionadas a qualquer tipo de uma consulta de acompanhamento de fluxo de trabalho. O exemplo de código é um perfil de rastreamento que mostra como uma anotação pode ser adicionada a um registro de rastreamento.  
  
    ```xml  
    <workflowInstanceQuery>  
         <states>  
              <state name="Started"/>  
         </states>  
         <annotations>  
              <annotation name="StockPriceWorkflow" value="Begin"/>  
         </annotations>  
    </workflowInstanceQuery>  
    ```  
  
4.  Os registros personalizados são emitidas de rastreamento de atividades definidos pelo usuário.  
  
     Os registros personalizados de rastreamento podem carregar os dados de carregamento útil definidos dentro desta atividade. Para assinar registros personalizados de rastreamento em um perfil de rastreamento permite a extração de carregamento útil no registro de rastreamento. Os registros personalizados de rastreamento podem ser extraídos com <xref:System.Activities.Tracking.TrackingQuery>personalizado. O exemplo de código é um perfil de rastreamento que extrai um registro de rastreamento personalizada juntamente com sua carga útil.  
  
    ```xml  
    <customTrackingQuery name="QuoteLookupEvent" activityName="GetStockPrice"/>  
    ```  
  
 O exemplo demonstra a extração de variáveis, argumentos, registros personalizado e anotações adicionar usando um perfil especificado em um Web.config. O rastreamento está ativado no serviço de fluxo de trabalho de exemplo adicionando um elemento do comportamento de `<etwTracking>` . O exemplo de código ativar o rastreamento para `ExtractWorkflowVariables` que controla o perfil.  
  
```xml  
<serviceBehaviors>  
     <behavior>  
               <etwTracking profileName="ExtractWorkflowVariables"/>  
     </behavior>  
</serviceBehaviors>  
```  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de WFStockPriceApplication.sln.  
  
2.  Para criar a solução, pressione CTRL+SHIFT+B.  
  
3.  Para executar a solução, pressione F5.  
  
     A janela do navegador abre e mostra a listagem de diretório para o aplicativo.  
  
4.  No navegador, clique StockPriceService.xamlx.  
  
5.  O navegador exibe a página de StockPriceService, que contém o endereço de WSDL de serviço local. Copie este endereço.  
  
     O exemplo a seguir mostra um endereço de WSDL de serviço local. `http://localhost:53797/StockPriceService.xamlx?wsdl`  
  
6.  Antes de chamar o serviço, ligue o visualizador de eventos e certifique-se de que o log de eventos é escutando eventos de rastreamento emissores de serviço de fluxo de trabalho.  
  
7.  Do **iniciar** menu, selecione **ferramentas administrativas** e **Visualizador de eventos**.  
  
8.  Na exibição de árvore no Visualizador de eventos, navegue até **Visualizador de eventos**, **Applications and Services Logs**, e **Microsoft**. Clique com botão direito **Microsoft** e selecione **exibição** e **Mostrar Logs analíticos e depuração**.  
  
     Certifique-se de que o **Mostrar Logs analíticos e depuração** opção estiver marcada.  
  
9. Na exibição de árvore no Visualizador de eventos, navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**,  **Aplicativos de servidor de aplicativo**. Clique com botão direito **analítico** e selecione **Habilitar Log**.  
  
10. Usando [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], abra o cliente de teste de windows.  
  
     O cliente de teste do WCF (WcfTestClient.exe) está localizado no \< [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] pasta de instalação > \Common7\IDE\ pasta.  
  
     A pasta de instalação de [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] é C:\Program Files\Microsoft Visual Studio 10,0.  
  
11. No cliente de teste do WCF, selecione **Adicionar serviço** do **arquivo** menu.  
  
     Adicione o endereço de WSDL de serviço local você copiou anterior na caixa de entrada.  
  
12. No cliente de teste de windows, clique duas vezes em `GetStockPrice`.  
  
     Isso abre o método de `GetStockPrice` . A solicitação aceita um parâmetro. Use o valor **Contoso**.  
  
13. Clique em **invocar**.  
  
14. Retorne ao Visualizador de eventos e navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**,  **Aplicativos de servidor de aplicativo**. Clique com botão direito **analítico** e selecione **atualizar**. Os eventos de fluxo de trabalho são em intervalos de identificação de evento 100-199.  
  
     Os eventos contêm as anotações, variáveis, os argumentos e os registros personalizados de rastreamento que podem ser exibidos no visualizador de eventos.  
  
## <a name="cleaning-up-in-the-event-viewer"></a>Limpar no visualizador de eventos  
 O canal analítico no log de eventos pode ser limpado no visualizador de eventos fazendo o seguinte.  
  
#### <a name="to-clean-up-optional"></a>Para limpar (opcional)  
  
1.  Visualizador de EventosAberto.  
  
2.  Navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**, **aplicativo Aplicativos de servidor**. Clique com botão direito **analítico** e selecione **desabilitar Log**.  
  
3.  Navegue até **Visualizador de eventos**, **Applications and Services Logs**, **Microsoft**, **Windows**, **aplicativo Aplicativos de servidor**. Clique com botão direito **analítico** e selecione **Limpar Log**.  
  
     Escolha o **limpar** opção para limpar os eventos.  
  
## <a name="known-issue"></a>Problema conhecido  
  
> [!NOTE]
>  Há um problema conhecido em Visualizador de Eventos onde pode não decodifica eventos de ETW. Você pode ver a uma mensagem de erro semelhante ao seguinte.  
>   
>  `The description for Event ID <id> from source Microsoft-Windows-Application Server-Applications cannot be found. Either the component that raises this event is not installed on your local computer or the installation is corrupted. You can install or repair the component on the local computer.`  
>   
>  Se você encontrar esse erro, clique em **atualização** no painel Ações. O evento agora deve decodificar corretamente.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\ExtractWfData`  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de monitoramento do AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
