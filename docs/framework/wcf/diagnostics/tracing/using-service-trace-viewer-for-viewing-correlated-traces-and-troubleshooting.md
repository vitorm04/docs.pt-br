---
title: "Utilizando o visualizador de rastreamento de serviço para visualização de rastreamento correlacionados e soluções de problemas"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 05d2321c-8acb-49d7-a6cd-8ef2220c6775
caps.latest.revision: "22"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1742caba38dc0b2cc4b53dbc0c3ffcf595cf7f9c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting"></a>Utilizando o visualizador de rastreamento de serviço para visualização de rastreamento correlacionados e soluções de problemas
Este tópico descreve o formato dos dados de rastreamento, como exibir e abordagens que usam o Visualizador de rastreamento de serviço para solucionar problemas de seu aplicativo.  
  
## <a name="using-the-service-trace-viewer-tool"></a>Usando a ferramenta Visualizador de Rastreamento de Serviço  
 O [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] ferramenta do Visualizador de rastreamento de serviço ajuda a correlacionar rastreamentos de diagnóstico produzidos por [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] ouvintes para localizar a raiz causam um erro. A ferramenta fornece uma maneira de exibir facilmente, grupo, e rastreamentos de filtro para que você pode diagnosticar, reparar e verificar problemas com [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] serviços. Para obter mais informações sobre como usar essa ferramenta, consulte [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).  
  
 Este tópico contém as capturas de tela de gerado pela execução de rastreamentos a [rastreamento e registro em log de mensagem](../../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) de exemplo, quando exibido usando o [ferramenta de Visualizador de rastreamento de serviço (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Este tópico demonstra como compreender o conteúdo de rastreamento, atividades e correlação e como analisar grandes números de rastreamentos ao solucionar o problema.  
  
## <a name="viewing-trace-content"></a>Exibição de conteúdo de rastreamento  
 Um evento de rastreamento contém as seguintes informações mais significativas:  
  
-   Nome da atividade quando foi definido.  
  
-   Hora de emissão.  
  
-   Nível de rastreamento.  
  
-   Nome de origem do rastreamento.  
  
-   Nome do processo.  
  
-   Id do thread.  
  
-   Um identificador de rastreamento exclusivo, que é uma URL que aponta para um destino na Microsoft Docs, do qual você pode obter mais informações sobre o rastreamento.  
  
 Todos esses podem ser vistos no painel superior direito no Visualizador de rastreamento de serviço ou no **informações básicas** seção no modo de exibição formatada do painel inferior direito, ao selecionar um rastreamento.  
  
> [!NOTE]
>  Se o cliente e o serviço estiverem no mesmo computador, os rastreamentos de ambos os aplicativos estarão presentes. Eles podem ser filtrados usando o **nome do processo** coluna.  
  
 Além disso, o modo de exibição formatado também fornece uma descrição para o rastreamento e informações detalhadas adicionais quando disponíveis. Este último pode incluir exceção tipo e a mensagem, pilhas de chamadas, ação de mensagem, de/para campos e outras informações de exceção.  
  
 No modo de exibição XML, as marcas xml úteis incluem o seguinte:  
  
-   \<Subtipo > (o nível de rastreamento).  
  
-   \<TimeCreated >.  
  
-   \<Fonte > (nome de origem de rastreamento).  
  
-   \<Correlação > (id da atividade definida ao emitir o rastreamento).  
  
-   \<Execução > (id de thread e processo).  
  
-   \<Computador >.  
  
-   \<ExtendedData >, incluindo \<ação >, \<MessageID > e o \<ActivityId > definido no cabeçalho da mensagem ao enviar uma mensagem.  
  
 Se você examinar o rastreamento do "Enviado uma mensagem por um canal", você poderá ver o conteúdo a seguir.  
  
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
  
## <a name="servicemodel-e2e-tracing"></a>Rastreamento de ServiceModel E2E  
 Quando o `System.ServiceModel` origem de rastreamento é definida com um `switchValue` diferente de desativado, e `ActivityTracing`, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] cria atividades e transfere para [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] de processamento.  
  
 Uma atividade é uma unidade lógica de processamento que grupos de todos os rastreamentos relacionam a essa unidade de processamento. Por exemplo, você pode definir uma atividade para cada solicitação. Transferências de criar uma relação causal entre as atividades dentro de pontos de extremidade. Propagando a ID de atividade permite relacionar as atividades em pontos de extremidade. Isso pode ser feito definindo `propagateActivity` = `true` na configuração em cada ponto de extremidade. Atividades, transferência e propagação permitem executar a correlação de erro. Dessa forma, você pode encontrar a causa raiz de um erro mais rapidamente.  
  
 No cliente, um [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] atividade é criada para cada chamada de modelo de objeto (por exemplo, abrir ChannelFactory, adicionar, divisão e assim por diante.) Cada uma das chamadas de operação é processada em uma atividade de "Processo ação".  
  
 Captura de tela a seguir, extraído do [rastreamento e registro em log de mensagem](../../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) exemplo o painel esquerdo exibe a lista de atividades criadas no processo de cliente, classificado por hora de criação. A seguir está uma lista cronológica de atividades:  
  
-   Construir uma fábrica de canais (ClientBase).  
  
-   Abrir a fábrica de canais.  
  
-   Processar a ação Adicionar.  
  
-   Configurar a sessão segura (este ocorrido na primeira solicitação) e processado de três mensagens de resposta de infraestrutura de segurança: primeira, RSTR, SCT (processo mensagem 1, 2, 3).  
  
-   Processado subtrair, multiplicar e dividir as solicitações.  
  
-   Fechado a fábrica de canais, e isso fechou a sessão segura e processar a resposta de mensagem de segurança Cancelar.  
  
 Podemos ver as mensagens de infraestrutura de segurança devido o wsHttpBinding.  
  
> [!NOTE]
>  Em [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], mostramos processadas inicialmente em uma atividade separada (mensagem de processo) de mensagens de resposta antes de correlacionamos para a atividade de ação do processo correspondente que inclui a mensagem de solicitação, por meio de uma transferência. Isso acontece para mensagens de infraestrutura e solicitações assíncronas e se deve ao fato de que podemos deve inspecionar a mensagem, ler o cabeçalho activityId e identificar a atividade de ação de processo existente com essa id para correlacionar a ele. Para solicitações síncronas, podemos estão bloqueando para a resposta e, portanto, saber qual ação de processo, a resposta está relacionado ao.  
  
 ![Usando o Visualizador de rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace4.gif "e2eTrace4")  
Atividades do cliente WCF listadas por hora de criação (painel esquerdo) e suas atividades aninhadas e rastreamentos (painel direito superior)  
  
 Quando selecionamos uma atividade no painel esquerdo, podemos ver atividades aninhadas e rastreamentos no painel superior direito. Portanto, essa é uma redução exibição hierárquica da lista de atividades do lado esquerdo, com base na atividade pai selecionado. Como a ação selecionada do processo adicionar é a primeira solicitação feita, essa atividade contém a atividade definir segurança de sessão (transferência de transferência do) e rastreamentos para o processamento real da ação Adicionar.  
  
 Clique duas vezes em que a ação de processo Adicionar atividade no painel esquerdo, podemos ver uma representação gráfica do cliente [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] as atividades relacionadas a adicionar. A primeira atividade à esquerda é a atividade raiz (0000), que é a atividade padrão. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]transferências de fora da atividade de ambiente. Se não for definido, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] transferências fora 0000. Aqui, a segunda atividade adicionar da ação de processo, transfere fora de 0. Em seguida, podemos ver a sessão de segurança de instalação.  
  
 ![Usando o Visualizador de rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace5.gif "e2eTrace5")  
