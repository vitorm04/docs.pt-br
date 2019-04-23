---
title: Utilizando o visualizador de rastreamento de serviço para visualização de rastreamento correlacionados e soluções de problemas
ms.date: 03/30/2017
ms.assetid: 05d2321c-8acb-49d7-a6cd-8ef2220c6775
ms.openlocfilehash: dd5fe08054b3a10c1663a7dd7dab5f9de5327cbb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59329044"
---
# <a name="using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting"></a>Utilizando o visualizador de rastreamento de serviço para visualização de rastreamento correlacionados e soluções de problemas
Este tópico descreve o formato dos dados de rastreamento, como exibir e abordagens que usam o Visualizador de rastreamento de serviço para solucionar problemas de seu aplicativo.  
  
## <a name="using-the-service-trace-viewer-tool"></a>Usando a ferramenta Visualizador de Rastreamento de Serviço  
 A ferramenta Visualizador de rastreamento de serviço do Windows Communication Foundation (WCF) ajuda a correlacionar rastreamentos de diagnóstico produzidos por ouvintes do WCF para localizar a causa raiz de um erro. A ferramenta fornece uma maneira de exibir, grupo e filtrar os rastreamentos para que você possa diagnosticar, reparar e verificar problemas com os serviços WCF facilmente. Para obter mais informações sobre como usar essa ferramenta, consulte [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
 Este tópico contém as capturas de tela de gerado pela execução de rastreamentos a [rastreamento e registro em log de mensagem](../../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) de exemplo, quando exibido usando o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Este tópico demonstra como compreender o conteúdo de rastreamento, atividades e correlação e como analisar grandes quantidades de rastreamentos ao solucionar o problema.  
  
## <a name="viewing-trace-content"></a>Exibição de conteúdo de rastreamento  
 Um evento de rastreamento contém as informações mais importantes a seguir:  
  
-   Nome da atividade quando definido.  
  
-   Hora de emissão.  
  
-   Nível de rastreamento.  
  
-   Nome da origem de rastreamento.  
  
-   Nome do processo.  
  
-   Id do thread.  
  
-   Um identificador exclusivo de rastreamento, que é uma URL que aponta para um destino no Microsoft Docs, do qual você pode obter mais informações relacionadas ao rastreamento.  
  
 Todos eles podem ser vistos no painel superior direito no Visualizador de rastreamento de serviço ou na **informações básicas** seção no modo de exibição formatada do painel inferior direito ao selecionar um rastreamento.  
  
> [!NOTE]
>  Se o cliente e o serviço estiverem no mesmo computador, os rastreamentos de ambos os aplicativos estará presentes. Eles podem ser filtrados usando o **nome do processo** coluna.  
  
 Além disso, a exibição formatada também fornece uma descrição para o rastreamento e informações detalhadas adicionais quando disponíveis. A última opção pode incluir exceção tipo e a mensagem, as pilhas de chamadas, ação de mensagem, de/para campos e outras informações de exceção.  
  
 Na exibição de XML, as marcas xml úteis incluem o seguinte:  
  
-   `<SubType>` (nível de rastreamento).  
  
-   `<TimeCreated>`.  
  
-   `<Source>` (nome de origem de rastreamento).  
  
-   `<Correlation>` (id da atividade definido ao emitir o rastreamento).  
  
-   `<Execution>` (id thread e processo).  
  
-   `<Computer>`.  
  
-   `<ExtendedData>`, incluindo `<Action>`, `<MessageID>` e o `<ActivityId>` definido no cabeçalho da mensagem ao enviar uma mensagem.  
  
 Se você examinar o rastreamento "Enviados uma mensagem por um canal", você poderá ver o conteúdo a seguir.  
  
```xml  
<E2ETraceEvent xmlns="http://schemas.microsoft.com/2004/06/E2ETraceEvent">  
   <System xmlns="http://schemas.microsoft.com/2004/06/windows/eventlog/system">  
      <EventID>262163</EventID>  
      <Type>3</Type>  
      <SubType Name="Information">0</SubType>  
      <Level>8</Level>  
      <TimeCreated SystemTime="2006-08-04T18:45:30.8491051Z" />  
      <Source Name="System.ServiceModel" />  
       <Correlation ActivityID="{27c6331d-8998-43aa-a382-03239013a6bd}"/>  
       <Execution ProcessName="client" ProcessID="1808" ThreadID="1" />  
       <Channel />  
       <Computer>TEST1</Computer>  
   </System>  
   <ApplicationData>  
       <TraceData>  
          <DataItem>  
             <TraceRecord xmlns="http://schemas.microsoft.com/2004/10/E2ETraceEvent/TraceRecord" Severity="Information">  
                 <TraceIdentifier>http://msdn.microsoft.com/library/System.ServiceModel.Channels.MessageSent.aspx</TraceIdentifier>  
                 <Description>Sent a message over a channel.</Description>  
                 <AppDomain>client.exe</AppDomain>  
                 <Source>System.ServiceModel.Channels.ClientFramingDuplexSessionChannel/35191196</Source>  
                <ExtendedData xmlns="http://schemas.microsoft.com/2006/08/ServiceModel/MessageTransmitTraceRecord">  
  
                  <MessageProperties>  
                     <AllowOutputBatching>False</AllowOutputBatching>  
                  </MessageProperties>  
                  <MessageHeaders>  
                     <Action d4p1:mustUnderstand="1" xmlns:d4p1="http://www.w3.org/2003/05/soap-envelope" xmlns="http://www.w3.org/2005/08/addressing">http://Microsoft.ServiceModel.Samples/ICalculator/Multiply</Action>  
                     <MessageID xmlns="http://www.w3.org/2005/08/addressing">urn:uuid:7c6670d8-4c9c-496e-b6a0-2ceb6db35338</MessageID>  
                     <ActivityId CorrelationId="b02e2189-0816-4387-980c-dd8e306440f5" xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">27c6331d-8998-43aa-a382-03239013a6bd</ActivityId>  
                     <ReplyTo xmlns="http://www.w3.org/2005/08/addressing">  
                        <Address>http://www.w3.org/2005/08/addressing/anonymous</Address>  
                    </ReplyTo>  
                    <To d4p1:mustUnderstand="1" xmlns:d4p1="http://www.w3.org/2003/05/soap-envelope" xmlns="http://www.w3.org/2005/08/addressing">net.tcp://localhost/servicemodelsamples/service</To>  
                  </MessageHeaders>  
                  <RemoteAddress>net.tcp://localhost/servicemodelsamples/service</RemoteAddress>  
                </ExtendedData>  
            </TraceRecord>  
          </DataItem>  
       </TraceData>  
   </ApplicationData>  
</E2ETraceEvent>  
```  
  
## <a name="servicemodel-e2e-tracing"></a>Rastreamento E2E de ServiceModel  
 Quando o `System.ServiceModel` origem de rastreamento é definida com um `switchValue` diferente de desativado, e `ActivityTracing`, o WCF cria atividades e transfere para o processamento do WCF.  
  
 Uma atividade é uma unidade lógica de processamento que grupos de todos os rastreamentos relacionados a essa unidade de processamento. Por exemplo, você pode definir uma atividade para cada solicitação. Transferências de criar um relacionamento causal entre as atividades dentro de pontos de extremidade. Propagando a ID de atividade permite relacionar as atividades entre pontos de extremidade. Isso pode ser feito definindo `propagateActivity` = `true` na configuração em cada ponto de extremidade. As atividades, transferências e propagação permitem que você executar a correlação de erro. Dessa forma, você pode encontrar a causa raiz de um erro mais rapidamente.  
  
 No cliente, uma atividade WCF é criada para cada chamada de modelo de objeto (por exemplo, abrir ChannelFactory, adicionar, divisão e assim por diante.) Cada uma das chamadas de operação é processada em uma atividade de "Ação de processo".  
  
 Na captura de tela a seguir, extraído do [rastreamento e registro em log de mensagem](../../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) exemplo o painel esquerdo exibe a lista de atividades criadas no processo de cliente, classificado por hora de criação. A seguir está uma lista cronológica de atividades:  
  
-   Construído a fábrica de canais (ClientBase).  
  
-   Abrir a fábrica de canais.  
  
-   Processar a ação Adicionar.  
  
-   Configure a sessão segura (esse ocorrido na primeira solicitação) e infraestrutura de segurança processado de três mensagens de resposta: RST, RSTR, SCT (processo mensagem 1, 2, 3).  
  
-   Processado a subtração, multiplicação e divisão de solicitações.  
  
-   Fechado a fábrica de canais, e isso fechou a sessão segura e processado a resposta de mensagem de segurança ' Cancelar '.  
  
 Podemos ver as mensagens de infra-estrutura de segurança devido a wsHttpBinding.  
  
> [!NOTE]
>  No WCF, vamos mostrar mensagens de resposta que está sendo processadas inicialmente em uma atividade separada (mensagem de processo) antes que podemos correlacioná-las para a atividade de ação do processo correspondente que inclui a mensagem de solicitação, por meio de uma transferência. Isso acontece para mensagens de infraestrutura e as solicitações assíncronas e é devido ao fato de que estamos deve inspecionar a mensagem, ler o cabeçalho de activityId e identificar a atividade de ação de processo existente com essa id para correlacionar a ele. Para solicitações síncronas, podemos estão bloqueando para a resposta e, portanto, saber qual ação de processo, a resposta está relacionado ao.  
  
A imagem a seguir mostra as atividades do cliente WCF listadas por hora de criação (painel esquerdo) e suas atividades aninhadas e rastreamentos (painel superior direito):

 ![Captura de tela mostrando as atividades listadas por hora de criação de cliente do WCF.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-client-activities-creation-time.gif)  
  
 Quando selecionamos uma atividade no painel esquerdo, podemos ver atividades aninhadas e rastreamentos no painel à direita superior. Portanto, essa é uma redução exibição hierárquica da lista de atividades, à esquerda, com base na atividade pai selecionado. Como a ação selecionada do processo adicionar é a primeira solicitação feita, essa atividade contém a atividade definir segurança de sessão (transferência para transferência do) e rastreamentos para o processamento real da ação Adicionar.  
  
 Se podemos clicar duas vezes a ação de processo Adicionar atividade no painel esquerdo, podemos ver uma representação gráfica das atividades do WCF cliente relacionados a adicionar. A primeira atividade à esquerda é a atividade raiz (0000), que é a atividade padrão. Transferências WCF fora da atividade de ambiente. Se não estiver definido, o WCF transfere fora 0000. Aqui, a segunda atividade adicionar da ação de processo, transfere proveito do 0. Em seguida, podemos ver que a sessão de seguro de instalação.  

 A imagem a seguir mostra um modo de exibição de gráfico do cliente do WCF de atividades, especificamente ambiente atividade (aqui 0), processar ação e configurar a sessão segura:   

 ![No Visualizador de rastreamento que mostra a ação de atividade de ambiente e o processo de gráfico.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-activities-graph-ambient-process.gif)   
  
 No painel superior direito, podemos ver todos os rastreamentos relacionados à atividade de ação do processo de adicionar. Especificamente, podemos ter enviou a mensagem de solicitação ("enviados uma mensagem por um canal") e recebeu a resposta ("recebeu uma mensagem por um canal") na mesma atividade. Isso é mostrado no seguinte gráfico. Para maior clareza, a atividade da sessão segura de configurar é recolhida no gráfico.  
  
 A imagem a seguir mostra uma lista de rastreamentos para a atividade de ação de processo. Podemos enviar a solicitação e receber a resposta na mesma atividade.
 
 ![Captura de tela do Visualizador de rastreamento que mostra uma lista de rastreamentos para a atividade de ação de processo](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/process-action-traces.gif)  
  
 Aqui, podemos carregar os rastreamentos de cliente apenas para fins de esclarecimento, mas rastreamentos de serviço (mensagem de solicitação recebida e mensagem de resposta enviada) são exibidos na mesma atividade se eles também são carregados na ferramenta e `propagateActivity` foi definida como `true.` isso é mostrado na ilustração posterior.  
  
 No serviço, o modelo de atividade mapeia para os conceitos do WCF da seguinte maneira:  
  
1. Podemos construir e abra um ServiceHost (Isso pode criar várias atividades relacionadas ao host, por exemplo, no caso de segurança).  
  
2. Podemos criar uma atividade de escuta em para cada ouvinte no ServiceHost (com transferências dentro e fora de ServiceHost aberto).  
  
3. Quando o ouvinte detecta uma solicitação de comunicação iniciada pelo cliente, ele transfere a uma atividade de "Bytes de recebimento", na qual todos os bytes enviados do cliente são processados. Essa atividade, podemos ver os erros de conexão que ocorreram durante a interação de serviço do cliente.  
  
4. Para cada conjunto de bytes que é recebido que corresponde a uma mensagem, podemos processar esses bytes em uma atividade de "Processo de mensagem", onde podemos criar o objeto Message do WCF. Essa atividade, podemos ver erros relacionados a um envelope incorreto ou uma mensagem malformada.  
  
5. Depois que a mensagem é formada, podemos transferir para uma atividade de ação de processo. Se `propagateActivity` é definido como `true` sobre o cliente e o serviço, essa atividade tem a mesma id que aquele definido no cliente e descrito anteriormente. Nesta fase, vamos começar se beneficiar de correlação direta entre os pontos de extremidade, como todos os rastreamentos emitidos no WCF que estão relacionados à solicitação estão na mesma atividade, incluindo o processamento da mensagem de resposta.  
  
6. Para a ação de out-of-process, podemos criar uma atividade de "Execute código do usuário" para isolar os rastreamentos emitidos no código do usuário daqueles emitidos no WCF. No exemplo anterior, o rastreamento "Serviço envia a resposta de adicionar" é emitido na atividade de "Código de usuário Execute", não na atividade propagada pelo cliente, se aplicável.  
  
 Na ilustração a seguir, a primeira atividade à esquerda é a atividade raiz (0000), que é a atividade padrão. As próximas três atividades são abrir o ServiceHost. A atividade na coluna 5 é o ouvinte e as atividades restantes (6 to 8) descrevem o processamento do WCF de uma mensagem, de bytes de processamento para ativação de código do usuário.  

 A imagem a seguir mostra um modo de exibição de gráfico de atividades de serviço do WCF:   

 ![Captura de tela do Visualizador de rastreamento que mostra uma lista de atividades de serviço do WCF](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-service-activities.gif)  

 Captura de tela a seguir mostra as atividades para o cliente e o serviço e realça a atividade de ação do processo de adicionar entre processos (laranja). As setas estão relacionados as mensagens de solicitação e resposta enviados e recebidos pelo cliente e serviço. Os rastreamentos de ação de processo são separados entre processos no gráfico, mas mostrados como parte da mesma atividade no painel superior direito. Neste painel, podemos ver rastreamentos de cliente para mensagens enviadas, seguidos de rastreamentos de serviço para mensagens recebidas e processadas.  
  
 As imagens a seguir mostra uma exibição de gráfico de ambas as atividades de cliente e o serviço do WCF  
 
 ![Gráfico do Visualizador de rastreamento que mostra as duas atividades de cliente e o serviço do WCF.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/wcf-client-service-activities.gif)   
  
 No cenário de erro a seguir, o erro e rastreamentos de aviso no serviço e cliente estão relacionados. Primeiro, uma exceção é lançada no código do usuário no serviço (mais à direita verdes de atividade que inclui um aviso de rastreamento para a exceção "o serviço não pode processar essa solicitação no código do usuário."). Quando a resposta é enviada ao cliente, um rastreamento de aviso novamente é emitido para denotar a mensagem de falha (atividade rosa esquerda). O cliente, em seguida, feche seu cliente WCF (atividade amarela no canto inferior esquerdo), que anula a conexão ao serviço. O serviço gera um erro (atividade rosa mais longo no lado direito).  
  
 ![Usando o Visualizador de rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")  
Correlação de erro entre cliente e de serviço  
  
 O exemplo usado para gerar esses rastreamentos é uma série de solicitações síncronas usando o wsHttpBinding. Há os desvios esse gráfico para cenários sem segurança, ou com solicitações assíncronas, em que a atividade de ação de processo abrange as operações begin e end que constituem a chamada assíncrona e mostra as transferências para uma atividade de retorno de chamada. Para obter mais informações sobre cenários adicionais, consulte [cenários de rastreamento de ponta a ponta](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).  
  
## <a name="troubleshooting-using-the-service-trace-viewer"></a>Solução de problemas usando o Visualizador de rastreamento de serviço  
 Quando você carrega arquivos de rastreamento na ferramenta de Visualizador de rastreamento de serviço, você pode selecionar qualquer atividade vermelha ou amarela no painel à esquerda para rastrear a causa de um problema em seu aplicativo. A atividade 000 normalmente tem exceções sem tratamento que emergem até o usuário.  
  
  A imagem a seguir mostra como selecionar uma atividade de vermelha ou amarela para localizar a raiz do problema.   
 ![Captura de tela de atividades de vermelhas ou amarelas para localizar a raiz do problema.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/service-trace-viewer.gif)  

 No painel à direita superior, você pode examinar os rastreamentos para a atividade selecionada à esquerda. Em seguida, você pode examinar os rastreamentos de vermelhos ou amarelos nesse painel e ver como elas são correlacionadas. No gráfico anterior, podemos ver rastreamentos de aviso para o cliente e o serviço na mesma atividade de ação de processo.  
  
 Se esses rastreamentos não fornecem a você a causa do erro, você pode utilizar o gráfico clicando duas vezes a atividade selecionada no painel à esquerda (ação de processo aqui). O gráfico com atividades relacionadas é exibido. Em seguida, você pode expandir atividades relacionadas (clicando nos sinais de "+") para localizar o primeiro rastreamento emitido em vermelho ou amarelo em uma atividade relacionada. Manter expandindo as atividades que ocorreram antes do rastreamento de vermelho ou amarelo de interesse, seguindo as transferências de atividades relacionadas ou fluxos de mensagens entre pontos de extremidade, até que você acompanhar a causa raiz do problema.  
  
 ![Usando o Visualizador de rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")  
Expandindo as atividades para acompanhar a causa raiz de um problema  
  
 Se ServiceModel `ActivityTracing` é desativada, mas o rastreamento de ServiceModel estiver ativado, você pode ver os rastreamentos de ServiceModel emitidos na atividade de 0000. No entanto, isso requer mais esforço para entender a correlação desses rastreamentos.  
  
 Se a mensagem de registro em log estiver habilitado, você pode usar a guia mensagem para ver qual mensagem é afetada pelo erro. Clicando duas vezes em uma mensagem em vermelho ou amarelo, você pode ver a exibição do gráfico de atividades relacionadas. Essas atividades são aqueles mais estreitamente relacionados à solicitação em que ocorreu um erro.  
  
 ![Captura de tela do Visualizador de rastreamento com o log de mensagens habilitado.](./media/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting/message-logging-enabled.gif)  

Para iniciar a solução de problemas, você também pode escolher um rastreamento de mensagem de vermelho ou amarelo e clique duas vezes para acompanhar a causa raiz.  
  
## <a name="see-also"></a>Consulte também

- [Cenários de rastreamento ponta a ponta](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [Ferramenta Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
- [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
