---
title: Host de WorkflowApplication ReadLine
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f7b362be-cb42-40d7-b9ef-cfc4aed2455b
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1ba33dff4be8ae3e75ee4d1873feeb4d5e5944b7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="workflowapplication-readline-host"></a>Host de WorkflowApplication ReadLine
Este exemplo é um host genérica de ReadLine. Você pode carregar e executar qualquer fluxo de trabalho usando a atividade incluída de `ReadLine` (ou outras atividades como ele obtém dados de indexadores continuados com cadeias de caracteres). A saída de atividade ou de qualquer coisa de `WriteLine` gravação para a extensão de <xref:System.Activities.Statements.WriteLine.TextWriter%2A> está direcionada para a janela aeromoça. Quando uma instância estiver ocioso, os indicadores disponíveis para essa instância aparecem em uma caixa de combinação. Selecione um marcador, inserir texto, e pressione o botão do indexador de resumo continuam a execução de fluxo de trabalho. Você também pode cancelar, nulo, ou finalizar um fluxo de trabalho selecionado. Persistência está ativada por padrão – você pode fechar o host e trazer-lhe a voltar, e a lista de instância é preenchida com instâncias armazenadas na base de dados. O rastreamento é usado para produzir <xref:System.Activities.WorkflowApplication>- eventos de nível para o host com a opção adicionar controle detalhado a nível de atividade.  
  
## <a name="sample-details"></a>Detalhes de exemplo  
 Há duas camadas para este host: a exibição e gerente da instância. A exibição consiste nas classes de `HostView` e de `WorkflowApplicationInfo` . O padrão geral para este host é a classe de `HostView` exiba opções disponíveis para o usuário com base em objetos de `WorkflowApplicationInfo` que são mantidos bastante em sincronia com instâncias que representam. A camada do gerenciador de instância consiste na classe de `WorkflowApplicationManager` , que é o núcleo de todas as comunicações host, e a classe de `WorkflowDefinitionExtension` , que persiste a relação entre uma instância e a definição de programa foi iniciado com e algumas outras classes. Operações de controle de chamadas de `HostView` em `WorkflowApplicationManager`. Essas chamadas assíncronas são normalmente manter uma interface de usuário responde. Quando fazer chamadas assíncronas, `WorkflowApplicationManager` faz chamadas de novo na camada de exibição através de uma interface bem definido (`IHostView`). A classe de `HostView` distribui com mais freqüência essas chamadas de classe de `WorkflowApplicationManager` ao encadeamento de interface do usuário. Gravação de texto é feita aos objetos thread-safe de <xref:System.Activities.Statements.WriteLine.TextWriter%2A> fornecidos pela classe de `HostView` . A interface do usuário não é a única coisa que gerencia eventos. Os objetos de <xref:System.Activities.WorkflowApplication> também sinalizam quando `WorkflowApplicationManager` vão `Idle`, `Complete`, ou são `Aborted`, por exemplo. A classe de `WorkflowApplicationManager` sai do segmento do evento distribuir limpa ou atualizar o trabalho para o host.  
  
 A gravação do arquivo usado para iniciar <xref:System.Activities.WorkflowApplication> é facilitada pela classe de `WorkflowDefinitionExtension` . Implementa a interface de <xref:System.Activities.Persistence.PersistenceIOParticipant> para participar na persistência e persistir o caminho para a definição de fluxo de trabalho.  
  
 O método de `WorkflowApplicationManager.Load` usa o caminho armazenado para instanciar os programas de fluxo de trabalho necessários carregando objetos incompletas de <xref:System.Activities.WorkflowApplication> .  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1.  Este exemplo requer o SQL express para ser instalado. O SQL express vem com [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Abra um prompt de comando Visual Studio 2010.  
  
3.  Navegue para o diretório de exemplo (\ \ WF básico \ \ execução ControllingWorkflowApplications) e a CreateInstanceStore.cmd executado.  
  
4.  O script de CreateInstanceStore.cmd tentar criar o base de dados na instância padrão do SQL Server 2008 Express. Se você deseja instalar o base de dados em uma instância diferente, modifique o script para fazer isso.  
  
5.  Compile o projeto de WorkflowApplicationReadLineHost e executá-lo de linha de comando.  
  
6.  Depois de executar opcionalmente, você pode desativar a persistência ou sobre. Mais, você pode opcionalmente girar controlar detalhado da atividade ligado/desligado.  
  
7.  Pressione o botão de reticências ao lado de **executar** botão para procurar um fluxo de trabalho definido em um arquivo XAML  
  
     Dois exemplos podem ser localizados na pasta de SampleWorkflows. O exemplo de parallel1.xaml vai ociosa.  
  
8.  Depois que um exemplo é selecionado, pressione a **executar** botão.  
  
9. Se ou quando o fluxo de trabalho fica inativo, o **indicadores** caixa de combinação é preenchida com indicadores disponíveis.  
  
10. As opções são nesse momento retomar um marcador, cancelar, nulo, ou finalizar o fluxo de trabalho. Você também pode fechar o host e reinicie. Se a persistência é deixada em, as instâncias são descarregadas no desligamento e recarregados rapidamente iniciar anterior.  
  
     Para retomar um indicador, selecione o indicador desejado, digite um valor na caixa de texto ao lado da caixa de combinação e pressione **retomar indicador**.  
  
#### <a name="to-remove-the-instance-store-database"></a>Para remover o base de dados do armazenamento de instância  
  
1.  Abra um prompt de comando Visual Studio 2010.  
  
2.  Navegue para o diretório de exemplo (\ \ WF básico \ \ execução ControllingWorkflowApplications) e a RemoveInstanceStore.cmd executado.  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Execution\ControllingWorkflowApplications`