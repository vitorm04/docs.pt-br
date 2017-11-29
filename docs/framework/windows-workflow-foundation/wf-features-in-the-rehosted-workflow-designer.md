---
title: Suporte para novas Funcionalidades do Workflow Foundation 4.5 no Designer de Fluxo de Trabalho hospedado novamente
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a4a4038-d8e6-41dd-99ea-93bd76286772
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 346dc5f06fd5f655426d8f41164a9a2f24acdb5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="support-for-new-workflow-foundation-45-features-in-the-rehosted-workflow-designer"></a>Suporte para novas Funcionalidades do Workflow Foundation 4.5 no Designer de Fluxo de Trabalho hospedado novamente
O [!INCLUDE[wf](../../../includes/wf-md.md)] no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] introduziu muitos novos recursos, incluindo vários aprimoramentos à experiência do designer de fluxo de trabalho. Este tópico detalha quais desses recursos têm suporte no designer hospedado novamente e que não têm suporte no momento.  
  
> [!NOTE]
>  Para obter uma lista de todos os novos [!INCLUDE[wf](../../../includes/wf-md.md)] recursos introduzidos no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], incluindo aqueles que estão relacionados a nova hospedagem de designer, consulte [o que há de novo no Windows Workflow Foundation no .NET 4.5](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md).  
  
## <a name="activities"></a>Atividades  
 A biblioteca de atividades embutida contém novas atividades e novos recursos para atividades existentes. Todas essas novas atividades têm suporte no designer hospedado novamente. Para obter mais informações sobre essas novas atividades, consulte o [atividades](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_NewActivities) seção [o que há de novo no Windows Workflow Foundation no .NET 4.5](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md).  
  
## <a name="c-expressions"></a>Expressões C#  
 Antes do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], todas as expressões em fluxos de trabalho podiam ser escritas no Visual Basic. No [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], as expressões do Visual Basic são usadas apenas para os projetos criados usando o Visual Basic. Os projetos do Visual C# agora usam o C# para expressões. Ao criar fluxos de trabalho no [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], um editor de expressão C# completamente funcional é fornecido com recursos como realce de gramática e intellisense. Os projetos do fluxo de trabalho C# criados em versões anteriores que usam expressões do Visual Basic continuarão funcionando.  
  
> [!WARNING]
>  As expressões C# não têm suporte no designer hospedado novamente.  
  
## <a name="new-designer-capabilities"></a>Novos recursos do designer  
  
### <a name="designer-search"></a>Pesquisa do designer  
 O [localização rápida](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) e [localizar nos arquivos](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) recursos introduzidos com [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] não têm suporte no designer de rehosted. A pesquisa de `Toolbox` tem suporte no designer hospedado novamente. Para obter mais informações sobre esses recursos, consulte [Designer pesquisa](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_DesignerSearch).  
  
> [!WARNING]
>  [Localização rápida de](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) e [localizar nos arquivos](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) não têm suporte no designer de rehosted.  
  
### <a name="delete-context-menu-item-in-variable-and-argument-designer"></a>Excluir item de menu de contexto no designer de argumento e variável  
 No [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], as variáveis e os argumentos somente podem ser excluídos no designer usando o teclado. A partir do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], as variáveis e os argumentos podem ser excluídos com o menu de contexto. Esse recurso tem suporte no designer hospedado novamente.  
  
 A captura de tela a seguir mostra o menu de contexto do designer de variável e argumento.  
  
 ![Variável e o Menu de contexto do Designer do argumento](../../../docs/framework/windows-workflow-foundation/media/designercontextmenu.png "DesignerContextMenu")  
  
