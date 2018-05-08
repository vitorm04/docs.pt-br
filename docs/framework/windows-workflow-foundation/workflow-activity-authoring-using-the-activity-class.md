---
title: Criação de atividade de fluxo de trabalho usando a classe de atividades
ms.date: 03/30/2017
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
ms.openlocfilehash: 040fe777e332efdfb296e6fb6565935f466ded71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a>Criação de atividade de fluxo de trabalho usando a classe de atividades
A maneira mais simples para criar uma atividade usando o Windows Workflow Foundation (WF) no [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] é criar uma classe que herda de <xref:System.Activities.Activity> que cria funcionalidade montando personalizado atividades ou atividades do [interno Biblioteca de atividades](../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md). Este tópico demonstra como criar uma atividade duas mensagens que grava no console.  
  
### <a name="to-create-a-custom-activity-using-the-activity-designer"></a>Para criar uma atividade personalizado utilizando o designer de atividades  
  
1.  Abra [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)].  
  
2.  Arquivo, Selecione Novo, Projeto. Selecione **Workflow 4.0** em **Visual C#** no **tipos de projeto** janela e selecione o **v2010** nó. Selecione **biblioteca de atividades** no **modelos** janela. Nomeie o novo projeto HelloActivity.  
  
3.  Abra a nova atividade.  Arraste uma atividade de <xref:System.Activities.Statements.Sequence> da caixa de ferramentas para a superfície de designer.  
  
4.  Arraste uma atividade de <xref:System.Activities.Statements.WriteLine> na atividade de <xref:System.Activities.Statements.Sequence> . Digite `"Hello World"` (entre aspas) para o **texto** campo.  
  
5.  Arraste uma atividade de <xref:System.Activities.Statements.WriteLine> de segundo na atividade de <xref:System.Activities.Statements.Sequence> , abaixo da primeira. Digite `"Goodbye"` (entre aspas) para o **texto** campo.
