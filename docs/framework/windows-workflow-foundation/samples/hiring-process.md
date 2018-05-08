---
title: Processo de aluguer
ms.date: 03/30/2017
ms.assetid: d5fcacbb-c884-4b37-a5d6-02b1b8eec7b4
ms.openlocfilehash: 87327692e35e9386dab4cf906ab33cbe08d73fdd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="hiring-process"></a>Processo de aluguer
Este exemplo demonstra como implementar um processo enterprise usando as atividades de mensagem e os dois fluxos de trabalho hospedados como serviços de fluxo de trabalho. Esses fluxos de trabalho são parte da infraestrutura de TI de uma empresa fictícia chamada Contoso, Inc.  
  
 O processo de fluxo de trabalho de `HiringRequest` (implementado como <xref:System.Activities.Statements.Flowchart>) solicita a autorização de vários gerentes na organização. Para alcançar essa meta, o fluxo de trabalho usa outros serviços existentes na organização (no nosso caso, um serviço de caixa de entrada e um serviço de dados organizacionais implementados como serviços do Windows Communication Foundation (WCF) simples).  
  
 O fluxo de trabalho `ResumeRequest` (implementado como <xref:System.Activities.Statements.Sequence>) publica um anúncio de emprego externa no site de carreiras de Contoso e gerencia a aquisição de resumos. Um anúncio de emprego está disponível no site externo por um período de tempo fixo (até que um tempo limite expire) ou até que um funcionário de Contoso decida o remover.  
  
 Este exemplo demonstra os seguintes recursos de [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]:  
  
-   <xref:System.Activities.Statements.Flowchart> e fluxos de trabalho <xref:System.Activities.Statements.Sequence> para modelar processos comerciais.  
  
-   Serviços de fluxo de trabalho.  
  
-   Atividades de mensagem.  
  
-   Correlação conteudo base.  
  
-   Atividades personalizados (declarativo e o código baseado).  
  
-   Sistema forneceu persistência de servidor SQL.  
  
-   <xref:System.Activities.Persistence.PersistenceParticipant>personalizado.  
  
-   Controle personalizado.  
  
-   Rastreamento de evento para acompanhar do Windows (ETW).  
  
-   Composição de atividades.  
  
-   atividades de<xref:System.Activities.Statements.Parallel> .  
  
-   atividade de<xref:System.Activities.Statements.CancellationScope> .  
  
-   Timers duráveis (atividade de<xref:System.Activities.Statements.Delay> ).  
  
-   Transações.  
  