### <a name="auto-surround-with-sequence"></a>Envolvimento automático com sequência  
 Como um fluxo de trabalho ou algumas atividades do contêiner (como <xref:System.Activities.Statements.NoPersistScope>) só podem conter uma única atividade do corpo, adicionar uma segunda atividade exigia que o desenvolvedor excluísse a primeira atividade, adicionasse uma atividade <xref:System.Activities.Statements.Sequence> e, em seguida, adicionasse as duas atividades para a atividade de sequência. A partir do [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], ao adicionar uma segunda atividade para a superfície do designer, uma atividade de `Sequence` será criada automaticamente para incluir as duas atividades. Esse recurso tem suporte no designer hospedado novamente.  
  
 A captura de tela a seguir mostra uma atividade de `WriteLine` no `Body` de um `NoPersistScope`.  
  
 ![Auto &#45; surround drop local](../../../docs/framework/windows-workflow-foundation/media/autosurround1.png "AutoSurround1")  
  
 A captura de tela a seguir mostra a atividade de `Sequence` criada automaticamente no `Body` quando um segundo `WriteLine` é solto abaixo do primeiro.  
  
 ![Criado automaticamente atividade sequence](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")  
  
### <a name="pan-mode"></a>Modo panorâmico  
 Para navegar mais facilmente um grande fluxo de trabalho no designer, o modo panorâmico pode ser habilitado, permitindo que o desenvolvedor clique e arraste para mover a parte visível do fluxo de trabalho, em vez de precisar usar as barras de rolagem. O botão para ativar o modo de superfície está no canto inferior direito do designer. Esse recurso tem suporte no designer hospedado novamente.  
  
 A captura de tela a seguir mostra o botão de panorâmica qual está localizado no canto inferior direito do designer de fluxo de trabalho.  
  
 ![Botão Panorâmica no designer de fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/media/panbutton.png "PanButton")  
  
 O botão do meio do mouse ou a barra de espaço também podem ser usados para executar uma panorâmica do designer de fluxo de trabalho.  
  
### <a name="multi-select"></a>Multisseleção  
 Várias atividades podem ser selecionadas ao mesmo tempo, arrastando um retângulo ao redor delas (quando o modo panorâmico não está habilitado), ou mantendo pressionada a tecla CTRL e clicando nas atividades desejadas. Esse recurso tem suporte no designer hospedado novamente.  
  
 Várias seleções de atividade também podem ser arrastadas e soltadas dentro do designer, e também podem ser interagidas usando o menu de contexto.  
  
### <a name="outline-view-of-workflow-items"></a>Exibição de destaque de itens de fluxo de trabalho  
 Para facilitar a navegação de fluxos de trabalho hierárquicos, os componentes de um fluxo de trabalho são mostrados em uma exibição de destaque em estilo de árvore. O modo de exibição de estrutura de tópicos é exibido no **esboço de documento** exibição. Para abrir este modo de exibição [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], no menu superior, selecione **exibição**, **outras janelas**, **esboço de documento**, ou pressione Ctrl W, U. Clicar em um nó na exibição de destaque navegará para a atividade correspondente no designer de fluxo de trabalho, e a exibição da estrutura será atualizada para mostrar as atividades que estão selecionadas no designer. Esse recurso tem suporte no designer hospedado novamente.  
  
 A seguinte captura de tela do fluxo de trabalho concluído do [Tutorial de Introdução](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) mostra a exibição de estrutura de tópicos com um fluxo de trabalho sequencial.  
  
 ![Estrutura de tópicos no Designer de fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/media/outlineviewinworkflowdesigner.jpg "OutlineViewinWorkflowDesigner")  
  
### <a name="more-control-of-visibility-of-shell-bar-and-header-items"></a>Mais controle da visibilidade da barra de shell e dos itens de cabeçalho  
 Em um designer hospedado novamente, alguns dos controles padrão de interface do usuário não podem ter o significado de um fluxo de trabalho específico, e podem ser desativados. No [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], essa personalização é suportada apenas pela barra de shell na parte inferior do designer. No [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], a visibilidade dos itens de cabeçalho do shell na parte superior do designer pode ser ajustada definindo o <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> com o valor apropriado <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility>.  
  
### <a name="auto-connect-and-auto-insert-in-flowchart-and-state-machine-workflows"></a>Conexão automática e inserção automática em fluxograma e fluxos de trabalho de máquina de estado  
 No [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], as conexões entre nós em um fluxo de trabalho de fluxograma precisavam ser adicionadas manualmente. No [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], os nós de fluxograma e da máquina de estado têm pontos de conexão automática que se tornam visíveis quando uma atividade é arrastada da caixa de ferramentas na superfície do designer. Soltar uma atividade em um destes pontos adiciona automaticamente a atividade junto com a conexão necessária.  
  
 A captura de tela a seguir mostra os pontos de anexação que ficam visíveis quando uma atividade é arrastada da caixa de ferramentas.  
  
 ![Nó de início de fluxograma mostrando pontos de conexão automática](../../../docs/framework/windows-workflow-foundation/media/autoconnect1.png "Autoconnect1")  
  
 As atividades também podem ser arrastadas em conexões entre nós de fluxograma e estados para inserção automática do nó entre dois outros nós. A captura de tela a seguir mostra a linha de conexão realçada em que as atividades podem ser arrastadas da caixa de ferramentas e soltas.  
  
 ![Auto &#45; identificador para remover atividades de inserção](../../../docs/framework/windows-workflow-foundation/media/autoinsert.png "Autoinsert")  
  
 A conexão automática e a inserção automática têm suporte no designer hospedado novamente.  
  
### <a name="designer-annotations"></a>Anotações do designer  
 Para facilitar o desenvolvimento de fluxos de trabalho maiores, o designer agora permite adicionar anotações para ajudar a controlar o processo de design. A anotação pode ser adicionada a atividades, estados, nós de fluxograma, variáveis e argumentos. A captura de tela a seguir mostra o menu de contexto usado para adicionar anotações para o designer.  
  
 ![Menu de contexto de anotação](../../../docs/framework/windows-workflow-foundation/media/annotationdialog.png "annotationdialog")  
  
 As anotações do designer não têm suporte no designer hospedado novamente.  
  
### <a name="define-and-consume-activitydelegate-objects-in-the-designer"></a>Definir e consumir objetos ActivityDelegate no designer  
 As atividades no [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] usavam objetos <xref:System.Activities.ActivityDelegate> para expor pontos de execução onde outras partes do fluxo de trabalho podiam interagir com a execução de um fluxo de trabalho, mas usar esses pontos de execução necessários geralmente exigia uma grande quantidade de código. Nesta versão, os desenvolvedores podem definir e consumir representantes de atividade usando o designer de fluxo de trabalho. Para obter mais informações, consulte [como: definir e consumir representantes de atividades no Designer de fluxo de trabalho](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).  
  
 Os delegados de atividade não têm suporte no designer hospedado novamente.  
  
### <a name="build-time-validation"></a>Validação de tempo de compilação  
 No [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], os erros de validação do fluxo de trabalho não eram contados como erros de compilação durante a compilação de um projeto de fluxo de trabalho. Isso significava que criar um projeto de fluxo de trabalho poderia ter êxito mesmo se houvesse erros de validação do fluxo de trabalho. No [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], os erros de validação do fluxo de trabalho causam a falha na compilação.  
  
> [!WARNING]
>  A validação de tempo de compilação não tem suporte no designer hospedado novamente.  
  
### <a name="design-time-background-validation"></a>Validação em segundo plano do tempo de design  
 No [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], os fluxos de trabalho eram validados como um processo de primeiro plano, o que poderia parar a interface do usuário durante processos de validação complexos ou demorados. A validação do fluxo de trabalho agora ocorre em um thread em segundo plano, de modo que a interface do usuário não seja bloqueada.  
  
 A validação em segundo plano do tempo de design não tem suporte no designer hospedado novamente.  
  
### <a name="view-state-located-in-a-separate-location-in-xaml-files"></a>Estado de exibição localizado em um local separado em arquivos XAML  
 No [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], as informações de estado de exibição para um fluxo de trabalho são armazenadas no arquivo XAML em muitos lugares diferentes. Isso é inconveniente para os desenvolvedores que desejam ler XAML diretamente, ou gravar código para remover informações de estado de exibição. Em [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], as informações de estado de exibição no arquivo XAML são serializadas como um elemento separado no arquivo XAML.  Os desenvolvedores podem facilmente localizar e editar as informações de estado de exibição de uma atividade ou remover completamente o estado de exibição.  
  
 Esse recurso tem suporte no designer de fluxo de trabalho hospedado novamente.  
  
### <a name="opt-in-for-workflow-45-features-in-rehosted-designer"></a>Aceitação dos recursos do Workflow 4.5 no designer hospedado novamente  
 Para preservar a compatibilidade com versões anteriores, alguns novos recursos incluídos no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] não estão habilitados por padrão no designer hospedado novamente. Este é para garantir que aplicativos existentes que usam o designer hospedado novamente não sejam interrompidos ao atualizar para a versão mais recente. Para habilitar novos recursos no designer hospedado novamente, defina <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> como ".NET Framework 4.5" ou defina membros individuais do conjunto de <xref:System.Activities.Presentation.DesignerConfigurationService> para habilitar recursos individuais.  
  
## <a name="new-workflow-development-models"></a>Novos modelos de desenvolvimento de fluxo de trabalho  
 Além do fluxograma e de modelos sequenciais de desenvolvimento de fluxo de trabalho, esta versão inclui fluxos de trabalho da Máquina de Estado e serviços de fluxo de trabalho de primeiro contrato.  
  
### <a name="state-machine-workflows"></a>Fluxo de trabalho de máquina de estado  
 Fluxos de trabalho de máquina de estado foram introduzidos como parte do .NET Framework 4.0.1 no [Microsoft .NET Framework 4 Platform Update 1](http://go.microsoft.com/fwlink/?LinkID=215092). Essa atualização incluiu várias novas classes e atividades que permitiram que os desenvolvedores criassem fluxos de trabalho de máquina do estado. Essas classes e atividades foram atualizadas para o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. As atualizações incluem:  
  
1.  A capacidade de definir pontos de interrupção em estados  
  
2.  A capacidade de copiar e colar transições no designer de fluxo de trabalho  
  
3.  Suporte de designer para criação de transição do disparador compartilhado  
  
4.  Atividades usadas para criar fluxos de trabalho da máquina de estado, incluindo: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State> e <xref:System.Activities.Statements.Transition>.  
  
 Captura de tela a seguir mostra o fluxo de trabalho de máquina de estado concluído do [Tutorial de Introdução](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) etapa [como: criar um fluxo de trabalho de máquina de estado](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md).  
  
 ![Fluxo de trabalho de máquina de estado concluído](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 Para obter mais informações sobre a criação de fluxos de trabalho de máquina de estado, consulte [fluxos de trabalho de máquina de estado](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md). Os fluxos de trabalho da máquina de estado têm suporte no designer hospedado novamente.  
  
### <a name="contract-first-workflow-development"></a>Desenvolvimento de fluxo de trabalho de primeiro contrato  
 A ferramenta de desenvolvimento de fluxo de trabalho de primeiro contrato permite que o desenvolvedor crie um contrato no código primeiro e, em seguida, com alguns cliques no [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)], gere automaticamente um modelo de atividade na caixa de ferramentas representando cada operação. Essas atividades são então usadas para criar um fluxo de trabalho que implementa as operações definidas pelo contrato. O designer de fluxo de trabalho validará o serviço de fluxo de trabalho para assegurar que essas operações sejam implementadas e a assinatura do fluxo de trabalho corresponda à assinatura do contrato. O desenvolvedor também pode associar um serviço de fluxo de trabalho a uma coleção de contratos implementados. Para obter mais informações sobre o desenvolvimento de serviço de fluxo de trabalho do contrato, primeiro, consulte [como: criar um serviço de fluxo de trabalho que consome um contrato de serviço existente](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).  
  
> [!WARNING]
>  O desenvolvimento de fluxo de trabalho de primeiro contrato não tem suporte no designer de fluxo de trabalho.
