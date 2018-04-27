---
title: Depurando fluxos de trabalho
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b23b4814-ebb1-4c51-b7a9-469f4da7a96d
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 866fe3ebcec295b57444f937b3b6fd6677bfe0f4
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="debugging-workflows"></a>Depurando fluxos de trabalho
[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] oferece várias opções para depurar fluxos de trabalho em execução do ambiente de desenvolvimento. Fluxos de trabalho podem ser depurado no designer, em XAML, e no código.  
  
## <a name="debugging-in-the-workflow-designer"></a>Depuração no Designer de Fluxo de Trabalho  
 Pontos de interrupção podem ser definidos em atividades no designer de fluxo de trabalho o realce a atividade e pressionando **F9** ou usando o menu de contexto da atividade. A execução de fluxo de trabalho interrompe então quando o host de fluxo de trabalho é executado no modo de depuração. Na seguinte captura de tela, a execução de fluxo de trabalho é pausada em um ponto de interrupção. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Depurando fluxos de trabalho com o Designer de fluxo de trabalho](/visualstudio/workflow-designer/debugging-workflows-with-the-workflow-designer).  
  
## <a name="debugging-in-xaml"></a>Depuração em XAML  
 Se um fluxo de trabalho pausou em um ponto de interrupção no designer, o fluxo de trabalho também pode ser depurado em XAML. Para exibir o ponto de execução em XAML, selecione **modo de exibição XAML** no designer de fluxo de trabalho quando a execução do fluxo de trabalho está em pausa. A depuração pode ser trocada de volta para o designer pela abertura o fluxo de trabalho no designer do gerenciador de solução. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Como: depurar o XAML e o Designer de fluxo de trabalho](/visualstudio/workflow-designer/how-to-debug-xaml-with-the-workflow-designer).  
  
## <a name="debugging-in-code"></a>Depuração em código  
 Os pontos de interrupção de código podem ser usados em [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] da mesma forma que podem ser usados em outros aplicativos obrigatórios. Clique na margem esquerda do painel de código para criar um ponto de interrupção do código, ou pressione **F9** para colocar um ponto de interrupção na posição do cursor.  
  
## <a name="attaching-to-a-workflow-process"></a>Anexar a um processo de fluxo de trabalho  
 Fluxo de trabalho que depurar também suporta usando a infraestrutura do Visual Studio para anexar a um processo. Isso permite que o autor de fluxo de trabalho para depurar um execução de fluxo de trabalho em um ambiente diferente de host como Serviços de Informações da Internet (IIS) 7,0.  
  
## <a name="remote-debugging"></a>Depuração remota  
 Depuração remota do Windows Workflow Foundation (WF) funciona da mesma forma a depuração remota para outros componentes do Visual Studio. Para obter informações sobre como usar a depuração remota, consulte [como: Ativar depuração remota](http://go.microsoft.com/fwlink/?LinkId=196257).  
  
> [!NOTE]
>  Se o aplicativo de fluxo de trabalho tem como alvo o x86 arquitetura e está hospedado em um computador executando um sistema operacional de 64 bits, a depuração remota não funcionará a menos que o Visual Studio está instalado no computador remoto ou o destino para o aplicativo de fluxo de trabalho é alterado para **Qualquer CPU**.  
  
## <a name="extending-the-workflow-debugging-service"></a>Estendendo o serviço de depuração de fluxo de trabalho  
 O serviço do depurador de fluxo de trabalho WF agora é público e pode ser usado para criar aplicativos personalizados como o monitoramento, a simulação, e depuração em um designer novamente hospedado. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] o tópico de <xref:System.Activities.Presentation.Debug.DebuggerService> .
