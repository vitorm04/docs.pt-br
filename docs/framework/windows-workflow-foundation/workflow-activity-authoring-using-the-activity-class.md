---
title: "Criação de atividade de fluxo de trabalho usando a classe de atividades"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 94433d398f662a96bf046603574ad881128a2081
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a>Criação de atividade de fluxo de trabalho usando a classe de atividades
A maneira mais simples para criar uma atividade usando [!INCLUDE[wf](../../../includes/wf-md.md)] na [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] é criar uma classe que herda de <xref:System.Activities.Activity> que cria funcionalidade montando personalizado atividades ou atividades do [biblioteca de atividades internas ](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md). Este tópico demonstra como criar uma atividade duas mensagens que grava no console.  
  
### <a name="to-create-a-custom-activity-using-the-activity-designer"></a>Para criar uma atividade personalizado utilizando o designer de atividades  
  
1.  Abra [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
2.  Arquivo, Selecione Novo, Projeto. Selecione **Workflow 4.0** em **Visual C#** no **tipos de projeto** janela e selecione o **v2010** nó. Selecione **biblioteca de atividades** no **modelos** janela. Nomeie o novo projeto HelloActivity.  
  
3.  Abra a nova atividade.  Arraste uma atividade de <xref:System.Activities.Statements.Sequence> da caixa de ferramentas para a superfície de designer.  
  
4.  Arraste uma atividade de <xref:System.Activities.Statements.WriteLine> na atividade de <xref:System.Activities.Statements.Sequence> . Digite `"Hello World"` (entre aspas) para o **texto** campo.  
  
5.  Arraste uma atividade de <xref:System.Activities.Statements.WriteLine> de segundo na atividade de <xref:System.Activities.Statements.Sequence> , abaixo da primeira. Digite `"Goodbye"` (entre aspas) para o **texto** campo.