Gráfico de modo de exibição de atividades do cliente WCF: atividade de ambiente (0 aqui), ação de processo e definir a sessão segura  
  
 No painel superior direito, podemos ver todos os rastreamentos relacionados à atividade de ação do processo de adicionar. Especificamente, podemos enviou a mensagem de solicitação ("enviado uma mensagem por um canal") e recebeu a resposta ("recebida uma mensagem por um canal") na mesma atividade. Isso é mostrado no gráfico a seguir. Para maior clareza, o conjunto de atividade de sessão segura é recolhido no gráfico.  
  
 ![Usando o Visualizador de rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace6.gif "e2eTrace6")  
Lista de rastreamentos para a atividade de ação do processo: podemos enviar a solicitação e receber a resposta na mesma atividade.  
  
 Aqui, podemos carregar rastreamentos de cliente apenas para fins de esclarecimento, mas rastreamentos de serviço (mensagem de solicitação recebida e mensagem de resposta enviada) aparecem na mesma atividade se elas também são carregadas na ferramenta de e `propagateActivity` foi definida como `true.` isso é mostrado na ilustração posterior.  
  
 Sobre o serviço, o modelo de atividade é mapeado para o [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] conceitos da seguinte maneira:  
  
1.  Vamos construir e abrir um ServiceHost (Isso pode criar várias atividades relacionadas ao host, por exemplo, no caso de segurança).  
  
