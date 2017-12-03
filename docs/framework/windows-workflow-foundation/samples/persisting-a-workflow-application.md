---
title: Gravando um aplicativo de fluxo de trabalho
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: abcff14c-f047-4195-ba26-d27f4a82c24e
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7a3cdc10b7ed801b6a9b2dcb62dae5d5d6746c66
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="persisting-a-workflow-application"></a>Gravando um aplicativo de fluxo de trabalho
Este exemplo demonstra como executar <xref:System.Activities.WorkflowApplication>, descarrega-o quando vai ociosa, e recarregar-lo para continuar a execução.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 <xref:System.Activities.WorkflowApplication> é um host para uma única instância de fluxo de trabalho que fornece uma interface simples e permite várias de mais comuns de hospedagem. Um cenário é fluxos de trabalho longo facilitados pela persistência. O controle do host de persistência é executado chamando-se uma operação de persistência em <xref:System.Activities.WorkflowApplication>, ou tratando um evento de <xref:System.Activities.WorkflowApplication> e indicando que <xref:System.Activities.WorkflowApplication> deve manter.  
  
 O fluxo de trabalho de exemplo é uma atividade de <xref:System.Activities.Statements.WriteLine> que solicitam o usuário para seu nome, uma atividade de `ReadLine` para receber o nome como entrada com a ressunção de <xref:System.Activities.Bookmark>, e outro <xref:System.Activities.Statements.WriteLine> para ecoar uma saudação de volta para o usuário. Quando um fluxo de trabalho está aguardando entrada, este fornece um ponto natural para persistência. Isso é freqüentemente conhecido como um ponto de <xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent.Idle> . <xref:System.Activities.WorkflowApplication> gerencie o evento de <xref:System.Workflow.Runtime.Tracking.TrackingWorkflowEvent.Idle> sempre que o programa de fluxo de trabalho pode ser persistido, está aguardando em uma ressunção do indexador, e nenhum outro trabalho está sendo executado. No fluxo de trabalho deste exemplo, o ponto vem imediatamente após a atividade de `ReadLine` começa a ser executado.  
  
 Um <xref:System.Activities.WorkflowApplication> está configurado para executar a persistência com um <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore`. Este exemplo usa <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>. O <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore` deve ser atribuído para o <xref:System.Activities.WorkflowApplication.InstanceStore%2A> propriedade antes do <xref:System.Activities.WorkflowApplication> é executado.  
  
 O exemplo adiciona um manipulador para o evento de <xref:System.Activities.WorkflowApplication.PersistableIdle%2A> . O manipulador para este evento indica que o <xref:System.Activities.WorkflowApplication> deve fazer retornando <xref:System.Activities.PersistableIdleAction>. Quando <xref:System.Activities.PersistableIdleAction.Unload> é retornado, <xref:System.Activities.WorkflowApplication> é descarregado.  
  
 O exemplo então aceita entrada do usuário e carrega o fluxo de trabalho mantido em novo <xref:System.Activities.WorkflowApplication>. Ele faz isso criando um novo <xref:System.Activities.WorkflowApplication>, recriando o <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore`e associar os eventos descarregados e concluídos para a instância e, em seguida, chamar <xref:System.Activities.WorkflowApplication.Load%2A> com o identificador da instância de fluxo de trabalho de destino. A instância é adquirida uma vez, o indexador de atividade de `ReadLine` é continuada. O fluxo de trabalho continua a execução de dentro de atividade de `ReadLine` e execute-a para a conclusão. Quando o fluxo de trabalho for concluída e descarrega, o <!--zz <xref:System.Runtime.Persistence.InstanceStore> --> `System.Runtime.Persistence.InstanceStore` é chamado pela última vez para excluir o fluxo de trabalho.  
  
#### <a name="to-use-this-sample"></a>Para usar este exemplo  
  
1.  Abra um prompt de comando do [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
     Este exemplo requer o SQL Server Express edition, que é instalado por padrão com [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Navegue para o diretório de exemplo (\ \ WF básico persistência InstancePersistence \ \ \ CS) e a CreateInstanceStore.cmd executado.  
  
    > [!CAUTION]
    >  O script de CreateInstanceStore.cmd tentar criar o base de dados na instância padrão do SQL Server 2008 Express. Se você deseja instalar o base de dados em uma instância diferente, modifique o script para fazer isso.  
  
3.  Usando [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], abra o arquivo de solução de Persistence.sln e pressione CTRL+SHIFT+B para compilá-lo.  
  
    > [!CAUTION]
    >  Se você instalou o base de dados em uma instância não padrão do SQL Server, atualizar a cadeia de conexão no código antes de criar a solução.  
  
4.  Executar o exemplo com privilégios de administrador, navegue até o diretório do projeto bin (\WF\Basic\Persistence\InstancePersistence\bin\Debug) em [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], clicando duas vezes Workflow.exe e selecionando **executar como administrador**.  
  
#### <a name="to-remove-the-instance-store-database"></a>Para remover o base de dados do armazenamento de instância  
  
1.  Abra um prompt de comando do [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Navegue para o diretório de exemplo e o RemoveInstanceStore.cmd executado.  
  
> [!IMPORTANT]
>  Os exemplos podem mais ser instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Persistence\InstancePersistence`  
  
## <a name="see-also"></a>Consulte também  
 [Exemplos de persistência e hospedagem de AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