-   Mais de um fluxo de trabalho na mesma solução.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\HiringProcess`  
  
## <a name="description-of-the-process"></a>Descrição do processo  
 Contoso, Inc. deseja que o controle de fechamento do número de funcionários em cada um dos seus departamentos. Portanto, quando qualquer funcionário deseja iniciar um novo processo de aluguer, precisam fazer uma aprovação de aluguer do processo de solicitação antes que o recrutamento possa realmente acontecer. Esse processo é chamado solicitação de aluguer de processo (definida no projeto de HiringRequestService) e consiste as seguintes etapas:  
  
1.  Um funcionário (solicitador) começa a solicitação de aluguer do processo.  
  
2.  O gerenciador do solicitador deve aprovar a solicitação:  
  
    1.  O gerenciador pode descartar a solicitação.  
  
    2.  O gerenciador pode retornar a solicitação ao solicitador para informações adicionais:  
  
        1.  O solicitador revise e envia a solicitação de volta ao gerenciador.  
  
    3.  O gerenciador pode aprovar.  
  
3.  Depois que o gerenciador do solicitador aprova, o proprietário do departamento deve aprovar a solicitação:  
  
    1.  O proprietário do departamento pode descartar.  
  
    2.  O proprietário do departamento pode aprovar.  
  
4.  Depois que o proprietário do departamento aprova, o processo requer a aprovação de gerentes de 2 horas ou de CEO:  
  
    1.  O processo pode fazer a transição de estado aceito ou descartado.  
  
    2.  Se o processo é aceito, uma nova instância do fluxo de trabalho `ResumeRequest` é iniciada (`ResumeRequest` é associado a HiringRequest.csproj com uma referência de serviço.)  
  
 Uma vez que os gerentes aprovam o aluguer de um novo empregado, a hora deve encontrar o candidato apropriado. Esse processo é executado pelo segundo fluxo de trabalho (`ResumeRequest`, definido em ResumeRequestService.csproj). Este fluxo de trabalho define o processo para enviar um anúncio de emprego com uma oportunidade de carreira a carreiras externos site de Contoso, recebe resumos dos candidatos, e monitora o estado do anúncio de emprego. As posições estão disponíveis por um período de tempo fixo (até que uma hora expirem) ou até que um funcionário de Contoso decida o remover. O fluxo de trabalho `ResumeRequest` consiste as seguintes etapas:  
  
1.  Um funcionário de Contoso em informações sobre a posição e uma duração de tempo limite. Uma vez que o funcionário nessa informação, a posição é remetida no site de carreiras.  
  
2.  Uma vez que a informação é publicado, as partes interessadas podem enviar seus resumos. Quando um resumo é enviado, é armazenado em um registro associado à oportunidade de emprego.  
  
3.  Os candidatos podem enviar resumos até que o tempo limite expire ou alguém departamento de Contoso hora decidir remover explicitamente a postagem parando o processo.  
  
## <a name="projects-in-the-sample"></a>Projetos no exemplo  
 A tabela a seguir mostra os projetos na solução de exemplo.  
  
|Projeto|Descrição|  
|-------------|-----------------|  
|ContosoHR|Contém contratos de dados, objetos comerciais e classes de armazenamento.|  
|HiringRequestService|Contém a definição do fluxo de trabalho aluguer do processo de solicitação.<br /><br /> Este projeto é implementado como um aplicativo de console que são host o fluxo de trabalho (arquivo de xaml) como um serviço.|  
|ResumeRequestService|Um serviço de fluxo de trabalho que coleta resumos dos candidatos até que um tempo limite expire ou alguém decidir que o processo tem que ser interrompido.<br /><br /> Este projeto é implementado como um serviço declarativa de fluxo de trabalho (xamlx).|  
|OrgService|Um serviço que expõem informações de organização (funcionários, posições, PositionTypes, e departamentos). Você pode pensar esse serviço como o módulo de organização de um plano (ERP) de recurso de empresa.<br /><br /> Este projeto é implementado como um aplicativo de console que expõe um serviço do Windows Communication Foundation (WCF).|  
|InboxService|Um caixa de entrada que contém tarefas acionáveis para funcionários.<br /><br /> Este projeto é implementado como um aplicativo de console que expõe um serviço windows.|  
|InternalClient|Um aplicativo da Web para interagir com o processo. Os usuários podem começar, participar, e exibir seus fluxos de trabalho HiringProcess. Usando este aplicativo, também podem iniciar e monitorar processos de ResumeRequest.<br /><br /> Esse site é implementada para ser interna a intranet de Contoso. Este projeto é implementado como uma página web ASP.NET.|  
|CareersWebSite|Um site externo que expõe as posições abertas em Contoso. Qualquer candidato potencialmente pode navegar para esse site e enviar um resumo.|  
  
## <a name="feature-summary"></a>Resumo de recurso  
 A tabela a seguir descreve como cada recurso é usado neste exemplo.  
  
|Recurso|Descrição|Projeto|  
|-------------|-----------------|-------------|  
|Fluxograma|O processo empresarial é representado como um fluxograma. Esta descrição do fluxograma representa o processo da mesma maneira na qual um negócio o desenharia em um whiteboard.|HiringRequestService|  
|Serviços de fluxo de trabalho|O fluxograma com a definição de processo é hospedado em um serviço (nesse exemplo, o serviço está hospedado em um aplicativo de console).|HiringRequestService|  
|Atividades de mensagem|O fluxograma usa atividades de mensagem de duas maneiras:<br /><br /> -Para obter informações do usuário (para receber as decisões e informações relacionadas em cada etapa de aprovação).<br />-Para interagir com outros serviços existentes (InboxService e OrgDataService, usada por meio de referências de serviço).|HiringRequestService|  
|O conteúdo com base correlação|As mensagens aprovação de correlacionam na propriedade ID de solicitação de aluguer:<br /><br /> -Quando um processo é iniciado, o identificador de correlação é inicializado com a ID da solicitação.<br />-Mensagens de aprovação entrada correlacionam em sua ID (o primeiro parâmetro de cada mensagem de aprovação é a ID da solicitação).|HiringRequestService/ResumeRequestService|  
|Atividades personalizados (declarativas e código com base)|Há várias atividades personalizados nesse exemplo:<br /><br /> -   `SaveActionTracking`: Essa atividade emite um personalizado <xref:System.Activities.Tracking.TrackingRecord> (usando <xref:System.Activities.NativeActivityContext.Track%2A>). Esta atividade foi criada usando código obrigatório que estende <xref:System.Activities.NativeActivity>.<br />-   `GetEmployeesByPositionTypes`: Esta atividade recebe uma lista de IDs de tipo de posição e retorna uma lista de pessoas que têm a posição na Contoso. Esta atividade foi criado declarativamente (usando o designer de atividade).<br />-   `SaveHiringRequestInfo`: Essa atividade salva as informações de um `HiringRequest` (usando `HiringRequestRepository.Save`). Esta atividade foi criada usando código obrigatório que estende <xref:System.Activities.CodeActivity>.|HiringRequestService|  
|Sistema forneceu persistência do SQL Server|A instância de <xref:System.ServiceModel.Activities.WorkflowServiceHost> que hospeda a definição de processo do fluxograma é configurado para usar o sistema forneceu persistência do SQL Server.|HiringRequestService/ResumeRequestService|  
|Rastreamento personalizada|O exemplo inclui um participante personalizado de rastreamento que salva o histórico de `HiringRequestProcess` (esse registro que ação foi feita, por quem, e quando). O código-fonte está na pasta de rastreamento de HiringRequestService.|HiringRequestService|  
|Rastreamento de ETW|Sistema forneceu o rastreamento de ETW é configurado no arquivo App.config no serviço de HiringRequestService.|HiringRequestService|  
|Composição de atividades|A definição de processo usa a composição livre de <xref:System.Activities.Activity>. O fluxograma contém vários a sequência e as atividades paralelas que contêm ao mesmo tempo outras atividades (e assim por diante).|HiringRequestService|  
|Atividades paralelas|-   <xref:System.Activities.Statements.ParallelForEach%601> é usado para registrar-se na caixa de entrada do CEO e gerentes de RH em paralelo (aguardando a etapa de aprovação de gerentes de RH duas).<br />-   <xref:System.Activities.Statements.Parallel> é usado para realizar algumas tarefas de limpeza nas etapas concluídas e rejeitados|HiringRequestService|  
|Cancelar modelo|O fluxograma usa <xref:System.Activities.Statements.CancellationScope> para criar o comportamento de cancelamento (neste caso faz qualquer limpeza.)|HiringRequestService|  
|Participante de persistência do cliente|`HiringRequestPersistenceParticipant` salva dados de uma variável de fluxo de trabalho a uma tabela armazenada na base de dados de Contoso hora.|HiringRequestService|  
|Serviços de fluxo de trabalho|`ResumeRequestService` é implementado usando serviços de fluxo de trabalho. A definição de fluxo de trabalho e informações de serviço estão contidas em ResumeRequestService.xamlx. O serviço está configurado para usar a persistência e o rastreamento.|ResumeRequestService|  
|Timers duráveis|`ResumeRequestService` usa timers duráveis para definir a duração de um anúncio de emprego (uma vez para o tempo limite expirar, o anúncio de emprego é fechado).|ResumeRequestService|  
|Transações|<xref:System.Activities.Statements.TransactionScope> é usado para garantir a consistência de dados dentro da execução de várias atividades (quando um novo resumo é recebido).|ResumeRequestService|  
|Transações|O participante personalizado de persistência (`HiringRequestPersistenceParticipant`) e uso personalizado de participante de rastreamento (`HistoryFileTrackingParticipant`) a mesma transação.|HiringRequestService|  
|Usando [!INCLUDE[wf1](../../../../includes/wf1-md.md)] em aplicativos de [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] .|Fluxos de trabalho são acessados de dois aplicativos de [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] .|InternalClient/CareersWebSite|  
  
## <a name="data-storage"></a>Armazenamento de dados  
 Os dados são armazenados em uma base de dados SQL Server (chamado `ContosoHR` script para criar este base de dados está localizado na pasta de `DbSetup` ). As instâncias de fluxo de trabalho são armazenadas em uma base de dados SQL Server (chamado `InstanceStore` os scripts para criar o armazenamento de instância são parte de distribuição de [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] ).  
  
 Os bancos de dados são criados ao executar o script de Setup.cmd em um prompt de comando do Visual Studio.  
  
## <a name="running-the-sample"></a>Executando o exemplo  
  
#### <a name="to-create-the-databases"></a>Para criar os bases de dados  
  
1.  Abra um prompt de comando do Visual Studio.  
  
2.  Navegue até a pasta de exemplo.  
  
3.  Executar Setup.cmd.  
  
4.  Verifique se os dois bases de dados `ContosoHR` e `InstanceStore` foram criados em SQL express.  
  
#### <a name="to-set-up-the-solution-for-execution"></a>Para configurar a solução para a execução  
  
1.  Execute o Visual Studio como um administrador. HiringRequest.sln aberto.  
  
2.  Com o botão direito na solução **Solution Explorer** e selecione **propriedades**.  
  
3.  Selecione a opção **vários projetos de inicialização** e defina o **CareersWebSite**, **InternalClient**, **HiringRequestService**, e **ResumeRequestService** para **iniciar**. Deixe **ContosoHR**, **InboxService**, e **OrgService** como None.  
  
4.  Crie a solução. CTRL+SHIFT+B pressionando. Verifique se a compilação foi bem-sucedida.  
  
#### <a name="to-run-the-solution"></a>Para executar a solução  
  
1.  Após criar a solução, pressione CTRL+F5 para executar sem depuração. Verifique se todos os serviços comecem.  
  
2.  Clique com botão direito **InternalClient** na solução e, em seguida, selecione **exibir no navegador**. A página padrão para `InternalClient` é exibida. Certifique-se de que os serviços estão sendo executado, clique o link.  
  
3.  O **HiringRequest** módulo é exibido. Você pode seguir o cenário detalhado aqui.  
  
4.  Uma vez que `HiringRequest` estiver concluída, você pode começar `ResumeRequest`. Você pode seguir o cenário detalhado aqui.  
  
5.  Quando `ResumeRequest` é enviado, está disponível no site pública (site de carreiras de Contoso.) Para ver o anúncio de emprego (e para aplicar para a posição), navegue para o site de carreiras.  
  
6.  Clique com botão direito **CareersWebSite** na solução e selecione **exibir no navegador**.  
  
7.  Navegue de volta para o `InternalClient` clicando **InternalClient** na solução e selecionando **exibir no navegador**.  
  
8.  Vá para o **JobPostings** seção clicando o **vagas** link no menu superior da caixa de entrada. Você pode seguir o cenário detalhado aqui.  
  
## <a name="scenarios"></a>Cenários  
  
### <a name="hiring-request"></a>Solicitação de aluguer  
  
1.  Michael Alexander (Software Engineer) deseja solicitar uma nova posição para contratar uma Software Engineer no teste (SDET) no departamento de engenharia que tenha pelo menos 3 anos de experiência em C#.  
  
2.  Após a criação, a solicitação é exibida na caixa de entrada de Michael (clique **atualizar** se você não vir a solicitação) está aguardando aprovação de Peter Brehm, que é o Gerenciador de Michael.  
  
3.  Peter deseja atuar na solicitação de Michael. Pense as demandas da posição 5 anos de experiência C# em vez de 3, o que envia comentários volta para revisão.  
  
4.  Michael vê uma mensagem no caixa de entrada de seu gerente e alterações para atuar. Michael consulta o histórico de solicitação de posição e concorda com o Peter. Michael altera a descrição para exigir 5 anos de experiência de C# e aceitar a alteração.  
  
5.  Atua de Peter na solicitação modificada de Michael e aceitar-la. A solicitação agora deve ser aprovada pelo diretor de engenharia, Tsvi Reiter.  
  
6.  Tsvi Reiter deseja expedir a solicitação, o que colocados em um comentário para dizer que a solicitação é urgente e aceitar-la.  
  
7.  A solicitação agora tem que ser aprovada por dois gerentes de hora ou por CEO. O CEO, Brian Richard Goldstein, consulta a solicitação urgente por Tsvi. Atua na solicitação aceitando a assim, ignorando a aprovação por dois gerentes de hora.  
  
8.  A solicitação é removido da caixa de entrada de Michael e o processo de contratar um SDET agora tem iniciado.  
  
### <a name="start-resume-request"></a>Solicitação de resumo de Início  
  
1.  Agora, a posição de trabalho está esperando para ser lançada para um site externo em que as pessoas podem aplicar (você pode vê-lo clicando o **vagas** link). Atualmente, a posição de trabalho é sentando-se com um representante de hora que é responsável para finalizar a posição de trabalho e a postagem.  
  
2.  HR deseja editar este cargo (clicando o **editar** link), definindo um tempo limite de 60 minutos (em termos práticos, isso poderia ser dias ou semanas). O tempo limite permite que a posição de trabalho é decolada o site externo de acordo com os momentos especificados.  
  
3.  Depois de salvar a posição de trabalho editado, ele aparece no **continua recebendo** guia (atualizar a página da Web para ver a nova posição de trabalho).  
  
### <a name="collecting-resumes"></a>Coletando resumos  
  
1.  A posição de trabalho deve aparecer no site externo. Como uma pessoa interessada em aplicar para o trabalho, você pode usar para essa posição e enviar seu resumo.  
  
2.  Se você voltar para o serviço de lista de lançamentos de trabalho, você poderá "Exibir currículos" que tenham sido coletados até o momento.  
  
3.  A hora também pode parar de coletar resumos (por exemplo, uma vez que o candidato à direita foi identificado).  
  
## <a name="troubleshooting"></a>Solução de problemas  
  
1.  Certifique-se de que você está executando o Visual Studio com privilégios de administrador.  
  
2.  Se a solução não compilar, verifique o seguinte:  
  
    -   A referência ao `ContosoHR` não está ausente do `InternalClient` ou `CareersWebSite` projetos.  
  
3.  Se a solução não executa, verifique o seguinte:  
  
    1.  Todos os serviços estão executando.  
  
    2.  Referências de serviço são atualizadas.  
  
        1.  Abra a pasta App_WebReferences  
  
        2.  Clique com botão direito **Contoso** e selecione **referências de Web/serviço de atualização**.  
  
        3.  Recompile a solução pressionando CTRL + SHIFT + B no Visual Studio.  
  
## <a name="uninstalling"></a>Desinstalando  
  
1.  Exclua o armazenamento da instância do SQL Server em execução Cleanup.bat, localizado na pasta de DbSetup.  
  
2.  Exclua o formulário de origem seu disco rígido.