2.  Podemos criar uma atividade escutar para cada ouvinte de ServiceHost (com transferências e abrir ServiceHost).  
  
3.  Quando o ouvinte detecta uma solicitação de comunicação iniciada pelo cliente, ele transfere para a atividade de "Bytes de recebimento", em que todos os bytes enviados do cliente são processados. Nesta atividade, podemos ver os erros de conexão que ocorreram durante a interação do serviço de cliente.  
  
4.  Para cada conjunto de bytes recebidos que corresponde a uma mensagem, podemos processar esses bytes em uma atividade de "Mensagem de processo", em que criamos o [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] objeto de mensagem. Nesta atividade, podemos ver erros relacionados a um envelope incorreto ou uma mensagem malformada.  
  
5.  Depois que a mensagem é formada, podemos transferir a uma atividade de ação de processo. Se `propagateActivity` é definido como `true` no cliente e no serviço, essa atividade tem a mesma id que aquele definido no cliente e descritos anteriormente. Nesta fase começar a se beneficiar da correlação direta entre pontos de extremidade, porque todos os rastreamentos emitido em [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] que estão relacionados à solicitação são essa mesma atividade, incluindo o processamento de mensagem de resposta.  
  
6.  Para a ação de fora do processo, podemos criar uma atividade de "Executar o código do usuário" para isolar os rastreamentos emitidos no código do usuário daquelas emitido em [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]. No exemplo anterior, o rastreamento do "Serviço envia a resposta de adicionar" é emitido na atividade de "Código de usuário Execute", não na atividade propagada pelo cliente, se aplicável.  
  
 Na ilustração a seguir, a primeira atividade à esquerda é a atividade raiz (0000), que é a atividade padrão. As próximas três atividades são abrir o ServiceHost. A atividade na coluna 5 é o ouvinte e as atividades restantes (6 to 8) descrevem o processamento do WCF de uma mensagem, de bytes de processamento para ativação de código do usuário.  
  
 ![Usando o Visualizador de rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace7.gif "e2eTrace7")  
Lista de atividades de serviço do WCF  
  
 Captura de tela a seguir mostra as atividades para o cliente e o serviço e realça a atividade de ação do processo adicionar entre processos (laranja). Setas relacionam as mensagens de solicitação e resposta enviados e recebidos pelo serviço e cliente. Os rastreamentos de ação de processo são separados em processos no gráfico, mas mostrados como parte da mesma atividade no painel superior direito. Este painel, podemos ver rastreamentos de cliente para mensagens enviadas seguidos de rastreamentos de serviço de mensagens recebidos e processados.  
  
 ![Usando o Visualizador de rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace8.gif "e2eTrace8")  
