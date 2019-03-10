---
title: Criação de atividade de fluxo de trabalho usando a classe de atividades
ms.date: 03/30/2017
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
ms.openlocfilehash: abdabc46aa54e19d5a04c5b34d6d2b9be07488d6
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711857"
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a>Criação de atividade de fluxo de trabalho usando a classe de atividades
A maneira mais simples para criar uma atividade usando o Windows Workflow Foundation (WF) no [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] é criar uma classe que herda <xref:System.Activities.Activity> que cria a funcionalidade montando personalizado atividades ou atividades do [interno Biblioteca de atividade](net-framework-4-5-built-in-activity-library.md). Este tópico demonstra como criar uma atividade duas mensagens que grava no console.

### <a name="to-create-a-custom-activity-using-the-activity-designer"></a>Para criar uma atividade personalizado utilizando o designer de atividades

1.  Abra o Visual Studio 2012.

2.  Arquivo, Selecione Novo, Projeto. Selecione **Workflow 4.0** sob **Visual c#** no **tipos de projeto** janela e selecione o **v2010** nó. Selecione **biblioteca de atividades** na **modelos** janela. Nomeie o novo projeto HelloActivity.

3.  Abra a nova atividade.  Arraste uma atividade de <xref:System.Activities.Statements.Sequence> da caixa de ferramentas para a superfície de designer.

4.  Arraste uma atividade de <xref:System.Activities.Statements.WriteLine> na atividade de <xref:System.Activities.Statements.Sequence> . Insira `"Hello World"` (com aspas) para o **texto** campo.

5.  Arraste uma atividade de <xref:System.Activities.Statements.WriteLine> de segundo na atividade de <xref:System.Activities.Statements.Sequence> , abaixo da primeira. Insira `"Goodbye"` (com aspas) para o **texto** campo.
