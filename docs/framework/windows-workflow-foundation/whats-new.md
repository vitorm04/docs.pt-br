---
title: Novidades no Windows Foundation Workflow
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Workflow Foundation [WF], what's new
- WF [WF], what's new
ms.assetid: 11f96014-001e-41a0-bcc2-d0684a52fa43
ms.openlocfilehash: 327a2ddbf9a45bc1d4633548ced7a8f39928345b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263791"
---
# <a name="whats-new-in-windows-workflow-foundation"></a>Novidades no Windows Foundation Workflow
Windows Workflow Foundation (WF) no [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] altera vários paradigma de desenvolvimento de versões anteriores. Fluxos de trabalho agora são mais fáceis de criar, executar e manter, e implementam um host da nova funcionalidade. Para obter mais informações sobre como migrar aplicativos de fluxo de trabalho de .NET 3.0 e 3.5 do .NET para usar a versão mais recente, consulte [diretrizes de migração](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).  
  
## <a name="workflow-activity-model"></a>Modelo de atividade de fluxo de trabalho  
 A atividade agora é a unidade base da criação de um fluxo de trabalho, em vez de usar as classes <xref:System.Workflow.Activities.SequentialWorkflowActivity> ou <xref:System.Workflow.Activities.StateMachineWorkflowActivity>. A classe <xref:System.Activities.Activity> fornece a abstração básica do comportamento de fluxo de trabalho. Os autores de atividade podem implementar o <xref:System.Activities.CodeActivity> para a funcionalidade básica de atividade personalizada ou <xref:System.Activities.NativeActivity> para a funcionalidade de atividade personalizada que usa a largura do tempo de execução. <xref:System.Activities.Activity> é uma classe usada por autores de atividade para expressar novos comportamentos de forma declarativa em termos de outros <xref:System.Activities.NativeActivity>, <xref:System.Activities.CodeActivity>, <xref:System.Activities.AsyncCodeActivity>, ou <xref:System.Activities.DynamicActivity> objetos, independentemente de estarem personalizado ou esteja incluída no [interno de atividade Biblioteca](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md).  
  
## <a name="rich-composite-activity-options"></a>Opções de atividades compostas avançadas  
 <xref:System.Activities.Statements.Flowchart> é uma nova atividade avançada de fluxo de controle que permite que os autores modelem loops arbitrários e ramificação condicional. <xref:System.Activities.Statements.Flowchart> fornece um modelo de programação orientada para evento que anteriormente somente podia ser implementada com <xref:System.Workflow.Activities.StateMachineWorkflowActivity>. Fluxos de trabalho de procedimentos aproveitam as novas atividades de controle de fluxo que modelam estruturas tradicionais de controle de fluxo, como <xref:System.Activities.Statements.TryCatch> e <xref:System.Activities.Statements.Switch%601>.  
  
## <a name="expanded-built-in-activity-library"></a>Biblioteca interna expandida da atividade  
 Os novos recursos da biblioteca de atividade incluem:  
  
-   Novas atividades de controle de fluxo, como, <xref:System.Activities.Statements.DoWhile>, <xref:System.Activities.Statements.Pick>, <xref:System.Activities.Statements.TryCatch>, <xref:System.Activities.Statements.ForEach%601>, <xref:System.Activities.Statements.Switch%601> e <xref:System.Activities.Statements.ParallelForEach%601>.  
  
-   Atividades para manipular dados de membro, como <xref:System.Activities.Statements.Assign> e atividades de coleção como <xref:System.Activities.Statements.AddToCollection%601>.  
  
-   Atividades para controlar transações, como <xref:System.Activities.Statements.TransactionScope> e <xref:System.Activities.Statements.Compensate>.  
  
-   Novas atividades de mensagem, como, <xref:System.ServiceModel.Activities.SendContent> e <xref:System.ServiceModel.Activities.ReceiveReply>.  
  
## <a name="explicit-activity-data-model"></a>Modelo de dados explícito de atividade  
 O [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] inclui novas opções para armazenar ou mover dados. Os dados podem ser armazenados em uma atividade usando <xref:System.Activities.Variable>. Ao mover dados dentro e fora de uma atividade, os tipos de argumento especializados são usados para determinar quais dados de direção estão movendo. Esses tipos são <xref:System.Activities.InArgument>, <xref:System.Activities.InOutArgument> e <xref:System.Activities.OutArgument>. Para obter mais informações, consulte [modelo de dados do Windows Workflow Foundation](../../../docs/framework/windows-workflow-foundation/data-model.md).  
  
## <a name="enhanced-hosting-persistence-and-tracking-options"></a>Hospedagem aprimorada, persistência e opções de rastreamento  
 O [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] contém os aprimoramentos de persistência como o seguinte:  
  
-   Há mais opções para executar fluxos de trabalho, inclusive <xref:System.ServiceModel.Activities.WorkflowServiceHost>, <xref:System.Activities.WorkflowApplication> e <xref:System.Activities.WorkflowInvoker>.  
  
-   Os dados do estado de fluxo de trabalho podem ser persistidos usando a atividade <xref:System.Activities.Statements.Persist>.  
  
-   Um host pode persistir um <xref:System.Activities.ActivityInstance> sem descarregá-lo.  
  
-   Um fluxo de trabalho pode especificar zonas de não persistência enquanto trabalham com dados que não podem ser persistidos, de modo que a persistência é adiada até que a zona de não persistência seja encerrada.  
  
-   As transações podem fluir em um fluxo de trabalho usando <xref:System.Activities.Statements.TransactionScope>.  
  
-   O rastreamento é obtido mais facilmente usando <xref:System.Activities.Tracking.TrackingParticipant>.  
  
-   O rastreamento para o log de eventos do sistema é fornecido com <xref:System.Activities.Tracking.EtwTrackingParticipant>.  
  
-   Retomar um fluxo de trabalho pendente é agora gerenciado usando um objeto <xref:System.Activities.Bookmark>.  
  
## <a name="easier-ability-to-extend-wf-designer-experience"></a>Maior capacidade de estender a experiência do WF Designer  
 O novo Designer de WF baseia-se no Windows Presentation Foundation (WPF) e fornece um modelo mais simples a ser usado ao rehosting o Designer do WF fora do Visual Studio e também oferece mecanismos mais fáceis para criar designers personalizados de atividade. Para obter mais informações, consulte [Personalizando a experiência de Design de fluxo de trabalho](../../../docs/framework/windows-workflow-foundation/customizing-the-workflow-design-experience.md).