Modo de exibição de gráfico de ambas as atividades de cliente e o serviço do WCF  
  
 No cenário de erro a seguir, estão relacionados de erro e rastreamentos de aviso no serviço e cliente. Primeiro, uma exceção é gerada no código do usuário no serviço (atividade de verde mais à direita que inclui um aviso de rastreamento para a exceção "o serviço não pode processar esta solicitação no código do usuário."). Quando a resposta será enviada ao cliente, um rastreamento de aviso é emitido novamente para indicar a mensagem de falha (atividade rosa esquerda). O cliente, em seguida, fecha o seu cliente WCF (atividade amarela na parte inferior esquerda), que anula a conexão ao serviço. O serviço gera um erro (atividade rosa mais longo no lado direito).  
  
 ![Usando o Visualizador de rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")  
Correlação de erro entre o cliente e de serviço  
  
 O exemplo usado para gerar esses rastreamentos é uma série de solicitações síncronas usando o wsHttpBinding. Há os desvios esse gráfico para cenários sem segurança ou com solicitações assíncronas, onde a atividade de ação de processo abrange as operações de início e término que constituem a chamada assíncrona e mostra as transferências para uma atividade de retorno de chamada. Para obter mais informações sobre cenários adicionais, consulte [cenários de rastreamento ponta a ponta](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).  
  
## <a name="troubleshooting-using-the-service-trace-viewer"></a>Solução de problemas usando o Visualizador de rastreamento de serviço  
 Quando você carrega arquivos de rastreamento na ferramenta de Visualizador de rastreamento de serviço, você pode selecionar qualquer atividade vermelha ou amarela no painel esquerdo para rastrear a causa de um problema em seu aplicativo. A atividade 000 normalmente tem exceções não tratadas que vão para o usuário.  
  
 ![Usando o Visualizador de rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace10.gif "e2eTrace10")  
Selecionar atividade vermelha ou amarela para localizar a raiz de um problema  
  
 No painel superior direito, você pode examinar os rastreamentos para a atividade selecionada à esquerda. Você pode examinar os rastreamentos vermelhos ou amarelos no painel e ver como eles são correlacionados. No gráfico anterior, podemos ver rastreamentos de aviso para o cliente e o serviço na mesma atividade de ação de processo.  
  
 Se os rastreamentos não fornecer a causa do erro, você pode utilizar o gráfico clicando duas vezes a atividade selecionada no painel esquerdo (ação de processo aqui). O gráfico com as atividades relacionadas é exibido. Em seguida, você pode expandir as atividades relacionadas (clicando nos sinais de "+") para localizar o primeiro rastreamento emitido em vermelho ou amarelo em uma atividade relacionada. Manter expandindo as atividades que ocorreram antes do rastreamento vermelho ou amarelo de interesse, seguir transferências para atividades relacionadas ou fluxos de mensagens entre pontos de extremidade, até que você controla a causa raiz do problema.  
  
 ![Usando o Visualizador de rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/media/wcfc-e2etrace9s.gif "wcfc_e2etrace9s")  
Atividades de expansão para rastrear a causa raiz de um problema  
  
 Se ServiceModel `ActivityTracing` é desativada, mas o rastreamento de ServiceModel está ativada, você pode ver rastreamentos de ServiceModel emitidos na atividade 0000. No entanto, isso requer mais esforço para entender a correlação desses rastreamentos.  
  
 Se o log de mensagens estiver habilitado, você pode usar a guia mensagem para ver qual mensagem é afetada pelo erro. Clicando duas vezes em uma mensagem em vermelho ou amarelo, você pode ver a exibição do gráfico das atividades relacionadas. Essas atividades são os mais relacionadas à solicitação em que ocorreu um erro.  
  
 ![Usando o Visualizador de rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/media/e2etrace11.gif "e2eTrace11")  
Para iniciar a solução de problemas, você também pode escolher um rastreamento de mensagem vermelho ou amarelo e clique duas vezes nele para acompanhar a causa raiz  
  
## <a name="see-also"></a>Consulte também  
 [Cenários de rastreamento ponta a ponta](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) (Ferramenta Visualizador de rastreamento de serviço (SvcTraceViewer.exe))  
 [Rastreamento](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)
