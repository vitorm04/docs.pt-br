---
title: Criação de atividade de fluxo de trabalho usando a classe de atividades
ms.date: 03/30/2017
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
ms.openlocfilehash: 1bec10b6ae9fb43319cfb6acbf59133e1acca09c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770757"
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a>Criação de atividade de fluxo de trabalho usando a classe de atividades
A maneira mais simples para criar uma atividade usando o Windows Workflow Foundation (WF) no [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] é criar uma classe que herda <xref:System.Activities.Activity> que cria a funcionalidade montando personalizado atividades ou atividades do [interno Biblioteca de atividade](net-framework-4-5-built-in-activity-library.md). Este tópico demonstra como criar uma atividade duas mensagens que grava no console.

### <a name="to-create-a-custom-activity-using-the-activity-designer"></a>Para criar uma atividade personalizado utilizando o designer de atividades

1. Abra o Visual Studio 2012.

2. Arquivo, Selecione Novo, Projeto. Selecione **Workflow 4.0** sob **Visual c#** no **tipos de projeto** janela e selecione o **v2010** nó. Selecione **biblioteca de atividades** na **modelos** janela. Nomeie o novo projeto HelloActivity.

3. Abra a nova atividade.  Arraste uma atividade de <xref:System.Activities.Statements.Sequence> da caixa de ferramentas para a superfície de designer.

4. Arraste uma atividade de <xref:System.Activities.Statements.WriteLine> na atividade de <xref:System.Activities.Statements.Sequence> . Insira `"Hello World"` (com aspas) para o **texto** campo.

5. Arraste uma atividade de <xref:System.Activities.Statements.WriteLine> de segundo na atividade de <xref:System.Activities.Statements.Sequence> , abaixo da primeira. Insira `"Goodbye"` (com aspas) para o **texto** campo.
